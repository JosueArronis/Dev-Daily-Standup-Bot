# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this project does

Dev-Daily-Standup-Bot — a bot for automating developer daily standups.

This bot reads recent git commits and today's task list,
then writes a formatted standup and posts it to Microsoft Teams.

## Tools available

- `git log` — use to read commit history
- `cat tasks.txt` — use to read the current task list
- `memory.json` — read/write to remember yesterday's standup
- `.env` — contains TEAMS_WEBHOOK_URL (never print this value)

## Output rules

- Standup format: Yesterday / Today / Blockers
- Keep each section to 2-3 bullet points maximum
- Use plain language, no jargon
- Never fabricate tasks that are not in git log or tasks.txt

## What NOT to do

- Do not commit .env
- Do not print the webhook URL in any output
- Do not invent blockers if there are none — write 'No blockers'

## Memory

- Before writing the standup, read `memory.json`
- If `last_standup` is not null and `last_run_date` is yesterday,
  start the standup with a comparison line
- After posting, update `memory.json` with today's standup and today's date
