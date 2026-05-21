# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Java 25 Maven project (`org.example:playwright-java`) intended for Playwright browser automation. The pom.xml currently has no dependencies — Playwright for Java and any test framework dependencies need to be added before writing automation code.

## Commands

```bash
# Compile
mvn compile

# Run tests
mvn test

# Run a single test class
mvn test -Dtest=ClassName

# Package
mvn package
```

## Structure

- `src/main/java/org/example/` — application code
- `src/test/java/` — test code (empty; test framework not yet configured)

## Git Workflow

**IMPORTANT:** Before starting any new task, always create and switch to the `develop` branch:
```bash
git checkout develop 2>/dev/null || git checkout -b develop
```
Never work directly on `main`.

After merging a PR:
1. Switch locally to `main`
2. Delete the merged branch locally (`git branch -d <branch>`) and remotely (`git push origin --delete <branch>`)
3. Pull latest `main` from remote (`git pull origin main`)

## Adding Playwright

To get started, add to `pom.xml`:

```xml
<dependency>
    <groupId>com.microsoft.playwright</groupId>
    <artifactId>playwright</artifactId>
    <version>1.49.0</version>
</dependency>
```

Install browsers after adding the dependency:

```bash
mvn exec:java -e -D exec.mainClass=com.microsoft.playwright.CLI -D exec.args="install"
```
