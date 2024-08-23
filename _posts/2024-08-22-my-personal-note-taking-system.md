---
layout: post
title:  My personal note-taking system
date:   2024-08-22 10:14:32 -0600
categories: markdown writing notes productivity engineering
---

If you're like me, you have a terrible working memory. Without writing things down, functioning as a person or productive engineer is impossible. I've tried various note-taking tools (OneNote, Evernote, Google Keep, etc.). But for a high-level engineer, plain markdown is hard to beat.

See ["Why I Use Markdown, and Why You Should Too"](./2024-07-31-why-use-markdown.md) for my general pitch for writing in plain text files like Markdown.


The article describes a writing method that can be tightly integrated with engineering work, builds a centralized, version controlled, personal knowledge base, and enables to access your notes in a project-specific context. While not for everyone, if you also need to switch between codebases, projects, and writing tasks, these ideas could interest you.

# My writing app of choice?
I use VS Code for a lot of reasons, a big one being... it's familiar. 

An engineer spends a lot of time in their IDE during working hours. You get to know all of its various shortcuts and text editing features, and it becomes second nature. 

Guess what? Turns out that your IDEs are fantastic general purpose writing applications. They'd let you do so many things that you could never get in most writing software. 
- Multiline editing? I used it all the time! 
- Regex search and replace? Essential! 
- Case switching and formatting? Key bound!
- Markdown header navigation? It's central to how everything is organized. 
- Plus there's tons of plug-ins that extend abilities further.

But more important then familiarity and features... is that my writing can be integrated with my projects. What does "integrated writing with my projects" look like?

# A personal, private, and project specific notes folder
You're working on a ticket, doing some initial discovery. You're walking through code paths between half a dozen files, trying to make sense of the logic so you can either implement a feature or decide to do some refactoring beforehand.

Then, of course, you get paged. There's a fire in another service, and you need to put all of this aside.

What is incredibly helpful for me is that whenever I have a project repository open in my IDE, I have a place to dump markdown files related to what I'm working on. This helps keep me organized, remember my tasks, and provides a place to store references, links, snippets, ideas, and thoughts.

The easiest way to work with project-specific notes is to have them saved inside the project directory so that they're easily opened within the IDE. However, these are personal notes, and you don't want them committed to the project repository. You also don't want any reference to your personal notes in the `.gitignore` file (if we're being professional about it). So how do we prevent these notes from being checked in?

## Using the ~/.gitignore_global
Create and configure git to have a `.gitignore_global` file

```bash 
touch ~/.gitignore_global 
git config --global core.excludesfile ~/.gitignore_global
```

Now think of a folder name you want to as your secret notes directory. I chose `ryan.notes`. It's easy to remember, personal to me, and unlikely to collide with any files or folders in a given project repo.

```bash
echo ryan.notes >> ~/.gitignore_global
```

So now, if I'm working in any project repo, I can create a `ryan.notes` folder anywhere, and anything I put in there will never get checked in. 

### What goes into these repo-specific note folders?
-   Markdown file for specific Jira tickets or projects
    -   Story descriptions
    -   Task lists
    -   Jira links
    -   Merge Request links
    -   Confluence links
    -   Helpful stack overflow/GPT generated solution
-   Scripts and snippets that are personally useful but not worth
    checking into the repo
-   Support references

I like to prefix all notes with a date `2022-12-14-JIRA-####-my-project-name.md` which is helpful to keep chronological context.

Essentially, in each project repo that I work on professionally or otherwise, I'm building an extensive knowledge base for myself that makes me more proficient. It's instantly accessible whenever I open that project and can be accessed however I want from the IDE's command palette. This has supercharged my ability to onboard myself into new projects, work on many different tracks of work long and short term, while staying organized and having access to all the information needed right where I'm doing my work. This is really helpful if you're like me and you're in and out of a dozen given repos, potentially in a few different languages, over the course of a sprint.

What's nice about confining notes to each project is that you only see the notes relevant to that project when you're searching and not files from other projects. This is useful for isolation as your knowledge base grows.

# Improvements to this system
For a long time, this was all I had, and it worked well. But there was more that I wanted from my notes system:

- I want to have my notes version controlled. The `gitignore` solution deliberately prevent them from being checked in. However, if I had a hardware issue, I could potentially lose these very valuable notes.
- Sometimes I needed to find notes from across projects, but that was not easy to do unless I mounted all projects into one IDE, which is a total waste of resources for the rare moments when I need to do this.
- I wanted to expand the use cases for this system. There are notes that aren't specific to work project repos. What about other tools, admin projects, or meta projects that span many repos?

How do I consolidate all these disparate, project-specific folders scattered throughout my file system into a flexible, searchable, centralized version-controlled repository without sacrificing my ability to isolate access to those notes when focusing on a specific project repository?

## Centralizing notes into a single repo
I created a private `notes` repo in my companies GitLab under my personal namespace as a starting point.

I moved the various `ryan.notes` folders into it. This was the folder structure I chose:
```
repos/project 1/*
repos/project 2/*
repos/project 3/*
```
So now I have everything in one place, it's version-controlled, and I can search across projects, etc.

## Accessing the relevant notes in your projects using symlinks
But how can I get my context-specific notes back when I have a project open in my IDE? Use symlinks to create a pointer in your project repo to the relevant folder in your notes repo.

```
# In the project repo 
ln -s ~/notes/repos/my-project-repo ryan.notes
```
Now, when I open my project repository in my IDE, I have a `ryan.notes` folder again, and it only includes the slice of my knowledge base that I need in that context.

Additionally, you can edit your notes in either the central repository
or the relevant project repository, it's just two views of the same files.

# In summary
The system has been a godsend for my personal productivity. What I've come to appreciate about it is its flexibility to adapt to your needs, being as relaxed or structured as you want depending on your role, the type of task, and your goals. I use this knowledge base for personal administrative needs like self-reviews and reflections, journals, planning documents, and architectural proposals, and team management. Essentially, it's a starting point for almost everything that I do as a staff engineer.

There are many many more tactics that are dependant on this markdown knowledge base foundation that I have acquired throughout the years that I plan to dive deeper into in future articles. Many of these tactics now incorporate the use of GPT models seamlessly into the writing and solutioning process with the help of my CLI tool Mark. 

Everyones working style is different, and the specifics of my process might not cleanly map on to yours. But I hope these ideas spark some inspiration for you to build a markdown knowledge base that works for you.

If you have any questions or suggestions, please feel free to reach out to me

