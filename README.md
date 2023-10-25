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
  - [Coding Standards](#coding-standards)
      - [Directory Structure](#directory-structure)
      - [Code Formatting](#code-formatting)
      - [Dependency Management](#dependency-management)
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
  - [Conclusion](#conclusion)

## Introduction

In today's fast-paced development environment, maintaining consistency, clarity, and efficiency is paramount. As our project evolves, the need for a standardized approach to collaboration becomes increasingly evident. This document aims to address that need, providing clear guidelines and best practices for our Nest.js backend project.

The primary objective of this guide is to ensure that we, as a team, are aligned in our development efforts. By adhering to these standards, we can ensure that our codebase remains clean, our endpoints are intuitively named, and our collaboration is seamless. Furthermore, a standardized approach reduces the learning curve for new team members, facilitates effective code reviews, and promotes a culture of excellence.

## Issues

#### Atomicity
For our project, every bug, documentation update, or new feature should be split into atomic parts. Each atomic part will be represented as an individual issue on our project management tool or version control platform.

#### Naming Convention
To maintain consistency and clarity in our issue tracker, we've established the following naming convention:

Backend Issues: [BE] Feature/Bug/Docs: Detailed Issue Description
Frontend Issues: [FE] Feature/Bug/Docs: Detailed Issue Description
For example:

A backend feature might be named: [BE] Feature: Implement authentication middleware
A frontend bug might be named: [FE] Bug: Fix alignment in login form

#### Issue types

There are 4 issue types for zima project.

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

Explanation on why `/resource/action` is discouraged and the benefits of using a RESTful approach.

## Coding Standards

#### Directory Structure

Briefly discuss the recommended directory structure for Nest.js projects.

#### Code Formatting

Mention tools like Prettier or ESLint and any specific configurations or rules the team should follow.

#### Dependency Management

Guidelines on adding new dependencies, ensuring compatibility, and keeping the `package.json` and `package-lock.json` files clean.

## Commit and Merge Requests Guidelines

#### Branching naming convention
Branching naming convention

#### Commit Messages

Emphasize clear, concise commit messages. Maybe follow a pattern like: `<issue label>: <description>`.

#### Code Reviews

The importance of peer reviews, what to look for, and how to provide constructive feedback.

## Testing Standards

#### Unit Testing

Briefly describe the importance of unit tests, tools (e.g., Jest), and coverage targets.

#### Integration Testing

Discussion on how to write integration tests, especially for the endpoints.

## Documentation Standards

#### Inline Comments

Guidance on where and how to comment within code.

#### API Documentation

Recommend tools like Swagger for API documentation and how to ensure it's consistently updated.

## Conclusion

Reiterate the importance of these standards and encourage team members to suggest improvements as the project evolves.

