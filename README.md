# Vibe Code 101 V2
**by Austin Sebastian Marviano**

**Written on:** 8 Oct 2025  
**Last Update:** October 06, 2025

---

## Quick Start
so u wanna build stuff with ai? cool! u basically need one of these two tools:  
- **Claude Sonnet 4.5**, in Claude Code
- **gpt-5-codex (high)**, in Codex CLI 

this guide works for both terminal versions and vscode extensions (both codex and claude code have extensions with tneir interfaces).

*(btw: i used to use **Grok 3**, then switched to **Gemini 2.5 Pro**. now im using **Claude 4.5** (or **gpt-5-codex (high)**))*


getting everything set up right is super important. if ure serious about making a fully working and nice looking game (or app), take time to build a solid foundation.  

**main rule:** *planning is key.* dont let the ai plan by itself, or ur codebase will turn into a total mess.

---

## Getting Everything Ready

### 1. Project Requirements Doc
- take ur game idea and ask **gpt-5** or **sonnet 4.5** to make a simple **project requirements document** in markdown: `project-requirements.md`.  
- check and improve the doc to make sure it matches ur vision. its fine if its basic—the point is to give ur ai context about the projects structure and goals. dont over-engineer bcs i'll iterate later.

### 2. Tech Choices and `RULES.md` / `GUIDELINES.md`
- ask **gpt-5** or **sonnet 4.5** to suggest the best tech stack for ur game (like threejs and ibsocket for multiplayer 3d games). save this as `tech-choices.md`.
  - challenge it to suggest the *simplest but most solid stack possible*.  
- in ur terminal, open **claude code** or **codex cli** and use the `/init` command. it'll use the two .md files u made so far. this creates rules so ur llm is guided properly. 
- **super important:** review the generated rules. make sure they focus on **modularity** (multiple files) and avoid **monoliths** (one huge file). u might need to manually adjust or add rules. also check when they trigger.
  - **critical:** some rules are essential for keeping context and should be set as **"always"** rules. this makes sure the ai *always* checks them before writing code. consider adding rules like these and marking them as "always":
    > ```
    > # CRITICAL:
    > # always read project-docs/@architecture.md before writing any code. include full database schema.
    > # always read project-docs/@project-requirements.md before writing any code.
    > # after adding a major feature or finishing a milestone, update project-docs/@architecture.md.
    > ```
  - example: make sure other (non-"always") rules guide the ai toward best practices for ur stack (like networking, state management, etc.).
  - *this whole rules setup is required if u want a game that's as optimized as possible, and code as clean as possible.*

### 3. Development Roadmap
- give **gpt-5** or **sonnet 4.5** these files:  
  - the project requirements document (`project-requirements.md`)
  - the tech stack suggestions (`tech-choices.md`)
- ask it to create a detailed **development roadmap** in markdown (`.md`) which is a list of step-by-step instructions for ur ai developers.  
  - steps should be small and specific.  
  - each step must include a test to check correct implementation.  
  - no code—just clear, concrete instructions.  
  - focus on the *core game*, not the full feature set (details come later).  

### 4. Project Docs
- create a new folder for ur project and open it in vscode.
- inside the project folder, create a subfolder named `project-docs`.  
- add these files to `project-docs`:  
  - `project-requirements.md`  
  - `tech-choices.md`  
  - `development-roadmap.md`  
  - `completed-tasks.md` (create this empty file for tracking finished steps)  
  - `architecture.md` (create this empty file for documenting file purposes)

---

## Vibing the Core App

### making sure everything makes sense
- open **codex** or **claude code** in vscode extensions or launch claude code or codex cli in ur project terminal. 
- prompt: read all the documents in `/project-docs`, is `development-roadmap.md` clear? what questions do u have to make it 100% clear?
- it usually asks 9-10 questions. answer them and prompt it to edit the `development-roadmap.md` accordingly, so its even better.

### ur first build prompt
- open **codex** or **claude code** in vscode extensions or launch claude code or codex cli in ur project terminal.  
- prompt: read all the documents in `/project-docs`, and proceed with step 1 of the development roadmap. i will run the tests. dont start step 2 until i validate the tests. once i validate them, open `completed-tasks.md` and document what u did for future developers. then add any architectural insights to `architecture.md` to explain what each file does.
- **always** start with "ask" mode or "plan mode" (`shift+tab` in claude code) and once u are satisfied, allow the ai to go through the step.

