# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added
- LICENSE file (MIT License)
- CONTRIBUTING.md with contribution guidelines
- CHANGELOG.md for tracking changes

### Changed
- Updated README.md to use latest Claude Code installation method (`claude plugin install`)
- Updated template files with latest installation instructions
- Enhanced .gitignore.template with comprehensive Node.js exclusions

### Fixed
- Directory structure update: `skills/` → `commands/`
- Removed deprecated `capabilities` field from plugin.json
- Added `argument-hint` to create-plugin command

---

## [1.0.0] - 2025-01-17

### Added
- Initial release of Plugin Generator
- `/create-plugin` command for scaffolding Claude Code plugins
- Template files for plugin.json, hello.md, README.md, and .gitignore
- Comprehensive README.md with beginner-friendly documentation
- Test scripts in package.json

### Features
- Automatic plugin directory structure creation
- Sample command generation
- Markdown-based command definitions
- Error handling for existing directories
- `--force` option for overwriting existing plugins
- Plugin name validation (alphanumeric and hyphens only)

[Unreleased]: https://github.com/ShunsukeHayashi/plugin-generator/compare/v1.0.0...HEAD
[1.0.0]: https://github.com/ShunsukeHayashi/plugin-generator/releases/tag/v1.0.0
