---
name: bnbskillcreator
description: Help a beginner create a Codex/Claude skill, publish it in a public GitHub repository, and submit a valid metadata pull request to bnb-chain/skills-hub. Use this whenever the user wants to create a new skill for BNB Chain Skills Hub, submit a skill to https://github.com/bnb-chain/skills-hub, prepare a `<skillname>-metadata.json`, or needs end-to-end help with GitHub, forks, branches, commits, and pull requests, especially if the user is not technical or does not yet have a GitHub account.
---

# bnbskillcreator

Use this skill as a concierge workflow for non-technical contributors. The user may not know what a repository, fork, branch, JSON, or pull request is. Keep the experience calm, explicit, and concrete.

## Core mission

Get the user from idea to merged submission with as little friction as possible.

The finished outcome is usually:

1. A public GitHub repository that contains the user's skill.
2. A valid metadata file for `bnb-chain/skills-hub`:
   `skills/<skill-id>-metadata.json`
3. A ready PR title and PR description for `https://github.com/bnb-chain/skills-hub`.

Do not stop at “here is how you could do it.” Prefer doing the work, drafting the files, and giving the user the next exact click or command.

## What is true about `skills-hub`

These rules are essential and should be treated as the source of truth unless the repository changes:

- The contributor submits one JSON file inside the `skills/` folder.
- The file name must be `<skill-id>-metadata.json`.
- Required fields are:
  - `github_url`: public GitHub repository URL
  - `category`: array of tags
  - `description`: one or two sentences
- `name` is optional, but usually helpful.
- The file name, minus `-metadata.json`, becomes the skill identifier.
- One PR should contain one skill.
- The repository URL must be public.
- GitHub Actions enriches the metadata automatically after the PR is opened or merged; the contributor does not need to add enrichment fields manually.

Use this starter shape:

```json
{
  "name": "My Skill Name",
  "github_url": "https://github.com/owner/repo-containing-skills",
  "category": ["category1", "category2"],
  "description": "One or two sentences describing what this skill does and when to use it."
}
```

## Default operating style

- Use plain language first. Explain jargon only when needed.
- Assume the user wants you to reduce manual work.
- Prefer browser-friendly GitHub flows when the user is inexperienced.
- If the user is comfortable with terminal + git, you may use that path.
- If the user has no GitHub account, start by helping them create one, then continue.
- If the user has no public repository yet, create the repo plan before writing `skills-hub` metadata.
- If the user already has a repo, validate that it is public and that the skill files are present or can be added.
- Keep the user moving. Ask only for information that cannot be inferred or drafted safely.

## Always collect these inputs

Collect or infer the minimum needed set:

- Skill purpose: what problem it solves
- Trigger moments: when someone should use it
- Expected outputs or deliverables
- Preferred skill name
- Public GitHub repo URL for the skill, if it already exists
- Categories for `skills-hub`
- Short description for the metadata file

If the user does not know how to answer, propose strong defaults and ask for confirmation only at the end of the batch.

## Two deliverables, not one

Keep the user aware that there are two separate artifacts:

### A. The skill repository

This is the user-owned public repository that contains the actual skill. For a single-file skill, that usually means:

```text
<repo-root>/
└── <skill-folder>/
    └── SKILL.md
```

The `SKILL.md` should follow the usual skill pattern:

- YAML frontmatter with `name` and `description`
- Lean body instructions
- Strong trigger wording in the description
- Enough examples and workflow detail to be useful
- No extra filler docs unless truly needed

### B. The `skills-hub` submission

This is a separate PR to `bnb-chain/skills-hub` that adds only:

```text
skills/<skill-id>-metadata.json
```

Do not confuse these two repositories.

## Skill design principles to preserve

When helping the user create the skill itself, preserve the useful core ideas from Anthropic's skill-creator approach:

- Keep `SKILL.md` concise. Include only what the model needs that it would not already know.
- Put trigger guidance in frontmatter `description`, not buried in the body.
- Prefer clear workflow steps over long theory.
- Use examples sparingly but concretely.
- Be “pushy” enough in the description that the skill triggers when it should.
- Default to a single-file skill unless deterministic scripts or large references are genuinely needed.
- If the skill can be expressed cleanly in one `SKILL.md`, do that.

## Workflow

Follow this sequence unless the user already completed part of it.

### Step 1: Determine the user's starting point

Classify the user into one of these states:

- No GitHub account
- Has GitHub account but no skill repo
- Has skill repo but no valid skill yet
- Has valid skill repo and needs `skills-hub` submission
- Has draft PR and needs review/fix

Adapt the help accordingly.

### Step 2: Create or refine the skill

If the user only has an idea, turn it into a single-file skill first.

Produce:

- Skill folder name
- `SKILL.md`
- Recommended repo name
- Short explanation of what the skill does

When drafting `SKILL.md`:

- Normalize the skill name to lowercase letters, digits, and hyphens when used as an identifier.
- Keep the frontmatter description explicit about when to use the skill.
- Write the body in imperative style.
- Include a simple workflow, constraints, and output expectations.
- Include 2 to 4 realistic example prompts if they materially improve reliability.

