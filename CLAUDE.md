# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a VS Code extension called "gitollama" (display name: "Ollama Auto Commits") that integrates Ollama with Git for automated commit message generation. The project is in early development with minimal functionality currently implemented.

## Development Commands

**Build and Development:**
- `bun run compile` - Compile TypeScript to JavaScript
- `bun run watch` - Compile in watch mode for development
- `bun run vscode:prepublish` - Prepare for publishing (runs compile)

**Code Quality:**
- `bun run format` - Format and lint code using Biome
- `bun run pretest` - Compile and format before testing

**Testing:**
- `bun run test` - Run tests using VS Code test framework

## Architecture

**Core Structure:**
- `src/extension.ts` - Main extension entry point with activate/deactivate functions
- `src/test/` - Test files
- `out/` - Compiled JavaScript output (generated)

**Key Technologies:**
- TypeScript with strict mode enabled
- Biome for formatting and linting (2 space indentation, double quotes)
- VS Code Extension API
- Bun as package manager and test runner

**Extension Configuration:**
- Main entry: `./out/extension.js`
- Single command registered: `gitollama.helloWorld`
- Target: VS Code 1.102.0+

## Development Notes

The extension currently only has a "Hello World" command placeholder. The main functionality for Ollama integration and Git commit automation is yet to be implemented.

TypeScript is configured with Node16 module system and ES2022 target. Biome is configured with recommended rules and automatic import organization.