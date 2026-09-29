# Download complete survey description using the Qualtrics v3 "Get Survey" API endpoint.

Download complete survey description using the Qualtrics v3 "Get Survey"
API endpoint.

## Usage

``` r
fetch_description(surveyID, elements = NULL, legacy = FALSE, ...)
```

## Arguments

- surveyID:

  A string. Unique ID for the survey you want to download. Returned as
  "id" by the
  [all_surveys](https://docs.ropensci.org/qualtRics/reference/all_surveys.md)
  function.

- elements:

  A character vector. Lists elements of survey definition to be
  maintained. Possible elements are "metadata", "surveyoptions", "flow",
  "blocks", "questions", "responsesets", and/or "scoring"
  (case-insensitive). If `legacy = TRUE`, then possible elements are
  "metadata", "questions", "responsecounts", "blocks", "flow",
  "embedded_data", and/or "comments".

- legacy:

  Logical. If TRUE, will use older Get Survey API endpoint via a call to
  legacy function
  [metadata](https://docs.ropensci.org/qualtRics/reference/metadata.md).

- ...:

  Additional options, only used when `legacy = TRUE`. User may pass an
  argument called `questions`, a vector containing the names of
  questions for which you want to return metadata.

## Value

A list containing survey description metadata. The contents of the
returned list depend on `elements`.

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

# Retrieve a list of surveys
surveys <- all_surveys()

# Get description for a survey
descrip <- fetch_description(surveyID = surveys$id[6])

# Get metadata with specific elements
descrip_specific <- fetch_description(
  surveyID = id,
  elements = c("questions", "flow")
)

} # }
```
