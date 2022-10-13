# metadata-schema changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased] - ...
### Added
- BP.submission.xsd derived from SRA.submision.xsd with added BP types.

### Changed
- CaseType is now included in SAMPLE_SET
- SpecimenType can optionally reference a case with the PART_OF_CASE-element, replacing the RELATED_SPECIMENS-element on CaseType.
- For ObservationType the item an observation is made on is moved to the OBSERVED_ON-element.


## [0.2.0] - 2022-09-02
### Added
- StainType to describe stains separately from Slide-object.
- CaseType that can reference BiologicalBeings and Specimens.
- ObservationType to describe diagnoses, findings, etc on samples.

## [0.1.1] - 2022-06-02
### Changed
- BP.dataset no longer extends EGA.dataset.

## [0.1.0] - 2022-06-01
### Added
- Implementation of MSMdad 0.1.0.


[Unreleased]: https://github.com/imi-bigpicture/metadata-schema/compare/0.2.0..HEAD
[0.2.0]: https://github.com/imi-bigpicture/metadata-schema/compare/v0.1.1..v0.2.0
[0.1.1]: https://github.com/imi-bigpicture/metadata-schema/compare/v0.1.0..v0.1.1
[0.1.0]: https://github.com/imi-bigpicture/metadata-schema/tree/refs/tags/v0.1.0

