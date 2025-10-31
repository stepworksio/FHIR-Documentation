# Practitioner

A person who is directly or indirectly involved in the provisioning of healthcare or related services.

## Scope and Usage

Practitioner covers all individuals who are engaged in the healthcare process and healthcare-related services as part of their formal responsibilities and this Resource is used for attribution of activities and responsibilities to these individuals. Practitioners include (but are not limited to):

-   physicians, dentists, pharmacists
-   physician assistants, nurses, scribes
-   midwives, dietitians, therapists, optometrists, paramedics
-   medical technicians, laboratory scientists, prosthetic technicians, radiographers
-   social workers, professional homecare providers, official volunteers
-   receptionists handling patient registration
-   IT personnel merging or unmerging patient records
-   service animal (e.g., ward assigned dog capable of detecting cancer in patients)
-   a bus driver for a community organization
-   a lawyer acting for a hospital or a patient
-   a person working for a supplier of a healthcare organization

The Practitioner resource is used for anyone involved in the provision of care or services to a Patient associated with an organization. The RelatedPerson resource is used for anyone involved in the care for a patient, typically having a personal *relationship *or non-healthcare-specific professional relationship to the patient.

## Table Name

-   Current: `marketing_contacts`
-   New: `fhir_practitioners`

## Table Columns

| Old Column    | New Column   | Old Type   | New Type         | Nullable | Default |
| ------------- | ------------ | ---------- | ---------------- | -------- | ------- |
| `id`          |              | `int`      | `cuid`           | No       |         |
| `created`     | `created_at` | `datetime` |                  | No       |         |
| `modified`    | `updated_at` | `datetime` |                  | No       |         |
| `active`      |              | `tinyint`  | `boolean`        | No       | `true`  |
| `staffID`     | `staff_id`   | `int`      |                  | No       |         |
| `orgId`       | `org_id`     | `int`      |                  | No       |         |
| `firstName`   | REMOVED      |            |                  |          |         |
| `lastName`    | REMOVED      |            |                  |          |         |
|               | `name`       |            | `HumanName[]`    | No       |         |
|               | `telecom`    |            | `ContactPoint[]` | No       | `[]`    |
| `role`        |              | `varchar`  |                  | No       |         |
| `email`       | REMOVED      |            |                  |          |         |
| `description` |              | `varchar`  |                  | Yes      | `NULL`  |
| `address`     |              |            | `Address[]`      | No       | `[]`    |
| `street`      | REMOVED      |            |                  |          |         |
| `street2`     | REMOVED      |            |                  |          |         |
| `zip`         | REMOVED      |            |                  |          |         |
| `phone`       | REMOVED      |            |                  |          |         |
| `phoneExt`    | REMOVED      |            |                  |          |         |
| `fax`         | REMOVED      |            |                  |          |         |
