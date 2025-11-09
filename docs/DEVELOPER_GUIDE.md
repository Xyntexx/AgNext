---
owner: ??  
status: Draft
last_reviewed: -  
related_tickets: []  
---

# This is a draft

This guide is only a draft, as there is currently no source code it stands simply as a draft to be completed later as we begin development


# Developer Guide

This guide summarizes local environment setup, repeatable build commands, and key
references for AgOpenNext contributors. For architecture or product scope, start with the
[SRS overview](SRS/00_ReadMe.md) and the [documentation index](../INDEX.md).

## Prerequisites

Install the following tools before cloning the repository:

- .NET 10 SDK
- Git 2.40+
- Visual Studio 2022, VS Code, Jetpack Rider. or another IDE with C# support
- Docker Desktop (optional, for containerized testing and packaging)

## Initial Setup

```bash
# Clone and enter the workspace
git clone ???
cd ???

# Restore dependencies
dotnet restore
```

> Tip: Run `dotnet tool restore` if you add local tooling through `dotnet-tools.json`.

## Build & Test Commands

```bash
# Full solution build
dotnet build

# Build a specific project (example: core services)
dotnet build "???"

# Run all tests
dotnet test

# Filter tests by category
dotnet test --filter "Category=Integration"

# Simulation smoke tests (requires AgOpenNext CLI tooling)
agopennext sim smoke
```

Record the commands you execute in your PR summary and keep `tasks.md` in sync with
status updates.

## Workflow Expectations

1. Select a ready ticket from `tasks.md` and branch from `main` (`feat/NX-###-slug`).
2. Design before coding—outline requirements or ADR updates as needed.
3. Keep changes scoped; update documentation and validation artifacts alongside code.
4. Run required checks (build, tests, smoke) and capture logs for reviewers.
5. Reference the ticket ID in commit messages and pull requests.

## Key References


These references evolve with the platform—check the linked documents for the latest
procedures and cross-link updates from your PRs.
