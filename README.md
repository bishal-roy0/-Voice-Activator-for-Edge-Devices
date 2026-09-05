# Voice Activator for Edge Devices

A low-cost, low-power voice activation system for ESP32-S3. A custom TinyML model listens locally for a wake word. Only after detection does the device record a spoken command and send it to a remote, open-source ASR/STT service.

## Project goals

- Keep wake-word detection local to the ESP32-S3.
- Use an open-source TinyML and ASR/STT stack.
- Target less than 256 KB RAM and under 10% idle CPU while listening.
- Measure accuracy, false activations, model size, RAM, CPU, and end-to-end latency.
- Demonstrate the complete pipeline on physical low-power hardware.

The core pipeline is: microphone -> ESP32-S3 -> preprocessing -> TinyML wake-word detection -> command recording -> Wi-Fi -> ASR/STT server -> text -> command handler/dashboard.

## Repository map

| Area | Owner | Purpose |
| --- | --- | --- |
| [`tinyml/`](tinyml/README.md) | Member 1 | Dataset rules, training, quantization, and model evaluation. |
| [`esp32/`](esp32/README.md) | Member 2 | ESP32-S3 microphone, inference, state machine, and streaming firmware. |
| [`server/`](server/README.md) | Member 3 | Audio receiver, ASR/STT, and command mapping. |
| [`dashboard/`](dashboard/README.md) | Member 4 | Integration status, logs, metrics, testing, and demo evidence. |
| [`docs/`](docs/architecture.md) | All members | Architecture, decisions, handoffs, and test evidence. |

## Start here

1. Read the [architecture](docs/architecture.md), [team tasks](docs/team_tasks.md), and [interface decision log](docs/interfaces.md).
2. The team agrees on the custom wake word and freezes the first audio/interface contract before cross-module integration.
3. Each member creates work on their own branch and opens a pull request into `dev`.
4. The project leader reviews integration-ready work in `dev`; only tested `dev` changes move to `main`.

## Branch workflow

```text
member branch -> pull request to dev -> review and integration testing -> pull request to main
```

Use the following branches:

- `main` - stable, demo-ready work only.
- `dev` - shared integration branch.
- `member1-tinyml`, `member2-esp32`, `member3-server`, `member4-integration` - member working branches.

Never commit Wi-Fi credentials, API keys, `.env` files, raw recordings, or generated model binaries. See [CONTRIBUTING.md](CONTRIBUTING.md) before opening a pull request.

## Scope boundary

The core solution does not use proprietary wake-word SDKs, cloud wake-word APIs, continuous ASR, TTS, or an LLM. Optional features can be considered only after the wake -> stream -> ASR pipeline is demonstrated and measured.

## License

This project is licensed under the [GNU GPL v3.0](LICENSE).
