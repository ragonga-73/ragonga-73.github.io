---
layout: post
title: "Zero Day Number One"
date: 2026-02-13
tags: [intro, security, mindset, detection-engineering]
---

There are two types of security analysts: those who have been paged at 3:00 AM, and those who will be.

I officially fall into the former category as of last week.

---

### Why This Blog Exists

I started this site for three reasons:

**1. To document the grind.**
Security is a war of attrition. It's not just the zero-days and the red team exercises—it's the log fatigue, the false positives, the vendor sales calls that somehow take 45 minutes. I want to write down what this actually looks like, not the Hollywood version.

**2. To think out loud.**
Some of the best intel I've ever gotten came from a random blog post someone wrote at 2:00 AM after fighting a SIEM query for six hours. If I run into a weird detection gap or an obscure IOC format, I'm putting it here. Someone else will need it.

**3. To stay sharp.**
Explaining a problem is the best way to truly understand it. If I can't write a clear post-mortem on an attack path, I probably didn't understand the engagement well enough.

---

### What to Expect

This won't be a news blog. I'm not here to recap the latest CISA alert (you already read those). I want to talk about:

- **Detection engineering:** Why certain rules fail in production.
- **Threat hunting:** What I'm looking for and why.
- **The boring stuff:** Log ingestion pipelines, parsing errors, and the quiet victories.
- **Imposter syndrome:** Because we all have it, and pretending we don't is bad for the industry.

---

### Current State of Affairs

Right now, I'm 18 months into this role. I've triaged roughly 2,400 alerts, written 23 detection rules that actually made it to production, and spent approximately 14 hours waiting for EDR agents to sync.

I still feel like I don't know enough. That's the point.

If you're also staring at a terminal wondering if you missed something, you're in the right place.

---

*Next post: Why my first detection rule caught Slack notifications and not the actual malware.*
