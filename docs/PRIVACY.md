# Privacy model

- Cloud AI, speech and email providers receive the content necessary for the feature when configured and used. Their own policies apply.
- Local-only AI prevents cloud fallback for AI generation. Speech has a separate cloud permission. Other installed apps are outside this policy.
- API credentials are user-supplied and encrypted for the device. Never publish exported credentials, keys or app data.
- Household profiles separate preferences and watchlists but are not a secure multi-user boundary.
- Phone sharing creates a temporary read-only snapshot. Anyone with its link and network access can read that snapshot until it expires or is revoked. Treat the QR as a private link.
- The public source contains no personal conversation history, account email, device address, signing key or configured stream feed.
- Debug logs and screenshots should be reviewed before sharing. Do not assume that every third-party SDK or system service is offline.
