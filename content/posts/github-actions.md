---
title: "Augment your code review workflow with GitHub Actions"
description: "Learn how GitHub Actions can be used to augment and improve your code review workflow."
publishdate: 2019-03-18
lastmod: 2019-03-18
url: github-actions
draft: false
postTitle: "Augmenting your code review workflow with GitHub Actions"
---

When [GitHub Actions](https://github.com/actions) were announced last October, I immediately began thinking about what they could be used for. Automated test and deployment pipelines seemed like obvious use cases, but what else?

As the founder of [Pull Panda](http://pullpanda.com) (formerly Pull Reminders), I talk to teams every day about their GitHub code review workflows and ways they can improve their processes. It's not uncommon for me to encounter teams with highly unique workflows. 

For example, a few weeks ago I spoke with a team that was using a hierarchy of five labels to keep track of reviews and pull request statuses. In another case, I encountered a team that was still using [assigness](https://github.blog/2016-05-27-multiple-assignees-on-issues-and-pull-requests/) instead of [review requests](https://github.blog/2016-12-07-introducing-review-requests/) because their process hadn't been updated since review requests were released in 2016. I'll talk more about this team later.

On a platform as large as GitHub, it is common for teams to adopt custom processes to meet the needs of their organizations. But when workflows deviate from the norm, teams can face challenges managing their workflows within GitHub's UI or 3rd-party tools like Pull Panda.

As anyone who builds software knows, it's impossible for tools like GitHub and Pull Panda to be designed to handle every use case. Thankfully, GitHub Actions provide a new way to bridge these gaps. In this post I'll share two recent examples of how GitHub Actions have helped augment and improve our customers’ code review processes.


# Augmenting your workflow

I recently met with a team that had a fairly typical code review workflow. Pull requests were assigned reviewers and considered approved once they had two approvals.

One of the things this organization was having difficulty with – both on GitHub and in Pull Panda – was tracking pull requests that were fully approved but not merged. Their management team wanted better visibility into these pull requests in order to understand why code might not be deployed after going through all the effort of producing it.

After discussing their problem, it was clear that neither GitHub nor Pull Panda could solve it without making substantial changes. Instead, we looked into GitHub Actions. 

With GitHub Actions, you can subscribe to specific triggers and manipulate pull requests through the [GitHub API](https://developer.github.com/v3/). So we built a GitHub Action that would execute whenever a pull request was approved and automatically add an "Approved" label if the pull request had two or more approvals.

Here's a demo of what it looks like (be sure to also [check out the code](https://github.com/pullreminders/label-when-approved-action)):

![](https://github.com/pullreminders/label-when-approved-action/raw/master/docs/images/example.png)


Using this GitHub Action, all of their approved pull requests are clearly labeled and their team can easily identify them on GitHub as well in Pull Panda.


# Migrating your workflow

I mentioned earlier that I had encountered a team using [assigness](https://github.blog/2016-05-27-multiple-assignees-on-issues-and-pull-requests/) instead of [review requests](https://github.blog/2016-12-07-introducing-review-requests/). This was because their code review process hadn't been updated since review requests were released at the end of 2016.

This organization *wanted* to switch to using review requests to take advantage of better tracking features on GitHub and in Pull Panda, but hadn't because they believed that not everyone would be willing or able to change their workflows.

This isn't an uncommon problem in larger organizations. Old habits die hard, and workflow changes can turn into chaos if things become inconsistent.

GitHub Actions provided a powerful way for us to normalize their process and help them make the transition. We built a GitHub Action that automatically mirrors review requests and assignees. If you add an assignee, the GitHub Action also adds them a reviewer. And if you remove an assignee, the GitHub Action removes them from the reviewers.

Here's a demo of what it looks like (be sure to also [check out the code](https://github.com/pullreminders/assignee-to-reviewer-action)):

![](https://github.com/pullreminders/assignee-to-reviewer-action/raw/master/docs/images/example.png)


Using this GitHub Action, their organization has the confidence to switch to using review requests without concern over what might happen if someone accidentally uses assignees out of habit.


# Wrap-up

I hope you’ve seen a couple of examples of how GitHub Actions can augment existing workflows and help smoothen the transition to better ones. 
