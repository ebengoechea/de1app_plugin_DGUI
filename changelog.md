# Changelog - "Describe GUI" Decent DE1app plugin

Format based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

## [1.03] - [Unreleased]
### Added
- New proc `ensure_size` allows fixing the size after the first time the widget is painted. Useful for text-based 
widgets like entry or listbox whose size can only be defined in number of characters, whereas ensure_size lets us use
pixel weights and avoid collisions with other widgets when the font is changed.

### Changed
- All 3 pages NUME, IS & TXT now use `ensure_size` as needed, and also ensure necessary redrawings are only done
per page, with the addition of namespace variable `page_painted`.
- Adapted `set_scrollbar_dims` to work correctly after using `ensure_size` (need to get sizes from 
`.can coords` instead of `winfo`)

## [1.02] - 2021-02-28
### Added
- New procs `set_symbols` and `add_button3`.
- New namespace variable `github_repo` for the `GitHub plugins` plugin.

### Changed
- Adapt to new plugins and logging systems in de1app v1.34.14.
- Improve description.
- Correct bug in `add_variable` proc when referencing a textvariable name from the page data array.
- Default fontawesome symbols now are only those used by DGUI itself. Others must be declared by client code, using the
new proc `set_symbols`.

## [1.01] - 2021-02-20
### Changed
- Data dictionary functions moved from SDB to DGUI to avoid circular dependencies.
- Add -state hidden to arcs and lines in rounded_rectangle_outline.
- Manage load/preload procs.
- Correct bug introduced when started to use [string is true] in proc add_checkbox.
- Add friendly plugin `name` namespace variable and improve description.

## [1.00] - 2021-02-08 [Unreleased]

### Added
- Define the commands exported by the namespace
- New proc `add_select_entry` instead of `add_entry` with dropdown arguments
- New proc `value_or_default`

### Changed
- Initial code split off the GUI, IS, NUME and TXT namespaces from the [DSx DYE plugin](https://github.com/ebengoechea/dye_de1app_dsx_plugin/blob/main/changelog.md).
- Homogenize a bit the callabe commands

