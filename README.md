# AI Career Path Automation System

## Overview

The AI Career Path Automation System is an automated workflow that generates personalized learning plans using AI. It integrates webhook triggers, workflow automation, and language models to deliver instant career guidance at scale.

## Features

* Uses conditional logic to differentiate between professional career goals and personal hobbies.
* Leverages GPT-3.5-Turbo to generate structured learning steps and suggest specific free online courses or YouTube titles.
* Sends the final roadmap directly to the user's Gmail in a "colorful theme" HTML format.
* Automatically updates a Google Sheet to log whether a plan was successfully processed or if an error occurred.

## Tech Stack

1. n8n Platform
2. gpt-3.5-turbo AI Model
3. Required Credentials:
   * OpenAI API
   * Google Sheets OAuth2
   * Gmail OAuth2

## How It Works

1. A Webhook receives data (likely from a Google Form or custom frontend) containing the user's name, email, desired skills, and timeframe.
2. An If Node checks the "Why you want to learn it?" field.
* If "Work": It triggers a prompt focused on job-readiness.
* If "Hobby": It triggers a prompt focused on personal enjoyment.
  
3. The OpenAI Node uses the provided skills and timeframe to build a step-by-step plan.
4. * The system emails the plan via Gmail and marks the row as "done" in Google Sheets.
   * If the AI fails, an automated error notification is sent to the user, and the sheet is marked with "Error".

## Results

Processes user requests in under 10 seconds, eliminates manual planning effort, and scales reliably across multiple users.

## Future Improvements

* Web dashboard for user tracking
* Expanded AI personalization features
* Analytics for learning progress monitoring
