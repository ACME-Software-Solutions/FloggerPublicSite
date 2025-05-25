---
title:  "Voice Transcription Strategies"
date:   2025-05-18 10:22:46 -0500
excerpt: "My custom excerpt"
---

Both iOS and Android offer on-device voice transcription.  This is fine for transcribing short messages, but probably does not compare well against dedicated models like OpenAI Whisper.  That said, it should be fine for transcribing Command Entries.

A Command Entry is a short vocal instruction to log something: "I drank 350 milliliters of water," "My neck hurts, five out of ten."  These instructions are transcribed and passed to a Router Model.  In addition to the transcribed audio command, the Router is given an API specification and is instructed to determine which Command to execute, along with the proper arguments needed to execute it.  You could probably leverage the OpenAPI spec in order to to that, which the LLM should be familiar with it. 

```
paths:
  /water-intake:
    post:
      summary: Record water intake
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/WaterIntake'
  /symptoms:
    post:
      summary: Record a symptom
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/SymptomRecord'
components:
  schemas:
    WaterIntake:
      type: object
      required:
        - amount
      properties:
        amount:
          type: number
          description: Amount of water consumed in ml.
          example: 250

    SymptomRecord:
      type: object
      required:
        - symptomName
        - severity
      properties:
        symptomName:
          type: string
          description: Name of the symptom.
          example: 'Neck pain'
        severity:
          type: integer
          description: Severity of the symptom (e.g., on a scale of 1-10).
          minimum: 1
          maximum: 10
          example: 3
```


For example, if the user says, "I drank 350ml water," the Router Model would view the API spec and determine that it should call the `/water-intake` input with a data object like `{ amount: 350 }`

### Options for handling command events

- Siri intent, generic intent name, "Hey Siri, log entry, 'I drank 350 milliliters of water,' with Flogger"
- Siri shortcut, record audio, send transcription to API, "Hey Siri, <shortcut name>" <wait for a chime> "I drank 350 milliliters of water"

The first one is on its face, much more ideal because you could avoid having to pause and wait for the app to load and begin recording.

Questions still persist: It would be *really* nice if the Command could be entered while the phone was locked.
