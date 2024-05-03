# EagleAI Security Assist

## Overview:

We enhance security systems by legeraging AI to provide immediate, actionable security reports. Our system, EAGLE (Enhanced Automated Guardian for Living Environments) AI, reduces false positive notifications and provides detailed summaries of any detected irregularities.

## Inspiration:

After using popular security systems, we noticed a large amount of false positive notifications. Eventually, many of us became desensitized to these notifications, making it hard to determine if the alert was for an actual emergency or for something as minor as a stray animal. Receiving notifications such as "There Is Motion Detected at Your Front Door" didn't tell us the severity of the notification. This is a huge problem, especially in home security, where every second counts.

## Features:

- Detailed summary of irregularities instead of generic notifications.
- Estimates severity and provides options for next steps.
- Applications in personal security and large-scale surveillance.

This empowers the users with the immediate information needed to respond to the situation instead of them needing to manually classify the severity of the situation by rewatching security footage.

## How It Works:

- Part 1: Google Nest API: Using the Google Nest developer API, we are able to access a backhand route to getting the camera feed of any Nest camera. We then process the WebRTC stream through the YOLOve model to parse
through the frames and analyze whether or not there is a person being detected. If it detects a person, it will send it to Gemini.

- Part 2: Gemini: Once the frames are sent to Gemini, the model will process the frames and also, with a given prompt that asks for a detailed report, it will generate a detailed report ergarding the main events, the suspicion level, and recommended steps if needed.

- Part 3: Text Message: Once the report is finalized, using Python's EmailMessage library, we will send a text message of the report to the individual user notifying them of the situation and what the recommended next steps are.

## Add-On:

Considering that access to a Nest camera and using the Nest developer API to get this system working isn't available for everyone, we built an alternative to the general system on StreamLit. Instead of using a Nest camera, it will employ the webcam of a computer as the camera and run the model using your webcam feed. Link to StreamLit: 
