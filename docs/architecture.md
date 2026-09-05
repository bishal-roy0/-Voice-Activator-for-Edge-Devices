# System architecture

## Approved core flow

```text
I2S microphone
  -> ESP32-S3 audio capture and buffering
  -> preprocessing compatible with the TinyML training pipeline
  -> local TinyML wake-word inference
  -> command recording after a positive wake decision
  -> Wi-Fi transfer to the ASR/STT server
  -> recognized text and command result
  -> dashboard/logs and demo action
```

Wake-word detection runs continuously on the device. Remote ASR receives only post-wake command audio. The core pipeline must use open-source software and must not replace local wake-word detection with a cloud or proprietary SDK.

## Device state machine

| State | Entry condition | Required behavior | Exit condition |
| --- | --- | --- | --- |
| `LISTENING` | Device starts or a prior request completes | Capture frames and run local wake-word inference. | Accepted wake decision. |
| `WAKE_DETECTED` | Confidence passes the approved threshold | Log confidence and prepare command capture. | Command capture starts or a short guard interval ends. |
| `RECORD_COMMAND` | Wake event accepted | Capture only the following command audio. | End-of-command, timeout, or user cancellation. |
| `SEND_TO_SERVER` | Command audio is available | Send agreed audio and metadata; handle timeout/error safely. | Response, retry limit, or failure. |
| `LISTENING` | Request resolves or fails | Resume low-power wake-word listening. | Next accepted wake decision. |

## Non-negotiable compatibility rule

The TinyML training pipeline and ESP32 preprocessing must use the same approved sample rate, windowing, feature extraction, tensor shape, and output interpretation. The exact initial values are recorded only after agreement in [interfaces.md](interfaces.md).
