---
name: teams-post
description: >
  Posts a message to Microsoft Teams via webhook.
  Use when asked to send, post, or deliver a standup to Teams.
---

# Teams Post Skill

When this skill is triggered:

1. Read the TEAMS_WEBHOOK_URL from the .env file using:
   `grep TEAMS_WEBHOOK_URL .env | cut -d= -f2`
2. Format the message as a Teams Adaptive Card JSON payload
3. Post using curl:
   curl -H "Content-Type: application/json" \
    -d '{"text": "YOUR_MESSAGE"}' \
    $TEAMS_WEBHOOK_URL
4. Confirm success by checking the HTTP response code
5. NEVER print the webhook URL in any output
