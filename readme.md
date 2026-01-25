# FeathersJS Project Overview

This is the main repository for the University of British Columbia Software Engineering 2026 FeathersJS project.

## Important links

- [**This repository**](https://github.com/feathersjs/cpsc319)
- [**Project tasks and questions**](https://github.com/feathersjs/cpsc319/issues)
- [**Feathers Discord**](https://discord.gg/qa8kez8QBx)
- [**FeathersJS homepage**](https://feathersjs.com)
- [**Github**](https://github.com/feathersjs/feathers)

Go to [**Project tasks and questions**](https://github.com/feathersjs/cpsc319/issues) to get started and see currently open tasks or to ask questions.

## Background

[FeathersJS](https://feathersjs.com/) is a open-source web framework used to build web applications and REST-APIs using JavaScript / TypeScript.

**Key Features**

- Supports many databases and backend technologies out of the box
- Works over web sockets (important for real-time data streaming) and HTTP
- You create services, and feathers does the boiler plate CRUD code behind the scenes

**Key Use cases**

### 1. Real-Time Dashboards and Chat Apps

Because Web Sockets are "baked in," Feathers is great for apps where data needs to update instantly across multiple users (e.g., a stock ticker, a collaborative editing tool, or a chat interface).

### 2. Rapid Prototyping (MVP)

Feathers provides a CLI that can generate a fully functional, authenticated API connected to a database in minutes. If you need to develop a PoC quickly without sacrificing code quality.

### 3. Microservices

Feathers is extremely lightweight. Its modular nature makes it easy to break a large application into smaller, independent services that communicate with each other seamlessly.

## The Project

### **Background**

FeathersJS has long used a CLI for generating new projects and files used in a FeathersJS project.

The CLI and static code generation can be hard to maintain, is rigid, and does not fit the current scaffolding workflow of many developers who prefer to use LLMs for this purpose.  FeathersJS wants a flexible, `LLM friendly` approach, where developers can more effectively choose technologies and approaches that fit their needs.

### **Key Objectives**

- Explore how LLM assisted developer workflows use open source tools
    - What open source tools exist, i.e [Open Web UI](https://openwebui.com/)
- Provide context and documentation to LLM coding agents
    - Making sure this documentation is up to date
- Create an MCP server to replace the CLI code generation
    - The LLM could either write the code itself, or learn how to use the Feathers CLI to create the code based on the user’s requirements
    - Either way, MCP / RAG will be needed to provide context and how to either use the commands, or how to generate the proper code
- Create examples and documentation on how to integrate FeathersJS with different technologies
    - Blog post style format for other developers
        - Test and make a working example prototype using the AI assisted workflow
        - LLMs can ideally create the documentation for integrating with many different technologies, very manual to write them out.  Student can write assisted by LLM
    - Documents for LLMs to read through *Structured Interfaces*
        - I.e machine readable documents, more focused on providing precise examples and instructions vs documents teaching a human so that they understand.

### Deliverables

**MVP**: 

- Investigate and determine if, and how an MCP server can be built using **open- source** tools to ingest documents, and provide context to an LLM for working with FeathersJS.  (A functional proof of concept)
- Integrate MCP server with LLM assisted developer workflow(s)  (i.e Claude code, Cline, etc.)

**Final Project:**

- Deployed and tested implementation of the MCP server.
- Create a public Feathers API containing an evolving database of questions and best practices (A knowledge base).
- Integrate MCP server with the knowledge base, allowing LLMs to access their content.
- Through the MCP server allow the LLM to summarise questions and best practices inside a project to be reviewed and submitted to the knowledge base.
- Blog posts (one per student) explaining how to use this new workflow to integrate feathers with other technologies.  Any technology stack the students are interested in.

### **Nice to Haves**

Report back a summary of how Claude (or other LLMs) discovered a use case for Feathers, or a new way to use the technology.
- Contributing back to the community of developers
- Create cleaner code, instead of complex CLI code

### Users

**Primary:** Developers using FeathersJS to create REST APIs

**Secondary:** Integrated platforms, and users of these integrated platforms (Cloudflare workers, Deno, Bun). 

### Required Technology

- TypeScript / JavaScript
- LLMs and related tools (e.g. OpenAI, Claude Code, etc.)
- Deno, NodeJS, Bun, Cloudflare Workers
- Model Context Protocol (MCP)
- Github, Open-source
