# FAQ


### What versions of software did we use? (Updated March 2019)

IntelliJ Community Edition 2016-2018, Java SDK 1.8, Gradle 5.2.1

### Where is the local Gradle distribution?

When installing Gradle with Homebrew (on Mac) the files are placed in /usr/local/Cellar/gradle/5.2.1 (found at root level using "ls -a").
IntelliJ can find the Gradle files easier if you move them to your user folder (on Mac). If you move Gradle to documents, for example, then this will work in the IntelliJ setup for "local Gradle distribution": /Users/insert_your_username/Documents/gradle/libexec. 

### How did we produce gradle files for creating plugins?

The gradle-intellij-plugin
[plugin](https://github.com/JetBrains/gradle-intellij-plugin) easied the
creation of a buildable, minimal plugins.

### How did we handle left recursion when making sure our BNF file worked? 

See the [languages](https://github.com/uo-ide-seminar/JetBrains-language-plugins/blob/master/Languages.md) section for more information on this.

