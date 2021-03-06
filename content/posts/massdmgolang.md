---
title: "Tool to mass DM followers on Twitter in Go"
date: 2020-07-25T10:25:04+05:30
draft: false
tags: [Go, Twitter, API, SQLite]
---

## Background

I recently came across bounty by [Balaji Srinivasan](https://twitter.com/balajis/status/1271945241881268224?s=20) to send Direct Message to all twitter followers. *Currently, i do not intend to participate in bounty and this is mere exercise.*

This is an attempt to write CLI tool in [Golang](https://golang.org) in response to it.

For detailed requirements, refer [here](https://github.com/balajis/twitter-export)

## Approach

In Brief,

* CLI should,
    * accept arguments like Twitter API Key,Auth token, DM Message
    * Download all followers (with profile details)
    * Rank them by Criteria (e.g. Location)
    * Send each follower a DM with provided message (upto daily DM Limit)
    * be easy to use and maintain

* Notes,
    * Due to Daily DM Limit, Follower details will have to be persisted alongside flag indicating if DM has been sent. SQLIte is used from simplicity perspective.
    * There should be a scheduled job that will send the DM upto daily DM Limit. At the same time, it needs to refetch any new followers and push them in the flow (reconcile).
    * Potentially, this could be extended to other social media providers other than twitter.
    * Milestones,
        * Create code structure
            * Plan is to have separation between CLI & have twitter as go package
        * Accept Arguments and Connect to Twitter
        * Study and complete follower retrieval
        * Ranking of followers
        * Persisting followers
        * Sending DM upto Daily limit
    * Rules, 
        * Use golang's in-built packages as much as possible
        * Every milestone to have associated Unit test cases

## Current Status
    
The code is ready and functionality to retrieve followers and saving in local DB is tested. Code to send DM is not yet tested as it will require setting up dummy twitter account.

## Roadmap

* In addition to CLI, Expose the utility as responsive Web Application
* Possibly extend this to social media platforms other than [Twitter](https://twitter.com)

Have a look at code on [Github](https://github.com/sachinsu/twitterexport) and let me know what you think.

Happy Coding !!

---

{{< comments >}}