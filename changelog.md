# Changelog - "Describe GUI" Decent DE1app plugin

Format based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

## [1.0] - 2021-03-?

### Added
- New proc `set_symbols`.

### Changed
- Adapt to new plugins and logging systems in 1.34.14.
- Improve description.
- Correct bug in add_variable when referencing a textvariable name from the page data array.
- Default fontawesome symbols now are only those used by DGUI itself. Others must be declared by client code, using 
new proc `set_symbols`.
- New namespace variable `github_repo` for the `GitHub plugins` plugin.

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


# Define Fontawesome symbols by name. If a symbol name is already defined and the value differs, it is not changed
#	and a warning added to the log.
proc ::plugins::DGUI::set_symbols { args } {
	variable symbols
	
	array set new_symbols $args
	set n [expr {[llength $args]-1}]
	for { set i 0 } { i < $n } { incr i 2 } {
		set sn [lindex $args $i]
		set sv [lindex $args [expr {$i+1}]]
		set idx [lsearch [array names symbols] $sn]
		if { $idx == -1 } {
			set symbols($sn) $sv
		} elseif { $symbols($sn) ne $sv } {
			msg -WARN "symbol '$sn' already defined with a different value"
		}
	}
}