Workflow
===

This document describes how the agent will work with the human.

## Overview

The human will direct you on what task or spec you will be working on together.

A typical task development cycle comprises the following steps:

1. Understand the task
2. Gather resources
3. Plan the solution
4. Plan test items
5. Execute plan
6. Update history

**Important:**

- The human may ask you to create or improve a task spec first.
- Some steps may require a few rounds of back-and-forth discussion before proceeding.
- Confirm explicit permission from the human before moving on to the next step.
- The human may ask you to skip steps in the implementation plan.
- For large tasks, the human will want to work on one milestone at a time.


### 1. Understand the task

Ideate and articulate how you understand the spec.
List logical milestones for larger tasks to surface sequencing and scope.
This helps identify constraints and opportunities early.
The human may correct or enhance what you write as clarification or additional context.


### 2. Gather resources

Building on a good understanding of the spec,
it is now time to gather the resources we will use to plan the solution.
This step improves focus and context management —
like a chef preparing every ingredient and tool before cooking.

This typically goes through the following substeps:

1. Collect project and external docs
2. Identify affected systems
3. Identify affected source files
4. Identify security implications


### 3. Plan the solution

With everything on the table,
start thinking about how to create and put things together.
Design patterns and architecture principles come into play here.


### 4. Plan test items

With the plan of attack set,
decide how to verify the outcomes of the solution.
Testing patterns come into play here.


### 5. Execute plan

At this point there is a solid plan of attack.
Execute the solution and test plans as requested by the human.
Expect several iterations and updates to both plan and tests as you progress.


### 6. Update history

We’re done with this task or a milestone.
The human will ask you to write a changelog prior to committing.


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
- one-liner summary of changes; usable for a git commit
- most recent update goes first
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
- one-liner summary of changes; usable for a git commit
- most recent update goes first
{:/comment}

**Changes**

{::comment}
- bullets of what has changed for this log
{:/comment}
```

## Exceptions and nuances

Depending on the task,
some or all of these steps may be unnecessary —
this is where the understanding step comes in.
Make judgment calls and note suggestions for handling nuances in the future.
