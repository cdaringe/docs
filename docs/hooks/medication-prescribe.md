# `medication-prescribe`

| Metadata | Value
| ---- | ----
| specificationVersion | 1.0
| hookVersion | 1.0

## Workflow

The user is in the process of prescribing one or more new medications.

## Context

The set of medications proposed or in progress of being prescribed. All FHIR resources in this context MUST be based on the same FHIR version.

Field | Optionality | Prefetch Token | Type | Description
----- | -------- | ---- | ---- | ----
`patientId` | REQUIRED | Yes | *string* |  The FHIR `Patient.id` of the current patient in context
`encounterId` | OPTIONAL | Yes | *string* |  The FHIR `Encounter.id` of the current encounter in context
`medications` | REQUIRED | No | *array* | DSTU2 - An array of MedicationOrder resources <br/> STU3 - An array of MedicationRequest resources

### Example (DSTU2)

```json 
"context":{
  "patientId":"1288992",
  "encounterId":"89284",
  "medications":{
    "resourceType":"Bundle",
    "entry":[
      {
        "resource":{
          "resourceType":"MedicationOrder",
          "id":"smart-MedicationOrder-103",
          "status":"draft",
          "patient":{
            "reference":"Patient/smart-1081332"
          },
          "medicationCodeableConcept":{
            "coding":[
              {
                "system":"http://www.nlm.nih.gov/research/umls/rxnorm",
                "code":"617993",
                "display":"Amoxicillin 120 MG/ML / clavulanate potassium 8.58 MG/ML Oral Suspension"
              }
            ],
            "text":"Amoxicillin 120 MG/ML / clavulanate potassium 8.58 MG/ML Oral Suspension"
          },
          "dosageInstruction":[
            {
              "text":"5 mL bid x 10 days",
              "timing":{
                "repeat":{
                  "boundsPeriod":{
                    "start":"2005-01-04"
                  },
                  "frequency":2,
                  "period":1,
                  "periodUnits":"d"
                }
              },
              "doseQuantity":{
                "value":5,
                "unit":"mL",
                "system":"http://unitsofmeasure.org",
                "code":"mL"
              }
            }
          ],
          "dispenseRequest":{
            "numberOfRepeatsAllowed":1,
            "quantity":{
              "value":1,
              "unit":"mL",
              "system":"http://unitsofmeasure.org",
              "code":"mL"
            },
            "expectedSupplyDuration":{
              "value":10,
              "unit":"days",
              "system":"http://unitsofmeasure.org",
              "code":"d"
            }
          }
        }
      },
      {
        "resource":{
          "resourceType":"MedicationOrder",
          "id":"smart-MedicationOrder-104",
          "status":"draft",
          "patient":{
            "reference":"Patient/smart-1081332"
          },
          "medicationCodeableConcept":{
            "coding":[
              {
                "system":"http://www.nlm.nih.gov/research/umls/rxnorm",
                "code":"211307",
                "display":"Azithromycin 20 MG/ML Oral Suspension [Zithromax]"
              }
            ],
            "text":"Azithromycin 20 MG/ML Oral Suspension [Zithromax]"
          },
          "dosageInstruction":[
            {
              "text":"15 mL daily x 3 days",
              "timing":{
                "repeat":{
                  "boundsPeriod":{
                    "start":"2005-01-18"
                  },
                  "frequency":1,
                  "period":1,
                  "periodUnits":"d"
                }
              },
              "doseQuantity":{
                "value":15,
                "unit":"mL",
                "system":"http://unitsofmeasure.org",
                "code":"mL"
              }
            }
          ],
          "dispenseRequest":{
            "numberOfRepeatsAllowed":1,
            "quantity":{
              "value":1,
              "unit":"mL",
              "system":"http://unitsofmeasure.org",
              "code":"mL"
            },
            "expectedSupplyDuration":{
              "value":3,
              "unit":"days",
              "system":"http://unitsofmeasure.org",
              "code":"d"
            }
          }
        }
      }
    ]
  }
}
```
## Change Log

Version | Description
---- | ----
1.0 | Initial Release
