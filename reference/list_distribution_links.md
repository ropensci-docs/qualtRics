# Download distribution links for a distribution from Qualtrics

Download distribution links for a distribution from Qualtrics

## Usage

``` r
list_distribution_links(distributionID, surveyID)
```

## Arguments

- distributionID:

  String. Unique distribution ID for the distribution links you want to
  download.

- surveyID:

  String. Unique ID for the survey you want to download.

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
distribution_links <- list_distribution_links(distributions$id[1], surveyID = surveys$id[1])
} # }
```
