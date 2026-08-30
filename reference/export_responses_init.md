# Initiate a request to the export-responses API endpoint

Initiate a request to the export-responses API endpoint

## Usage

``` r
export_responses_init(surveyID, body)
```

## Arguments

- surveyID:

  ID of survey whose responses are being pulled

## Details

If the request to the Qualtrics API made by this function fails, the
request will be retried. If you see these failures on a 500 error (such
as a 504 error) be patient while the request is retried; it will
typically succeed on retrying. If you see other types of errors,
retrying is unlikely to help.
