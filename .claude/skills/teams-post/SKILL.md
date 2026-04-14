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
2. The standup message may contain literal `\n` escape sequences or actual newlines.
   Normalize them into actual newlines first:
   `MESSAGE=$(printf '%b' "$STANDUP_TEXT")`
3. Build the JSON payload safely using jq so newlines are properly encoded:
   `JSON=$(jq -n --arg text "$MESSAGE" '{"text": $text}')`
4. Post using curl:
   curl -s -o /tmp/teams_response.txt -w "%{http_code}" \
    -H "Content-Type: application/json" \
    -d "$JSON" \
    "$TEAMS_WEBHOOK_URL"
5. Confirm success by checking the HTTP response code (expect 200 or 202)
6. NEVER print the webhook URL in any output