### Step 3: Get the skill into a public GitHub repository

Choose the least intimidating path.

#### Preferred path for beginners: GitHub web UI

Guide the user through:

1. Create a GitHub account if needed.
2. Click “New repository”.
3. Choose a simple repo name.
4. Make it public.
5. Add a short description.
6. Create the repo.
7. Add the skill folder and `SKILL.md` using the web editor or file upload.

If the user is confused, give exact filenames and folder names to create.

#### Terminal path for users who can handle git

If appropriate, provide exact commands for:

1. Cloning the repo
2. Creating the skill folder
3. Adding `SKILL.md`
4. Committing
5. Pushing

Do not force terminal instructions on a beginner who did not ask for them.

### Step 4: Validate the repo before touching `skills-hub`

Check these conditions:

- The repo URL is public and reachable.
- The repo clearly contains the skill.
- The skill file is named `SKILL.md`.
- The frontmatter has `name` and `description`.
- The skill description says when to use it.

If something is missing, fix that first.

### Step 5: Draft the `skills-hub` metadata file

Create:

```json
{
  "name": "<display name>",
  "github_url": "https://github.com/<owner>/<repo>",
  "category": ["tag1", "tag2"],
  "description": "One or two sentences describing what this skill does and when to use it."
}
```

Rules:

- The file name must be `<skill-id>-metadata.json`.
- `skill-id` should be stable, lowercase, and hyphenated.
- Categories should be short, concrete tags.
- The description should say both what it does and when to use it.
- Do not add enrichment fields like stars, owner profile, or timestamps.

### Step 6: Prepare the `skills-hub` PR path

For beginners, prefer GitHub web UI instructions:

1. Open `https://github.com/bnb-chain/skills-hub`
2. Fork the repository
3. In the fork, open the `skills/` folder
4. Add `/<skill-id>-metadata.json`
5. Paste the JSON
6. Commit to a new branch
7. Open a pull request against `bnb-chain/skills-hub:main`

Also draft:

- PR title
- PR description
- Very short explanation of what happens next

Suggested PR title pattern:

```text
Add <skill-id> metadata
```

Suggested PR body pattern:

```text
## Summary
- add metadata for <skill name>
- include public GitHub repository URL
- include categories and description

## Repository
- <repo url>
```

### Step 7: Explain the automation correctly

Make clear that after submission:

- GitHub Actions checks the GitHub URL
- GitHub Actions enriches metadata automatically
- The contributor does not need to manually fetch owner data, stars, commit hash, or security scan fields

This is important because beginners may try to over-edit the JSON.

## Error handling

When something is wrong, explain the fix in one sentence first, then give the exact replacement.

Common problems:

- Repo is private
- Repo URL points to a profile instead of a repository
- `category` is a string instead of a string array
- Description is too vague
- Metadata file name does not match the intended skill ID
- User tries to submit the full skill into `skills-hub` instead of only metadata
- User opens a PR against the wrong base repository

## Output templates

When the user asks for end-to-end help, prefer this output order:

1. Suggested skill name
2. Suggested repo name
3. Final `SKILL.md`
4. Final `<skill-id>-metadata.json`
5. PR title
6. PR body
7. Next exact actions

## Communication rules for beginners

- Never assume the user knows GitHub vocabulary.
- Replace “fork” with “make your own copy on GitHub” the first time you mention it.
- Replace “PR” with “pull request” first, then you may shorten it later.
- If the user seems overwhelmed, collapse choices and recommend one path.
- If the user writes in Chinese, respond in Chinese unless they ask otherwise.
- Use short numbered steps for browser actions.

## Review checklist

Before finishing, verify all of the following:

- The skill repository URL is public.
- The repository actually contains the skill.
- The skill is understandable as a single-file skill.
- The metadata JSON uses the correct file naming convention.
- The JSON fields match `skills-hub` expectations.
- The description says what the skill does and when to use it.
- The PR targets `bnb-chain/skills-hub`.
- The user has a copy-paste-ready final payload.

## Example of a good contribution package

### Skill repo

- Repo: `https://github.com/<owner>/<repo>`
- Contains: `<skill-folder>/SKILL.md`

### Metadata file

File name:

```text
skills/<skill-id>-metadata.json
```

Content:

```json
{
  "name": "<Human Friendly Skill Name>",
  "github_url": "https://github.com/<owner>/<repo>",
  "category": ["bnb-chain", "automation"],
  "description": "Helps users do X and should be used when they need Y."
}
```

### Pull request

- Base repo: `bnb-chain/skills-hub`
- Base branch: `main`
- Scope: one metadata file for one skill

## What not to do

- Do not ask a beginner to learn a full git workflow if the browser can solve it.
- Do not create extra documentation files unless the user explicitly wants them.
- Do not submit the actual `SKILL.md` into `skills-hub`.
- Do not invent unsupported metadata fields.
- Do not leave the user with an abstract checklist if you can provide the exact file content.

