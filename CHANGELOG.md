# metadata-schema changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased] -

### Changed

- Changed the name of `BPObjectType` to `ObjectType`, `BPRefObjectType` to `ReferenceObjectType`, and `BPSampleSetType` to `SampleSetType`.

- The single element `BPDATASET` in `BP.dataset.xsd` is renamed to `DATASET` to be consistent with the `DATASET_SET` element.

## [0.9.0] - 2024-01-05

### Changed

- `BPObjectType` is no longer and extension of SRA `ObjectType`.
- Changed `alias` to be a required attribute for `BPObjectType`.
- References to other `BpObjectType` now through `BPRefObjectType` with required attribute `alias`, replacing the SRA `RefObjectType` with optional attribute `refname`.
- `StudyRef` for `ImageType`, `AnnotationType`, and `ObervationType` is now optional and with `maxOccurs=1`.
- `AnnotationType` can now only have one `IMAGE_REF`.

## [0.8.0] - 2023-11-14

### Changed

- Added _REF to the name of all `RefObjectType` elements and simplified type definition.
- Removed nesting `observed on` element in `ObservationType`.

## [0.7.0] - 2023-11-09

### Changed

- Changed max occurs of "CREATED_FROM" in SlideType to 1.
- Split observer definition from observation file to BP.observer.xsd.
- Renamed `BPAttributesType` to `AttributesType` and the contained `ATTRIBUTE` element to `STRING_ATTRIBUTE`, the `CODED_ATTRIBUTE` to `CODE_ATTRIBUTE`, and the `ATTRIBUTE_SET` element to `SET_ATTRIBUTE`.
- Renamed `CodedAttributeType` to `CodeAttributeType` and `BPCodedAttributesType` to `CodeAttributesType`.
- Renamed `AttributeSetType` to `SetAttributeType` and moved the contained attribute sequence to a `VALUE`-element of `AttributesType` that is nillable.
- Normalized names for attributes in `StatementType`.
- Normalized name for set of datasets to `DATASET_SET` and element names to `DATASET`.

## [0.6.0] - 2023-07-07

### Added

- MeasurementAttributeType for measurements with numeric value and a unit.

### Changed

- NumericAttributeType can no longer have a unit.
- Renamed `CODE` in CodedAttributeType to `VALUE`.

## [0.5.0] - 2023-06-30

### Added

- OBSERVER_TYPE for OBSERVER

### Fixed

- Min occurs for OBSERVER for ObservationType set to 0 .
- Max occurs for FILES for ImageType set to 1.

## [0.4.0] - 2023-06-30

### Changed

- Checksum required for FileBaseType.
- ImageType now must contain at least one FILES-element.
- String, Numeric, and Coded AttributeType are now nillable. This is likely a breaking change, especially the changes to CodedAttributeType.
- The ATTRIBUTES-element for BPObjectType and CODED_ATTRIBUTES_SET, CUSTOM_ATTRIBUTES_SET, FREETEXT, and ATTRIBUTES elements for StatementType and OBSERVER-element on ObservationType now haw a minOccours of 1 and are nillable.

### Removed

- Support for MD5 checksums.

## [0.3.0] - 2023-01-16

### Added

- BP.submission.xsd derived from SRA.submission.xsd with added BP types.

### Changed

- CaseType is now included in SAMPLE_SET
- SpecimenType can optionally reference a case with the PART_OF_CASE-element, replacing the RELATED_SPECIMENS-element on CaseType.
- For ObservationType the item an observation is made on is moved to the OBSERVED_ON-element.
- Replaced StatementCodedAttributeSetType and StatementCustomAttributeSetType with common types BPCodedAttributesType and BPAttributesType.
- Replaced Stain with Staining that can contain staining procedure information or stains

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

[Unreleased]: https://github.com/imi-bigpicture/metadata-schema/compare/0.6.0..HEAD
[0.6.0]: https://github.com/imi-bigpicture/metadata-schema/compare/v0.5.0..v0.6.0
[0.5.0]: https://github.com/imi-bigpicture/metadata-schema/compare/v0.4.0..v0.5.0
[0.4.0]: https://github.com/imi-bigpicture/metadata-schema/compare/v0.3.0..v0.4.0
[0.3.0]: https://github.com/imi-bigpicture/metadata-schema/compare/v0.2.0..v0.3.0
[0.2.0]: https://github.com/imi-bigpicture/metadata-schema/compare/v0.1.1..v0.2.0
[0.1.1]: https://github.com/imi-bigpicture/metadata-schema/compare/v0.1.0..v0.1.1
[0.1.0]: https://github.com/imi-bigpicture/metadata-schema/tree/refs/tags/v0.1.0
