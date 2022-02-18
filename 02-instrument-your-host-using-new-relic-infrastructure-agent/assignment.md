---
slug: instrument-your-host-using-new-relic-infrastructure-agent
id: vvlepjwl6wlw
type: challenge
title: Instrument your hosts using New Relic infrastructure agent
teaser: Install New Relic infrastructure agent on your hosts
notes:
- type: text
  contents: Your application is now running on distributed infrastructure and your
    goal is to monitor your infrastructure so you could identify any degradation in
    your system and mitigate the situation before this degradation disrupts your services.
    Instrument your hosts with New Relic infrastructure agent to gain insights into
    your infrastructure.
tabs:
- title: host 1
  type: terminal
  hostname: host-1
- title: host 2
  type: terminal
  hostname: host-2
difficulty: basic
timelimit: 1800
---


With your app now running on distributed infrastructure, your goal is to monitor your infrastructure to identify and mitigate any issues, as needed. To achieve your goal, instrument your hosts with New Relic infrastructure agent to gain insights into your infrastructure.

## Install New Relic infrastructure agent

With New Relic infrastructure, you get complete observability of your system. You can monitor the health and performance of all your hosts and identify any degradation in your system. This allow you to take in-time action and mitigate issues with your infrastructure before they affect your users.

To observe your infrastructure in New Relic, you first need to install New Relic infrastructure agent on your hosts. The easiet way is to use guided install.

Open a new tab in your browser and go to [New Relic One](https://one.newrelic.com). In the top-right, click on **Add more data**.
![Add more data](../assets/add-more-data.png)

Scroll down to **Host Operating Systems** and choose **Ubuntu**.
![infrastructure agent for ubuntu operating system](../assets/infra-ubuntu.png)

On the next page, click **Begin Installation**.
![begin installing infrastructure agent for ubuntu](../assets/begin-install.png)

Here, you see the installation instruction.

![install infrastructure agent for ubuntu](../assets/copy-command.png)

Copy it to the terminal window of **host 1** to begin installaing the infrastructure agent.

The guided install discovers and recommends integrations appropriate for your system. However, we're only sticking to _Logs integration_ and _Golden Signal Alerts_ instrumentation.
![Logs and Golden signal instrumentation for ubuntu](../assets/installation.png)

The installation will take a few minutes to complete. Meanwhile, move to **host 2** and install the infrastructure agent.

- Note: New Relic infrastructure agent can be installed on several hosts simultaneously. Instead of going through the whole process again, you execute the same command on **host 2** to install the infrastructure agent.


Once the installation finishes, you see your hosts in New Relic.

## View your infrastructure

Once you install the New Relic infrastructure agent on your hosts, you see them in New Relic.

In [New Relic One](https://one.newrelic.com), go to **Hosts** in left hand menu.
![View your hosts](../assets/view-infra.png)
Here, you see a list of all your hosts. This view also shows you important statistics like **CPU usage**, **Memory usage**, **Storage usage**, about your hosts so you have a quick glance of your infrastructure.

- Note: The above screenshot shows the new **Host** view. If you're using the old view, toggle the **Show new view** button in top right corner to switch to new **Host** view before proceeding.
![View your hosts in new host view](../assets/new-host-view.png)

With New Relic infrastructure agent now installed on your hosts, you observe and monitor the system for any degradation when occurs.