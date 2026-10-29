# Runs 3-part request to export-responses endpoint, downloading and unzipping file

Runs 3-part request to export-responses endpoint, downloading and
unzipping file

## Usage

``` r
export_responses_request(surveyID, body, verbose = TRUE, tmp_dir)
```

## Arguments

- surveyID:

  ID of the survey to be downloaded

- body:

  payload/body of API request containing desired params

- verbose:

  give verbose response

- tmp_dir:

  temporary directory for zip file
