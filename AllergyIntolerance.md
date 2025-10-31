# AllergyIntolerance

Risk of harmful or undesirable physiological response which is specific to an individual and associated with exposure to a substance.

## Scope and Usage

A record of a clinical assessment of an allergy or intolerance; a propensity, or a potential risk to an individual, to have an adverse reaction on future exposure to the specified substance, or class of substance.

Where a propensity is identified, to record information or evidence about a reaction event that is characterized by any harmful or undesirable physiological response that is specific to the individual and triggered by exposure of an individual to the identified substance or class of substance.

Substances include, but are not limited to: a therapeutic substance administered correctly at an appropriate dosage for the individual; food; material derived from plants or animals; or venom from insect stings.

## Table Name

-   Current: `client_allergies`
-   New: `fhir_allergy_intolerances`

## Table Columns

| Old Name    | New Name         | Old Type       | New Type                                              | Nullable | Default                 |
| ----------- | ---------------- | -------------- | ----------------------------------------------------- | -------- | ----------------------- |
| `id`        |                  | `int(11)`      | `cuid`                                                | No       |                         |
|             | `legacy_id`      | `int`          |                                                       | Yes      | `NULL`                  |
| `created`   | `created_at`     | `datetime`     |                                                       | No       |                         |
| `modified`  | `updated_at`     | `datetime`     |                                                       | No       |                         |
| `active`    |                  | `tinyint(1)`   | `boolean`                                             | No       | `true`                  |
| `staffID`   | `staff_id`       | `int(11)`      |                                                       | No       |                         |
| `clientID`  | `patient_id`     | `int(11)`      |                                                       | No       |                         |
| `substance` | `code`           | `varchar(255)` | `{ "text": string }`                                  | No       |                         |
|             | `type`           |                | `{ "text": allergy \| intolerance }`                  | No       | `{ "text": "allergy" }` |
|             | `category`       |                | `food` \| `medication` \| `environment` \| `biologic` | No       |                         |
|             | `last_occurence` |                | `datetime`                                            | Yes      | `NULL`                  |
| `notes`     | `reaction`       | `varchar(255)` | `{ "manifestation": { "text": string }[] }[]`         | No       | `[]`                    |

## Added fields

### `type`

The `type` field identifies what kind of adverse reaction is being documented — specifically whether it’s an allergy (immune-mediated) or an intolerance (non-immune response).

-   **Clinical clarity:** Helps differentiate between immune-based allergies (e.g. penicillin → anaphylaxis) and non-immune intolerances (e.g. lactose → GI upset).
-   **Improved safety alerts:** Systems can tailor their warnings — e.g., flagging anaphylaxis risks differently from mild intolerances.
-   **Better coding & interoperability:** Aligns with FHIR’s `AllergyIntolerance.type` to allow accurate export/import with other systems.
-   **Data quality:** Prevents confusion where both allergic and non-allergic reactions were historically lumped together in one field.

⸻

### `category`

The `category` field classifies the type of substance or exposure that caused the adverse reaction.

Typical values include:

-   `food` — e.g., shellfish, nuts
-   `medication` — e.g., amoxicillin, morphine
-   `environment` — e.g., pollen, dust
-   `biologic` — e.g., vaccines, hormones
-   **Structured filtering:** Allows clinicians and staff to quickly find relevant categories (e.g., “show all medication allergies”).
-   **Simplified workflows:** Enables logic like hiding environmental allergies when entering a new prescription.
-   **Reporting & analytics:** Useful for dashboards — e.g., “most common medication allergies in facility.”
-   **FHIR alignment:** Matches `AllergyIntolerance.category`, making FHIR exports straightforward.

⸻

### `lastOccurrence`

The `lastOccurrence` field records the most recent known time the reaction occurred.

-   **Clinical significance:** A reaction that occurred recently is more relevant than one decades ago.
-   **Risk assessment:** Providers can better determine whether the allergy is still active or might have resolved.
-   **Tracking improvement:** Supports documentation of desensitization therapy or tolerance development.
-   **FHIR compliance:** Directly corresponds to `AllergyIntolerance.lastOccurrence`, ensuring consistent FHIR data representation.
-   **Data analysis:** Enables time-based insights (e.g., recurring reactions, trends, or outdated allergy data).
