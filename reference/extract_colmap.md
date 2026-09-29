# Extract column map from survey data download

Helper function to extract the column map attached to a response data
download obtained from
[`fetch_survey()`](https://docs.ropensci.org/qualtRics/reference/fetch_survey.md)
(using the default `add_column_map = TRUE`)

## Usage

``` r
extract_colmap(respdata)
```

## Arguments

- respdata:

  Response data including a column map dataframe as an attribute

## Details

If the request to the Qualtrics API made by this function fails, the
request will be retried. If you see these failures on a 500 error (such
as a 504 error) be patient while the request is retried; it will
typically succeed on retrying. If you see other types of errors,
retrying is unlikely to help.

## Examples

``` r
if (FALSE) { # \dontrun{
# Retrieve a list of surveys
surveys <- all_surveys()

# Retrieve a single survey
mysurvey <- fetch_survey(surveyID = surveys$id[6])

# Extract column mapping for survey
extract_colmap(mysurvey)
} # }
```
