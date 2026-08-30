# Monitor progress from response request download, then obtain file download location

Monitor progress from response request download, then obtain file
download location

## Usage

``` r
export_responses_progress(surveyID, requestID, verbose = FALSE)
```

## Arguments

- surveyID:

  ID of survey whose responses are being pulled

- requestID:

  exportProgressId from
  https://api.qualtrics.com/37e6a66f74ab4-get-response-export-progress

- verbose:

  See
  [`fetch_survey()`](https://docs.ropensci.org/qualtRics/reference/fetch_survey.md)

## Details

If the request to the Qualtrics API made by this function fails, the
request will be retried. If you see these failures on a 500 error (such
as a 504 error) be patient while the request is retried; it will
typically succeed on retrying. If you see other types of errors,
retrying is unlikely to help.
