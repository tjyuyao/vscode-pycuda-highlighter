# PyCUDA highlighter for VSCode

## Highlight CUDA Docstring

Use `//cuda` and `//!cuda` to specify a docstring as embedded cuda, then the highlight will work. For example:

```python
import pycuda.driver as drv
import pycuda.tools
import pycuda.autoinit
import numpy
import numpy.linalg as la
from pycuda.compiler import SourceModule

mod = SourceModule("""
//cuda
__global__ void multiply_them(float *dest, float *a, float *b)
{
  const int i = threadIdx.x;
  dest[i] = a[i] * b[i];
}
//!cuda
""")

multiply_them = mod.get_function("multiply_them")

a = numpy.random.randn(400).astype(numpy.float32)
b = numpy.random.randn(400).astype(numpy.float32)

dest = numpy.zeros_like(a)
multiply_them(
        drv.Out(dest), drv.In(a), drv.In(b),
        block=(400,1,1))

print(dest-a*b)
```

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
