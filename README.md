# Meeting Scheduler Bot for n8n

An intelligent Telegram bot that automates scheduling 1-to-1 meetings between a business owner and employees. The bot collects missing details conversationally, (optionally) checks the owner's calendar for conflicts, gets final confirmation, creates the event in Google Calendar, and notifies the employee via email.

## Problem It Solves

Scheduling individual meetings manually is time-consuming and error-prone:
- Back-and-forth messages to find a suitable time
- Forgetting to check calendar availability
- Typing the same details multiple times (employee email, agenda, location, etc.)
- Risk of double-booking or missed invitations
- No centralized record or automated reminders

This bot eliminates all of that by turning a simple Telegram message into a fully booked calendar event with zero manual intervention after confirmation.

## Key Features

- **Conversational flow**: Asks only for missing information, one compact question at a time
- **Smart employee lookup**: Pulls email, role, and phone number from a Google Sheet by employee name
- **Calendar conflict detection** (optional): Checks owner's Google Calendar before proposing a time
- **Flexible meeting options**:
  - Duration (default 1 hour)
  - Location: `office` or `video` (automatically creates and includes Google Meet link)
  - Custom title/agenda
  - Optional extra participants (multiple emails)
- **Final summary & confirmation**: Shows a clear overview and waits for "Confirm / Edit / Cancel"
- **Automated actions on confirmation**:
  - Creates event in Google Calendar
  - Sends detailed email to employee (with Meet link if video)
  - Sends confirmation message to owner on Telegram
- **Session memory**: Uses Simple Memory to maintain conversation state
- **Timezone aware**: All times handled in **Africa/Cairo (UTC+2)**

## Tools & Integrations

- Telegram (trigger & messaging)
- Google Sheets (employee directory lookup)
- Google Calendar (conflict check & event creation)
- Gmail (employee notification)
- OpenAI GPT (natural language parsing & response generation)
- Simple Memory (conversation state)

## Quick Start with Docker

```bash
git clone https://github.com/YOUR_USERNAME/meeting-scheduler-bot.git
cd meeting-scheduler-bot
docker compose up -d