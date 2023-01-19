
\*\* note this is a initial version of the README file which will be
updated for the future milestones\*\*

# sanityzeR

<!-- badges: start -->
<!-- badges: end -->

The goal of sanityzeR:

Data scientists often need to remove or redact Personal Identifiable
Information (PII) from their data. This package provides utilities to
spot and redact PII from r data frames/Tibbles.

PII can be used to uniquely identify a person. This includes names,
addresses, credit card numbers, phone numbers, email addresses, and
social security numbers, and therefore regulatory bodies such as the
European Union’s General Data Protection Regulation (GDPR) and the
California Consumer Privacy Act (CCPA) require that PII be removed or
redacted from data sets before they are shared an further processed

## Why `sanityzeR` ?

Because it’s a fun name and it’s a play on the word “sanitize” which is
what we are doing to the data

## Similar R packages

**add to this**

## Installation

You can install the development version of sanityzeR from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("UBC-MDS/sanityzeR")
```

## Example

This is a basic example which shows you how to solve a common problem:
**edit this**

``` r
library(sanityzeR)
## basic example code
```

## Features and Usage

Conceptually, `sanityzeR` is a package that provides a way to remove PII
from Pandas data frames. The package provides a number of default
spotters, which can be used to identify PII in the data and redact them.

The main entry point to the package is the `Cleanser` class. The
`Cleanser` class is used to add `Spotter`s to the cleanser, which will
be used to identify PII in the data. The cleanser can then be used to
cleanse the data, and redact the PII from the given data frame (all
future data structures that will be suppportd by the package, in the
future). **edit this as needed**

The package comes with a number of default spotters, as subclassess of
`Spotter`: 1. `CreditCardSpotter` - identifies credit card numbers 2.
`EmailSpotter` - identifies email addresses

Spotters can be added to it using the `add_spotter()` method. The
cleanser can then be used to cleanse data using the `cleanse()` method
which takes a Pandas data frame and returns a Pandas data frame with PII
redacted.

The redaction options provided by
``` sanityze`` are: 1. Redact using a fixed string - The string in this case is the ID of the spotter. For example, if the spotter is an instance of ```CreditCardSpotter`, the string will be`{{CREDITCARD}}`, or`{{EMAILADDRS}}`for an instance of`EmailSpotter`. 2. Redact using a hash of the input - The hash is computed using the`hashlib`package, and the hash function is`md5`. For example, if the spotter is an instance of`CreditCardSpotter`, the string will be`{{6a8b8c6c8c62bc939a11f36089ac75dd}}`, if the input is contains a PII`1234-5678-9012-3456\`.

## Classes and Functions

1.  `Cleanser`: the main class of the package. It is used to add
    spotters to it, and then cleanse data using the spotters.
    1.  `add_spotter()`: adds a spotter to the cleanser
    2.  `remove_spotter()`: removes a spotter from the cleanser
    3.  `clean()`: cleanses the data in the given data frame, and
        returns a new data frame with PII redacted
2.  `EmailSpotter`: a spotter that identifies email addresses
    1.  `getUID()`: returns the unique ID of the spotter
    2.  `process()`: performs the PII matching and redaction
3.  `CreditCardSpotter`: a spotter that identifies credit card numbers
    1.  `getUID()`: returns the unique ID of the spotter
    2.  `process()`: performs the PII matching and redaction

> You can checkout detailed API Documentations
> [here](https://ubc-mds.github.io/sanityze/).

Below is a simple quick start example:

``` python
import pandas as pd
from sanityze import Cleanser, EmailSpotter

# Create a cleanser, and don't add the default spotters
cleanser = Cleanser(include_default_spotters=False)
cleaner.add_spotter(from sanityze import Cleanser, EmailSpotter())
cleaned_df = cleanser.clean(df)
```

## High-level Design

To better understand the design of the package, we have provided a
high-level design document, which will be kept up to date as the package
evolves. The document can be found [here](HighLevelDesign.md).

## Contributing

Interested in contributing? Check out the [contributing
guidelines](CONTRIBUTING.md). Please note that this project is released
with a Code of Conduct. By contributing to this project, you agree to
abide by its terms.

## License

`sanityzeR` was created by Caesar Wong, Jonah Hamilton and Tony Zoght.
It is licensed under the terms of the [MIT license](LICENSE).

## Credits

`sanityzeR` was created with
[`cookiecutter`](https://cookiecutter.readthedocs.io/en/latest/) and the
`py-pkgs-cookiecutter`
[template](https://github.com/py-pkgs/py-pkgs-cookiecutter).

## Quick Links

- [Documentation](https://ubc-mds.github.io/sanityze/)
- [Kanban Board](https://github.com/orgs/UBC-MDS/projects/15)
- [Issues](https://github.com/UBC-MDS/sanityze/issues)
- [High Level Design](HighLevelDesign.md)
- [Contributing Guidelines](CONTRIBUTING.md)
- [Code of Conduct](CODE_OF_CONDUCT.md)
- [License](LICENSE)
