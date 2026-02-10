# Changelog

## [1.0.0] - YYYY-MM-DD

### Added
- Enhanced `generate_surrogate_key` macro with `trim` parameter
- When `trim=true`, the macro removes leading and trailing whitespace from string fields before hashing
- Maintains backward compatibility with `trim=false` (default behavior)