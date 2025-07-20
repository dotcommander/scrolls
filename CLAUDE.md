# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Endless Scrolls is a self-contained, single-page web application that presents interconnected articles in an interactive explorer format. The entire application lives in `/public/index.html` with no build process or dependencies.

## Architecture

### Single File Structure
- **Location**: `/public/index.html` (1876 lines)
- **CSS**: Lines 14-948 - Responsive styles with mobile-first design
- **JavaScript**: Lines 950-1815 - `ScrollsExplorer` class handling all functionality
- **Content**: Article content embedded in `articleLibrary` object

### Key Components

1. **ScrollsExplorer Class**
   - Manages article navigation and history
   - Handles favorites with LocalStorage persistence
   - Implements search functionality
   - Controls model switching (gpt-4.1, gpt-4o, etc.)
   - Simulates article generation with loading animations

2. **Article System**
   - Articles stored in `articleLibrary` object
   - Keywords in articles are clickable links to related topics
   - Breadcrumb navigation tracks reading history
   - Each article has tags for categorization

3. **Interactive Elements**
   - Quick action buttons: mythology, dig deeper, trivia, surprise me, genealogy
   - Search toggle with animated reveal
   - Favorites system with add/remove functionality
   - Model switcher cycling through AI models

## Development Commands

Since this is a static HTML file:
- **Run locally**: Open `/public/index.html` in any web browser
- **Test changes**: Refresh browser after editing
- **Deploy**: Copy the public folder to any static hosting service

## API Integration

The application now supports OpenAI-compatible APIs for dynamic article generation:

### Key Components

1. **EndlessScrollsAPI Class** (lines 1369-1502)
   - Handles API communication with OpenAI-compatible endpoints
   - Implements intelligent caching (in-memory + localStorage)
   - Supports custom endpoints for local models or proxies

2. **Settings UI**
   - Click the settings icon (gear) in the header
   - Configure API key and endpoint
   - Test connection before saving
   - Manage article cache

3. **Model Switching**
   - Click on model name in footer to cycle through: gpt-4.1, gpt-4o, gpt-4o-mini, gpt-4.1-mini
   - Model selection persists across sessions
   - Each model's responses are cached separately

### API Features

- **Progressive Enhancement**: Works without API key using static articles
- **Smart Caching**: Articles cached for 7 days to minimize API costs
- **Error Handling**: Graceful fallback to static content on API errors
- **Prompt Engineering**: Maintains conspiracy theory aesthetic in generated content

## Prompt System

The application now supports externalized, customizable prompts:

### Directory Structure
```
public/prompts/
├── config.json              # Main configuration
└── styles/                  # Writing style templates
    ├── conspiracy-system.txt
    ├── academic-system.txt
    └── mystical-system.txt
```

### Configuration
The `prompts/config.json` file defines:
- Available writing styles (conspiracy, academic, mystical)
- Temperature and token settings per style
- Keyword themes and requirements
- User prompt templates with variables

### Adding New Styles
1. Add style definition to `config.json`
2. Create system prompt file in `styles/`
3. Style automatically appears in future UI updates

### Key Features
- **Hot Reloading**: Prompts loaded fresh on each request during development
- **Style Persistence**: Selected style saved in localStorage
- **Fallback Support**: Uses inline prompts if external files missing
- **Template Variables**: {topic}, {minKeywords}, {maxKeywords}

## Design Patterns

### Styling Approach
- All styles are inline in the HTML file
- Uses CSS custom properties for theming
- Mobile-first responsive breakpoints at 768px and 1024px
- Khaki/brown paper-like aesthetic throughout

### JavaScript Patterns
- Event delegation for dynamic content clicks
- LocalStorage for persistent user preferences
- Simulated async operations for loading states
- No external dependencies or frameworks

## Important Implementation Details

1. **Article Navigation**: Keywords wrapped in `<span class="keyword">` are automatically clickable
2. **Loading Simulation**: Uses `setTimeout` with random delays (800-2000ms) for realistic feel
3. **Model Switching**: Cycles through hardcoded model array, stored in LocalStorage
4. **Search**: Case-insensitive search through article content and tags
5. **Favorites**: Stored as array of article IDs in LocalStorage key 'scrollsFavorites'

## Adding New Content

To add new articles:
1. Add entry to `articleLibrary` object with unique ID
2. Include `title`, `content` (HTML string), and `tags` array
3. Use `<span class="keyword">existing-article-id</span>` for cross-references

## Developer Experience (DX) Features

### Development Mode
Activates automatically when:
- Running on localhost
- URL contains `?dev=true`
- Loading config.local.js (if present)

### Developer Panel (Cmd/Ctrl + .)
- **Quick Config**: Apply API key and switch styles instantly
- **Cache Management**: View and clear cache with stats
- **Quick Actions**: Reload prompts, test all styles, random articles
- **API Logs**: Real-time view of API calls with timing and status

### Keyboard Shortcuts
- `Cmd/Ctrl + .` - Toggle developer panel
- `Cmd/Ctrl + K` - Quick search
- `Cmd/Ctrl + Shift + C` - Clear all caches
- `1, 2, 3` - Quick style switching (conspiracy/academic/mystical)
- `R` - Reload prompt configuration
- `?` - Show help
- `D` - Load random dev topic (if configured)

### Auto-Configuration
1. Copy `config.local.js.example` to `config.local.js`
2. Set your API key and preferences
3. File auto-loads in dev mode
4. Supports multiple API endpoints (OpenAI, Ollama, custom)

### API Logging
In dev mode, all API calls are logged with:
- Request parameters (model, style, temperature)
- Response timing and token usage
- Cache hit/miss status
- Error details

### Development Tips
- Use `window.scrollsExplorer` in console for debugging
- Check `window.DEBUG = true` for verbose logging
- API logs show last 10 calls in dev panel
- Test prompts quickly with number keys (1-3)