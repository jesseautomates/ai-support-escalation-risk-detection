# AI Support Escalation Risk Detection

This project builds on my first support automation workflow by adding an escalation risk layer on top of AI ticket classification and routing.

Using the same ticket dataset from Project 1, this workflow analyzes sentiment, frustration level, ticket age, reopen count, account tier, and routing context to identify tickets that may require urgent escalation before they become bigger support incidents.

## Why I Built This

In many support environments, tickets are routed by category first, but that alone does not always capture operational risk.

A ticket may look like a standard login, billing, or technical issue on the surface, but still carry escalation signals such as:

- repeated reopenings
- customer frustration
- urgent business impact
- long ticket age
- enterprise account sensitivity

This workflow adds a second decision layer so support teams can identify and act on risky tickets earlier.

## What This Workflow Does

The automation:

1. Loads support ticket data
2. Enriches each ticket with additional operational context
3. Normalizes the ticket schema
4. Uses AI to classify the ticket and recommend the appropriate queue
5. Applies validation and fallback handling
6. Analyzes escalation risk using AI sentiment and risk signals
7. Calculates a final escalation score
8. Generates a human-readable escalation alert
9. Routes urgent cases to an escalation path
10. Sends non-urgent tickets to the appropriate support queue

## Workflow Architecture

Ticket Dataset  
→ Ticket Enrichment  
→ Normalize Ticket Schema  
→ AI Ticket Classification  
→ Validation + Fallback  
→ Merge Valid + Fallback Tickets  
→ Persist Routing Fields  
→ Enrich Ticket Priority  
→ AI Escalation Risk Analysis  
→ Reattach Routing Fields  
→ Parse Escalation Analysis JSON  
→ Calculate Escalation Risk Score  
→ Generate Escalation Alert  
→ Normalize Escalation Score  
→ Escalation Action Decision  
→ Critical/Urgent → Route Ticket to Urgent Escalation  
→ Non-Urgent → Restore Recommended Queue → Route Ticket by AI Queue

## Key Features

- AI-based support ticket classification
- Escalation risk detection using sentiment and ticket context
- Rule-based escalation scoring for explainability
- Human-readable escalation alerts
- Routing preservation from the original classification workflow
- Validation and fallback handling for more reliable automation

## Example Escalation Signals

The workflow considers factors such as:

- frustration score
- negative or angry sentiment
- previous reopen count
- ticket age in hours
- account tier
- current priority
- original routing context

## Example Alert Output

🚨 Escalation Risk Detected

Ticket: TICK-1024  
Customer: Example Customer (Enterprise)

Risk Level: HIGH  
Score: 11

Signals: customer frustration, repeated reopenings, long ticket age

## Tools Used

- n8n
- OpenAI
- Google Sheets
- JSON parsing and code nodes for scoring and routing logic

## Relationship to Project 1

This project uses the same sample ticket dataset as Project 1 and extends the original AI ticket triage workflow with escalation risk detection.

Project 1 focused on:  
**classification + routing**

Project 2 adds:  
**risk detection + escalation override**

That makes this a more realistic support operations automation system rather than a standalone workflow demo.

## What I Learned

A useful support workflow often needs more than classification alone.

This build reinforced the idea that:
- category and urgency are separate decisions
- operational risk can override normal routing
- preserving upstream context matters when adding downstream AI layers
- explainability is important when AI influences escalation decisions

## Future Enhancements

Potential next steps for this workflow:

- SLA breach prediction
- manager notification via Slack or Teams
- write-back to a support system or dashboard
- escalation trend reporting
- customer health or churn risk enrichment

## Files Included

- `workflow.json` — exported n8n workflow
- `screenshots/workflow-overview.png` — workflow architecture screenshot
- `screenshots/escalation-alert-example.png` — sample escalation output

## About This Portfolio Series

Previous project: [AI Support Ticket Triage] ((https://github.com/jesseautomates/ai-support-ticket-triage-automation))

This project is part of a broader set of support operations automation workflows focused on practical AI use cases in support environments.

Previous project:
**AI Support Ticket Triage**
