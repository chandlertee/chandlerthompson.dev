---
layout: til
title: Adding a Today I Learned (TIL) section to my website
date: 2025-01-13 08:45 -0600
tags: 
- Jekyll
- TIL
---

In `_config.yml`, I added a new collection specifically for TIL posts:

```yaml
collections:
  til:
    output: true
    permalink: /til/:title/
```

[See the Pull Request](https://github.com/chandlertee/chandlerthompson.dev/pull/15)
