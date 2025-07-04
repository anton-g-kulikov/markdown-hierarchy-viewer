# Project Documentation

This document provides comprehensive information about the Markdown Hierarchy Viewer VS Code extension project.

## Project Overview

**Markdown Hierarchy Viewer** is a VS Code extension that provides beautiful live tree visualization for Markdown files. It displays document structure including headers, lists, paragraphs, and offers real-time updates with elegant typography.

## Architecture

### Core Components

1. **Extension Entry Point** (`src/extension.ts`)

   - Handles extension activation and deactivation
   - Registers commands and manages extension lifecycle

2. **Command Manager** (`src/commandManager.ts`)

   - Manages all extension commands
   - Coordinates between different components

3. **Markdown Parser** (`src/markdownParser.ts`)

   - Parses Markdown content into structured tree format
   - Handles headers, lists, paragraphs, and code blocks
   - Provides formatting and HTML escaping
   - **Enhanced List Processing**: Implements smart detection to distinguish between nested lists and indented code blocks
   - **Mixed Content Analysis**: Uses `isPartOfMixedCodeBlock` logic to correctly identify code blocks vs deeply nested lists
   - **Indentation Handling**: Properly processes list items with 4+ spaces indentation as lists, not code blocks

4. **Tree Renderer** (`src/treeRenderer.ts`)

   - Converts parsed tree structure into visual representation
   - Applies styling and generates HTML output

5. **Webview Manager** (`src/webviewManager.ts`)

   - Manages VS Code webview panels
   - Handles webview content updates and messaging

6. **Configuration Manager** (`src/configuration.ts`)

   - Manages extension settings and user preferences
   - Provides configuration access and defaults

7. **Style Manager** (`src/styleManager.ts`)

   - Handles CSS generation and styling logic
   - Manages theme integration and customization

8. **Logger** (`src/logger.ts`)

   - Provides centralized logging functionality

9. **File Detection** (`src/fileDetection.ts`)
   - Enhanced Markdown file detection beyond basic language ID checking
   - Supports multiple Markdown file extensions (.md, .markdown, .mdown, .mkd, etc.)
   - Content-based detection for files without proper extensions
   - Fallback detection for edge cases where VS Code doesn't properly identify Markdown files

### Key Features

- **Real-time Updates**: Live preview that updates as you edit
- **Beautiful Typography**: Elegant fonts and spacing
- **Customizable Styling**: User-configurable colors, fonts, and symbols
- **Multiple Content Types**: Headers, lists, paragraphs, code blocks, and links
- **Advanced List Support**: Correctly handles deeply nested lists (3rd, 4th level) with 4+ spaces indentation
- **Smart Content Detection**: Distinguishes between nested lists and indented code blocks using context analysis
- **VS Code Integration**: Native command palette and menu integration

## Design Patterns

- **Modular Architecture**: Each component has a single responsibility
- **Configuration-Driven**: Extensive user customization options
- **Error Handling**: Comprehensive error handling throughout
- **Memory Management**: Proper resource cleanup and disposal

## Development Standards

- **TypeScript**: All code written in TypeScript with strict mode
- **ESLint**: Code quality enforcement
- **TDD**: Test-driven development approach
- **Documentation**: Comprehensive inline and external documentation

## Configuration Schema

The extension provides extensive configuration options:

- **Tree Symbols**: Customizable branch, last, vertical, and spacing symbols
- **Colors**: Tree symbols, content text, and background colors
- **Fonts**: Separate fonts for content and tree symbols
- **Styling**: Line height and padding customization

## Related Documentation

- **Test Documentation**: `/test/test-documentation.md`
- **Task List**: `/meta/project-task-list.md`
- **Development Guide**: `/meta/DEVELOPMENT.md`
- **Publishing Guide**: `/meta/PUBLISHING.md`
- **ADR-001**: `/meta/ADR-001-enhanced-file-detection.md` - Enhanced File Detection System
- **ADR-002**: `/meta/ADR-002-nested-list-parsing-fix.md` - Nested List Parsing Priority Fix

## Extension Lifecycle

1. **Activation**: Triggered when opening Markdown files
2. **Command Registration**: Extension commands registered with VS Code
3. **Content Parsing**: Markdown content parsed into tree structure
4. **Rendering**: Tree rendered with user-configured styling
5. **Webview Display**: Content displayed in VS Code webview panel
6. **Live Updates**: Content automatically updates on file changes

## Performance Considerations

- **Efficient Parsing**: Optimized regex patterns for Markdown parsing
- **Minimal Redraws**: Only update webview when content actually changes
- **Memory Management**: Proper disposal of webview panels and resources
- **Background Processing**: Non-blocking parsing and rendering operations

## Troubleshooting

### File Recognition Issues

If the extension doesn't recognize some files as Markdown:

1. **File Extension Check**: Ensure the file has a supported Markdown extension:

   - `.md` (most common)
   - `.markdown`
   - `.mdown`
   - `.mkd`
   - `.mdwn`
   - `.mdtxt`
   - `.mdtext`
   - `.text`

2. **Force Markdown Mode**: Use the command "Markdown: Force Markdown Language Mode" from the Command Palette to manually set the language mode.

3. **Content Detection**: For files without proper extensions, the extension will analyze content for Markdown patterns (headers, lists, code blocks, links, emphasis).

4. **VS Code Language Detection**: Check if VS Code itself recognizes the file as Markdown by looking at the language mode in the status bar.

5. **File Association**: You can manually associate file patterns with Markdown in VS Code settings:
   ```json
   "files.associations": {
     "*.custom": "markdown"
   }
   ```
