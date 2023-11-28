Changelog
=========

[0.1.0] - 2023-11-28
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

- Rename module to `find_imports`
- Rename `get` to `parse_file`
- Rename `parse` to `parse_source`, and allow passing a `filename` argument
  through to `ast.parse` for error messages
- CLI more permissive about files it can't parse; reports the error and moves
  on, and reports the total number of errors at the end.

### Fixed

- Don't error out on `from . import x` statements
