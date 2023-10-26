# zima-standards
Repository that holds standardized information about contributing in the Zima project


## Table of Contents

- [zima-standards](#zima-standards)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Issues](#issues)
      - [Atomicity](#atomicity)
      - [Naming Convention](#naming-convention)
      - [Issue types](#issue-types)
      - [Acceptance criteria](#acceptance-criteria)
        - [About](#about)
        - [Format](#format)
      - [Creating an issue](#creating-an-issue)
  - [Endpoint Naming Conventions](#endpoint-naming-conventions)
      - [RESTful Principles](#restful-principles)
      - [Standard Structure](#standard-structure)
      - [Avoiding Exposed Actions](#avoiding-exposed-actions)
      - [Nesting for relationships](#nesting-for-relationships)
  - [Coding Standards](#coding-standards)
      - [Directory Structure](#directory-structure)
      - [Code Formatting](#code-formatting)
  - [Commit and Merge Requests Guidelines](#commit-and-merge-requests-guidelines)
      - [Branching naming convention](#branching-naming-convention)
      - [Commit Messages](#commit-messages)
      - [Code Reviews](#code-reviews)
  - [Testing Standards](#testing-standards)
      - [Unit Testing](#unit-testing)
      - [Integration Testing](#integration-testing)
  - [Documentation Standards](#documentation-standards)
      - [Inline Comments](#inline-comments)
      - [API Documentation](#api-documentation)

## Introduction

In today's fast-paced development environment, maintaining consistency, clarity, and efficiency is paramount. As our project evolves, the need for a standardized approach to collaboration becomes increasingly evident. This document aims to address that need, providing clear guidelines and best practices for our Nest.js backend project.

The primary objective of this guide is to ensure that we, as a team, are aligned in our development efforts. By adhering to these standards, we can ensure that our codebase remains clean, our endpoints are intuitively named, and our collaboration is seamless. Furthermore, a standardized approach reduces the learning curve for new team members, facilitates effective code reviews, and promotes a culture of excellence.

## Issues

#### Atomicity
For our project, every bug, documentation update, or new feature should be split into atomic parts. Each atomic part will be represented as an individual issue on our project management tool or version control platform.

#### Naming Convention
To maintain consistency and clarity in our issue tracker, we've established the following naming convention:

Backend Issues: [BE] Feature/Bug/Docs: Issue title
Frontend Issues: [FE] Feature/Bug/Docs: Issue title
For example:

A backend feature might be named: [BE] Feature: Implement authentication middleware
A frontend bug might be named: [FE] Bug: Fix alignment in login form

#### Issue types

There are 4 possible labels for issues.

| Feature | Bug | Documentation | Won't fix |
|---------|----------|---------|-----------|
| Used for new features / enhancements  | For creating issues that point to bugs / defects  | For writing documentation | If the issue will not be worked on

#### Acceptance criteria

##### About
Acceptance criteria provide a clear understanding of the expected outcome of an issue. They offer a set of conditions that the implemented solution must meet to be considered complete.

Key Components of Acceptance Criteria
- Clear & Concise: They should be straightforward and easy to understand.
- Testable: The criteria should allow for verification through tests.
- Objective: They must be free from personal biases and be based on the issue's requirements.

##### Format
A commonly used format is the "Given-When-Then" structure:

- Given: Describes the initial context.
- When: Describes the action or trigger.
- Then: Describes the expected outcome.

```
Given: I am a logged-in user
When: I click on the 'Delete' button next to a post
Then: 
    - The post should be removed
    - A confirmation message should be shown
```

#### Creating an issue

An issue can be created by navigating to zima github project and hitting the __+__ button under one of the boards tabs.

Then, from the left menu, click __+__ and __Create a new issue__
Then add the following info:
- Title: based on the above mentioned naming convetion
- Description: based on the above mentioned __acceptance criteria__
- Label: choose one of the four possible __labels__
- Milestone: Select one of the available __sprints__
- Assignee: can be directly assigned to a team member *(optional)*

## Endpoint Naming Conventions

#### RESTful Principles

A quick introduction to RESTful principles, emphasizing uniformity, statelessness, and client-server architecture.

#### Standard Structure

- **Resources**: Always use plural nouns (e.g., `users`, `orders`).
- **Actions**: Instead of exposing endpoints like `/users/create` or `/update-user`, we'll adopt a more RESTful approach:
  - `POST /users`: Create a new user.
  - `PUT /users/{id}`: Update a user with a specific ID.
  - `DELETE /users/{id}`: Delete a user with a specific ID.
  - And so on...

#### Avoiding Exposed Actions

In order to better comply to restful standards, we have to make use of __HTTP verbs__ instead of using verbs in the URL.

Instead of using `/resource/update` or  `/resource/delete`, we have to let the __HTTP verbs__ describe the action we are applying to that resource. 

So, a more restful approach would be creating two enpoints:

- `PUT: /resource/{id}`
- `DELETE: /resource/{id}`

This way we only use nouns instead of verbs when exposing endpoints.

#### Nesting for relationships

Different endpoints can be interlinked, like getting a specific message from a specific user. This would require looking into the list of messages for a message sent by the specific user.

Such an endpoint might look like this:

`/messages/userId` 
`/messages/{userId}`
`/messages/user/{userId}` 

They all comply with restfull standards and tell the user of the api that this enpoint looks into the messages resource by user id.


## Coding Standards

#### Directory Structure

When using nest.js, the code format is based on the modules. A module reflects a resource and actions that are taken on that resource, thus, a module can contain:
- controller
- service
- repository layer
- dtos
- interface
- specific middleware for this module

A good directory structure is to include everything tied to the resource in a directory named by the resource, this means that for the __cat__ module we will have a directory named "cat" and the following files and directories

- cat (directory)
  - cat.service
  - cat.module
  - cat.controller
  - dtos (directory)
    - catCreateDto
    - catDeleteDto
    - etc
  - interface (directory)
    - cat.interface
    - cat.schema

#### Code Formatting

We use Pretier for formatting code.

## Commit and Merge Requests Guidelines

#### Branching naming convention
Branching naming convention follow those of issue naming convention.
The following naming strategy applies

`<type>/<issue-title>` with "-" between issue title words.


For an issue 
`[BE] Feature: create oauth2 controller` we create a branch:
`feature/create-oauth2-controller`

Same goes for an issue:
 `[BE] Bug: user controller not using http codes` we create a branch:
`bug/user-controller-not-using-http-codes`


#### Commit Messages

Commit messages should be atomic and granular. This means that when working on a issue there should be multiple commits that can each be reversed to a stable build.

Commit messages should follow roughly the format by [convetional commits](https://www.conventionalcommits.org/en/v1.0.0/).

This means that based on the issue label and issue title, a commit message will look like this:

`<type>:<issue title> <description>`

Type can be:
- *fix* for *bug* issue label
- *feat* for *feature* issue label
- *docs* for *documentation issue label*

The description should be short and concise and reflect what work has been done to the issue.

Example

`feat: create-user-repo: created repository and user dtos `
`fix: fix-login-alignment: fixed login page alignment `


#### Code Reviews

Before merging pull requests, a PR has to be approved by at least another member of the team, and not have any conflict.

If quality gates are implemented, a PR should pass all quality gates and build without any errors before merging.

## Testing Standards

#### Unit Testing

Write unit tests at least (update here)

#### Integration Testing

Idk if needed (update here)

## Documentation Standards

#### Inline Comments

Use inline comments whenever the codes gets too complex and too hard to understand.

#### API Documentation

Currently using Swagger for API documentation to better link the frontend and backend teams.