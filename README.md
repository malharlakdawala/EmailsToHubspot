# Emails To HubSpot

Make.com automation that routes positive email responses from outbound campaigns to HubSpot CRM and syncs lead data with Airtable for tracking.

## Workflow

<img width="843" height="704" alt="Emails to HubSpot Workflow" src="https://github.com/user-attachments/assets/1d5310b0-c8f9-4750-babd-93f641b32a98" />

## Flow

```
Email Bison (positive reply detected)
  → Make.com webhook
  → Parse email metadata + reply content
  → Sentiment classification
  → Create/update HubSpot contact
  → Add timeline note with reply text
  → Log to Airtable
  → Notify sales team on Slack
```

## Field Mapping

| Email Bison Field | HubSpot Property | Airtable Column |
|-------------------|------------------|-----------------|
| `lead_email` | `email` | Email |
| `lead_name` | `firstname`, `lastname` | Name |
| `company` | `company` | Company |
| `reply_text` | `notes` (timeline) | Response |
| `campaign_name` | `utm_campaign` | Campaign |
| `sentiment` | `lead_status` | Sentiment |
| `reply_date` | `last_activity_date` | Reply Date |

## Setup

1. Import `Positive to Hubspot CRM and Airtable.blueprint.json` into Make.com
2. Configure Email Bison webhook trigger
3. Add HubSpot API credentials (private app token)
4. Add Airtable API credentials
5. Configure Slack incoming webhook for notifications

## Routing Rules

| Sentiment | HubSpot Status | Slack Channel |
|-----------|---------------|---------------|
| Interested | Qualified Lead | #qualified-leads |
| Meeting request | Meeting Booked | #meetings |
| Question | Nurture | #nurture-queue |
| Not interested | Closed Lost | — |
