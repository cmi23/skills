---
name: research-approach
description: Research canonical and trending open-source GitHub repos that solve a similar task and analyze their implementation. Use when the user asks how to implement or design something and wants real-world examples.
---

1. Inspect the user's codebase to identify the ecosystem.
2. Find 2-3 actively maintained, canonical, and trending (= what devs are actually reaching for right now, not just what's historically dominant) GitHub repos from the same ecosystem that solve the user's problem.
3. Present the candidates as a list, each with a link and a brief summary of the pattern they use. Ask the user to select a repo.
4. Analyse the selected repo's pattern. Walk down each branch of the design tree, resolving dependencies between decisions one by one.
5. Briefly present the repo's pattern, with links to specific GitHub files. Keep in mind the user is NOT familiar with the internals of these codebases.
