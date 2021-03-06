# JetBrains-language-plugins
Documentation and examples of our experience learning to build language-specific plugins for JetBrains IDEs

## Top Level Structure 

* Intro
  * Goals
  * Sources and credits (brief version)
  
* Projects

* Languages 

* FAQ

* License & Credits (full version)

## Intro
These projects are from a Winter 2019 Seminar Class at University of Oregon. Our intent was to try building plugins for JetBrains IDEs, including support for new languages. Our approach was to have individuals or small groups work on different small projects.

### Goals
Goals for the quarter are listed below:
1. Use IntelliJ IDEA to create plugins
2. Use Gradle for building plugins and learn more about how it works as a build tool
3. Work with Grammar-Kit and the PSI-Viewer, and learn about specific features
4. Create at least one working plugin supporting a new language
5. Determine what areas in the above processes are lacking documentation
6. Share our results including the problems that we ran into in order to help others in the future

### Sources and Credits
* [Grammar-Kit](https://github.com/JetBrains/Grammar-Kit), [PSI-Viewer](https://plugins.jetbrains.com/plugin/227-psiviewer)

## Projects

| Name          | Description           | Status  |
| ------------- |-----------------------| -------:|
| Simple Language Plugin| The simple language plugin subdirectory contains an implementation of a minimal plugin using the Gradle build system. The plugin includes syntax hightlighting, custom file extension support, as well as custom icons associated with file types. See https://github.com/Nosler/simple_language_plugin/blob/1d05335e23be63e18ec7e44cd4a140112d98c675/README.md for more.  |   complete   |
| [dl-plugin](https://github.com/zachsully/dl-plugin) | A plugin for the [DL](https://github.com/zachsully/dl): a Dual Language for computing with algebraic data types and coalgebraic codata types. | see plugin repo for features |
| Quack      | description              |   complete   |
| Quilt | description              |    *incomplete*   |
| Docstring Generator | Generate a python Docstring              |    *incomplete*   |
| Eidos | description              |    *incomplete*   |

## Languages
Please see this [readme](https://github.com/uo-ide-seminar/JetBrains-language-plugins/blob/master/Languages.md) for more information on the language plugins specifically.

## FAQ
We ran into many problems and found that a lot of tutorials lacked adequate documentation. We tried to summarize some of those common issues in the following [FAQ](https://github.com/uo-ide-seminar/JetBrains-language-plugins/blob/master/FAQ.md)
