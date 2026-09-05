# ASR/STT backend module

**Owner:** Member 3

This module will contain the lightweight service that receives post-wake audio, validates it, invokes an open-source ASR/STT engine, returns recognized text and timing data, and maps simple demo commands.

Define the transport, audio contract, timeouts, retry behavior, and response shape with Member 2 and Member 4 in `docs/interfaces.md` before creating integration-dependent code. Never commit server credentials or access tokens.
