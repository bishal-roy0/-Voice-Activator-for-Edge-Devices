# Team tasks and handoffs

| Member | Owns | Deliverables | Receives / hands off |
| --- | --- | --- | --- |
| Member 1 | Dataset and TinyML | Collection rules, labelled dataset process, training pipeline, quantized model, evaluation report. | Gives Member 2 the model, feature settings, tensor shape, output meaning, and proposed threshold. |
| Member 2 | ESP32-S3 firmware | I2S capture, local inference, state machine, Wi-Fi transfer, resource/timing logs. | Matches Member 1 preprocessing; agrees the audio transfer contract with Member 3. |
| Member 3 | ASR/STT backend | Audio receiver, open-source ASR/STT integration, text response, command mapping, latency logs. | Returns the agreed response structure to Member 4. |
| Member 4 | Integration and evaluation | End-to-end checklist, dashboard/logs, test evidence, metrics, and demo readiness. | Coordinates integration issues and publishes demo evidence. |

## Milestones

1. Create branches and approve this repository foundation.
2. Choose the wake word and approve the initial shared interfaces.
3. Validate ESP32-S3 microphone capture and train the first laptop/Colab model.
4. Deploy the model to ESP32-S3 and show wake detection with an LED/state signal.
5. Send post-wake audio to the backend and return recognized text.
6. Integrate the complete pipeline, capture metrics, optimize, and rehearse the demo.

## Definition of ready for integration

A module change is ready when its owner has documented the interface impact, supplied a repeatable test, recorded observed results, and opened a focused pull request to `dev`.
