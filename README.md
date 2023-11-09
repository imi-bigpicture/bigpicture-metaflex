# metadata-schema

Metadata schemas for BIGPICTURE data submission. Based on SRA/EGA/ENA metadata schemas.

## BIGPICTURE Metadata Specification Dependencies

This version of the BIGPICTURE Metadata Storage File Fromat Specification (v.0.6.0) complies to and depends on:

- The Common Mandatory Metadata Structure (CMMS) version 0.1.1
- The Mandatory Submission Metadata for Directly Accessible Datasets (MSMdad) version 0.1.1

## Structure

The schema developed explicitly for BIGPICTURE, extending the SRA/EGA/ENA metadata schema, are located in files prefixed with BP. The following paragraphs discuss each of the newly created files in more depth.

### BP.common.xsd

Implements several types that are used FileBaseType which is in other BIGPICTURE types:

- FileBaseType: Type for representing a submitted data file with filename and checksum.
- AttributeBaseType: A base attribute type that is identified by a `TAG`. StringAttributeType, NumericAttributeType, MeasurementAttributeType, CodeAttributeType, and SetAttributeType extends from this type.
- StringAttributeType: An attribute for a string value.
- NumericAttributeType: An attribute for a numeric value.
- MeasurementAttributeType: An attribute for a numeric value and a string unit.
- CodeAttributeType: An attribute defined by code, schema, code meaning, and optional schema version.
- SetAttributeType: A complex attribute that can hold one or several AttributeType, NumericAttributeType, CodeAttributeType, and/or SetAttributeType.
- AttributesType: A collection of attributes of different types.
- BPObjectType: An extension of the SRA ObjectType with the addition of an a `AttributesType` element. The base SRA ObjectType has, among other attributes:

  - `alias`: Submitter designated name for the object. The name must be unique within the submission account.

### BP.sample.xsd

Implements the following types:

- BiologicalBeingType: A human being or animal.
- SpecimenType: A removed part of a human/animal being. The `EXTRACTED_FROM` element references the biological being the specimen was extracted from.
- BlockType: A part or a collection of parts of one or many Specimens that has/have been sampled and processed for further investigation. This can for example be a block. The `SAMPLED_FROM` element references the specimen(s) the block was sampled from.
- SlideType: A physical slide that has been created out of one or more Blocks. The `CREATED_FROM` element references the block the slide was created from.

All types extends `BPObjectType`, and different types of attributes can thus be assigned to the `ATTRIBUTES` element.

### BP.image.xsd

Implements the ImageType that captures image objects. The ImageType extends `BPObjectType` and has the following elements:

- `STUDY_REF`: Identifies the parent study.
- `IMAGE_OF`: Identifies the slide the image was imaged from.
- `FILES`: Data files associated with the image.

### BP.annotation.xsd

Implements the AnnotationType that captures annotation objects. The AnnotationType extends `BPObjectType` and has the following elements:

- `STUDY_REF`: Identifies the parent study.
- `IMAGE_REF`: One or more images associated with the annotation.
- `FILES`: Data files associated with the annotation.

### BP.dataset.xsd

Implements the BPDatasetType which is an extension of the EGA DatasetType with the additions of:

- `IMAGE_REF`: Identifies the images which are part of this dataset.
- `ANNOTATION_REF`: Identifies the annotations which are part of this dataset.

### BP.observation.xsd

Implements the ObservationType that captures observation objects. The ObservationType extends `BPObjectType` and has the following elements:

- `STUDY_REF`: Identifies the parent study.
- `OBSERVER`: Identifies the observer (optional).
- `STATEMENT`: The statement for the observation.

The object that the observation references is defined by using one (and only one) of the following elements:

- `ANNOTATION`: Identifies the referenced annotation.
- `CASE`: Identifies the referenced case.
- `BIOLOGICALBEING`: Identifies the referenced biological being.
- `SPECIMEN`: Identifies the referenced specimen.
- `BLOCK`: Identifies the referenced block.
- `SLIDE`: Identifies the referenced slide.
- `IMAGE`: Identifies the referenced image.

The `STATEMENT` is of StatementType, which has the following elements:

- `STATEMENT_TYPE`: The type of the statement. Either:
  - `Diagnosis`
  - `Macroscopic Description`
  - `Microscopic Description`
  - `Finding`
- `STATEMENT_STATUS`: The status of the statement. Either:
  - `Summary`: Integrating downstream information into the statement about the given entity, thereby the statement is not necessarily true for all downstream entities (e.g. BP Images) but only true for the entire collection/set of downstream or related entities.
  - `Distinct`: The statement is true for the entity it is related to and all downstream entities.
- `CODE_ATTRIBUTES_SET`: These types of attributes refer to attributes that can be coded by the means of some internationally or at least published schema, classification, nomenclature or ontology. They comprise the same functionality as all `CodeAttributeTypes` in the BP XSD Schema. As the complexity of a pathological statement can be in many instances not be coded using only one Ontology/Classifiation/Nomenclature (I.e. ICDO + TNM or multiple SEND/CDISC Variables) it was decided that one can add multiple coded Attributes to a given statement.
- `CUSTOM_ATTRIBUTES_SET`: These types of attributes refer to information which can be stored by the means of a 'TAG' > 'VALUE' concept. All different types of BP XSD Schema Attributes can be used here.  As the complexity of a pathological statement can require a set of Custom Attributes (I.e. set of customly defined morphological descriptors) it was decided that multiple Custom Attributes can be assigned to a given statement.
- `FREETEXT`: This section of a statement comprises information that is only available as free text. It should be used to store original unparsed data, extracted from some source.

### BP.staining.xsd

Implements the StainType that captures stain objects. The StainType extends `BPObjectType`. A stain is defined by Attributes (string, coded, numeric or set) using tags `staining_compound`, `taining_target`, `staining_method`, `staining_reporter_type`, and/or `staining_reporter`.

### BP.case.xsd

Implements the CaseType that represents a pathological case that references one biological being and one or more specimens. The CaseType extends `BPObjectType` and has the following elements:

- `BIOLOGICAL_BEING`: Reference to the biological being the case belongs to.
- `RELATED_SPECIMEN`: References to specimens belonging to the case.

### BP.schema.xsd

Collects the required schema files into one file through imports.

## Study, Policy, DAC, and Submission

The Study, Policy, DAC, and sumbission types are used as in EGA.

## License

Since the SRA/EGA/ENA metadata schemas are distributed under the Apache 2.0 license that's what we start with.

## Acknowledgement

This project is part of a project that has received funding from the Innovative Medicines Initiative 2 Joint Undertaking under grant agreement No 945358. This Joint Undertaking receives support from the European Union’s Horizon 2020 research and innovation programme and EFPIA. IMI website: <www.imi.europa.eu>
