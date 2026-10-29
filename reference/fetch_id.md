# Fetch a unique Qualtrics survey ID based on survey name in the Qualtrics UI

Fetch a unique Qualtrics survey ID based on survey name in the Qualtrics
UI

## Usage

``` r
fetch_id(.data, survey_name, partial_match = FALSE)
```

## Arguments

- .data:

  Data frame of active surveys created by the function
  [`all_surveys()`](https://docs.ropensci.org/qualtRics/reference/all_surveys.md).

- survey_name:

  String. Name of the survey as it appears in the Qualtrics UI. Must be
  unique to be passed to `fetch_id()`.

- partial_match:

  Boolean. Will match all surveys containing the exact string provided.
  Defaults to FALSE, which matches against the entire name.

## Details

Survey names in the Qualtrics platform are not required to be unique,
but the `survey_name` argument for this function *must* be unique. If
input results in multiple surveys being matched, will error with a list
of up to 5 matches & their IDs

## Examples

``` r
if (FALSE) { # \dontrun{
# Register your Qualtrics credentials if you haven't already
qualtrics_api_credentials(
  api_key = "<YOUR-API-KEY>",
  base_url = "<YOUR-BASE-URL>"
)

# Retrieve a list of surveys
surveys <- all_surveys()

# Retrieve surveyID for a unique survey
my_id <- fetch_id(surveys, "Unique Survey Name")

} # }
```
