# language-jass

A TextMate grammar for **JASS**, the original scripting language of Warcraft III.

- Scope name: `source.jass`
- Grammar: [`syntaxes/jass.tmLanguage.json`](syntaxes/jass.tmLanguage.json)
- Editor configuration: [`language-configuration.json`](language-configuration.json)

The grammar highlights comments, every literal form (strings, character and FourCC literals, decimal/octal/hex/real numbers), declarations, statements, operators, and keywords, and flags invalid tokens.
It works directly as a VS Code extension (see below).
Registering it with [GitHub Linguist][linguist], for syntax highlighting on GitHub itself, is planned but still needs a PR.

## JASS, not vJASS

The grammar targets **original JASS only** — the language the game accepts and the World Editor emits.
[vJASS][vjass]/JassHelper, Zinc, Wurst and C-style preprocessor dialects are deliberately out of scope.
vJASS is not a strict superset of JASS (for example, `debug` applies to the entire following statement in JASS, but only to its own line in vJASS), so the two are best served by separate grammars.

## Working on the extension

The repository is a complete VS Code extension — [`package.json`](package.json) declares the language and grammar, and there is no build step.

- **Run it**: open the folder in VS Code and press <kbd>F5</kbd> (or run `code --extensionDevelopmentPath="$PWD"`). An Extension Development Host window opens with the extension loaded; open any `.j`, `.ai` or `.jass` file to see the highlighting.
- **Inspect highlighting**: run *Developer: Inspect Editor Tokens and Scopes* from the Command Palette and hover a token to see its scope stack and the theme rule that coloured it. After editing the grammar, run *Developer: Reload Window* in the host window to pick up the change.
- **Install locally**: package with `npx @vscode/vsce package` and install the resulting `.vsix` through `code --install-extension language-jass-<version>.vsix` (or *Extensions: Install from VSIX…* in the Extensions view).

## Licence

[MIT](LICENSE) — Copyright (c) Drake53 and Contributors.

[linguist]: https://github.com/github-linguist/linguist
[vjass]: https://www.hiveworkshop.com/threads/introduction-to-vjass.238281/
