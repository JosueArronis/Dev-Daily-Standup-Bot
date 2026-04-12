# /standup (with Agent Review)

1. Spawn the `writer` agent with context: git log, tasks.txt, memory.json
   → Collect the draft standup text

2. Spawn the `reviewer` agent and pass it the draft
   → Collect the review: APPROVED or REVISION NEEDED

3. If REVISION NEEDED:
   → Show the feedback to the user
   → Ask the writer agent to revise (max 1 retry)

4. Show the final draft to the user
   → Ask: 'Post to Teams? (yes/no)'

5. If yes, use the `teams-post` skill to send it

6. Update memory.json with the final standup and today's date
