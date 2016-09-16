# step-slack

[![wercker status](https://app.wercker.com/status/c7a3b4d90d8746931cbc8a1aa825b8c6/m/master "wercker status")](https://app.wercker.com/project/bykey/c7a3b4d90d8746931cbc8a1aa825b8c6)

A slack notifier written in `bash` and `curl`. Make sure you create a Slack
webhook first (see the Slack integrations page to set one up).

![screenshot](https://raw.githubusercontent.com/futabooo/step-slack/master/screenshot.png)


# Options

- `url` The Slack webhook url
- `username` Username of the notification message
- `channel` (optional) The Slack channel (excluding `#`)
- `icon_url` (optional) A url that specifies an image to use as the avatar icon in Slack
- `notify_on` (optional) If set to `failed`, it will only notify on failed
builds or deploys.
- `branch` (optional) If set, it will only notify on the given branch


# Example

```yaml
build:
    after-steps:
        - slack-notifier:
            url: $SLACK_URL
            channel: notifications
            username: myamazingbotname
            branch: master
```

The `url` parameter is the [slack webhook](https://api.slack.com/incoming-webhooks) that wercker should post to.
You can create an *incoming webhook* on your slack integration page.
This url is then exposed as an environment variable (in this case
`$SLACK_URL`) that you create through the wercker web interface as *deploy pipeline variable*.

# License

The MIT License (MIT)

# Changelog

## 1.2.5
- change slack message

## 1.2.3
- add commit title & commit url on slack message

## 1.2.0

- added `branch` option

## 1.1.0

- `channel` is now optional (wercker/step-slack#5)

## 1.0.0

- Initial release
