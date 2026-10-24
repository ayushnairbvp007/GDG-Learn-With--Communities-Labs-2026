# Google Cloud Challenge Labs 2026

A neatly organized reference for Google Cloud Skills Boost challenge labs, AI exercises, and copy-ready Cloud Shell commands.

> **Important:** These notes were organized from the supplied documents. They are not official Google instructions. Verify commands, project IDs, zones, API requirements, and lab-specific resource names in your active lab before running them. Some source commands have placeholders or inconsistencies and may need adjustment.

## Repository contents

| File | Labs covered |
|---|---|
| [`labs/ai-speech-and-generative-ai.md`](labs/ai-speech-and-generative-ai.md) | ARC131, GSP515, ARC100, GSP319, GSP529, ARC132 |
| [`labs/iam-and-compute.md`](labs/iam-and-compute.md) | ARC134, ARC120 |

## Quick start

1. Open the relevant lab file.
2. Read the task heading and check the lab ID.
3. Copy one complete command block at a time into **Google Cloud Shell**.
4. Replace placeholders such as `YOUR_API_KEY`, `PROJECT_ID`, `REGION`, and `ZONE` with the values for your own lab.
5. Verify the active project before making changes:

```bash
gcloud config get-value project
gcloud config list
```

## Suggested workflow

```bash
# Confirm the active Google Cloud project
gcloud config get-value project

# Set a variable only after confirming the correct project
export PROJECT_ID="$(gcloud config get-value project)"
echo "Project ID: ${PROJECT_ID}"
```

## Safety and troubleshooting

- Do not commit API keys, service-account keys, access tokens, or other secrets.
- Review shell scripts before running them, especially scripts downloaded with `curl`.
- IAM commands can grant broad permissions. Use only the roles required by the lab and remove temporary permissions when appropriate.
- Some original notes contain hard-coded project IDs or mismatched VM zones. Replace these with the values specified by your current lab.
- For API requests, confirm that the required APIs are enabled and that your identity has the necessary permissions.
- If a command fails, check the error message, active project, resource names, region/zone, and required APIs before retrying.

## Suggested repository name

`Google-Cloud-Challenge-Labs-2026`

## License

These notes are personal study material. Add a license only if you have the rights to license all included content and scripts.
