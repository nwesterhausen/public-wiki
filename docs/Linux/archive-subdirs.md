---
title: Script to Archive Subdirectories into Individual tar.gz files
summary: How to archive subdirectories into individual tar.gz files
authors:
    - Nick Westerhausen @nwesterhausen
date: 2019-01-18
---

```
#/bin/bash
DIRECTORY=/target/dir

cd "$DIRECTORY"
for dir in */
do
  base=$(basename "$dir")
  tar -czf "${base}.tar.gz" "$dir"
done
```
