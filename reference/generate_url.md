# Generate URL for specific API query by type and (if appropriate) ID

Generate URL for specific API query by type and (if appropriate) ID

## Usage

``` r
generate_url(query, ...)
```

## Arguments

- query:

  string. The specific API query desired. Generally named the same as
  associated functions but without underscores, so the request for
  [`fetch_survey()`](https://docs.ropensci.org/qualtRics/reference/fetch_survey.md)
  would be be "fetchsurvey".

- ...:

  Named elements of URL for specific query desired, such as `surveyID`
  or `mailinglistID`

## Value

Endpoint URL to be passed to querying tools
