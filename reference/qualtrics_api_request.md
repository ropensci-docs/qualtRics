# Send httr requests to Qualtrics API

Send httr requests to Qualtrics API

## Usage

``` r
qualtrics_api_request(
  verb = c("GET", "POST"),
  url = url,
  query = NULL,
  body = NULL,
  as = c("parsed", "raw"),
  ...
)
```

## Arguments

- verb:

  Type of request to be sent (@seealso
  [`httr::VERB()`](https://httr.r-lib.org/reference/VERB.html))

- url:

  Qualtrics endpoint URL created by
  [`generate_url()`](https://docs.ropensci.org/qualtRics/reference/generate_url.md)
  functions

- query:

  Optional query parameters used by some endpoints

- body:

  Options created by
  [`create_raw_payload()`](https://docs.ropensci.org/qualtRics/reference/create_raw_payload.md)
  function

- as:

  type of content to return, passed to `as` in httr::content(). current
  options "parsed" (since we get JSON mostly), "raw" (response .zips)

- ...:

  arguments passed to httr::content when parsing

## Details

If the request to the Qualtrics API made by this function fails, the
request will be retried. If you see these failures on a 500 error (such
as a 504 error) be patient while the request is retried; it will
typically succeed on retrying. If you see other types of errors,
retrying is unlikely to help.
