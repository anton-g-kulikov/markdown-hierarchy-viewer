# Project Task List

This document tracks all tasks, features, and improvements for the Markdown Hierarchy Viewer extension.

## Completed Tasks ✅

### 1.0.0 Release Preparation

- ✅ Rename extension to "Markdown Hierarchy Viewer"
- ✅ Update all repository URLs and references
- ✅ Modernize README.md with badges and clear structure
- ✅ Reset version to 1.0.0
- ✅ Clean up CHANGELOG.md for initial release
- ✅ Fix extension activation and command registration
- ✅ Update command titles to match new branding
- ✅ Comprehensive test coverage (unit and integration)
- ✅ Create test fixtures for realistic testing
- ✅ Fix TypeScript compilation issues
- ✅ Ensure all lint checks pass
- ✅ Organize project structure according to guidelines
- ✅ Create comprehensive documentation

### Project Organization

- ✅ Move all documentation to `/meta` folder
- ✅ Organize test files in `/test` folder with proper structure
- ✅ Create `test-documentation.md` with test case tracking
- ✅ Create `project-documentation.md` with architecture overview
- ✅ Update `.gitignore` for proper exclusions
- ✅ Ensure clean root folder organization

### Documentation Improvements

- ✅ Add screenshot to README.md (properly implemented with assets/screenshot.png)
- ✅ Review and update meta documentation references
- ✅ Create comprehensive publishing checklist and guidelines
- ✅ Add SUPPORT.md with troubleshooting and user support information

### Publishing Preparation (1.0.2)

- ✅ Create extension icon (icon.png) for marketplace visibility
- ✅ Add gallery banner configuration for professional marketplace presentation
- ✅ Update VS Code engine requirement to ^1.101.0 for latest API compatibility
- ✅ Complete all critical publishing requirements
- ✅ Extension ready for VS Code Marketplace publication

### Enhanced File Detection and UI (1.1.0)

- ✅ **Enhanced Markdown File Detection**: Added support for multiple Markdown extensions (.md, .markdown, .mdown, .mkd, .mdwn, .mdtxt, .mdtext, .text)
- ✅ **Content-based File Detection**: Implemented intelligent Markdown content analysis in `fileDetection.ts`
- ✅ **Custom Icon System**: Added custom SVG icons for commands and webview panel with theme-aware variants
- ✅ **Improved Command Menu**: Updated editor menu conditions to support all Markdown extensions
- ✅ **Force Markdown Mode Command**: Added utility command for troubleshooting file detection issues
- ✅ **VS Code Task Configuration Fix**: Fixed problem matchers in `.vscode/tasks.json` to resolve task provider errors
- ✅ **Context-aware UI**: Implemented conditional menu display based on active webview state
- ✅ **Comprehensive Documentation**: Updated README, CHANGELOG, and meta documentation with new features
- ✅ **Test Coverage**: Added test fixtures and documentation for new features
- ✅ **Release Preparation**: Bumped to version 1.1.0, committed, tagged, and pushed to GitHub

### UI and Typography Enhancements (1.1.1+)

- ✅ **Header Font Weight Optimization**: Modified header styling to make only headers level 1-2 bold, while headers 3-6 use normal font weight for better visual hierarchy

  - Updated `TreeRenderer` to add level-specific CSS classes (`header-1`, `header-2`, etc.)
  - Modified `StyleManager` to apply `font-weight: 600` only to headers 1-2 and `font-weight: 400` to others
  - Added comprehensive tests for header level styling in both TreeRenderer and StyleManager

- ✅ **Configurable Header Font Weight**: Made header font weight styling user-configurable through VS Code settings
  - Added new configuration options for header font weights by level (H1-H6) in `package.json`
  - Updated `ConfigurationManager` to handle header styling preferences with default values
  - Modified `StyleManager` to use configuration-driven header styling instead of hardcoded values
  - Added comprehensive tests for configuration-driven header styling (TDD approach)
  - Updated README.md with detailed header styling customization documentation and examples

### Release Management (1.2.0)

- ✅ **Version 1.2.0 Release Preparation**: Prepared release for configurable header styling feature
  - Incremented version from 1.1.1 to 1.2.0 (minor version for new feature)
  - Updated CHANGELOG.md with comprehensive release notes
  - Updated README.md version badge
  - Verified all tests pass and code compiles without errors

### Link Rendering Support (1.3.0)

- ✅ **CORE-TASK-001: Enhance markdown preview with links rendering** - ✅ **COMPLETED**
  - ✅ Add support for standard markdown links: `[text](url)`
  - ✅ Add support for reference-style links: `[text][ref]` with `[ref]: url`
  - ✅ Update `MarkdownParser.parseMarkdownFormatting()` with link parsing logic using balanced parentheses parser
  - ✅ Add CSS styling for links with hover effects and theme awareness
  - ✅ Update Content Security Policy in `StyleManager` to allow external navigation
  - ✅ Implement comprehensive test coverage for all link types including edge cases
  - ✅ Security: HTML-escape URLs and link text to prevent XSS attacks
  - ✅ Support nested formatting within link text (bold, italic, code in links)
  - ✅ Handle complex URLs with parentheses using balanced parsing algorithm
  - ✅ All 45 unit and integration tests passing successfully

### Critical Bug Fixes and Publishing (1.3.1)

