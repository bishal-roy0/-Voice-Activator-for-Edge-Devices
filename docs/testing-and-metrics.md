# Testing and metrics

## Required evidence

| Metric | Definition | Owner | Evidence |
| --- | --- | --- | --- |
| True-positive rate | Correct wake detections divided by valid wake-word attempts. | Members 1 and 4 | Speaker, distance, and noise-condition test log. |
| False activations | Wake detections during non-wake speech/noise over a defined test duration. | Members 1, 2, and 4 | Negative-audio and live-environment log. |
| Model size / flash | Quantized model size and total deployed flash usage. | Members 1 and 2 | Build output and model artifact version. |
| RAM and idle CPU | Resource use while continuously listening. | Member 2 | Device measurement method and captured readings. |
| Wake-to-server latency | Time from wake-word end to command audio reaching the server. | Members 2 and 3 | Timestamped transfer test. |
| ASR and total latency | Server recognition time and full command-to-text time. | Members 3 and 4 | Timestamped end-to-end test. |

## Test conditions

Run and record tests in quiet and noisy conditions, with multiple speakers, accents, speaking speeds, distances, similar-sounding phrases, ordinary conversation, and empty/timeout audio. Keep train, validation, and test recordings separated by speaker/session where possible to prevent leakage.

## Test record template

For every test, record the date, firmware/model/backend revision, hardware, test condition, sample count or duration, expected result, observed result, metric value, and any failure notes. Store summaries in pull requests or a versioned results document; do not commit raw personal recordings.
