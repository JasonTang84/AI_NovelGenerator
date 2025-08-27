# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

### Running the Application
```bash
python main.py
```
This launches the GUI application using CustomTkinter.

### Installing Dependencies
```bash
pip install -r requirements.txt
```
Install all required packages for the application.

### Building Executable
```bash
pip install pyinstaller
pyinstaller main.spec
```
Creates a standalone executable in the `dist/` directory using the provided spec file.

## Code Architecture

This is an AI-powered novel generation tool with a GUI built using CustomTkinter. The application generates novels through multiple stages using LLM APIs.

### Core Components

- **Main Entry**: `main.py` - Application entry point that initializes the GUI
- **UI Layer**: `ui/` directory containing all GUI components organized by functionality
  - `main_window.py` - Primary GUI class and window management
  - Individual tab modules for different features (config, chapters, characters, etc.)
- **Novel Generation Engine**: `novel_generator/` directory with core generation logic
  - `architecture.py` - Novel structure and world-building generation
  - `blueprint.py` - Chapter outline generation
  - `chapter.py` - Individual chapter content generation
  - `finalization.py` - Chapter finalization and state updates
- **LLM Integration**: `llm_adapters.py` - Unified interface for different AI providers
- **Configuration**: `config_manager.py` - Handles API keys, model settings, and user preferences

### Generation Workflow

The application follows a structured 4-step novel generation process:

1. **Architecture Generation** - Creates world-building, character dynamics, and plot structure
2. **Blueprint Generation** - Generates chapter-by-chapter outlines and structure
3. **Chapter Draft Generation** - Creates individual chapter content with context awareness
4. **Finalization** - Updates global state, character tracking, and vector store

### Key Features

- **Multi-LLM Support**: OpenAI, DeepSeek, Gemini, Azure, and custom endpoints
- **Vector Storage**: ChromaDB integration for context retrieval and consistency
- **State Management**: Tracks character states, plot arcs, and global narrative consistency
- **Embedding Integration**: Supports various embedding models for semantic search
- **GUI Workflow**: Complete visual interface for the entire novel generation process

### File Organization

Generated content is organized in the user-specified output directory:
- `Novel_setting.txt` - World-building and character information
- `Novel_directory.txt` - Chapter outlines and structure
- `chapter_X.txt` - Individual chapter content
- `character_state.txt` - Character development tracking
- `global_summary.txt` - Overall narrative summary
- `vectorstore/` - ChromaDB vector database for context retrieval

## Configuration

The application uses `config.json` for persistent settings including:
- API credentials for various LLM providers
- Model parameters (temperature, max_tokens)
- Novel generation parameters (genre, chapter count, word count)
- Embedding model configuration
- Output file paths

## Dependencies

Key dependencies include:
- `customtkinter` - Modern GUI framework
- `langchain` ecosystem - LLM integration and vector stores
- `chromadb` - Vector database for semantic search
- `sentence-transformers` - Embedding model support
- Multiple AI provider SDKs (OpenAI, Google Generative AI, Azure)

## Development Notes

- The codebase is primarily in Chinese with English comments in some areas
- All UI components use CustomTkinter for modern styling
- The application maintains backward compatibility with older config formats
- Error handling includes fallbacks for network issues and API failures
- Vector store can be cleared and rebuilt when switching embedding models