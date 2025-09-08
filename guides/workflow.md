Workflow
===

This document describes how the agent will work with the human.

## Overview

1. Understand the task
2. Gather resources
3. Plan the solution
4. Plan test items


### 1. Understand the task


### 2. Gather resources

1. Collect project and external docs
2. Identify affected systems
3. Identify affected source files
4. Identify security implications


### 3. Plan the solution


### 4. Plan test items


## Resources

### Task folder structure

All tasks reside in the `agentsmd/tasks` directory by category:

```
...
 agentsmd/tasks
├──  bug  # bug tickets
├──  feat  # feature tickets
├──  misc  # misc tickets (chore, docs, etc)
│   └──  0000-initalize_project  # task folder; naming <NNNN>-<short_name>
│       └──  spec.md  # task specifications doc
│       └──  implementation.md  # implementation details of the task
│       └──  attachments  # files (images, docs, snippets, etc) relevant to the task
└──  patch  # independent refactor or upgrade tickets
```

### spec.md

```
<Task title summary> - Spec
===

## Description

{::comment}
- loosely follow story card syntax: As a <role>, I want to <feature>, So that <benefit>
- include additional context, notes, references, attachments, etc
{:/comment}

## Behavior

{::comment}
- loosely follow BDD syntax: Given-When-Then
{:/comment}

## History

### <YYYY-MM-DD hh:mm>

**Summary**

{::comment}
- one-liner summary of changes; useable for a git commit
{:/comment}

**Changes**

{::comment}
- bullets of what has changed for this log
{:/comment}
```

### implementation.md

```
<Task title summary> - Implementation
===

## Understanding the task

{::comment}
- loose structure of internalized understanding of the spec
- ideate on any project/internal systems, libs, modules that can help or impede the task
- ideate on third-party/external systems, libs, tools that can help the task
{:/comment}

## Gathering resources

### Project docs references

{::comment}
- bullets of relevant project doc files and why it matters
{:/comment}

### External docs references

{::comment}
- bullets of relevant links, wikis, articles, topics to research;
  note why it matters
- reference new attachments when applicable
{:/comment}

### Affected behaviors and tests

{::comment}
- grouped bullets of possibly affected system behaviors (i.e. login, permissions, etc) and their corresponding tests;
  note why it matters
{:/comment}

### Affected source files

{::comment}
- grouped bullets of relevant project source files found that will be changed, created, and deleted as necessary.
- highlight relevant project config, module, function, class, etc;
  note why it matters
- highlight relevant third-party config, module, function, class, etc;
  note why it matters
{:/comment}

### Security considerations

{::comment}
- list of considerations per scenario if applicable
{:/comment}

## Solution plan

{::comment}
- loose structure; grouped checklists
- include pattern and design choices
- include config, module, function, class, etc, that will be changed, created, and deleted
{:/comment}

## Test plan

{::comment}
- grouped checklists items per scenario: unit tests to be created, modified, deleted
- if running tests is not possible in the environment, list manual testing guidance for the human
{:/comment}

## History

### <YYYY-MM-DD hh:mm>

**Summary**

{::comment}
- one-liner summary of changes; useable for a git commit
{:/comment}

**Changes**

{::comment}
- bullets of what has changed for this log
{:/comment}
```

## Exceptions and nuances

Depending on the task some or all of these steps may be unnecessary,
this where the understanding step comes in;
make judgement calls and note suggestions for handling nuances in the future
