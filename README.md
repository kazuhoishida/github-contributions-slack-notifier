# Github Contributions Slack Notifier

This repository contains a zsh script that retrieves contributions data from the GitHub API and posts it to a Slack channel. The script can be run manually or automatically using a cron job.

## Prerequisites

To use this script, you will need the following:

- A GitHub personal access token with the `repo` and `user` scope. You can create a new token [here](https://github.com/settings/tokens).
- A Slack bot token. You can create a new bot and token [here](https://api.slack.com/apps). Then, you need to add the bot to a channel.

## Usage

1. Set these env variables:

```
cat << EOF >> ~/.zshrc

#github
export GITHUB_TOKEN=your_github_token
export GITHUB_USERNAME=your_github_username
#slack
export SLACK_TOKEN=your_slack_token
export SLACK_GITHUB_CHANNEL=your_slack_channel_name
EOF
```

2. Modify `channel_name` in the code to a channel name you want to post a message to.

## Cron Job

Set up a cron job to run the script automatically at a specific time. See the Running the Script Automatically with Cron section below for instructions.

Running the Script Automatically with Cron
To run the github-slack-message.zsh script automatically at a specific time, you can use the cron utility on Unix-based systems. cron allows you to schedule commands or scripts to run at specific intervals, such as every day at a certain time.

1. Open your crontab file for editing by running the following command in your terminal:

```
crontab -e
```

2. Add a new line to the crontab file that specifies the schedule for the cron job and the command to run the github-slack-message.zsh script. For example, to run the script every day at 9:00 AM, you can add the following line:

```
# for example, on every Monday 9:00
0 9 * * 1 . ~/.zshrc; cd /path/to/directory && ./github-slack-message.zsh
```

3. Save and close the crontab file.
