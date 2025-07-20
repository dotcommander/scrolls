# Endless Scrolls Prompt System

## Overview

All prompts are now external for easy customization and hot reloading. No code changes needed to modify prompts!

## Directory Structure

```
prompts/
├── README.md           # This file
├── config.json         # Main configuration
└── styles/             # Style-specific system prompts
    ├── dramatic-system.txt
    ├── academic-system.txt
    ├── mystical-system.txt
    ├── investigative-system.txt
    ├── poetic-system.txt
    └── scientific-system.txt
```

## How to Add a New Style

1. Add style definition to `config.json`:
```json
"newstyle": {
  "name": "New Style",
  "description": "Description of your style",
  "temperature": 0.7,
  "maxTokens": 2000,
  "systemPromptFile": "styles/newstyle-system.txt",
  "userPromptTemplate": "Write an article about: {topic}",
  "keywords": {
    "min": 8,
    "max": 12
  }
}
```

2. Create `styles/newstyle-system.txt` with your system prompt

3. Reload prompts with 'R' key (in dev mode) or refresh the page

## Hot Reloading

In development mode (localhost):
- Press 'R' to reload all prompts without refreshing
- Changes take effect immediately for new articles
- Version number shown in reload confirmation

## Configuration Options

### Style Config
- `temperature`: Controls creativity (0.0-1.0)
- `maxTokens`: Maximum response length
- `systemPromptFile`: Path to system prompt file
- `userPromptTemplate`: Template for user prompts
- `keywords.min/max`: Keyword count range

### Global Options
- `basePrompt`: Shared base prompt for all styles
- `contextualPrompts`: Templates for "dig deeper", "mythology", "trivia"
- `formatting.rules`: Shared formatting instructions

## Tips

1. **Test prompts quickly**: Use number keys 1-6 to switch styles
2. **Clear cache**: Cmd/Ctrl+Shift+C to test new prompts
3. **Version your changes**: Update version in config.json
4. **Keep prompts focused**: Style-specific instructions in system files
5. **Use Wikipedia rule**: Tell AI to link anything with a Wikipedia page