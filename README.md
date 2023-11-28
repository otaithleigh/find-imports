## Installation & Usage

``` sh
$ pip install find-imports
$ python -m find_imports ...
```

Or use the CLI through [`pipx`](https://pypa.github.io/pipx/):

```
$ pipx run find-imports --help
Usage: find-imports [OPTIONS] [PATHS]...

  Search Python source file(s) for imported modules.

Options:
  -i, --ignore MODULE             Ignore a module and all its submodules. This
                                  option may be given multiple times.
  -R, --ignore-relative / --no-ignore-relative
                                  Ignore relative imports.
  -S, --ignore-stdlib / --no-ignore-stdlib
                                  Ignore standard library modules.
  -f, --show-files / --no-show-files
                                  For each import, list the files that import
                                  it.
  --version                       Show the version and exit.
  --help                          Show this message and exit.
```

## Examples

### Library

Setup:

``` pycon
>>> source = """
... import ast
... import click
... from .base import pkgfunc
... 
... def lazy_import():
...     import math
...     return math.sin(20.0)
... """
>>> with open('file.py', 'w') as f:
...     f.write(source)
```

Parse imports from a file:

``` pycon
>>> import find_imports
>>> find_imports.parse_file('file.py')
['math', 'ast', 'click', '.base']
```

Parse imports from a string:

``` pycon
>>> find_imports.parse_source(source)
['math', 'ast', 'click', '.base']
```

### Command-line interface

Exclude standard library modules:

``` sh
$ python -m find_imports --ignore-stdlib file.py
click
```

Exclude relative imports:

``` sh
$ python -m find_imports --ignore-relative file.py
ast
click
math
```

Search a directory:

``` sh
$ find . -type f -name '*.py' | xargs python -m find_imports
```

## Prior work

Based on [`list-imports`](https://github.com/andrewp-as-is/list-imports.py).
