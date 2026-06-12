# Lesson 04 — APIs & Keys

**Phase:** 00 — Setup & Tooling  
**Type:** Build | **Lang:** Python, TypeScript  
**Estimated time:** ~30 min  
**Status:** ✅ Reviewed — pending execution (requires API credits)

---

## What this lesson covers

- Storing API keys securely using environment variables and Colab Secrets
- Making an LLM API call using the Anthropic Python SDK
- Understanding raw HTTP calls vs SDK calls
- Handling common API errors (auth, rate limits, insufficient credits)

---

## Key concepts

**Never put API keys in code.** Use environment variables or a secrets manager. In Colab, use the 🔑 Secrets panel — the key never appears in the notebook.

```python
# In Colab — load key from Secrets panel
from google.colab import userdata
import os
os.environ["ANTHROPIC_API_KEY"] = userdata.get("ANTHROPIC_API_KEY")
```

**Every API call has the same structure:**
- **Endpoint** — the URL you send the request to
- **API key** — authenticates your account
- **Request body** — what you want (model, messages, max_tokens)
- **Response body** — what you get back

**SDK vs raw HTTP** — the SDK is a wrapper around a plain HTTP POST request. Understanding the raw version helps when debugging errors:

```python
# SDK version
client = anthropic.Anthropic()
response = client.messages.create(
    model="claude-sonnet-4-6",
    max_tokens=256,
    messages=[{"role": "user", "content": "What is a neural network in one sentence?"}]
)

# Raw HTTP version — same thing under the hood
headers = {
    "x-api-key": os.environ["ANTHROPIC_API_KEY"],
    "anthropic-version": "2023-06-01",
}
```

---

## API keys needed for this course

| API | When | Free tier |
|-----|------|-----------|
| Anthropic (Claude) | Phases 11–16 | $5 credit on signup |
| OpenAI | Phase 11 | $5 credit on signup |
| Hugging Face | Phases 4–10 | Free |

---

## Errors encountered

**`SecretNotFoundError`** — the secret name in Colab didn't match exactly. Fixed by making sure the name was `ANTHROPIC_API_KEY` in uppercase with no spaces.

**`BadRequestError 400 — credit balance too low`** — API calls require a minimum credit balance. This is a billing issue, not a code issue. The SDK and key setup are correct.

---

## Reference

- [Original lesson](https://github.com/rohitg00/ai-engineering-from-scratch/tree/main/phases/00-setup-and-tooling/04-apis-and-keys)
- [Anthropic Console](https://console.anthropic.com)
