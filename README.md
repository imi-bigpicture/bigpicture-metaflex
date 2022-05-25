# metadata-schema

Metadata schemas for BigPicture data submission. Based on ENA metadata schemas.

## Implemented MSMdad version

This version of the BigPicture metadata schema implements MSMdad version 0.1.0.

## Structure

The BigPicture-extension from the ENA metadata schema are located in files prefixed with BP.


### BP.common.xsd
Implements several types that are used FileBaseType which is in other BigPicture types:

- FileBaseType: Type for representing a submitted data file with filename and checksum.
- AttributeBaseType: A base attribute type that is identified by a `TAG`. NumericAttributeType, CodedAttributeType, and AttributeSetType extends from this type.
- NumericAttributeType: Version of the SRA AttributeType but for numeric values.
- CodedAttributeType: An attribute defined by code, schema, code meaning, and optional schema version.
- AttributeSetType: A complex attribute that can hold one or several AttributeType, NumericAttributeType, CodedAttributeType, and/or AttributeSetType.
- BPAttributesType: A collection of attributes of different types.
- BPObjectType: An extension of the SRA ObjectType with the addition of an a `BPAttributesType` element. The base SRA ObjectType has, among other attributes:

    - `alias`: Submitter designated name for the object. The name must be unique within the submission account.


### BP.sample.xsd
Implements the following types:

- BiologicalBeingType: A human being or animal.
- SpecimenType:A removed part of a human/animal being. The `EXTRACTED_FROM` element references the biological being the specimen was extracted from.
- BlockType: A part of a Specimen that has been sampled and processed for further investigation. This can for example be a block. The `SAMPLED_FROM` element references the specimen the block was sampled from.
- SlideType: A physical slide that has been created out of one or more Blocks. The `CREATED_FROM` element references the block the slide was created from.

All types extends the `BPObjectType`, and different types of attributes can thus be assigned to the `ATTRIBUTES` element.

### BP.image.xsd
Implements the ImageType that captures image objects. The ImageType extends the `BPObjectType` and has the following elements:

- `STUDY_REF`: Identifies the parent study.
- `IMAGE_OF`: One of more samples imaged by the image.
- `FILES`: Data files associated with the image.

### BP.annotation.xsd
Implements the AnnotationType that captures annotation objects. The AnnotationType extends the `BPObjectType` and has the following elements:

- `STUDY_REF`: Identifies the parent study.
- `IMAGE_REFERENCE`: One or more images associated with the annotation.
- `FILES`: Data files associated with the annotation.

### BP.dataset.xsd
Implements the BPDatasetType which is an extension of the EGA DatasetType with the additions of:
- `IMAGE_REF`: Identifies the images which are part of this dataset.
- `ANNOTATION_REF`: Identifies the annotations which are part of this dataset.


### BPschema.xsd
Collects the required schema files into one file through imports.

## Study, Policy, DAC, and Submission
The Study, Policy, DAC, and sumbission types are used as in EGA.

## License

Since the ENA metadata schemas are distributed under the Apache 2.0 license that's what we start with.
