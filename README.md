# `MindustryPluginTemplate`

[Mindustry](https://github.com/Anuken/Mindustry) Java plugin template, complete with syntax downgrader integration, works for both Android and PC.

## Using

Before going into using this template, be aware that a fair amount of Java knowledge and Git *(GitHub Desktop is fine, but `git` CLI is a million times better)* is **highly beneficial**. Going in blind isn't impossible, but you'll face a lot of problems. Not that people on [the Discord](https://discord.gg/mindustry) won't help, though, so be communicative!

1. Install JDK 17 or higher. Plain or terminal-based code editors are **completely *not* recommended!** Use an IDE like [IntelliJ IDEA](https://www.jetbrains.com/idea/download/); there are free Community Edition releases available, just scroll down a bit.
2. Click the `Use this template` button and create your repository.
3. Clone a local copy of the repository.

> [!IMPORTANT]
> A **local copy** is *not* a mere ZIP archive you obtain by downloading. This is where the Git knowledge comes to play. If you have GitHub CLI or GitHub Desktop installed, the site should provide instructions on how to use either, under the `<> Code` menu.
>
> `Download ZIP` is **not** a proper way to clone your repository.

4. Refactor namings to your preferences. The template is designed in such a way that this step should only require you to modify:
   - `gradle.properties`, the "Project configurations" section.
   - `plugin.json`, which is the entire metadata of your plugin.
   - `src/` folder and its contents, which is where your Java source files are stored. Rename folders, package, and class names as you prefer. Note that the main plugin class' full name *(package + class)* must correspond to the `main` property in `plugin.json`.
   - `.github/workflows/ci.yml`, which is the automated Continuous Integration that runs on your GitHub repository everytime you push a commit. You should only edit the last 2 lines about `name` and `path`.

5. Run `gradlew jar` *(or `./gradlew jar` on Mac/Linux)* on your terminal to build the plugin.

## Adding Dependencies

**Never** use `implementation` for Mindustry/Arc groups and their submodules. There's a reason they're `compileOnly`; they're only present in compilation and excluded from the final JARs, as on runtime they're resolved from the game instance itself. Other JAR-mod dependencies must also use `compileOnly`. Only ever use `implementation` for external Java libraries that must be bundled with your mod.

## License

The project is licensed under [GNU GPL v3](/LICENSE).
