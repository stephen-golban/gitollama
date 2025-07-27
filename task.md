<plan>
<model_selection>
**Model Selection and Ollama Integration:**

The extension implements **flexible model discovery and selection** to work with any models users have installed, while providing intelligent recommendations for optimal performance.

**Recommended Models** (when available):
- **CodeLlama:7b**: Primary recommendation for code understanding and git diff analysis
- **Llama2**: Secondary option with good general language capabilities
- **Mistral**: Alternative option with efficient performance

**Automatic Model Discovery:**
- Query Ollama `/api/tags` endpoint on startup and periodically to discover all available models
- Intelligent selection priority: recommended models first, then any compatible text-generation model
- Dynamic model list updates when users install/remove models (no extension restart required)
- Graceful fallback when no recommended models are available

**Ollama Integration Architecture:**

The integration will include:

1. **Connection Management**: Robust connection handling with health monitoring

2. **Dynamic Model Selection**:
   - Automatic discovery of all available models via `/api/tags` API
   - Intelligent priority-based selection (recommended → any compatible → fallback)
   - User override capability for manual model selection
   - Real-time model availability monitoring

3. **Request Configuration**: Optimized parameters for commit message generation

4. **Error Handling**: Graceful handling of model loading failures and network issues
5. **Performance Optimization**: Model warming and request caching

</model_selection>

<ui_ux_design>
**UI/UX Design:**

**Primary Interface:**
- **Generate Button**: A clean, minimalist button integrated into the Source Control view's top-bar with the VS Code design language
- **Icon**: Simple "✨" sparkle icon or AI-style icon consistent with VS Code's iconography
- **Auto-insertion**: Generated commit messages are automatically inserted into the VS Code source control panel's message input box
- **Placement**:

**Additional UI Elements:**
1. **Progress Indicator**: Subtle progress bar during generation (max 5 seconds)
2. **Edit Modal**: Inline editor overlay allowing users to modify generated messages before committing
3. **Template Selector**: Dropdown for custom templates (accessible via gear icon)
4. **Status Indicator**: Small colored dot showing Ollama connection status

**Design Principles:**
- Consistent with VS Code's design system colors and typography
- Minimal visual clutter
- Accessible keyboard navigation
- Responsive to VS Code themes (light/dark mode)
</ui_ux_design>

<feature_list>
**Core Features:**
1. **AI-Powered Generation**: Generate commit messages using local LLMs via Ollama
2. **Flexible Model Support**:
   - Automatic discovery of all available Ollama models via `/api/tags`
   - Intelligent selection priority (recommended models → any compatible → fallback)
   - Works with any text-generation model in user's Ollama installation
   - User override for manual model selection
3. **Flexible Commit Formats**:
   - Conventional Commits (feat:, fix:, docs:, etc.)
   - Semantic Commits (Add, Update, Fix, Remove, etc.)
   - Custom formats (user-defined templates)
   - Free-form descriptive messages
   - Team-specific conventions
4. **Auto-insertion**: Generated messages are automatically inserted into VS Code's source control message input box
5. **Diff Analysis**: Intelligent analysis of staged changes to create contextual messages
6. **Inline Editing**: Edit generated messages before committing
7. **Custom Templates**: Save and reuse personalized commit message templates
8. **Format Selection**: User choice between different commit message styles and conventions

**Advanced Features:**
8. **Dynamic Model Management**:
   - Real-time model discovery and availability monitoring
   - Automatic refresh when models are installed/removed (no restart required)
   - Model compatibility validation and performance profiling
   - Graceful fallback mechanisms for model failures
9. **Commit Format Customization**:
   - Multiple format presets (Conventional, Semantic, Angular, etc.)
   - Custom format creation with template variables
   - Team-specific convention support
   - Format validation and enforcement options
10. **Multi-Language Support**: Generate commit messages in multiple languages
11. **Smart Categorization**: Automatic categorization of changes by type and scope
12. **Breaking Change Detection**: Automatic detection and flagging of breaking changes
13. **Scope Detection**: Intelligent suggestion of commit scopes based on modified files
14. **Performance Optimization**: 5-second generation target with local caching
15. **Offline Operation**: Complete functionality without internet connectivity

