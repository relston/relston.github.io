---
layout: page
title: google-tasks-tui
permalink: /google-tasks-tui/
---

<p align="center">
  <img src="{{ '/assets/google-tasks-tui-logo.png' | relative_url }}" alt="google-tasks-tui logo" width="128" height="128">
</p>

**google-tasks-tui** is a fast terminal client for [Google Tasks](https://developers.google.com/workspace/tasks), written in Rust. Each task list is a column; tasks run down the column. It ships a Desktop OAuth client so you can sign in with Google without creating your own Cloud project.

- Source: [github.com/relston/google-tasks-tui](https://github.com/relston/google-tasks-tui)
- Install: `cargo install --git https://github.com/relston/google-tasks-tui.git`

The app runs on **your** computer. After you authorize Google Tasks access, OAuth tokens and an optional board cache stay under `~/.config/google-tasks-tui/` on your machine. There is no google-tasks-tui backend that receives your task data.

### Legal

- [Privacy Policy]({{ '/google-tasks-tui/privacy/' | relative_url }})
- [Terms of Service]({{ '/google-tasks-tui/terms/' | relative_url }})

### Contact

Ryan Elston — [ryan@ryanelston.com](mailto:ryan@ryanelston.com)