- ✅ **CORE-TASK-002: Fix nested list parsing issues** - ✅ **COMPLETED**
  - ✅ Resolved issue where 3rd and 4th level nested list items (with 4+ spaces indentation) were incorrectly rendered as code blocks
  - ✅ Improved `isPartOfMixedCodeBlock` detection with variable indentation support (`^\s*` patterns)
  - ✅ Enhanced parsing order to prioritize list detection over indented code block detection
  - ✅ Added smart context analysis to distinguish between genuine code blocks and deeply nested lists
  - ✅ Fixed indented header detection to prevent false header parsing in code blocks
  - ✅ All 52 tests now pass with comprehensive coverage of edge cases
  - ✅ Added ADR-002 documenting the nested list parsing fix architecture decision

- ✅ **PUB-TASK-001: Publish extension to VS Code Marketplace** - ✅ **COMPLETED**
  - ✅ Version bump from 1.3.0 to 1.3.1 for critical bug fixes
  - ✅ Created and pushed git tag v1.3.1
  - ✅ Verified all pre-publishing requirements (tests, linting, compilation)
  - ✅ Successfully published `Tony-g-K.markdown-hierarchy-viewer v1.3.1` to VS Code Marketplace
  - ✅ Extension available at: https://marketplace.visualstudio.com/items?itemName=Tony-g-K.markdown-hierarchy-viewer
  - ✅ Management hub accessible for future updates and analytics

## Active Tasks 🚧

_(No active tasks - ready for publishing)_

### Ready for Release

- [ ] **RELEASE-TASK-001: Prepare extension for publishing** - 📋 **READY**

  - Prerequisites: ✅ All critical bugs fixed, ✅ Test suite complete (52/52 passing), ✅ Documentation updated
  - Next steps: Version bump, CHANGELOG update, build and publish to marketplace
  - Status: 📋 **READY** - Extension ready for version 1.3.1 release

- [x] **CORE-TASK-001: Fix nested list parsing with 4+ spaces indentation** - ✅ **COMPLETED**

  - Issue: 3rd and 4th level nested list items are incorrectly rendered as code blocks
  - Root cause: Code block detection (4+ spaces) happens before list item detection
  - Solution: Modified parsing order to check for list items before indented code blocks, with smart detection for mixed content
  - Files modified: `src/markdownParser.ts`, test files
  - Additional fixes applied:
    - Fixed `isPartOfMixedCodeBlock` regex patterns to handle variable indentation using `^\s*` instead of `^    `
    - Added indentation check to header detection to prevent indented headers from being parsed as headers
    - Updated test assertions to match correct parser behavior
  - Documentation: ✅ ADR-002 created, project documentation updated
  - Acceptance criteria: ✅ Nested lists with 4+ space indentation render as list items, not code blocks
  - Test status: ✅ All 52 tests passing
  - Status: ✅ **COMPLETED** - Ready for publishing

- [x] **TEST-TASK-001: Align test suite with corrected parser behavior** - ✅ **COMPLETED**
  - Updated failing unit tests to match the correct parser output after nested list fix
  - Fixed test assertions for indented code blocks, nested lists, and mixed indentation scenarios
  - All edge cases properly covered and documented
  - Status: ✅ **COMPLETED** - All tests aligned and passing

## NOT Planned Tasks (as of yet) 📋

### Current Sprint Tasks

_(No tasks currently in progress)_

### Future Version Features

- 📋 Add collapsible tree sections
- 📋 Implement tree node navigation (click to jump to section)
- 📋 Add export functionality (HTML, PDF)
- 📋 Implement search within tree structure
- 📋 Add keyboard shortcuts for common actions

### Performance Optimizations

- 📋 Implement incremental parsing for large documents
- 📋 Add debounced updates for real-time editing
- 📋 Optimize rendering for very large documents
- 📋 Add virtual scrolling for massive trees

### User Experience Enhancements

- 📋 Add dark/light theme automatic detection
- 📋 Implement custom CSS injection option
- 📋 Add tree symbol presets (Unicode, ASCII, Custom)
- 📋 Create extension settings UI panel
- 📋 Add context menu integration

### Advanced Features

- 📋 Support for custom Markdown extensions
- 📋 Integration with outline view
- 📋 Multi-file workspace tree view
- 📋 Table of contents generation
- 📋 Document statistics display

### Testing & Quality

- 📋 Add performance benchmarking tests
- 📋 Implement automated visual regression testing
- 📋 Add accessibility testing
- 📋 Create comprehensive user acceptance tests
- 📋 Add stress testing with large documents

### Documentation & Community

- 📋 Create video demonstration
- 📋 Write detailed usage guide
- 📋 Add contributing guidelines
- 📋 Create issue templates
- 📋 Set up automated changelog generation

## Future Considerations 🔮

### Version 2.0.0 Ideas

- 🔮 Plugin system for custom parsers
- 🔮 Real-time collaboration features
- 🔮 Integration with external documentation tools
- 🔮 AI-powered document analysis
- 🔮 Custom visualization themes

### Technical Debt

- 🔮 Migrate to newer VS Code API patterns
- 🔮 Implement comprehensive error telemetry
- 🔮 Add internationalization support
- 🔮 Consider WebAssembly for parsing performance

## Task Categories

### Priority Levels

- **P0**: Critical bugs, security issues
- **P1**: Important features for next release
- **P2**: Nice-to-have improvements
- **P3**: Future considerations

### Labels

- **🔥 urgent**: Needs immediate attention
- **⚡ performance**: Performance-related improvements
- **🎨 ui/ux**: User interface and experience
- **🧪 testing**: Testing and quality assurance
- **📚 docs**: Documentation improvements
- **🔧 maintenance**: Code maintenance and refactoring

## Tracking Guidelines

1. **Update Status**: Move tasks between sections as they progress
2. **Add Estimates**: Include time estimates for complex tasks
3. **Link Issues**: Reference GitHub issues when applicable
4. **Document Decisions**: Note any important architectural decisions
5. **Regular Review**: Review and update this list weekly during active development