**User Experience Features:**
16. **Quick Actions**: Keyboard shortcuts for common operations
17. **History Tracking**: Recent generation history for quick reuse
18. **Model Health Monitoring**: Real-time status of Ollama and all available models
19. **Contextual Suggestions**: Suggestions based on file types and project structure
20. **Format Quick-Switch**: Easy switching between commit formats during generation
</feature_list>

<configuration_panel>
**Configuration Panel Design:**

**Model Configuration:**
- **Available Models**: Dynamic dropdown populated from Ollama `/api/tags` discovery
- **Model Selection Strategy**:
  - Automatic (intelligent priority: recommended → compatible → fallback)
  - Manual override (user selects specific model from available list)
- **Recommended Models**: Visual indicators for CodeLlama, Llama2, Mistral when available
- **Model Health Check**: Real-time availability testing and performance metrics
- **Auto-refresh**: Automatic model list updates when Ollama models change

**Generation Parameters:**
- **Temperature**: Slider (0.1 - 1.0) for creativity control
- **Max Tokens**: Input field (50-200) for response length
- **Timeout**: Generation timeout setting (3-10 seconds)

**Message Formatting:**
- **Format Selection**: Dropdown for commit message formats:
  - Conventional Commits (feat:, fix:, docs:, style:, refactor:, test:, chore:)
  - Semantic Commits (Add, Update, Fix, Remove, Refactor, etc.)
  - Angular Convention (feat, fix, docs, style, refactor, perf, test, build, ci, chore, revert)
  - Custom formats (user-defined templates)
  - Free-form descriptive
- **Commit Type Preferences**: Checkboxes for enabled commit types per format
- **Default Scope**: Text input for project-specific default scope
- **Language Selection**: Dropdown for commit message language
- **Format Validation**: Toggle for strict format enforcement vs. flexible formatting
- **Custom Format Builder**: Visual editor for creating custom commit message templates

**Template Management:**
- **Template Editor**: Rich text editor for custom templates
- **Template Variables**: Support for placeholders like {type}, {scope}, {files}
- **Import/Export**: JSON-based template sharing

**Advanced Settings:**
- **Ollama Connection**: Custom host/port configuration
- **File Filters**: Ignore patterns for diff analysis
- **Performance Mode**: Balance between speed and quality
- **Debug Logging**: Enable detailed logging for troubleshooting

**Integration Options:**
- **Auto-generate**: Toggle for automatic generation on stage changes
- **Confirmation Prompts**: Settings for user confirmation levels
- **Keyboard Shortcuts**: Customizable hotkey assignments
</configuration_panel>

<extension_description>
**AI Commit Message Generator for VS Code**

Transform your Git workflow with intelligent, locally-generated commit messages powered by Ollama. This extension seamlessly integrates with VS Code's Source Control interface to provide AI-powered commit message generation using local language models, ensuring complete privacy and offline functionality.

**Key Features:**
- 🤖 **Local AI Power**: Works with any Ollama model - automatic discovery and intelligent selection
- 📝 **Multiple Formats**: Support for Conventional Commits, Semantic Commits, Angular Convention, and custom formats
- ⚡ **Lightning Fast**: Sub-5-second generation optimized for developer productivity
- 🔒 **Privacy First**: 100% offline operation - your code never leaves your machine
- 🎨 **Customizable**: Flexible templates, multiple languages, and personalized settings
- 🔧 **Smart Analysis**: Intelligent diff analysis for contextually relevant messages
- 🔄 **Flexible Models**: Automatic model discovery with intelligent fallback and user override options
- 🎯 **Format Choice**: User control over commit message style and conventions

**Perfect for developers who want:**
- Consistent, professional commit message formatting
- AI assistance without cloud dependencies
- Seamless integration with existing VS Code workflows
- Enhanced team collaboration through standardized commits
- Flexibility to use any Ollama model they already have installed
- Choice of commit message formats to match team conventions

Compatible with VS Code 1.60+ and requires Ollama installation. Works with any text-generation model available in your Ollama instance.
</extension_description>

<implementation_plan>
**Implementation Plan:**

