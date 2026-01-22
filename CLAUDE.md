# CLAUDE.md - AI Assistant Guide

> **Repository**: redesigned-giggle
> **Last Updated**: 2026-01-22
> **Status**: New Repository - Initial Setup

This document serves as a comprehensive guide for AI assistants (like Claude) working on this codebase. It contains essential information about project structure, conventions, workflows, and best practices.

---

## 📋 Table of Contents

1. [Project Overview](#project-overview)
2. [Repository Structure](#repository-structure)
3. [Development Workflow](#development-workflow)
4. [Code Conventions](#code-conventions)
5. [Git Practices](#git-practices)
6. [Testing Strategy](#testing-strategy)
7. [AI Assistant Guidelines](#ai-assistant-guidelines)
8. [Common Tasks](#common-tasks)
9. [Troubleshooting](#troubleshooting)

---

## 🎯 Project Overview

### Current State
This is a newly initialized repository. As the project develops, this section should be updated with:
- Project purpose and goals
- Target audience
- Key features and functionality
- Technology stack
- Architecture decisions

### Quick Start
```bash
# Clone the repository
git clone <repository-url>
cd redesigned-giggle

# Install dependencies (update as project develops)
# npm install / pip install -r requirements.txt / etc.

# Run the project (update as needed)
# npm start / python main.py / etc.
```

---

## 📁 Repository Structure

```
redesigned-giggle/
├── .git/                 # Git repository data
├── CLAUDE.md            # This file - AI assistant guide
└── [To be populated as project develops]
```

### Planned Structure
As the project grows, document the directory structure here:

```
Example:
├── src/                 # Source code
│   ├── components/      # Reusable components
│   ├── utils/          # Utility functions
│   └── main.ext        # Entry point
├── tests/              # Test files
├── docs/               # Documentation
├── config/             # Configuration files
└── README.md           # User-facing documentation
```

---

## 🔄 Development Workflow

### Branch Strategy

**Main Branches:**
- `main` / `master`: Production-ready code (if applicable)
- Feature branches: `claude/<feature-name>-<session-id>`

**Branch Naming Convention:**
- Feature: `claude/feature-description-sessionid`
- Bug fix: `claude/fix-description-sessionid`
- Documentation: `claude/docs-description-sessionid`

### Development Process

1. **Start Work**
   - Ensure you're on the correct feature branch
   - Create branch if it doesn't exist: `git checkout -b claude/<branch-name>`
   - Fetch latest changes: `git fetch origin`

2. **Make Changes**
   - Read existing code before modifying
   - Follow established patterns in the codebase
   - Keep changes focused and minimal
   - Test changes locally

3. **Commit Changes**
   - Stage relevant files: `git add <files>`
   - Write clear commit messages (see Git Practices)
   - Commit: `git commit -m "message"`

4. **Push Changes**
   - Push to origin: `git push -u origin <branch-name>`
   - Branch must start with `claude/` and include session ID
   - Retry on network failure (up to 4 times with exponential backoff)

5. **Create Pull Request**
   - Use `gh pr create` with clear title and description
   - Include test plan and summary of changes
   - Link related issues if applicable

---

## 💻 Code Conventions

### General Principles

1. **Simplicity First**
   - Avoid over-engineering
   - No premature optimization
   - Make only requested changes
   - Keep solutions focused

2. **Code Quality**
   - Write self-documenting code
   - Add comments only where logic isn't self-evident
   - Follow existing patterns in the codebase
   - Maintain consistency with surrounding code

3. **Security**
   - Prevent injection vulnerabilities (SQL, XSS, Command)
   - Validate input at system boundaries
   - Don't add unnecessary error handling for impossible scenarios
   - Trust internal code and framework guarantees

4. **No Unnecessary Additions**
   - Don't add features beyond what's requested
   - Don't refactor unrelated code
   - Don't add docstrings to unchanged code
   - Don't create abstractions for one-time use
   - Delete unused code completely (no comments like `// removed`)

### Language-Specific Conventions

**To be added as the project's tech stack is determined:**

```
Example for JavaScript/TypeScript:
- Use const/let, never var
- Prefer arrow functions for callbacks
- Use async/await over promises.then()
- Follow ESLint configuration

Example for Python:
- Follow PEP 8 style guide
- Use type hints for function signatures
- Use f-strings for string formatting
- Follow project's linting rules
```

### File Naming

**To be defined based on project language:**
- Consistent casing (camelCase, snake_case, kebab-case)
- Descriptive names
- Follow framework conventions

---

## 🔀 Git Practices

### Commit Messages

**Format:**
```
<type>: <short summary>

[optional body]
[optional footer]
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `refactor`: Code refactoring
- `test`: Test additions/changes
- `chore`: Maintenance tasks
- `style`: Formatting changes

**Guidelines:**
- Use imperative mood ("add" not "added")
- Keep first line under 72 characters
- Focus on "why" rather than "what"
- Reference issues when applicable

**Examples:**
```
feat: add user authentication system

fix: resolve race condition in data loader

docs: update API documentation for v2 endpoints

refactor: simplify error handling in payment flow
```

### Git Safety Rules

1. **NEVER** update git config
2. **NEVER** run destructive commands (force push, hard reset) without explicit request
3. **NEVER** skip hooks (--no-verify) without explicit request
4. **NEVER** force push to main/master
5. **AVOID** `git commit --amend` unless:
   - User explicitly requested it, OR
   - Pre-commit hook auto-modified files
   - Commit was created in this session
   - Commit hasn't been pushed

### Network Retry Strategy

For `git push`, `git fetch`, `git pull`:
- Retry up to 4 times on network failure
- Use exponential backoff: 2s, 4s, 8s, 16s
- Example: `git push || (sleep 2 && git push) || (sleep 4 && git push)`

---

## 🧪 Testing Strategy

### Test Organization

**To be defined as project develops:**
```
tests/
├── unit/           # Unit tests
├── integration/    # Integration tests
├── e2e/           # End-to-end tests
└── fixtures/      # Test data
```

### Running Tests

```bash
# Update these commands as project develops
# npm test
# pytest
# cargo test
```

### Testing Guidelines

1. **When to Test**
   - After implementing new features
   - After fixing bugs
   - Before committing changes
   - When explicitly requested

2. **What to Test**
   - Critical business logic
   - Edge cases and error conditions
   - Public APIs and interfaces
   - Bug fixes (regression tests)

3. **What Not to Test**
   - Framework internals
   - Third-party libraries
   - Trivial getters/setters
   - Configuration files

---

## 🤖 AI Assistant Guidelines

### Core Principles

1. **Read Before Writing**
   - Always read files before modifying
   - Understand existing patterns
   - Never propose changes to unread code

2. **Stay Focused**
   - Address only the requested task
   - Don't add unrequested features
   - Don't refactor unrelated code
   - Keep changes minimal and targeted

3. **Use Tools Effectively**
   - Use TodoWrite for complex multi-step tasks
   - Use Task tool for codebase exploration
   - Prefer specialized tools over bash commands
   - Run independent operations in parallel

4. **Communicate Clearly**
   - Use file_path:line_number format for code references
   - Explain "why" not just "what"
   - Ask questions when requirements are unclear
   - Provide context for decisions

### Task Management

**Use TodoWrite when:**
- Task has 3+ distinct steps
- Task is complex or requires planning
- User provides multiple tasks
- User explicitly requests todo list

**Todo States:**
- `pending`: Not yet started
- `in_progress`: Currently working (only ONE task at a time)
- `completed`: Finished successfully

**Todo Format:**
- `content`: Imperative form ("Run tests")
- `activeForm`: Present continuous ("Running tests")

### Code References

When referencing code, use this format:
```
src/utils/helper.ts:45
```

This allows easy navigation to the specific location.

### Asking Questions

Use AskUserQuestion tool when:
- Requirements are ambiguous
- Multiple valid approaches exist
- User preference is needed
- Implementation details are unclear

Don't ask questions when:
- Answer is obvious from context
- Standard practices apply
- Decision is trivial

---

## 🛠️ Common Tasks

### Adding a New Feature

1. Use TodoWrite to plan the implementation
2. Read relevant existing code
3. Follow existing patterns
4. Implement minimal viable solution
5. Test the feature
6. Commit with descriptive message
7. Push to feature branch
8. Create pull request

### Fixing a Bug

1. Reproduce the issue
2. Locate the problematic code
3. Understand the root cause
4. Implement minimal fix
5. Add regression test if appropriate
6. Verify fix works
7. Commit and push

### Refactoring Code

1. Understand current implementation
2. Identify specific improvement
3. Make incremental changes
4. Ensure tests still pass
5. Verify behavior unchanged
6. Commit with clear explanation

### Writing Documentation

1. Identify documentation need
2. Research relevant information
3. Write clear, concise content
4. Include examples where helpful
5. Keep user perspective in mind
6. Update related documentation

---

## 🐛 Troubleshooting

### Common Issues

#### Git Push Fails with 403
**Cause**: Branch name doesn't match required format
**Solution**: Ensure branch starts with `claude/` and includes session ID

#### Tests Failing
**Cause**: Various
**Solution**:
1. Read test output carefully
2. Reproduce failure locally
3. Fix root cause
4. Verify all tests pass
5. Don't mark todo as complete if tests fail

#### Build Errors
**Cause**: Various
**Solution**:
1. Read error messages completely
2. Check for missing dependencies
3. Verify configuration files
4. Fix errors incrementally
5. Test after each fix

#### Merge Conflicts
**Cause**: Concurrent changes to same files
**Solution**:
1. Fetch latest from origin
2. Review conflicting changes
3. Resolve conflicts carefully
4. Test thoroughly after resolution
5. Commit resolution

---

## 📝 Maintenance

### Updating This Document

This document should be updated when:
- Project structure changes
- New conventions are established
- Technology stack is defined/updated
- Common patterns emerge
- New common issues are discovered
- Development workflow evolves

**Update Process:**
1. Read current CLAUDE.md
2. Identify outdated sections
3. Update with current information
4. Maintain consistent formatting
5. Update "Last Updated" date
6. Commit changes

### Document Sections to Update

As the project develops, prioritize updating:
1. **Project Overview** - Define purpose, tech stack, architecture
2. **Repository Structure** - Document actual directory layout
3. **Code Conventions** - Add language-specific guidelines
4. **Testing Strategy** - Define test commands and organization
5. **Common Tasks** - Add project-specific workflows
6. **Troubleshooting** - Document recurring issues

---

## 🔗 Related Resources

### Internal Documentation
- README.md - User-facing project documentation
- CONTRIBUTING.md - Contributor guidelines (if exists)
- docs/ - Additional documentation (if exists)

### External Resources
- [Conventional Commits](https://www.conventionalcommits.org/)
- [Semantic Versioning](https://semver.org/)
- Project-specific framework documentation (add as needed)

---

## 📮 Questions or Issues?

If this document is unclear or outdated:
1. Ask the user for clarification
2. Update this document with new information
3. Maintain accuracy and relevance

---

**Remember**: This is a living document. Keep it updated as the project evolves. Accurate documentation makes AI assistance more effective and helps maintain project quality.
