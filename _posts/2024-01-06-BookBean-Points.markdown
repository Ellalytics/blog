---
layout: single
title:  "BookBean Points System Design"
date:   2024-01-06 19:03:13 -0800
categories: E-commerce
author_profile: true
---


Designing an effective points system for BookBean platform requires balancing user engagement with fair usage. Below are key aspects of the points system, the potential risks, and how to mitigate them.

---

## Points System Design

1. **Marking a Donatable Book**:
   5 points awarded per book marked as donatable. Maximum of 10 books per user per day to prevent point farming.

2. **Successful Donation**:30 points awarded per successful donation. 30 points deducted per book received as a donation.

3. **User Reviews**: 5 points awarded for valid review submitted after each transaction. 5 reviews Maximum per user per day to avoid spammy feedback.

---

## Potential Risks and Solutions

### **Marking Abuse**
   - **Risk**: Users might mark excessive donatable books to farm points.
   - **Solution**: Limit 10 books per day and monitor for suspicious activity.

###  **Duplicate Donations**
   - **Risk**: Users might donate the same book multiple times.
   - **Solution**: Track donations via unique book identifiers.

###  **Fake Reviews**
   - **Risk**: Users may submit meaningless or fake reviews for points.
   - **Solution**: Require a minimum word count for reviews and implement a content moderation system to flag repetitive or suspicious reviews.

###  **Points Farming**
   - **Risk**: Users may exploit the system by creating fake transactions or using multiple accounts to accumulate points.
   - **Solution**: Monitor user activity for patterns like repeated donations or IP-based multiple accounts, and enforce penalties for suspicious behavior.

---
