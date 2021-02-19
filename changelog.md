# Changelog - "Describe GUI" Decent DE1app plugin

Format based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

## [1.01] - 2021-02-?

### Changed
- Data dictionary functions moved from SDB to DGUI to avoid circular dependencies.
- Added -state hidden to arcs and lines in rounded_rectangle_outline.
- Manage load/preload procs.
- Correct bug introduced when started to use [string is true] in proc add_checkbox.
- Add friendly plugin 'name' namespace variable.

## [1.00] - 2021-02-08 [Unreleased]

### Added
- Define the commands exported by the namespace
- New proc 'add_select_entry' instead of 'add_entry' with dropdown arguments
- New proc 'value_or_default'

### Changed
- Initial code split off the GUI, IS, NUME and TXT namespaceS from the [DSx DYE plugin](https://github.com/ebengoechea/dye_de1app_dsx_plugin/blob/main/changelog.md).
- Homogenize a bit the callabe commands
