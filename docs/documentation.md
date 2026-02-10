# Surrogate Key Trim Documentation

## Overview

The `surrogate_key_trim` package enhances the functionality of the standard `generate_surrogate_key` macro by adding the ability to trim whitespace from input fields before hashing.

## Why Use This Package?

When working with data that comes from various sources, it's common to encounter inconsistent spacing in string fields. For example:
- `'John Doe'`
- `'John Doe '` (trailing space)
- `' John Doe'` (leading space)
- `' John Doe '` (both leading and trailing spaces)

Without trimming, these would generate different surrogate keys even though they represent the same logical value. This package solves that problem.

## Usage

### Basic Syntax

```sql
{{ surrogate_key_trim.generate_surrogate_key(field_list, trim=false) }}
```

### Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `field_list` | list | required | A list of fields to be included in the surrogate key |
| `trim` | boolean | `false` | When `true`, trims leading and trailing whitespace before hashing |

### Examples

#### Without Trimming (Default Behavior)
```sql
{{ surrogate_key_trim.generate_surrogate_key(['first_name', 'last_name']) }}
```

This preserves all whitespace in the input fields, so `' John '` and `'John'` would generate different hashes.

#### With Trimming
```sql
{{ surrogate_key_trim.generate_surrogate_key(['first_name', 'last_name'], trim=true) }}
```

This removes leading and trailing whitespace before hashing, so `' John '`, `'John '`, `' John'`, and `'John'` would all generate the same hash.

## Backward Compatibility

The package maintains full backward compatibility. When `trim=false` (the default), the behavior is identical to the original `dbt_utils.generate_surrogate_key` macro.

## Handling Special Cases

The macro properly handles:
- NULL values (converted to a default string representation)
- Empty strings
- Strings with only whitespace
- Mixed data types (converted to string before processing)

## Configuration Variables

This package respects the same configuration variable as the original:
- `surrogate_key_treat_nulls_as_empty_strings`: When set to `true`, treats NULLs as empty strings instead of the default `_dbt_utils_surrogate_key_null_` string.