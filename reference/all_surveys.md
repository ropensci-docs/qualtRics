# Retrieve a data frame of all active surveys on Qualtrics

Retrieve a data frame of all active surveys on Qualtrics

## Usage

``` r
all_surveys()
```

## Details

If the request to the Qualtrics API made by this function fails, the
request will be retried. If you see these failures on a 500 error (such
as a 504 error) be patient while the request is retried; it will
typically succeed on retrying. If you see other types of errors,
retrying is unlikely to help.

## See also

See <https://api.qualtrics.com/> for documentation on the Qualtrics API.

## Examples

``` r
if (FALSE) { # \dontrun{
# Register your Qualtrics credentials if you haven't already
qualtrics_api_credentials(
  api_key = "<YOUR-API-KEY>",
  base_url = "<YOUR-BASE-URL>"
)

# Retrieve a list of all surveys
surveys <- all_surveys()

# Retrieve a single survey
mysurvey <- fetch_survey(surveyID = surveys$id[6])

mysurvey <- fetch_survey(
  surveyID = surveys$id[6],
  save_dir = tempdir(),
  start_date = "2018-01-01",
  end_date = "2018-01-31",
  limit = 100,
  label = TRUE,
  unanswer_recode = "UNANS",
  verbose = TRUE
)
} # }
```
