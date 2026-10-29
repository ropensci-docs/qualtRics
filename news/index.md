# Changelog

## qualtRics (development version)

## qualtRics 3.3.0

CRAN release: 2026-06-25

- Migrated
  [`all_mailinglists()`](https://docs.ropensci.org/qualtRics/reference/all_mailinglists.md)
  and
  [`fetch_mailinglist()`](https://docs.ropensci.org/qualtRics/reference/fetch_mailinglist.md)
  from the deprecated Research Core Contacts API endpoints to the XM
  Directory API endpoints, ahead of Qualtrics retiring the old endpoints
  on June 30, 2026
  ([\#386](https://github.com/ropensci/qualtRics/issues/386)). The
  directory ID is discovered automatically from the API (or can be set
  with the `QUALTRICS_DIRECTORY_ID` environment variable), so no change
  to your code is needed to keep these functions working.

  Note that the XM Directory endpoints return a **different data
  shape**, so code that referenced the old column names will need to be
  updated:

  - [`all_mailinglists()`](https://docs.ropensci.org/qualtRics/reference/all_mailinglists.md):
    the `id` column is now `mailingListId`; the `libraryId`, `category`,
    and `folder` columns are no longer returned; and `contactCount`,
    `ownerId`, and creation/modification date columns are now included.
  - [`fetch_mailinglist()`](https://docs.ropensci.org/qualtRics/reference/fetch_mailinglist.md):
    the `id` column is now `contactId`, and `externalDataReference` is
    now `extRef`.

## qualtRics 3.2.2

CRAN release: 2025-08-23

- Again changed how CSV files are extracted from the Qualtrics zip
  archive, to handle more special characters in survey titles
  ([\#355](https://github.com/ropensci/qualtRics/issues/355))

- Updated tests for latest versions of vcr and webmockr
  ([\#374](https://github.com/ropensci/qualtRics/issues/374),
  [\#375](https://github.com/ropensci/qualtRics/issues/375))

## qualtRics 3.2.1

CRAN release: 2024-08-16

- Fixed bug when a survey question has *both* recoded values and
  variable naming thanks to [@Haunfelder](https://github.com/Haunfelder)
  ([\#343](https://github.com/ropensci/qualtRics/issues/343))

- Changed how CSV files are extracted from the Qualtrics zip archive, to
  handle special characters in survey titles
  ([\#349](https://github.com/ropensci/qualtRics/issues/349))

- Fixed problem with a test using internet resources on CRAN
  ([\#350](https://github.com/ropensci/qualtRics/issues/350))

## qualtRics 3.2.0

CRAN release: 2024-01-24

- Changed how multiple choice questions are mapped to an R factor with
  the `convert` argument to
  [`fetch_survey()`](https://docs.ropensci.org/qualtRics/reference/fetch_survey.md),
  to now excluding `NA` as a factor level
  ([\#315](https://github.com/ropensci/qualtRics/issues/315))

- Deprecated the `save_dir` and `force_request` arguments for
  [`fetch_survey()`](https://docs.ropensci.org/qualtRics/reference/fetch_survey.md),
  so that survey response downloads are no longer cached; calls to
  [`fetch_survey()`](https://docs.ropensci.org/qualtRics/reference/fetch_survey.md)
  now always query the Qualtrics API
  ([\#317](https://github.com/ropensci/qualtRics/issues/317))

- Added new `tmp_dir` argument to
  [`fetch_survey()`](https://docs.ropensci.org/qualtRics/reference/fetch_survey.md)
  so users can specify where survey results are briefly stored on disk
  ([\#327](https://github.com/ropensci/qualtRics/issues/327))

## qualtRics 3.1.7

CRAN release: 2022-11-18

- Refactored code for checking arguments and errors, thanks to
  [@jmobrien](https://github.com/jmobrien)
  ([\#263](https://github.com/ropensci/qualtRics/issues/263))

- Fixed bug in
  [`fetch_survey()`](https://docs.ropensci.org/qualtRics/reference/fetch_survey.md)
  for `include_* = NA`, thanks to
  [@jmobrien](https://github.com/jmobrien)
  ([\#277](https://github.com/ropensci/qualtRics/issues/277))

- Updated test fixture for new version of vcr

## qualtRics 3.1.6

CRAN release: 2022-06-06

- Add
  [`fetch_distribution_history()`](https://docs.ropensci.org/qualtRics/reference/fetch_distribution_history.md)
  and
  [`list_distribution_links()`](https://docs.ropensci.org/qualtRics/reference/list_distribution_links.md)
  for more handling of distribution data, thanks to
  [@chrisumphlett](https://github.com/chrisumphlett) and
  [@dsen6644](https://github.com/dsen6644)
  ([\#221](https://github.com/ropensci/qualtRics/issues/221),
  [\#239](https://github.com/ropensci/qualtRics/issues/239))

- Changed handling of literal `"NA"` text input from users so it is no
  longer converted to an R `NA` value thanks to
  [@jmobrien](https://github.com/jmobrien)
  ([\#244](https://github.com/ropensci/qualtRics/issues/244))

- Use [`httr::RETRY()`](https://httr.r-lib.org/reference/RETRY.html)
  instead of
  [`httr::VERB()`](https://httr.r-lib.org/reference/VERB.html) in
  [`qualtrics_api_request()`](https://docs.ropensci.org/qualtRics/reference/qualtrics_api_request.md)
  to implement consistent API error-handling across all of the functions
  in the package. They will be retried up to 3 times if there is any
  non-4xx error. Thanks to
  [@chrisumphlett](https://github.com/chrisumphlett)
  ([\#217](https://github.com/ropensci/qualtRics/issues/217))

- Update
  [`fetch_distributions()`](https://docs.ropensci.org/qualtRics/reference/fetch_distributions.md)
  for changes to the Qualtrics API, thanks to
  [@chrisumphlett](https://github.com/chrisumphlett)
  ([\#250](https://github.com/ropensci/qualtRics/issues/250))

## qualtRics 3.1.5

CRAN release: 2021-09-14

- Add
  [`fetch_description()`](https://docs.ropensci.org/qualtRics/reference/fetch_description.md)
  to download complete survey description metadata from v3 API endpoint
  (more up-to-date than older
  [`metadata()`](https://docs.ropensci.org/qualtRics/reference/metadata.md))
  thanks to [@jmobrien](https://github.com/jmobrien)
  ([\#207](https://github.com/ropensci/qualtRics/issues/207))
- Warn users about possible incorrect results from API when
  `breakout_sets` and `label` are both FALSE
- Refactor internal URL creation for API calls thanks to
  [@jmobrien](https://github.com/jmobrien)
  ([\#225](https://github.com/ropensci/qualtRics/issues/225))
- Add
  [`fetch_id()`](https://docs.ropensci.org/qualtRics/reference/fetch_id.md)
  to return a `surveyID` based on a unique survey name as it appears in
  the Qualtrics UI thanks to
  [@markjrieke](https://github.com/markjrieke)
  ([\#230](https://github.com/ropensci/qualtRics/issues/230)).

## qualtRics 3.1.4

CRAN release: 2021-01-14

- Add
  [`fetch_distributions()`](https://docs.ropensci.org/qualtRics/reference/fetch_distributions.md)
  to access distribution data for a specific survey thanks to
  [@dsen6644](https://github.com/dsen6644)
  ([\#169](https://github.com/ropensci/qualtRics/issues/169))
- Handle mailing list embedded data better thanks to
  [@dsen6644](https://github.com/dsen6644)
  ([\#175](https://github.com/ropensci/qualtRics/issues/175))
- Updated links to API documentation
- Create unique column names for questions using `choiceId` thanks to
  [@lyh970817](https://github.com/lyh970817)
  ([\#182](https://github.com/ropensci/qualtRics/issues/182))
- Fix bug when `include_questions` only contains one QID thanks to
  [@lyh970817](https://github.com/lyh970817)
  ([\#197](https://github.com/ropensci/qualtRics/issues/197))
- Generate correct/updated column mapping for survey responses thanks to
  [@jmobrien](https://github.com/jmobrien)
  ([\#199](https://github.com/ropensci/qualtRics/issues/199)). These
  column mappings are available as an attribute on survey results or via
  the new
  [`extract_colmap()`](https://docs.ropensci.org/qualtRics/reference/extract_colmap.md)
  function.

## qualtRics 3.1.3

CRAN release: 2020-05-22

- Update `include_questions` argument to use correct name in API
  request.
- Build API payloads with jsonlite
  ([\#155](https://github.com/ropensci/qualtRics/issues/155)) thanks to
  [@jmobrien](https://github.com/jmobrien)
- Convert tests to webmockr and vcr
  ([\#140](https://github.com/ropensci/qualtRics/issues/140) and
  [\#161](https://github.com/ropensci/qualtRics/issues/161)) thanks to
  [@shaun-jacks](https://github.com/shaun-jacks) and
  [@dsen6644](https://github.com/dsen6644)
- Allow user to specify column types for both
  [`fetch_survey()`](https://docs.ropensci.org/qualtRics/reference/fetch_survey.md)
  and
  [`read_survey()`](https://docs.ropensci.org/qualtRics/reference/read_survey.md)
  ([\#162](https://github.com/ropensci/qualtRics/issues/162)) thanks to
  [@jntrcs](https://github.com/jntrcs)

## qualtRics 3.1.2

CRAN release: 2020-02-24

- For empty surveys, return zero row dataframe
  ([\#127](https://github.com/ropensci/qualtRics/issues/127))
- Remove unnecessary dependency on yaml and deprecate
  `qualtRicsConfigFile()`, to avoid unexpected behavior
- Deprecate old versions of functions: `getSurveys()`,
  `getSurveyQuestions()`, `getSurvey()`, `readSurvey()`
- Move to updated version of Qualtrics API
  ([\#130](https://github.com/ropensci/qualtRics/issues/130)) thanks to
  [@jmobrien](https://github.com/jmobrien)
- Correctly handle time zone conversions
  ([\#137](https://github.com/ropensci/qualtRics/issues/137)) thanks to
  [@jmobrien](https://github.com/jmobrien)
- Add `breakout_sets` parameter thanks to
  [@shaun-jacks](https://github.com/shaun-jacks)
- Fix bug in
  [`infer_data_types()`](https://docs.ropensci.org/qualtRics/reference/infer_data_types.md)
  for answers choices that include HTML
- Deprecate `last_response` argument no longer used by API
  ([\#153](https://github.com/ropensci/qualtRics/issues/153))

## qualtRics 3.1.1

CRAN release: 2019-09-23

- Fix bug in
  [`infer_data_types()`](https://docs.ropensci.org/qualtRics/reference/infer_data_types.md)
  to avoid errors with factors/numeric values
- Improvements to documentation, error checking
- Allow user to access column mapping for questions and IDs
  ([\#115](https://github.com/ropensci/qualtRics/issues/115))
- Deprecate `registerOptions()` to avoid unexpected behavior with
  options
- Make data import more robust with more condition and error checking,
  as well as better defaults

## qualtRics 3.1.0

CRAN release: 2019-04-12

- New maintainer: Julia Silge
- Add all previous contributors to DESCRIPTION as `ctb`
- Declare testthat dependency in DESCRIPTION (reason for previous
  archiving from CRAN)
- Simpler approach for storing API credentials as environment variables
  with
  [`qualtrics_api_credentials()`](https://docs.ropensci.org/qualtRics/reference/qualtrics_api_credentials.md)
  (`registerOptions()` is now soft deprecated with a warning)
- Simplify README (keep all existing detailed workflow documentation in
  vignette)
- Relicense from GPL-3 to MIT. See [consent from authors
  here](https://github.com/ropensci/qualtRics/issues/95).
- Improvements to documentation throughout
- Renaming (with warnings on old versions) of key functions for clarity
  and reduction in confusion, plus improvements:
  - [`all_surveys()`](https://docs.ropensci.org/qualtRics/reference/all_surveys.md)
    (from old version of `getSurveys()`)
  - [`survey_questions()`](https://docs.ropensci.org/qualtRics/reference/survey_questions.md)
    (from old version of `getSurveyQuestions()`)
  - [`fetch_survey()`](https://docs.ropensci.org/qualtRics/reference/fetch_survey.md)
    (from old version of `getSurvey()`)
  - [`read_survey()`](https://docs.ropensci.org/qualtRics/reference/read_survey.md)
    (from old version of `readSurvey()`)

## qualtRics 3.0 (2018-02-03)

CRAN release: 2018-02-05

#### NEW FEATURES

- Added ‘metadata’ function that allows the user to retrieve detailed
  metadata about survey.
- User can now convert specific question types automatically. See [this
  page](https://github.com/JasperHG90/qualtRics#automatic-conversion-of-variables)
  for more information.

#### MINOR IMPROVEMENTS

- Using package [httptest](https://CRAN.R-project.org/package=httptest)
  for mock API requests so that API calls can be tested.
- `getSurveys()` and `getSurveyQuestions()` now return a
  [tibble](https://CRAN.R-project.org/package=tibble)

#### BUG FIXES

- Added .onDetach conditions so that environment variables (root url and
  API key) are removed when package is unloaded. This prevents issues if
  user decides to load the package again.
- We found that surveys that use new lines in the questions break the
  readSurvey function. The problem is, that read.csv (and read.table as
  well as the readr library implementation) ignore the quote = “"”
  option when a skip = 2 or skip = 3 parameter is set. As a result the
  read function slices off the questions row somewhere in the middle
  when first importing just the table body using skip.

#### DEPRECATED AND DEFUNCT

- convertstandardcolumns deprecated since readr::read_csv does this
  automagically. It has been changed in config file to
  ‘convertvariables’.

## qualtRics 2.2 (2017-10-27)

CRAN release: 2017-10-27

- `readSurvey()` now takes an additional argument, fileEncoding, so that
  user can import surveys using a specific encoding. ‘fileEncoding’ can
  also be passed as optional argument in `getSurvey()`. Added new
  parameter that reads legacy data format.
- Better argument checking.
- `getSurveyQuestions()` now returns additional information. h/t
  [@phoebewong](https://github.com/phoebewong)
- Fixes several bugs and stability issues
- More informative error messages

## qualtRics 2.0 (2017-06-16)

CRAN release: 2017-06-16

- `registerOptions()` now takes more arguments. User can now set global
  options. See `qualtRicsConfigFile()` for more information. Same
  options are now passed through `...` in specific functions.
- Added appveyor testing.
- Added support for a configuration file to store API key and root url
  in the working directory.
- `registerApiKey()` has been replaced by `registerOptions()`. This
  function stores both a user’s API key and root url. Function also
  scans for a configuration file `.qualtRics.yml` that contains this
  information.
- Added a new script called `zzz.R`. When the package is loaded, the
  .onLoad() function in this file scans the working directory for a
  `.qualtRics.yml` configuration file so that the user doesn’t have to
  register this information manually.
- Added a new function `qualtRicsConfigFile()` that prints instructions
  for the user on how to set up a configuration file to the R Console.
- Removed the `root_url` parameter from all functions that required it.
- Dates are now converted without a specific timezone.
- Added a new function `getSurveyQuestions()` that allows the user to
  download a data frame containing question labels and IDs.
- Added parameter **includedQuestionIds** so user can select questions
  they want to download. Need to use the QID value from
  `getSurveyQuestions()`.
- Updated examples and documentation of functions.
- Added the following parameters to `getSurvey()`:
  - **seenUnansweredRecode:** String. Recode seen but unanswered
    questions with a string value.
  - **limit:** Integer. Maximum number of responses exported. Defaults
    to NULL (all responses).
  - **useLocalTime:** Boolean. Use local timezone to determine response
    date values.
- `getSurveys()` now retrieves \> 100 results.

## qualtRics 1.0 (2016-10-13)

CRAN release: 2017-04-26

- Added a new function `readSurvey()`. This function is used in the
  `getSurvey()` function but will also work with surveys downloaded
  manually from Qualtrics. Standard columns (completed
  survey/startDate/endDate etc.) are now converted to their proper data
  types. HT Adrian Brugger & Stefan Borer.
- User can only download surveys in CSV format, no longer in XML or
  JSON.
- Added several new parameters to `getSurvey()` function. HT
  [@samuelkaminsky](https://github.com/samuelkaminsky) &
  [@eknud](https://github.com/eknud)
  - *LastResponseId*: If used, only responses that were filled out later
    than this ID will be downloaded.
  - *UseLabels*: If TRUE, download will contain character labels. Else,
    download will contain choice labels.
  - *StartDate*: Only download responses after this date.
  - *EndDate*: Only download responses before this date.
- Survey downloads should be faster now; `getSurvey()` no longer sleeps
  when checking download status. Also added progress bar.

## qualtRics 0.03 \[beta\]

- User can choose to save results directly in a folder through
  ‘save_dir’ parameter in `getSurvey()`
- Results can now be requested in .csv, .json or .xml format. The
  packages `jsonlite` and `XML` are added to ‘Suggests’ in DESCRIPTION.
- `constructHeader()` is now deprecated and should no longer be used.
  Instead, users need to call `registerApiKey()`.
- Added a new function `registerApiKey()` which saves the user’s API key
  and header information in the
  [`tempdir()`](https://rdrr.io/r/base/tempfile.html) environment.

## qualtRics 0.02 \[beta\]

- Renamed ‘base url’ to ‘root url’ such that it corresponds to Qualtrics
  documentation.
- The root url no longer requires API-specific endpoints. So
  e.g. ‘<https://leidenuniv.eu.qualtrics.com>’ now works for all
  functions. The API-specific endpoints are added in the functions
  itself.
- Institution-specific root url is now required by `getSurvey()`

## qualtRics 0.01 \[beta\]

- Added first three functions (`constructHeader`, `getSurvey`,
  `getSurveyIDs`)
- base_url parameter is now uniform across functions. Parameter is
  called ‘root url’ to bring it in line with Qualtrics documentation.
