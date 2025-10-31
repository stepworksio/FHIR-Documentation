# Datatypes

The FHIR specification defines a set of datatypes that are used for the resource elements. There are five categories of datatypes:

-   The base abstract types that provide the foundation for all types
-   Simple / primitive types, which are single elements with a primitive value (below)
-   General-purpose complex types, which are re-usable clusters of elements (below)
-   MetaDatatypes: A set of types for use with metadata resources
-   Special purpose datatypes - defined elsewhere in the specification for specific usages: Reference, Meta, Narrative, Extension, xhtml, ElementDefinition and Dosage.

## Address

| Column       | Type                                             |
| ------------ | ------------------------------------------------ |
| `use`        | `home` \| `work` \| `temp` \| `old` \| `billing` |
| `type`       | `postal` \| `physical` \| `both`                 |
| `text`       | `string`                                         |
| `line`       | `string[]`                                       |
| `city`       | `string` \| `null` \| `undefined`                |
| `state`      | `string` \| `null` \| `undefined`                |
| `postalCode` | `string` \| `null` \| `undefined`                |

## CodeableConcept<T = undefined>

| Column | Type                            |
| ------ | ------------------------------- |
| `text` | `T === undefined ? string \| T` |

## ContactPoint

| Column   | Type                                                                |
| -------- | ------------------------------------------------------------------- |
| `system` | `phone` \| `fax` \| `email` \| `pager` \| `url` \| `sms` \| `other` |
| `value`  | `string`                                                            |
| `use`    | `home` \| `work` \| `temp` \| `old` \| `mobile`                     |

## HumanName

| Column   | Type                                                                                 |
| -------- | ------------------------------------------------------------------------------------ |
| `use`    | `usual` \| `official` \| `temp` \| `nickname` \| `anonymous` \| `old` \| `maiden` \| |
| `family` | `string`                                                                             |
| `given`  | `string[]`                                                                           |
| `prefix` | `string[]` \| `undefined`                                                            |
| `suffix` | `string[]` \| `undefined`                                                            |

## Period

| Column  | Type                |
| ------- | ------------------- |
| `start` | `Date \| undefined` |
| `end`   | `Date \| undefined` |
