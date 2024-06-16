# Telegram Notifications Integration GH Action

## Overview

This GitHub action can be used in any repository to send notifications to a Telegram chat.
The following PR events will trigger a notification:
- PR approval
- PR changes requested
- PR review commented
- PR opened (in draft or non-draft)
- PR is set as ready for review

## Example

Create the workflow in `.github/workflows` in a reposistory to make use of this action:

```yml
# telegram-notifications.yml

name: Telegram notifications

on:
    pull_request:
        types: [opened, ready_for_review]
    pull_request_review:
        types: [submitted]

jobs:
    notify:
        runs-on: ubuntu-latest
        steps:
            - name: Telegram Notify
              uses: invexa-foundation/github-action-telegram-notifications@main
              with:
                  to: ${{ secrets.TELEGRAM_TO }}
                  token: ${{ secrets.TELEGRAM_TOKEN }}
```
