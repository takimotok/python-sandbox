---
applyTo: "**"
description: "Basic guidelines for development environment and design principles"
---

# Development Environment and Design Principles

この文章は英語で書かれていますが, 次の点を特に遵守してください.

- Explain in simple Japanese language that middle school students can understand

## Development Environment

### System Environment

- **OS**: macOS 15.5
- **Docker**: version 28.3.2, build 578ccf6
- **Docker Compose**: version v2.38.2-desktop.1
- **Editor**: Neovim v0.11.1

## Basic Design Principles

### Single Responsibility Principle

- Do not mix multiple contexts
- Each class, function, and file should have only one responsibility

### Simple Design

- Avoid sacrificing simplicity while adhering to the `Single Responsibility Principle`
- When in doubt, prioritize simplicity
- Choose understandable implementations over complex ones

### Coding Standards

- Use **early return**
- When tempted to write `if ... else ...`, avoid using `else` whenever possible
- Do not pass or return `null` or `nil`
- Use guard clauses to reduce nesting

## Communication Guidelines

### Response and Explanation Style

- Explain in simple Japanese language that middle school students can understand
- Don't hesitate to point out when thinking is incorrect
- Actively ask questions when there are unclear points

### Code Review Perspective

- Verify adherence to design principles
- Emphasize readability and maintainability
- Validate that implementations are simple and understandable

### Language and Communication Requirements

- Point out when thinking or approach is incorrect
- Ask questions proactively when there are unclear points during work
