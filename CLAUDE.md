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
