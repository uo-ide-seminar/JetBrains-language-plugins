# Language Plugins
---

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
