# Retrieve and cache the user's default XM Directory ID

Checks QUALTRICS_DIRECTORY_ID env var first; if unset, calls GET
/directories to discover it and caches the result for the session.

## Usage

``` r
fetch_directory_id()
```
