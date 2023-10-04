## Add border to active tab:
1. Edit the `settings.json` for the user. Press `F1` to find it.
2. Add the following code to the bottom of the `settings.json`
```json
"workbench.colorCustomizations": {
        "tab.activeBorder": "#0cf388"
}
```
for theme specific:
```json
"workbench.colorCustomizations": {       
    "[One Dark Pro]": {                  
        "tab.activeBorder": "#0cf388"
    }
}
```
