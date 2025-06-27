# DAPT1 Test Suite

The DAPT1 Test Suite consists of a validation test suite.
The primary purpose of this test suite is to demonstrate adequate
implementation experience of each feature of [DAPT](https://www.w3.org/TR/DAPT/) that is not already
present in [TTML2](https://www.w3.org/TR/ttml2/) as required by
the DAPT Candidate Recommendation Exit Criteria, and listed in the DAPT Implementation Report.

Tests for TTML2 features can be found at [ttml2-tests](https://github.com/w3c/ttml2-tests).

The tests found in these test suites focus on functionality and constraints
thereof that derive directly from normative text in the DAPT Specification.
Additional tests that go beyond the normative specification text may be included here as well; however, though such tests are useful for wider interoperability testing, the results from their exercise are not reported in the [DAPT Implementation Report](https://www.w3.org/wiki/TimedText/DAPT_Implementation_Report). 

## Validation Test Suite

The validation test suite is found under the `validation` directory,
and is divided into two parts:
(1) tests for valid content (validity tests) and
(2) tests for invalid content (invalidity tests).
The result of each test can be characterized as PASS or FAIL.

A PASS result for a validity test occurs if the validator does not reject
(report a validation error for) the content of the test.
In contrast, a FAIL result for a validity test occurs if the validator rejects
(reports a validation error for) the content of the test, in which case,
such a result is deemed a false negative result.

A PASS result for an invalidity test occcurs if the validator rejects
(reports a validation error for) the content of the test.
In contrast, a FAIL result for an invalidity test occurs if the validator
does not reject (report a validation error for) the content of the test, in which case,
such a result is deemed a false positive result.

A validator is considered to strictly pass the test suite if it does not report
a false negative for any validity test.
A validator is considered to fully pass the test suite if it
(1) strictly passes the test suite and
(2) does not report a false positive for any invalidity test.

For the purpose of reporting an implementation of the validation function for
a specific (designated) feature,
the implementation must strictly pass all tests for that feature;
however, it is not required to fully pass all tests for that feature
since the DAPT specification does not require a validator
to detect all possibile invalidities,about which see
[validate document](https://www.w3.org/TR/ttml2/#semantics-procedure-validate-document).

A mapping from (designated) features to specific tests is found in
`validation/tests.json`, which, for each new DAPT feature designator,
lists validity and invalidity tests (by name), and optionally includes any of
(1) a per-test exclusion flag if the test is intended to be excluded from exit criteria consideration and
(2) an edition introduced (since) indicator.
We refer to this mapping file as the validation test manifest.

## Presentation Test Suite

There are currently no presentation tests.

In case we add presentation tests in the future,
the presentation test suite is found under the `presentation` directory,
and would include tests for presenting valid content.

A mapping from (designated) features to specific tests is found in
`presentation/tests.json`, which, for each new DAPT feature designator,
lists the presentation tests (by name), and optionally includes any of
(1) a per-test exclusion flag if the test is intended to be excluded from exit criteria consideration and
(2) an edition introduced (since) indicator.
We refer to this mapping file as the presentation test manifest.

For tests having primarily visual presentation semantics,
each presentation test is associated with a like named ZIP archive with the suffix `.expected.zip`,
which contains the output of a particular reference implementation (imscJS).
Each such reference archive contains a set of one or more image frames represented in some image format,
where each image represents the rendering of an ISD (intermediate synchronic document)
and has for its filename time of the beginning of that ISD.
In the present form of the reference archives, the image format is image/png.
These image frames should not be construed as normative,
but merely serve as a possible reference image for performing (human visual) comparisons of expected output.
