---
layout: til
title: Creating a TIL from the command line
date: 2025-01-16 18:16 -0600
tags:
- TIL
- Bash
- Jekyll
---

Just a bash script to Jekyll Compose a TIL and open it in VSCodium. 

```sh
#!/usr/bin/env bash

SITE_DIR="$HOME/<Site Directory...>" # Replace with the path to your site
# Take the first command line argument as the title
TITLE="$1"
# Change directory to the site directory
cd "$SITE_DIR" || exit
# Compose a new TIL
NEW_FILE_PATH=$(bundle exec jekyll compose "$TITLE" --collection='til' | grep -o '_til/.*')
# Open the newly created file
code "$SITE_DIR/$NEW_FILE_PATH"
# Start server
bundle exec jekyll s --livereload
```

Of course, I added it to a local bin directory in my PATH, so I can run the `til '<Title...>'` command from any location.
