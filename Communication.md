# Communication

A clinical or business level record of information being transmitted or shared; e.g. an alert that was sent to a responsible provider, a public health agency communication to a provider/reporter in response to a case report for a reportable condition.

## Scope and Usage

The purpose of a Communication resource is to surface that data was shared to track adherence to guidelines or protocols or to provide business documentation of actions taken. Communication can also be used as part of an information exchange to provide context about the information sharing occurring. Please see below for guidance on when this is appropriate.

Communication is one of the event resources in the FHIR workflow specification.

This resource is a record of a communication even if it is planned or has failed. A communication is a record of the conveyance of information from one entity, a sender, to another entity, a receiver. The sender and receivers may be patients, practitioners, related persons, organizations, or devices. Communication use cases include:

-   A reminder or alert delivered to a responsible provider
-   A recorded notification from the nurse to the on-call physician (or any other specified person) that a patient's temperature exceeds a value
-   A response from a public health agency to a provider caring for a patient presenting with a communicable disease reportable to the public health agency
-   Patient educational material sent by a provider to a patient
-   Unable to deliver lab results to ordering physician
-   Submission of supplementary health information to a payer in support of a claim

Non-patient specific communication use cases may include:

-   A nurse call from a hall bathroom
-   Advisory for battery service from a pump

## Table Name

-   Current: `marketing_note`
-   New: `fhir_communications`

## Table Columns

| Old Column          | New Column   | Old Type   | New Type                                                                                                                                                                                                                             | Nullable | Default |
| ------------------- | ------------ | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------- | ------- |
| `id`                |              | `int`      | `cuid`                                                                                                                                                                                                                               | No       |         |
|                     | `legacy_id`  | `int`      |                                                                                                                                                                                                                                      | Yes      | `NULL`  |
| `created`           | `created_at` | `datetime` |                                                                                                                                                                                                                                      | No       |         |
| `modified`          | `updated_at` | `datetime` |                                                                                                                                                                                                                                      | No       |         |
| `active`            |              | `tinyint`  | `boolean`                                                                                                                                                                                                                            | No       | `true`  |
| `staffID`           | `staff_id`   | `int`      |                                                                                                                                                                                                                                      | No       |         |
| `contactID`         | `sender_id`  | `int`      | `cuid`                                                                                                                                                                                                                               | No       |         |
| `touchDate`         | `sent`       | `datetime` |                                                                                                                                                                                                                                      | No       |         |
| `communicationType` | `medium`     | `varchar`  | `{ "text": PHYSICAL \| REMOTE \| VERBAL \| DICTATE \| FACE \| PHONE \| VIDEOCONF \| WRITTEN \| FAXWRIT \| HANDWRIT \| MAILWRIT \| ONLINEWRIT \| EMAILWRIT \| TYPEWRIT \| MSGWRIT \| SMSWRIT \| MMSWRIT \| APPWRIT \| ELECTRONIC }[]` | No       |         |
| `note`              | `payload`    | `varchar`  | `{ "contentCodeableConcept": { "text": string } }[]`                                                                                                                                                                                 | No       |         |
|                     | `follow_up`  |            | `{ "requestedPeriod"?: Period, "note"?: string }`                                                                                                                                                                                    | No       |         |
| `followupDate`      | REMOVED      |            |                                                                                                                                                                                                                                      |          |         |
| `followupNote`      | REMOVED      |            |                                                                                                                                                                                                                                      |          |         |
