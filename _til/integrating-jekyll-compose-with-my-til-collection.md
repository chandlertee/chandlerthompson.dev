---
layout: til
title: Integrating Jekyll Compose with my TIL Collection
date: 2025-01-15 08:53 -0600
tags:
- Jekyll
---

Since I have a custom layout for the TIL collection, I added default frontmatter for Jekyll Compose for the collection:

```yaml
jekyll_compose:
  default_front_matter:
    til:
      layout: "til"
```

This allows me to use the following command to create a TIL.
```sh
bundle exec jekyll compose "Some TIL title here" --collection "til"
``` 
