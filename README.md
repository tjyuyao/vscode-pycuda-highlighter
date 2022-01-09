# PyCUDA highlighter for VSCode

## Highlight CUDA Docstring

Use `//cuda` and `//!cuda` to specify a docstring as embedded cuda, then the highlight will work. For example:

<img src="https://github.com/tjyuyao/vscode-pycuda-highlighter/raw/master/demo.png" alt="Highlight CUDA Docstring">


## Customize text color

The text color can be customized by adding following configs to the user `settings.json` file (or default is the docstring color of python).

```json
    "editor.tokenColorCustomizations": {
      "textMateRules": [
          {
              "scope": "meta.embedded.block.cuda-cpp",
              "settings": {
                  "foreground": "#080644"
              }
          }
      ]
    },
```

## Author

Copyright (c) 2022, Yuyao Huang (huangyuyao at outlook dot com), currently a PhD candidate in Tongji University, Shanghai.