**Phase 1: Core Infrastructure (Weeks 1-2)**
1. **Project Setup**:
   - Initialize VS Code extension project using Yeoman generator
   - Configure TypeScript, webpack bundling, and testing framework
   - Set up CI/CD pipeline for automated testing and publishing

2. **Ollama Integration**:
   - Implement `/api/tags` endpoint integration for dynamic model discovery
   - Create intelligent model selection algorithm with priority-based fallback
   - Build connection health monitoring and automatic reconnection
   - Implement real-time model availability checking and validation
   - Design model compatibility testing and performance profiling system

3. **Source Control Integration**:
   - Integrate with VS Code's Source Control Manager (SCM) API
   - Implement automatic insertion of generated messages into the commit message input box
   - Implement git diff parsing and staged changes analysis

**Phase 2: AI Generation Engine (Weeks 3-4)**
1. **Message Generation Logic**:
   - Develop diff analysis algorithm to extract meaningful change summaries
   - Implement format-specific generation engines for different commit styles
   - Create prompt engineering templates for different commit types and formats
   - Build format validation and enforcement mechanisms

2. **Dynamic Model Management**:
   - Implement automatic model discovery via Ollama `/api/tags` API
   - Create intelligent model selection with priority-based fallback logic
   - Build universal model compatibility layer for any text-generation model
   - Add real-time model availability monitoring and auto-refresh capabilities
   - Optimize prompts for different model types and capabilities

3. **Performance Optimization**:
   -

- Add request caching and batching for improved performance
   - Ensure 5-second generation target through timeout management

**Phase 3: User Interface (Weeks 5-6)**
1. **UI Components**:
   - Design and implement clean, VS Code-consistent button interface
   - Create modal overlay for message editing and confirmation
   - Add progress indicators and status feedback

2. **Configuration Panel**:
   - Build comprehensive settings interface using VS Code's configuration API
   - Implement dynamic model selection UI with real-time discovery
   - Create template management system with CRUD operations
   - Add model health monitoring dashboard with availability status
   - Design model selection strategy configuration (automatic vs manual override)

**Phase 4: Advanced Features (Weeks 7-8)**
1. **Template and Format System**:
   - Create template engine with variable substitution
   - Implement multiple commit format support (Conventional, Semantic, Angular, Custom)
   - Build format selection and switching interface
   - Add predefined templates for common project types and formats
   - Implement template import/export functionality

2. **Multi-language Support**:
   - Implement localization for commit message generation
   - Add language detection and automatic switching
   - Create language-specific prompt templates

**Phase 5: Testing & Polish (Weeks 9-10)**
1. **Comprehensive Testing**:
   - Unit tests for all core functionality
   - Integration tests with mock Ollama instances
   - End-to-end testing with real repositories

2. **Error Handling & Reliability**:
   - Robust error handling for network failures and model issues
   - Graceful degradation when Ollama is unavailable
   - User-friendly error messages and troubleshooting guides

3. **Documentation & Packaging**:
   - Complete user documentation and setup guides
   - Create video tutorials and getting started materials
   - Package extension for VS Code Marketplace publication

**Key Implementation Challenges & Solutions:**

1. **Performance Constraints**: Use model warming, request optimization, and intelligent caching
2. **Universal Model Compatibility**:
   - Abstract model interface with adapter pattern for any text-generation model
   - Dynamic prompt optimization based on model capabilities and characteristics
   - Graceful handling of model-specific limitations and response formats
3. **Dynamic Model Discovery**:
   - Efficient `/api/tags` polling with smart caching to minimize API calls
   - Real-time model availability detection without impacting performance
   - Robust error handling for Ollama connectivity issues
4. **Git Integration Complexity**: Leverage VS Code's robust SCM API rather than direct git commands
5. **User Experience**: Extensive user testing and iterative UI refinement
6. **Error Recovery**: Comprehensive error handling with automatic retries and intelligent fallback options

**Technical Stack:**
- **Language**: TypeScript for type safety and VS Code API compatibility
- **Bundling**: Webpack for optimized extension packaging  
- **Testing**: Jest for unit testing, VS Code Test Runner for integration tests
- **HTTP Client**: Native Node.js fetch for Ollama API communication
- **Configuration**: VS Code Settings API for persistent configuration management
</implementation_plan>
</plan>