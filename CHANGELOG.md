# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/en/1.0.0/)
and this project adheres to [Semantic Versioning](http://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.0.8] - 2017-08-11
### Changed
- This plugin does not work with files containing a stream (`gulp.src(..., {buffer: false});`). So the plugin has been
changed so when passed file with streams it throws and error.

## [0.0.7] - 2017-08-10
### Added
- `CHANGELOG.md`, `.editorconfig` and other files to improve project structure and consistency.

### Changed
- Moved to a new Github repository.
- Missing metadata in the `package.json` has been added.

