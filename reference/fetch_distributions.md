# Download distribution data for a survey from Qualtrics

Download distribution data for a survey from Qualtrics

## Usage

``` r
fetch_distributions(surveyID)
```

## Arguments

- surveyID:

  String. Unique survey ID for the distribution data you want to
  download.

## Details

If the request to the Qualtrics API made by this function fails, the
request will be retried. If you see these failures on a 500 error (such
as a 504 error) be patient while the request is retried; it will
typically succeed on retrying. If you see other types of errors,
retrying is unlikely to help.

## Examples

``` r
if (FALSE) { # \dontrun{
# Register your Qualtrics credentials if you haven't already
qualtrics_api_credentials(
  api_key = "<YOUR-API-KEY>",
  base_url = "<YOUR-BASE-URL>"
)

surveys <- all_surveys()
distributions <- fetch_distributions(surveys$id[1])
} # }
```
