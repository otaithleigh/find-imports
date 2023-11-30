Changelog
=========

[0.1.2] - 2023-11-29
--------------------

### Fixed

- Detect Python source file encoding, falling back to UTF-8. Fixes parse errors
  on Windows, where the default encoding for `open()` is cp1252 if not in UTF-8
  mode.


[0.1.1] - 2023-11-29
--------------------

Initial release. Changes from `list-imports`:

### Added

- Pass directories to the CLI directly
- See which files are importing which modules with `--show-files`/`-f`
- Filter out standard library modules with `--ignore-stdlib`/`-S`
- Filter out relative imports with `--ignore-relative`/`-R`
- Filter out selected modules (and their submodules) with
  `--ignore MODULE`/`-i MODULE`

### Changed

- Rename module to `ls_imports`
- Rename `get` to `parse_file`
- Rename `parse` to `parse_source`, and allow passing a `filename` argument
  through to `ast.parse` for error messages
- CLI more permissive about files it can't parse; reports the error and moves
  on, and reports the total number of errors at the end.

### Fixed

- Don't error out on `from . import x` statements
