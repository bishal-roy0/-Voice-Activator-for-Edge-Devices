# Shared interface decisions

No initial wire format or model configuration is approved yet. Do not rely on a value marked pending. Record the decision, owners, evidence, and approval date here before code depending on it merges to `dev`.

## Decision register

| Contract | Required decision | Owners | Acceptance evidence | Status |
| --- | --- | --- | --- | --- |
| Wake word | Phrase, pronunciation guidance, and collection rules. | Member 1, project leader | Dataset plan and team approval. | Pending |
| Training and firmware preprocessing | Sample rate, frame/window size, feature method, normalization, tensor shape, and output labels. | Members 1 and 2 | Model runs on ESP32-S3 with matching test input. | Pending |
| Wake decision | Confidence threshold, smoothing, cooldown, and false-activation target. | Members 1, 2, and 4 | Quiet/noisy evaluation results. | Pending |
| Post-wake audio | Encoding, sample rate, channels, maximum duration, end-of-command rule, and metadata. | Members 2 and 3 | Device-to-server sample transfer succeeds. | Pending |
| Device-to-server transport | HTTP or WebSocket, endpoint/path, authentication method, timeout, retry, and error behavior. | Members 2 and 3 | Network failure and success tests. | Pending |
| Server response | Recognized text, command result, ASR latency, total latency, status, and error fields. | Members 3 and 4 | Stable response consumed by dashboard/logging. | Pending |

## Change control

1. The affected owner proposes a decision with a testable value and rationale in a pull request.
2. Every module owner affected by the contract reviews it.
3. The project leader marks the decision approved with the date and links the validating test evidence.
4. Any incompatible change updates this register and dependent modules in the same planned integration cycle.
