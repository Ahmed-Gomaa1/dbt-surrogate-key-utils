# Surrogate Key Trim

A dbt package that extends the functionality of `dbt_utils.generate_surrogate_key` with a trim parameter.

## Overview

This package provides an enhanced version of the generate_surrogate_key macro that includes the ability to trim whitespace from input fields before hashing. This is particularly useful when dealing with data that may have inconsistent spacing but should be treated as identical values.

## Installation

Include in your `packages.yml`:

```yaml
packages:
  - git: "https://github.com/YOUR_USERNAME/dbt-surrogate-key-trim.git"
    revision: v1.0.0  # Use the latest release tag
```

Then run:
```bash
dbt deps
```

## Usage

The package provides the `surrogate_key_trim.generate_surrogate_key` macro with the following signature:

```sql
{{ surrogate_key_trim.generate_surrogate_key(field_list, trim=false) }}
```

### Parameters

- `field_list` (required): A list of fields to be included in the surrogate key
- `trim` (optional, default: `false`): When set to `true`, trims leading and trailing whitespace from string fields before hashing. When `false`, preserves all whitespace in the input fields.

### Example

Basic usage (without trim):
```sql
{{ surrogate_key_trim.generate_surrogate_key(['field_a', 'field_b']) }}
```

Usage with trim enabled:
```sql
{{ surrogate_key_trim.generate_surrogate_key(['field_a', 'field_b'], trim=true) }}
```

When `trim=true`, the macro will remove leading and trailing whitespace from string fields before generating the hash. This is useful when dealing with data that may have inconsistent spacing but should be treated as identical values.

## Compatibility

This package is designed to work with dbt (data build tool) version 1.0.0 and later.

## License

MIT