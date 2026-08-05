# language-jass

A TextMate grammar for **JASS**, the original scripting language of Warcraft III.

- **Try it in the browser: [drake53.github.io/language-jass](https://drake53.github.io/language-jass/)** — a live highlighter that tokenises with the same engine VS Code uses, against the grammar in this repository. Type, paste, or drop a `.j`/`.ai`/`.jass` file, and switch to *Inspect* to see the scope stack of any token.
- Scope name: `source.jass`
- Grammar: [`syntaxes/jass.tmLanguage.json`](syntaxes/jass.tmLanguage.json)
- Editor configuration: [`language-configuration.json`](language-configuration.json)

The grammar highlights comments, every literal form (strings, character and FourCC literals, decimal/octal/hex/real numbers), declarations, statements, operators, and keywords, and flags invalid tokens.
It works directly as a VS Code extension (see below).
Registering it with [GitHub Linguist][linguist], for syntax highlighting on GitHub itself, is proposed in [linguist#8096][linguist-pr] and waiting for approval.

## JASS, not vJASS

The grammar targets **original JASS only** — the language the game accepts and the World Editor emits.
[vJASS][vjass]/JassHelper, Zinc, Wurst and C-style preprocessor dialects are deliberately out of scope.
vJASS is not a strict superset of JASS (for example, `debug` applies to the entire following statement in JASS, but only to its own line in vJASS), so the two are best served by separate grammars.

## Working on the extension

The repository is a complete VS Code extension — [`package.json`](package.json) declares the language and grammar, and there is no build step.

- **Run it**: open the folder in VS Code and press <kbd>F5</kbd> (or run `code --extensionDevelopmentPath="$PWD"`). An Extension Development Host window opens with the extension loaded; open any `.j`, `.ai` or `.jass` file to see the highlighting.
- **Inspect highlighting**: run *Developer: Inspect Editor Tokens and Scopes* from the Command Palette and hover a token to see its scope stack and the theme rule that coloured it. After editing the grammar, run *Developer: Reload Window* in the host window to pick up the change.
- **Install locally**: package with `npx @vscode/vsce package` and install the resulting `.vsix` through `code --install-extension language-jass-<version>.vsix` (or *Extensions: Install from VSIX…* in the Extensions view).
- **The browser highlighter**: [`syntax-highlighter.html`](syntax-highlighter.html) needs the grammar over HTTP, so serve the repository root (`python3 -m http.server`) and open <http://localhost:8000/syntax-highlighter.html>. Opened straight from disk it falls back to a *load grammar…* file picker. Pushing a change to it or to the grammar redeploys the [live page](https://drake53.github.io/language-jass/) via [`.github/workflows/pages.yml`](.github/workflows/pages.yml).

## Licence

[MIT](LICENSE) — Copyright (c) Drake53 and Contributors.

[linguist]: https://github.com/github-linguist/linguist
[linguist-pr]: https://github.com/github-linguist/linguist/pull/8096
[vjass]: https://www.hiveworkshop.com/threads/introduction-to-vjass.238281/
