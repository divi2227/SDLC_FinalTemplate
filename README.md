# 🧪 Demo Flow (Step-by-Step)
## Step 1️⃣ Clone & Open the Repository

## From GitHub:

- git clone <repository-url>
- cd <repository-name>
- code .


- Open the folder in VS Code.

## Step 2️⃣ Enable GitHub Copilot / Claude Code

- Open GitHub Copilot Chat / Claude Code Terminal

- Select GPT-5.2-Open AI or Claude (Opus/Haiku/Sonnet) as the model / Claude Opus 4.5

- Ensure Copilot / Claude has access to workspace files

## Step 3️⃣ Understand prompts.txt

## prompts.txt contains ordered instructions telling Copilot / Claude:

- Which files to generate

- In what sequence

- What context to use

👉 This is the single control file for the demo

## Step 4️⃣ Requirement Phase (AI-Assisted)

## Action:

## Open Copilot Chat / Claude Code and run:

- “Execute the prompts in prompts.txt under REQUIREMENTS sequentially for the requirements folder.”

## What AI Does:

- Reads 00_raw_input.md

- Generates structured content across:

=> Problem statement

=> Goals

=> Scope

=> PRD

=> User stories

=> Acceptance criteria

## Each file:

- Uses prior files as context

- Avoids hallucination (rules enforced in file headers)

- Produces review-ready content

# 📈 Result:

- Requirements preparation effort reduced by ~50–60%

## Step 5️⃣ Design Phase (HLD & LLD)

## Action:

## After requirements are complete, ask:

- “Re-read prompts.txt and execute the prompts for DESIGN phase - HLD & LLD.”

## High-Level Design (HLD)

## AI generates:

- System architecture overview

- Component boundaries

- Data flow descriptions

- Tech stack decisions

- Non-functional requirements

- Low-Level Design (LLD)

## AI generates:

- Component-level behavior

- API contracts

- Database schemas

- Sequence flows

- Error handling

- Open design questions

## Architecture Diagram
- AI generates the diagrams for HLD and LLD.

# 📈 Result:

- Design documentation generated faster with higher consistency and traceability.

## Step 6️⃣ Code Generation

## Action:

## Ask Copilot / Claude:

- “Generate the application code using the finalized PRD, HLD, and LLD.”

## AI Responsibilities:

- Follow design constraints

- Generate modular, readable code

- Align with documented APIs and schemas

- Human verifies correctness and feasibility.

## Step 7️⃣ AI-Assisted Code Review

## Action:

## Ask Copilot / Claude:

- “Read the CODE_REVIEW.md file which has the prompt to be executed and generate the content in that file.”

## AI checks for:

- Code smells

- Design violations

- Performance issues

- Security risks

- Readability and maintainability

## Step 8️⃣ AI-Driven Refactoring

## Action:

## After human review:

- “Fix the issues identified in the code review and refactor the code.”

## AI:

- Applies minimal, safe changes

- Preserves functionality

- Improves structure

## Step 9️⃣ Run the Application

## Human runs the application locally to ensure:

- It builds successfully

- Core flows work as expected

## Step 🔟 Automated Testing with AI (Playwright)

## Action:

## Ask Copilot / Claude:

- “Read the AI_TEST_CASES.md file which has the prompt to be executed and generate the test cases in 'PLAYWRIGHT' folder for Playwright to execute.”

## Test Coverage Includes:

✅ Unit tests

✅ API tests

✅ UI functional tests

✅ User journey tests

✅ Navigation & click-flow tests

✅ Error Handling

## AI generates:

- Test structure

- Assertions

- Test data

- Reusable utilities

- Tests are then executed locally.

## Deployment on RENDER

## Follow these steps to deploy the project on Render using GitHub integration:
## ✅ Pre-requisites:

- Project pushed to GitHub

- App runs locally

- Render account created

- Required config files present (package.json, requirements.txt, Dockerfile, etc.)

## 🧩 Steps

## Prepare the App

- Ensure the app listens on process.env.PORT

- Commit and push latest code to GitHub

## Create Render Service

- Go to Render Dashboard → New → Web Service

- Connect GitHub and select the repository

## Configure Service

- Environment: Node / Python / Docker / Java

- Branch: main

- Build Command: install & build dependencies

- Start Command: start the application

## Set Environment Variables

- Add secrets like DATABASE_URL, API_KEYS, etc. in Render dashboard

## Deploy

- Click Create Web Service

- Monitor logs until deployment succeeds

- Access the app using the generated public URL

## Auto Deploy

- Enabled by default

- Any push to the deployment branch triggers redeployment

## 🛠 Notes

- Free tier may have cold starts

- Check Render logs for errors if deployment fails
- 

# 📊 What This Demo Proves

- AI can accelerate every SDLC phase

- Productivity gains come from:

- Reduced blank-page effort

- Fewer clarification loops

- Automated testing & review

## Quality is preserved through:

- Structured prompts

- Human approval

- Version control

# 🧠 Key Takeaway

AI does not replace engineers — it removes friction.
Engineers focus on decisions, not repetition.








