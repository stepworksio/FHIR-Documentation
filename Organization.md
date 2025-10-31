# Organization

A formally or informally recognized grouping of people or organizations formed for the purpose of achieving some form of collective action. Includes companies, institutions, corporations, departments, community groups, healthcare practice groups, payer/insurer, etc.

## Scope and Usage

This resource may be used in a shared registry of contact and other information for various organizations or it can be used merely as a support for other resources that need to reference organizations, perhaps as a document, message or as a contained resource. If using a registry approach, it's entirely possible for multiple registries to exist, each dealing with different types or levels of organization.

## Table Name

-   Current: `marketing_organizations`
-   New: `fhir_organizations`

## Table Columns

| Old Column    | New Column   | Old Type   | New Type                                                                                             | Nullable | Default |
| ------------- | ------------ | ---------- | ---------------------------------------------------------------------------------------------------- | -------- | ------- |
| `id`          |              | `int`      | `cuid`                                                                                               | No       |         |
| `created`     | `created_at` | `datetime` |                                                                                                      | No       |         |
| `modified`    | `updated_at` | `datetime` |                                                                                                      | No       |         |
| `active`      |              | `tinyint`  | `boolean`                                                                                            | No       | `true`  |
| `staffID`     | `staff_id`   | `int`      |                                                                                                      | No       |         |
| `parentID`    | `part_of_id` | `int`      | `cuid`                                                                                               | Yes      | `NULL`  |
| `type`        |              | `varchar`  | `{ "text": prov \| dept \| team \| govt \| ins \| pay \| edu \| reli \| crs \| cg \| bus \| other }` | No       |         |
|               | `name`       | `varchar`  |                                                                                                      | No       |         |
| `description` |              | `varchar`  |                                                                                                      | Yes      | `NULL`  |
|               | `contact`    |            | `ExtendedContactDetail[]`                                                                            | No       |         |
| `street`      | REMOVED      |            |                                                                                                      |          |         |
| `street2`     | REMOVED      |            |                                                                                                      |          |         |
| `zip`         | REMOVED      |            |                                                                                                      |          |         |
| `phone`       | REMOVED      |            |                                                                                                      |          |         |
| `fax`         | REMOVED      |            |                                                                                                      |          |         |
