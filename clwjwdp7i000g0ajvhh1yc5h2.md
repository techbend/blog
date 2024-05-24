---
title: "It Started with a Typo: My Journey to Becoming a Contributor in PGMQ"
seoTitle: "It Started with a Typo: My Journey to Becoming a Contributor in PGMQ"
seoDescription: "A typo led to my journey as an open-source contributor in PGMQ, learning and growing with each contribution"
datePublished: Thu May 23 2024 23:42:05 GMT+0000 (Coordinated Universal Time)
cuid: clwjwdp7i000g0ajvhh1yc5h2
slug: it-started-with-a-typo-pgmq
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1716507661902/d9681d04-ba7c-4743-9b9b-617a3c312a1e.webp
tags: postgresql, python, opensource, python3

---

This story is based on true events and shows how anyone can become an open-source contributor with a little help from maintainers.

I was casually exploring GitHub when I stumbled upon PGMQ, a project using PostgreSQL for message queuing. I found a typo in the README and thought, "Why not fix it?" So, I forked the repo, corrected the typo, and submitted my first pull request. To my surprise, it got merged! Feeling like a hero, I decided to dive deeper.

Encouraged by my first success, I explored the codebase more. I noticed PGMQueue lacked support for environment variables. Thinking it was a simple task, I added the `python-dotenv` library and submitted another pull request [(PR #222)](https://github.com/tembo-io/pgmq/pull/222). Then came the feedback. One collaborator wasn't a fan of auto-loading environment files and suggested reading environment variables directly. Another contributor liked the idea but recommended avoiding the dependency on `python-dotenv`.

After much discussion and feedback, I removed `python-dotenv` and changed the implementation to use environment variables if provided. Additionally, we decided to use `unittest` instead of `pytest` for consistency. I rewrote all the tests, learning a lot along the way.

In another instance, I updated the development dependencies in the `pyproject.toml` file, only to receive feedback that I had removed some necessary ones. After some tweaks and running `poetry lock --no-update`, everything was sorted out.

We also revised the README to avoid using `python-dotenv`, making the setup simpler and cleaner. Despite the challenges, these experiences were full of insights and learning opportunities.

Feeling more confident, I tackled more significant features. One ongoing project is adding support for metrics to the Python library [(PR #227)](https://github.com/tembo-io/pgmq/pull/227). This should help users gain better insights into their queue operations.

Looking back, it's funny how a small typo led me to contribute to a project I really enjoy. Each task, no matter how simple, taught me something valuable. If you're thinking about contributing to open source, just go for it! Every little step counts.

For more details, check out my contributions: [PR #214](https://github.com/tembo-io/pgmq/pull/214), [PR #222](https://github.com/tembo-io/pgmq/pull/222), and [PR #227](https://github.com/tembo-io/pgmq/pull/227).