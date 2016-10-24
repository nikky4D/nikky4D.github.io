---
layout: post
title: "Hello World, Site Launched"
date: 2016-10-23
---

Testing out system for jekyll, and mathjax for documenting research

Testing equations: $$a^2 + b^2 = c^2$$

Testing **markdown**

To ensure I remember the workflow to publish:

#### Workflow to Publish new blog posts
Navigate to folder containing website. Navigate to posts

```bash
$ cd _posts
$ vi YYYY-MM-DD-file-name.markdown
```

Write the blogpost, saving in markdown. Use gedit/atom for now. Don't forget the Front matter like so:

```bash
---
layout: post
title:  " title"
excerpt: "Snippet of post/Post summary"
date:   YYYY-MM-DD Time
---

**markdown** post

```

Return to console, and build to preview site: 

```bash
$ cd ..
$ bundle exec jekyll serve
```

Push to github

```bash
$ cd ..
$ git add .
$ git commit -m "new blog post"
$ git push
```

Github automatically refreshes and post is live. 

Reference: These notes were modified from karpathy.github.io/2014-07-01-switching-to-jekyll.markdown
