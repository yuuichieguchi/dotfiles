# Azure Speech SDK Development Instructions

Read CLAUDE.md for universal coding rules, then apply the following Python/FastAPI/Azure Speech SDK specific patterns.

## CRITICAL: Always Check Documentation First

Before writing ANY Azure Speech SDK code, you MUST consult:
- Docs: https://learn.microsoft.com/en-us/azure/ai-services/speech-service/speech-sdk
- Samples: https://github.com/Azure-Samples/cognitive-services-speech-sdk/tree/master/samples/python

## Key Rules

1. **Never code from memory** - SDK changes frequently
2. **Verify current syntax** - Check official samples for the exact feature
3. **Use latest patterns** - Especially for async/await with FastAPI
4. **Check authentication** - Methods may have changed
5. **Private Endpoint** - We use private endpoints; verify custom domain and network config

## Common Implementation Areas

- **Speech-to-Text**: Check `/samples/python/console/` for recognition patterns
- **Text-to-Speech**: Verify SSML syntax and voice selection
- **WebSocket streaming**: Confirm FastAPI integration patterns
- **Error handling**: Use exception types from current samples
- **Private Endpoint**: Use custom domain URL, not default `.cognitiveservices.azure.com`

## Quick Check Commands

```bash
pip show azure-cognitiveservices-speech  # Verify version
pip install --upgrade azure-cognitiveservices-speech  # Update if needed
```

⚠️ **NEVER write code without checking the official documentation and samples FIRST**
