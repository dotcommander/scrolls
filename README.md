# Endless Scrolls

An interactive web explorer that presents interconnected articles in a conspiracy theory aesthetic. Navigate through mysterious topics, uncover hidden connections, and explore alternative perspectives on reality.

## Features

- **Dynamic Article Generation**: Powered by OpenAI-compatible APIs for endless content
- **Multiple Writing Styles**: Switch between conspiracy, academic, and mystical perspectives
- **Interactive Navigation**: Click keywords to explore related topics
- **Smart Caching**: Articles cached for 7 days to minimize API costs
- **Favorites System**: Save interesting articles for later reference
- **Search Functionality**: Find articles by content or tags
- **Developer Mode**: Advanced tools for testing and debugging
- **Progressive Enhancement**: Works without API key using static content

## Prerequisites

- Modern web browser (Chrome, Firefox, Safari, Edge)
- OpenAI API key (optional, for dynamic content generation)
- Web server or local file access

## Installation

1. Clone the repository:
```bash
git clone git@github.com:dotcommander/scrolls.git
cd scrolls
```

2. Configure API access (optional):
```bash
cp public/config.local.js.example public/config.local.js
# Edit config.local.js with your API key
```

3. Open in browser:
   - Direct file: Open `public/index.html` in your browser
   - Local server: Serve the `public/` directory with any web server

## Usage

### Basic Navigation
- Click any highlighted keyword to explore related topics
- Use breadcrumbs to navigate back through your reading history
- Click the heart icon to save articles to favorites
- Use the search icon to find specific topics

### Model Switching
Click the model name in the footer to cycle through:
- `gpt-4.1`: Advanced reasoning and creativity
- `gpt-4o`: Optimized performance
- `gpt-4o-mini`: Cost-effective option
- `gpt-4.1-mini`: Balanced performance

### Developer Mode
Activates automatically on localhost or with `?dev=true`. Press `Cmd/Ctrl + .` to open the developer panel.

**Keyboard Shortcuts:**
- `Cmd/Ctrl + .` - Toggle developer panel
- `Cmd/Ctrl + K` - Quick search
- `Cmd/Ctrl + Shift + C` - Clear all caches
- `1, 2, 3` - Quick style switching
- `R` - Reload prompt configuration
- `?` - Show help

## Configuration

### API Setup
1. Click the settings icon (gear) in the header
2. Enter your OpenAI API key
3. Optionally configure a custom endpoint for local models
4. Test connection before saving

### Writing Styles
The application supports three writing styles, configurable in `public/prompts/config.json`:
- **Conspiracy**: Deep state revelations and hidden truths
- **Academic**: Scholarly exploration of fringe theories
- **Mystical**: Esoteric wisdom and occult knowledge

### Adding Custom Styles
1. Add style definition to `prompts/config.json`
2. Create system prompt file in `prompts/styles/`
3. Style automatically appears in UI

## Project Structure

```
scrolls/
├── public/
│   ├── index.html          # Main application (HTML, CSS, JS)
│   ├── config.local.js.example  # API configuration template
│   └── prompts/
│       ├── config.json     # Prompt configuration
│       └── styles/         # Writing style templates
│           ├── conspiracy-system.txt
│           ├── academic-system.txt
│           └── mystical-system.txt
├── CLAUDE.md              # AI assistant instructions
└── README.md              # This file
```

## Architecture

The application is built as a self-contained single-page application with:
- **No build process**: Direct browser execution
- **No dependencies**: Pure HTML, CSS, and JavaScript
- **Modular prompts**: Externalized prompt system for easy customization
- **Local-first design**: All data stored in browser localStorage

## Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'feat: add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- Inspired by interconnected wiki systems and conspiracy theory websites
- Built for exploration of alternative narratives and hidden connections
- Designed to question consensus reality while maintaining plausible deniability