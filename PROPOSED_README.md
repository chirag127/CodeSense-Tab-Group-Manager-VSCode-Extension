<div align="center">

# CodeSense: Tab Group Manager VS Code Extension

<img src="https://raw.githubusercontent.com/chirag127/CodeSense-Tab-Group-Manager-VSCode-Extension/main/assets/codesense_logo.svg" alt="CodeSense Logo" width="150"/>

> **The ultimate session management solution for Visual Studio Code. Effortlessly save, name, restore, and organize your entire tab configurations across different projects, ensuring seamless context switching and zero friction.**

[![Build Status](https://img.shields.io/github/actions/workflow/status/chirag127/CodeSense-Tab-Group-Manager-VSCode-Extension/ci.yml?branch=main&style=flat-square&label=Build&logo=github)](https://github.com/chirag127/CodeSense-Tab-Group-Manager-VSCode-Extension/actions/workflows/ci.yml)
[![Code Coverage](https://img.shields.io/codecov/c/github/chirag127/CodeSense-Tab-Group-Manager-VSCode-Extension?style=flat-square&token=YOUR_TOKEN_HERE&logo=codecov)](https://app.codecov.io/gh/chirag127/CodeSense-Tab-Group-Manager-VSCode-Extension)
[![License](https://img.shields.io/github/license/chirag127/CodeSense-Tab-Group-Manager-VSCode-Extension?style=flat-square&label=License&logo=open-source-initiative)](LICENSE)
[![Tech Stack](https://img.shields.io/badge/Stack-TypeScript%20%7C%20VSCode%20API-3178C6?style=flat-square&logo=typescript)](https://www.typescriptlang.org/)
[![Linter](https://img.shields.io/badge/Linter-Biome-000000?style=flat-square&logo=biome)](https://biomejs.dev/)
[![GitHub Stars](https://img.shields.io/github/stars/chirag127/CodeSense-Tab-Group-Manager-VSCode-Extension?style=flat-square&logo=github)](https://github.com/chirag127/CodeSense-Tab-Group-Manager-VSCode-Extension/stargazers)

#### 🚀 Star ⭐ this Repo!

</div>

---

## Table of Contents

1.  [Overview](#overview)
2.  [Features & Capabilities](#features--capabilities)
3.  [Installation & Usage](#installation--usage)
4.  [Architecture](#architecture)
5.  [🤖 AI Agent Directives](#ai-agent-directives)
6.  [Development Setup](#development-setup)
7.  [License](#license)

---

## Overview

CodeSense addresses the core problem of context loss during complex development cycles. By managing tab groups (sessions), it allows developers to isolate tasks, switch seamlessly between projects, and maintain highly personalized workspace layouts. It features intelligent auto-save and robust storage mechanisms (global, workspace, or file-based) for maximum flexibility.

This project is built using modern TypeScript and leverages the VS Code Extension API for deep integration and performance.

## Features & Capabilities

*   **Intelligent Auto-Save:** Automatically persists the current tab state on window close or idle time.
*   **One-Click Restore:** Instantly load complex tab layouts using the Command Palette.
*   **Flexible Storage:** Choose to save sessions globally (across all VS Code instances) or workspace-specific.
*   **Custom Naming:** Assign clear, descriptive names to sessions for easy identification.
*   **Session Explorer:** A dedicated sidebar view for managing, editing, and deleting saved sessions.
*   **Conflict Resolution:** Handles cases where a session is restored into an already open workspace.

## Installation & Usage

### VS Code Marketplace

1.  Open VS Code.
2.  Navigate to the Extensions view (`Ctrl+Shift+X` or `Cmd+Shift+X`).
3.  Search for **"CodeSense Tab Manager"**.
4.  Click **Install**.

### Key Commands

| Command | Description | Shortcut (Configurable) |
| :--- | :--- | :--- |
| `codesense.saveCurrentSession` | Saves all open tabs in the current group. | `Ctrl+Alt+S` |
| `codesense.restoreSession` | Prompts selection of a saved session to load. | `Ctrl+Alt+R` |
| `codesense.openSessionExplorer` | Opens the dedicated sidebar management view. | N/A |

## Architecture

The extension adheres to an adapted Feature-Sliced Design (FSD) architecture, promoting high modularity and clear separation of concerns, especially between the VS Code API interactions and the core business logic.


. (Root)
├── src/
│   ├── core/           (Core Services: VS Code API Wrapper, State Management, Storage)
│   ├── commands/       (Command registration and handlers - Interface layer)
│   ├── entities/       (Data Models: Session, TabGroup, FileReference)
│   ├── features/       (Specific Logic Modules: AutoSave, RestoreFlow)
│   └── extension.ts    (Extension entry point and initialization)
├── package.json        (VS Code Extension Manifest)
└── tsconfig.json


## 🤖 AI Agent Directives

<details>
<summary>🤖 AI AGENT DIRECTIVES & TECHNICAL MANIFEST (CodeSense)</summary>

### 1. IDENTITY & PRIME DIRECTIVE
**Role:** Senior Principal Architect | Focus: Zero-Defect, High-Velocity, Future-Proof Extension Development.
**Context:** VS Code Extension Development (TypeScript, 2026 Standards).

### 2. ARCHITECTURAL MANDATES
*   **Architecture Pattern:** Apply **Feature-Sliced Design (FSD)** principles adapted for the VS Code extension environment.
*   **Key Layers:** `src/entities` (Data Models), `src/core` (VS Code State/API interactions, Storage), `src/features` (Specific command logic: SaveSession, RestoreSession, UI), `src/shared` (Utilities).
*   **VS Code API Usage:** Isolate all raw VS Code API calls within the `src/core` service layer to maintain testability and abstraction. Commands in `src/commands` should only dispatch events or call methods on the `CoreService`.

### 3. APEX TOOLCHAIN & STANDARDS
*   **Language & Runtime:** TypeScript 5.x (Strict Mode: `noImplicitAny`, `strictNullChecks`). Target Node 18+ runtime environment for VS Code.
*   **Linting & Formatting:** Use **Biome** for instantaneous feedback and strict adherence to codified style guides.
    *   *Verification Command:* `npm run lint -- --check`
*   **Testing Frameworks:** **Vitest** for unit testing core logic (isolated from VS Code API) and the dedicated **VS Code Extension Test Framework** for integration tests (running against a mock workspace).
    *   *Verification Command:* `npm run test:unit` and `npm run test:integration`
*   **Configuration Management:** All user settings and configuration options MUST be defined and documented clearly within `package.json`'s `contributes.configuration` section. Do not hardcode magic strings.

### 4. SECURITY & STORAGE PROTOCOL
*   **State Management:** Prioritize `vscode.workspace.globalState` or `workspaceState` for persistence based on scope. If sensitive data were involved (not applicable for tab names), `secretStorage` must be used.
*   **Serialization:** Use robust JSON serialization with schema validation for saved session files to ensure backward compatibility and prevent corruption upon restore.

</details>

## Development Setup

To contribute or debug the extension locally, follow these steps.

### Prerequisites

*   Node.js (LTS)
*   VS Code
*   `npm` or `pnpm` (pnpm preferred for dependency management)

### Setup Commands

bash
# 1. Clone the repository
git clone https://github.com/chirag127/CodeSense-Tab-Group-Manager-VSCode-Extension
cd CodeSense-Tab-Group-Manager-VSCode-Extension

# 2. Install dependencies
pnpm install

# 3. Run the development environment (opens a new VS Code instance with the extension loaded)
pnpm run watch

# 4. Run tests and linting checks
pnpm run lint
pnpm run test


### Key Scripts

| Script | Description | Notes |
| :--- | :--- | :--- |
| `watch` | Compiles source files and automatically watches for changes. | Essential for local development |
| `compile` | Runs the TypeScript compiler once. | For build/packaging |
| `lint` | Executes Biome for formatting and linting checks. | High-velocity quality assurance |
| `test` | Runs both unit and integration tests. | Requires Test Runner Extension in VS Code |
| `vsce:package` | Creates the VSIX package for distribution. | Requires VSCE utility installed |

## License

This project is licensed under the **Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)** License.

See the [LICENSE](LICENSE) file for details.