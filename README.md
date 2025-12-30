# ALGO — VS Code language support (local)

A lightweight, local Visual Studio Code language support package for the `.algo` notation. This project provides a TextMate grammar for syntax highlighting, a language configuration for indentation and comments, and a small collection of editor snippets.

## Features

- Syntax highlighting for core keywords: `procedure`, `if`, `then`, `else`, `while`, `for`, `do`, `return`, `expand`, `record`, `type`, `end`.
- Record definitions with fields and types.
- Type aliases for arrays and other constructs.
- Assignment arrows: `←` and `<-`.
- Comparison operators: `=`, `≠` / `!=`.
- Constants such as `NIL` and `∞`.
- Line comments using `//`.
- Basic snippets for procedures and control blocks.

## Quick install (local)

1. From the extension project folder, build a VSIX package:

```powershell
npx -y @vscode/vsce package
```

2. Install the generated VSIX locally (replace the filename as produced):

```powershell
code --install-extension ./algo-language-0.0.1.vsix
```

3. Restart VS Code and open a file with the `.algo` extension to see highlighting.

### Development and testing

- To test without installing the VSIX, open the project in VS Code and press `F5` to launch an Extension Development Host. Open a `.algo` file in that host to see syntax highlighting.
- Workspace snippets and editor settings can be used for convenience, but full syntax highlighting requires the grammar provided by this extension.

## Usage

- Indentation: lines ending with `:` are treated as block starters; pressing Enter increases indentation according to the language configuration.
- Comments: use `//` for single-line comments.
- Snippets: trigger snippets by typing the snippet prefix (for example, `proc`) and pressing `Tab`.

Example `.algo` code:

```algo
procedure Search(head, def):
    p <- head.next
    while p ≠ null and p.elem ≠ def:
        p <- p.next
    return p

record Node:
    data: any
    parent: int     // 0 for root
end

type ParentArray = array[1..n] of Node
```

## Extending the grammar and snippets

- Edit `syntaxes/algo.tmLanguage.json` to add or refine token patterns.
- Edit `language-configuration.json` to adjust indentation and comment behavior.
- Add or export snippets by updating `.vscode/snippets/algo.json` or adding `contributes.snippets` in `package.json`.

## Troubleshooting

- If highlighting does not appear after installing the VSIX, restart VS Code.
- Use `Developer: Inspect Editor Tokens and Scopes` to verify token scopes (should show `source.algo`).
- If `code` is not available on your PATH, install the `code` command from VS Code's Command Palette (`Shell Command: Install 'code' command in PATH`) or use the appropriate method for your platform.

## Contributing & roadmap

Contributions are welcome. Possible improvements:

- Add more language keywords and constructs.
- Refine token patterns for numbers, strings, and complex expressions.
- Add richer snippets or simple completions.
- Publish a packaged extension for wider reuse.

If you'd like any of these, open an issue or submit a PR with the desired changes.

---

This file was written to focus solely on the `vscode-algo` extension and to avoid any user-specific filesystem references.
