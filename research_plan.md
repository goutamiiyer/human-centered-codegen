# Introduction

As more developers turn to AI tools like GitHub Copilot and OpenAI Codex to help them write code, it's clear that these systems are reshaping the way we work. They’re fast, often helpful—but also a bit mysterious. Many developers have found themselves wondering: why did it suggest this piece of code? When the reasoning behind suggestions isn’t clear, it’s easy to misinterpret, misuse, or lose trust in the tool. That’s why I want to explore how we can make code generation tools more understandable. This project focuses on explainable AI (XAI) in the context of code, with the goal of helping developers better interpret and trust what these models produce.

# Motivation

Through my hands-on use of Copilot, I’ve noticed a pattern: the tool often gets things almost right, but misses the mark in subtle, important ways. Common problems include:

    Code that doesn’t reflect the developer’s actual intention
    Solutions that are functional, but not efficient
    Suggestions that could introduce security risks

One example that stood out:
Prompt: "Add logging to this function"

Copilot added verbose logging of entire objects—without filtering out sensitive or irrelevant information. That’s risky in real-world apps, especially when privacy and readability matter.

These moments highlight a deeper issue: Copilot and similar models don’t truly understand developer intent. And that’s where explainability could step in to bridge the gap.

# Methodology

My approach to this project will be hands-on, exploratory, and structured around real-world examples. Here’s the plan:

1. Data Collection: Use prompts for everyday coding tasks like adding logs, fixing bugs, or refactoring. Observe how Copilot responds.

2. Confusion Logging: Take notes on outputs that don’t meet expectations—those that are confusing, inefficient, or seem wrong.

3. Categorization: Organize examples into categories, such as:

    Mismatch between prompt and output (intent misalignment)
    Unsafe or risky code
    Unclear or over-complicated responses
    Missing awareness of code context

4. User Expectation Mapping: For each confusing case, I’ll include what I expected to see and what Copilot actually gave me. This comparison can reveal where an explanation would help most.

# Prototype (Optional)

If time allows, I’d love to build simple “explanation overlays” using Jupyter Notebooks or Markdown. These would show, in plain language:

    What the model probably interpreted from my prompt
    Why it generated the output it did
    What a better or safer alternative might be

This could help shape what an XAI system might look like—one that doesn’t just generate code, but talks you through it.

# Future Work

    Invite other developers to share confusing Copilot outputs (crowdsourced dataset)
    Build a basic plugin to add inline explanations or alerts
    Get feedback from developers on what kind of explanations help most
    Collaborate with researchers in human-computer interaction (HCI) to design better interfaces

# References

Users' Mental Models of GitHub Copilot – Stanford HCI Group

The Promises and Perils of Using AI Code Assistants – CMU

Explainable Code Summarization via Question Answering

Explainable AI for Developers

A Survey of Explainability Techniques in NLP