- **extreme vibe:** install [superwhisper](https://superwhisper.com) to talk casually with claude or gpt-5 instead of typing.  

### workflow
- after finishing step 1:  
- commit ur changes to git (if u dont know how, ask ur ai for help).  
- start a new chat (`/new` or `/clear`).  
- prompt: now go through all files in the project-docs, read completed-tasks.md to understand prior work, and proceed with step 2. dont start step 3 until i validate the test.
- repeat this process until the entire `development-roadmap.md` is complete.  

---

## Adding Features
congrats, uve built the core game! it might be rough and missing features, but now u can experiment and improve it.  
- want fog, post-processing, effects, or sounds? a better plane/car/castle? a beautiful sky?
- for each major feature, create a new `feature-roadmap.md` file with short steps and tests.  
- implement and test incrementally.  

---

## Fixing Bugs and Getting Unstuck
- if a prompt fails or breaks the game:  
- use `/rewind` in claude code and refine ur prompt until it works. if using gpt-5, u can commit often to git and reset when needed.
- for errors:  
    - **if javascript:** open the console (`f12`), copy the error, and paste it into vscode to provide a screenshot for visual glitches.  
    - **lazy option:** install [browsertools](https://browsertools.agentdesk.ai/installation) to skip manual copying/screenshotting.  
- if stuck:  
    - revert to ur last git commit (`git reset`) and retry with new prompts.  
- if *really* stuck:  
    - use [repoprompt](https://repoprompt.com/) or [uithub](https://uithub.com/) to get ur whole codebase in one file and ask **gpt-5 or claude** for help.  

---

## claude code & codex tips
- **codex cli or claude code in terminal:** run either tool inside vscode terminal to view diffs and feed extra context without leaving ur workspace.
- **claude code `/rewind`:** use this command to roll the project back to an earlier state if an iteration misses the mark.
- **custom claude code commands:** create helpers like `/explain $arguments` that trigger a prompt like "do a deep-dive on the code and understand how $arguments works. once u understand it, let me know, and i will provide the task i have for u." so the model pulls in rich context before editing.
- **clearing context:** clear context frequently with `/clear` or `/compact` if u still need previous conversations context.
- **save time (at ur own risk):** use `claude --dangerously-skip-permissions` or `codex --yolo` to start claude code or codex cli in a mode where it will never ask u confirmations.

## other tips
- **small edits:** use gpt-5 (medium)
- **great marketing copywriting:** use opus 4.1
- **generate great sprites (2d images):** use chatgpt and nano banana
- **generate music:** use suno
- **generate sound effects:** use elevenlabs
- **generate video:** use sora 2
- **better prompt outputs:** 
    - add "think as long as needed to get this right, i am not in a hurry. what matters is that u follow precisely what i ask u and execute it perfectly. ask me questions if i am not precise enough." 
    - for claude code, use specific phrases to trigger deeper reasoning: `think` < `think hard` < `think harder` < `ultrathink`.

---

## frequently asked questions
**q: i am making an app, not a game, is this the same workflow?**  
**a:** its mostly the same workflow, yes! instead of a gdd (game design document), u can do a prd (product requirements document). u can also use great tools like v0, lovable, or bolt.new to prototype first and then move ur code to github, and then clone it to continue on vscode or in the terminal with this guide.


**q: why is claude code or codex cli better than cursor right now?**  
**a:** it really is up to ur liking. i highlight that claude code is better at using claude sonnet 4.5, and codex cli is better at using gpt-5 than cursor is at using either of them. having them live in the terminal unlocks many more development workflows: working from any ide, hopping onto a remote server through ssh, and so on. there are poirful customization options such as custom commands, sub-agents, and hooks that will speed up both the quality and the pace of development over time. finally, if ure on the loir-tier claude or chatgpt plan, thats enough to get started.

**q: i dont know how to set up a server for my multiplayer game**  
**a:** ask ur ai.

---