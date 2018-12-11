---
title: IMAP Content Sensor
summary: Getting it configured correctly
authors:
    - Nick Westerhausen @nwesterhausen
date: 2018-12-11
---

The IMAP content sensor seems to be a little finnicky when getting set up. The
errors that show up are less than useful. Listed here are some things I ran into
and how to fix them.

## Setting up with GMAIL
If you have 2-Factor Auth set up, you need to use an 
[app password](https://myaccount.google.com/apppasswords).

## Setting up with AOL Mail
Initially I had issues getting the sensor to work, even with the correcty
IMAP server set and my username and password. There is an additional setting
under your account settings in "Security" where you need to all less secure
logins.

## Sensor unable to update
I had an issue where the emails it was looking for did not have a subject. This
caused the sensor to fail updating.