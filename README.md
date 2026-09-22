# Safejev

[![Status](https://img.shields.io/badge/status-early%20development-F4B942?style=flat-square)](#status)
[![License](https://img.shields.io/badge/license-Apache%202.0-2D6A4F?style=flat-square)](https://github.com/anandsaini18/Safejev/blob/main/LICENSE)

Real-time safety checks for LLM reasoning.

Safejev is a Python library that watches the thinking stream of any Claude or OpenAI inference call. It sends each chunk of reasoning to [JEV](https://docs.typesafe.ai), TypeSafe's fast decision model, and writes a warning log whenever JEV is at least 75% confident the reasoning is unsafe. The model's stream never waits for the check.

## The idea

- **Enable it on any inference call.** Wrap your client once; your existing calls stay unchanged.
- **Works across providers.** Adapters for Anthropic and OpenAI, built on their official SDKs.
- **Your criteria.** You define the rules, such as safety hazards or a support ticket's category, sentiment, and urgency, and JEV evaluates each input against them.
- **Configurable threshold.** Flags at 0.75 by default. Every flag is a structured WARN log entry.

## Planned usage

```bash
pip install safejev
```

```python
import safejev
from anthropic import AsyncAnthropic
from openai import AsyncOpenAI

claude = safejev.monitor(AsyncAnthropic())
gpt = safejev.monitor(AsyncOpenAI())
# Streamed calls through these clients are now checked by Safejev.
```

## Status

Early development. The API above is planned and not implemented yet, and it may change.

## License

Copyright 2026 Mukul Saini. Licensed under the [Apache License 2.0](https://github.com/anandsaini18/Safejev/blob/main/LICENSE).

JEV is a model by TypeSafe. Safejev is an independent project and is not affiliated with TypeSafe.
