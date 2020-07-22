# Visual Studio Code - settings and extensions

## Settings

@2020-07-22

| type              | method                                            |
|:------------------|:--------------------------------------------------|
| VSCode            | Use extension: Code Settings Sync                 |
| VSCode Insider    | Use [Preferences Sync][ref-vscode-settings-sync]  |

[ref-vscode-settings-sync]:https://code.visualstudio.com/docs/editor/settings-sync


## Extensions

If you use INSIDER version.
`code-insiders` instead in `code`.


### Windows

```PS:Export
# Export
code --list-extensions > vscode-extensions.txt
```

```PS:Import
# Import
get-content vscode-extensions.txt | % { code --install-extension $_ }
```

### Linux

```sh:Export
# Export
code --list-extensions | sed -e 's/^/code --install-extension /' > force-install-vscode-extensions.sh
```

```sh:Import
# Import
bash force-install-vscode-extensions.sh
```

