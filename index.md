# qualtRics

**Authors:** [Julia Silge](https://juliasilge.com/), [Joseph
O’Brien](https://docs.ropensci.org/qualtRics/joseph.m.obrien@gmail.com),
[Jasper Ginn](https://jasperhg90.github.io/)  
**License:** [MIT](https://opensource.org/license/mit)

[Qualtrics](https://www.qualtrics.com/) is an online survey and data
collection software platform. Qualtrics is used across many domains in
both academia and industry for online surveys and research. While users
can manually download survey responses from Qualtrics through a browser,
importing this data into R is then cumbersome. The qualtRics R package
implements the retrieval of survey data using the Qualtrics API and aims
to reduce the pre-processing steps needed in analyzing such surveys.
Currently, this package is the only package on CRAN that offers such
functionality, and is included in the official Qualtrics API
documentation.

Note that your institution must support API access and that it must be
enabled for your account. Whoever manages your Qualtrics account can
help you with this. Please refer to the [Qualtrics
documentation](https://api.qualtrics.com/) to find your API token.

The authors of this package are not affiliated with Qualtrics, and
Qualtrics does not offer support for this package. For specific
information about the Qualtrics API, you can refer to the [official
documentation](https://api.qualtrics.com/).

## Installation

This package can be installed from CRAN:

``` r

install.packages("qualtRics")
```

Alternatively, you can install the development version with the
[remotes](https://cran.r-project.org/package=remotes) package (or
alternatively, [devtools](https://cran.r-project.org/package=devtools)):

``` r

install.packages("remotes")
remotes::install_github("ropensci/qualtRics")
```

## Access your Qualtrics data

Currently, the package contains three core functions:

1.  [`all_surveys()`](https://docs.ropensci.org/qualtRics/reference/all_surveys.md)
    fetches a list of all surveys that you own or have access to from
    Qualtrics.
2.  [`fetch_survey()`](https://docs.ropensci.org/qualtRics/reference/fetch_survey.md)
    downloads a survey from Qualtrics and loads it into
    18. 
3.  [`read_survey()`](https://docs.ropensci.org/qualtRics/reference/read_survey.md)
    allows you to read CSV files you download manually from Qualtrics.

It also contains [multiple helper
functions](https://docs.ropensci.org/qualtRics/reference/index.html#other-helper-functions),
including:

1.  [`qualtrics_api_credentials()`](https://docs.ropensci.org/qualtRics/reference/qualtrics_api_credentials.md)
    stores your API key and base URL in environment variables.
2.  [`survey_questions()`](https://docs.ropensci.org/qualtRics/reference/survey_questions.md)
    retrieves a data frame containing questions and question IDs for a
    survey;
    [`extract_colmap()`](https://docs.ropensci.org/qualtRics/reference/extract_colmap.md)
    retrieves a similar data frame with more detailed mapping from
    columns to labels.
3.  [`metadata()`](https://docs.ropensci.org/qualtRics/reference/metadata.md)
    retrieves metadata about your survey, such as questions, survey
    flow, number of responses etc.

Note that you can only export surveys that you own, or to which you have
been given administration rights.

## Register your Qualtrics credentials

There are two important credentials you need to authenticate with the
Qualtrics API. These are your **API key** and **datacenter-specific base
URL**. The base URL you pass to the qualtRics package should look like
`yourdatacenterid.qualtrics.com`, without a scheme such as `https://`.
The [Qualtrics API documentation](https://api.qualtrics.com/) explains
how you can find your base URL.

You can store your API credentials `QUALTRICS_API_KEY` and
`QUALTRICS_BASE_URL` in your `.Renviron` file for repeated use across
sessions. The qualtRics package has a function to help with this.

``` r

library(qualtRics)

qualtrics_api_credentials(api_key = "<YOUR-QUALTRICS_API_KEY>", 
                          base_url = "<YOUR-QUALTRICS_BASE_URL>",
                          install = TRUE)
```

After you use this function, reload your environment
(`readRenviron("~/.Renviron")`) so you can use the credentials without
restarting R.

## A simple Qualtrics workflow

Once your Qualtrics API credentials are stored, you can see what surveys
are available to you.

``` r

surveys <- all_surveys() 
```

You can then download the data from any of these individual surveys (for
example, perhaps the sixth one) directly into R.

``` r

mysurvey <- fetch_survey(surveyID = surveys$id[6], 
                         verbose = TRUE)
```

See the qualtRics vignette for more details on variable metadata,
automatic conversion of variables, retrieving responses between specific
dates or for specific survey items, and more.

## Related work

- [Jason Bryer](https://github.com/jbryer/qualtrics) wrote an R package
  to work with the previous version of the Qualtrics API
- [QualtricsTools](https://github.com/emma-morgan/QualtricsTools)
  creates automatic reports in shiny.
- [qsurvey](https://github.com/jamesdunham/qsurvey) by James Dunham
  focuses on testing and review of surveys before fielding, and analysis
  of responses afterward.

### Community Guidelines

This project is released with a [Contributor Code of
Conduct](https://github.com/ropensci/qualtRics/blob/master/CONDUCT.md).
By participating in this project you agree to abide by its terms.
Feedback, bug reports (and fixes!), and feature requests are welcome;
file issues or seek support
[here](https://github.com/ropensci/qualtRics/issues).
