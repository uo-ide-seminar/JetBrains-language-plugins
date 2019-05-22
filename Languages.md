# Language Plugins

Of the plugins we explored, a number of them were adding custom language
support: [dl-plugin](https://github.com/zachsully/dl-plugin) and
[a modification of the simple-language-plugin](https://github.com/Nosler/cis407-W19),
and more **ADD Quack and Quilt links**. Further documentation can be found in
those repositories.

To aid us in the creation of our plugins, we followed the custom language
support
[tutorial](https://www.jetbrains.org/intellij/sdk/docs/tutorials/custom_language_support_tutorial.html).
We relied on the Grammar-Kit [plugin](https://github.com/JetBrains/Grammar-Kit)
to easily produce lexers and parsers for our languages. The
gradle-intellij-plugin
[plugin](https://github.com/JetBrains/gradle-intellij-plugin) (though not
mentioned in the tutorial) easied the creation of a buildable, minimal language
plugin.

## Grammar-Kit and PEG Grammars

Grammar-Kit comes with some documentation on pinning, recoverWhile, and handling
left-recursion in their
[HOW-TO guide](https://github.com/JetBrains/Grammar-Kit/blob/master/HOWTO.md).

### On pin and recoverWhile

### Left-recursive Woes

Unlike other parser generators like yacc and Happy, Grammar-Kits' PEG grammars
do not support left recursion. For instance, we may want to write the following
grammar for terms in our language.

```
Term ::= Term '+' Term           -- addition
       | Term1

Term1 ::= Term TermAtomic        -- function application
        | TermAtomic

TermAtomic ::= Num
             | Var
             | '(' Term ')'
```

Because the grammar contains left recursion, we have to massage the grammar to
get it in a non-left-recursive form. Using the
[HOW-TO guide](https://github.com/JetBrains/Grammar-Kit/blob/master/HOWTO.md),
we can keep the left-recursion with a trick.

```
{
  extends(".*Term")=Term
}

Term ::= add_Term
       | app_Term
       | Term_atom_group

private Term_atom_group ::= num_Term
                          | var_Term
                          | paren_Term

add_Term     ::= Term '+' Term
app_Term     ::= Term Var
num_Term     ::= Num
var_Term     ::= Var
paren_Term   ::= '(' Term ')'
```

We break the each production into its own rule and list the order in which they
are tried in the top level production. *Essential* in this technique is the line
in the PEG preamble `extends(".*Term")=Term`, which says that each rule whose
name ends in "Term" will be a subtype of the top level class "Term".

Unfortunately this trick does not work with all syntactic forms. We found that
the application form found in many ML descendant functional programming
languages does not work for this trick, that is `x y` where `x` is a function
begin applied to `y` is still rejected by the generator. As we see in the
example above, we had to limit applications to a non-recursive element in order
for the Grammar-Kit to accept our grammar. This means that plugins for the
popular functional languages Ocaml and Haskell will need to write this part of
the parser themselves.

## Running Projects with Command Line Tools

It's likely that our custom language already has a compiler or interpreter that
we can call from the command line. Configuring our plugin so that Intellij can
run our code involves setting up a a command configuration and a program
runner. The command configuration is used to specify the details of calling the
compiler, e.g. setting compiler flags. The programmer runner will take a command
configuration and run it in some manner.

Intellij provides some documentation for setting up command configurations and
runners
[Run Configuration Docs](http://www.jetbrains.org/intellij/sdk/docs/basics/run_configurations.html). Unfortunately,
they do not capture the minimum amount of code that we need to add to our plugin
to get our custom language running. For extra examples, we found that looking at
other plugins for Intellij was helpful. There is a convention of storing these
program runners and configurations in a `runconfig` subdirectory of the plugin.

Most plugins that support running projects with commandline tools have the
following two additions to their `plugin.xml` file:

```
<extensions defaultExtensionNs="com.intellij">
    ...
    <configurationType implementation="ConfigurationTypeImplementation"/>
    <programRunner implementation="ProgramRunnerImplementation"/>
</extensions>
```

### Run Configurations

### Program Runners
