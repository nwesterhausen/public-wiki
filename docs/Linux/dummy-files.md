---
title: Creating multiple dummy files
summary: Creating a set of dummy files for testing
authors:
    - Nick Westerhausen @nwesterhausen
date: 2019-01-18
---

Sometimes you may want to fill some directories with files to test acting on actual directories with files.

Using bash you can easily do this (replace n with the number of files you want):

If you want to create files in '.': `touch file{001..n}.txt` 

If you want to create files in all subdirectories: `touch */file{001..n}.txt`
