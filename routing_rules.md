# Routing Rules

## Sentiment-Based Actions

| Sentiment | HubSpot Action | Slack Channel |
|-----------|---------------|---------------|
| Positive (interested) | Set status: "Qualified Lead" | #qualified-leads |
| Positive (meeting request) | Set status: "Meeting Booked" | #meetings |
| Neutral (question) | Set status: "Nurture" | #nurture-queue |
| Negative (not interested) | Set status: "Closed Lost" | — |

## Priority Rules

- If company has > 100 employees → route to enterprise team
- If reply within 1 hour → flag as "hot lead"
- If contains pricing question → cc sales manager
