# Grafana Alert Template: Your Savior from the Depths of Hell 🚀

Are you tired of the torment and despair caused by Grafana's lack of documentation for alerting? Fear not, for I have descended from the heavens to rescue you! Introducing the **Grafana Alert Template**, your ultimate salvation in the realm of alerting.

With this easy-to-use template, you'll experience a euphoric escape from the fiery pits of confusion. Say goodbye to countless hours of frustration and confusion, and embrace the beauty of simplicity.

just make 2 templates for slack and telegram in your grafana with these and you will see how it feels to walk among Gods.

## Features:
- **Slack, Mattermost, Rocket Chat Integration**: Connect with your favorite messaging platforms and receive alerts directly to your team's channels. Stay informed and take swift action!
- **Telegram Integration**: Join the Telegram revolution and receive alerts in style. It's time to level up your alert game and impress your peers!

### Alert Templates
                                                 👇🏼 Slack - RocketChat - MatterMost 👇🏼
<image src=slack-1.png><image src=slack-2.png><image src=slack-3.png>
```
{{ define "slack_title" }}
{{ if gt (len .Alerts.Firing) 0 }}🔥 {{ len .Alerts.Firing }} alert(s) firing {{ end }}
{{ if gt (len .Alerts.Resolved) 0 }} ✅ {{ len .Alerts.Resolved }} alert(s) resolved {{ end }}
{{ end }}
{{ define "slack_message" }}
{{ if gt (len .Alerts.Firing) 0 }}
{{ range .Alerts.Firing }} {{ template "slack_alert_firing" .}} {{ end }} {{ end }}
{{ if gt (len .Alerts.Resolved) 0 }}
{{ range .Alerts.Resolved }} {{ template "slack_alert_resolved" .}} {{ end }} {{ end }}
{{ end }}  
{{ define "slack_alert_firing" }}
{{ .Labels.alertname }}
{{ .Annotations.summary }}
<{{ .PanelURL }}|Go to Dashboard>
{{ end }}
{{ define "slack_alert_resolved" }}
{{ .Labels.alertname }}
{{ .Annotations.summary }}
<{{ .PanelURL }}|Go to Dashboard>
{{ end }}
```
                                                          👇🏼 Telegram 👇🏼
<image src=telegram1.png><image src=telegram2.png><image src=telegram3.png>

```
{{ define "telegram_message" }}
{{ if gt (len .Alerts.Firing) 0 }} <b>🔥 {{ len .Alerts.Firing }} alert(s) firing:</b>
{{ range .Alerts.Firing }} {{ template "telegram_alert_firing" .}} {{ end }} {{ end }}
{{ if gt (len .Alerts.Resolved) 0 }} <b>✅ {{ len .Alerts.Resolved }} alert(s) resolved:</b>
{{ range .Alerts.Resolved }} {{ template "telegram_alert_resolved" .}} {{ end }} {{ end }}
{{ end }}
{{ define "telegram_alert_firing" }}
<b>{{ .Labels.alertname }}</b>
<b>{{ index .Annotations "summary" }}</b>
{{ with .PanelURL }}<a href="{{ . }}">Go to Dashboard</a>{{ end }}
{{ end }}
{{ define "telegram_alert_resolved" }}
<b>{{ .Labels.alertname }}</b>
<b>{{ index .Annotations "summary" }}</b>
{{ with .PanelURL }}<a href="{{ . }}">Go to Dashboard</a> {{ end }}
{{ end }}
```
