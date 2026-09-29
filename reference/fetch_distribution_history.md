# Download distribution history data for a distribution from Qualtrics

Download distribution history data for a distribution from Qualtrics

## Usage

``` r
fetch_distribution_history(distributionID)
```

## Arguments

- distributionID:

  String. Unique distribution ID for the distribution history you want
  to download.

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
distribution_history <- fetch_distribution_history(distributions$id[1])
} # }
```
