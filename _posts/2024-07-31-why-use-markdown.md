---
layout: post
title:  Why I Use Markdown, and Why You Should Too
date:   2024-07-31 10:14:32 -0600
categories: markdown writing
---

## Writing is important
It's a fact of any knowledge-working profession that when you reach a high level, you're going to be doing a lot of writing. It's one of the hallmarks of highly successful people. They keep journals, both professional and personal, creating their own knowledge base that they can draw from. These are habits that just make you more effective at life, full stop.

- At work, I have my own private repository where I take notes on all of my projects in Markdown format. Anything I work on, no matter how large or small, gets an entry. These notes keep records of Jira links, documentation and references, Slack messages, and code references, project plans, meeting notes, team management, personal goals, self reflections, performance reviews, and more.
- In my personal life, I have a separate repository that serves as my personal journal. Here, I recount the events of the day, make plans about the future, share thoughts about personal projects, work through financial planning, and create travel itineraries.

The value of building a personal knowledge base is self-evident and compounds as it grows. But what is the best way to build this knowledge base so that it continues to serve you, provides the maximum amount of utility for your needs, and remains useful for decades to come? For me, I found my answer.

## Why I choose Markdown
Over the years, I've tried all the tools you can imagine to help with these writing tasks: Evernote, Google Keep, Google Docs, OneNote, Notion, etc. But I always come back to the simplicity of writing in markdown files and developed a passionate appreciation for the Markdown format.

For a while, it was hard to explain to others what I saw in Markdown that made it so appealing over more sophisticated tools. There are always hundreds of little reasons that come to mind, but it took a while to land on the overarching themes that make the format work so well for essentially every writing task I have. I think these reasons will appeal to non-engineers as well. 

Markdown should be the tool of choice for anyone who prioritizes **simplicity**, **flexibility**, and **control** over their documents and writing process. 

Let's deep dive into these points and see why the format of Markdown is so powerful compared to other formats.

### Simplicity
In case you have never seen it, this is what markdown looks like:

```markdown
# My Heading or Title
You can emphasis content with **Bold** or _italic_ format text. 
And combine them for **_emphasis_**. 

The link format lets you link to [websites](https://example.com) 
or [other files relative to the current one](./path/to/other/file.md).

## My Subheader
An outline with bullet points is created like this:
- Item one
- Item two
  - Nested item

Or an ordered lists like this:
1. First
2. Second

## Another Subheader 
This is how we include an images:

![Alt text](https://example.com/image.jpg)

```
It's a very simple way of notating and structuring content. It only has a few features: headers, hierarchical lists, links, images, quotes, dividers, and tables. That's it. Markdown is simple. 

- **Easy to learn**: Some might see its learning curve as a barrier, but still simpler than learning Word or Google Docs for the first time and certainly easier than complex markup languages like HTML
- **Easy to write**: The small number of features enables the syntax to be used effortlessly while writing 
- **Easy to read**: The syntax is clean, intuitive and digestible by anyone when reading the raw text - even people unfamiliar with the syntax.

These features cover most writing needs and perfectly suited for the needs of a personal knowledge base. Even if it falls short for some tasks, I argue that it's the best starting point before converting to more complex formats.

However, being a simple "plain text" file gives it a few important qualities:
- **Compatibility**: Because Markdown files are plain text, they are highly portable and can be opened and edited in any text editor, on any operating system, making them accessible regardless of the technology you use.
- **Durability**: Markdown files are less likely to become corrupted or unreadable over time, as they are not tied to a specific software version or platform.

This makes it ideal for knowledge preservation in the long term. It's a format that will be readable in 10, 20, or 50 years from now.

### Flexibility
Whether it's the act of writing, or everything you plan to do with your written content, Markdown is the king of flexibility.

#### Limitless writing options
Sure you can write in any text editor, but there are many markdown-specific writing apps that can enhance the experience. Some of the most popular ones include:
- [ghostwriter](https://github.com/wereturtle/ghostwriter)
- [Formiko](https://github.com/ondratu/formiko)
- [ReText](https://github.com/retext-project/retext)
- [Typora](https://typora.io/)
- [StackEdit](https://stackedit.io)
- [Dillinger](https://dillinger.io/)
- [MarkdownPad](http://www.markdownpad.com/)
- [Markdown Edit](https://github.com/mike-ward/Markdown-Edit/)

Don't want to deal with the syntax? No problem. Need a focus mode? Got it. Need to edit on the phone? No problem. Need to sync between devices? Easy. Have to have built in publishing features? Done. Whatever writing workflow you are looking for there are tools available to help you.

#### Portability
As you can see, with Markdown your content is not tied to a specific app or platform, and you are free to pick up and switch to a new app at any time. This is not the case with proprietary formats or cloud-based solutions.

#### Search Efficiency
Since the content is encoded in plain text, the file size can't get much smaller. This means that it is much easier to index the content of these files and it make searching across them much faster. 

This is why creating a personal knowledge base is best done in simple markdown documents versus other systems and formats. Markdown is the easiest way to manage hundreds or thousands of different files that can contain notes, journals, plans, tasks, or any other type of personal knowledge or productivity system.

#### Searching Options
You are not limited to plain text search - depending on what tools you want to use you are now able to fuzzy search, regex search. With AI and semantic search tools becoming more common by the day you can even use natural language to query your markdown documents knowledge base. The number of searching options available are simply not present in proprietary systems that we have mentioned.

#### Convertibility
When needed, tools like Pandoc can easily convert markdown to various formats like PDF, HTML, and DOCX. This flexibility makes it suitable for multiple professional contexts. With cloud-based solutions you are subject to the grace of a cooperation to provide you with the export options you need.

#### Version Control
Markdown files integrate well with version control systems like Git, making it easy to track changes over time. This is especially useful for collaborative projects.

#### Metadata Tagging
Embedding metadata within your Markdown files can improve the efficiency of organizing and finding documents. Custom tags make it feasible to dynamically organize content beyond simple file hierarchies.

#### AI Ready
Once I got familiar with the incredible ecosystem around markdown it's easy to see why markdown is so flexible and powerful. But the main reason I'm so fired up about markdown is this: Markdown is **AI ready!**

All of the qualities that make plain text markdown files so easy to search and index also make it the perfect medium for any AI use cases you might have. Literally any other knowledge source would require some sort of conversion to be used with LLMs. But with markdown, you can use it as is.

This is of course, exactly [why I created mark](./2024-06-07-introducing-mark.md) - The command line interface tool designed to leverage markdown syntax to interact with LLMs.

## Control
This final point is not as fun but it is the most important. If you believe that the effort you put into what you write, including all of your thoughts and ideas, is valuable, then it should be under your control. 

### Loss prevention
Cloud-based solutions have their conveniences and useful features. However, they always lack the assurance that you are not giving up control of your content to a company that could change its business model, go under, suffer cyber-attacks, a technical disaster, or personal identity theft, that could impact your ability to access your data with no recourse. 

This point becomes more salient then you think about your personal photos. As you get older that collection of memories becomes more and more valuable. And I have seen the devastate look on people's faces when they realized they lost it all, from a simple mistake or even no fault of their own.

I have come to realize that my personal knowledge base that I have built over the years is a source of incredible value to me, not only professionally, but sentimentally as well. It's very much a part of who I am. I would never solely rely on a cooperation to keep that safe for me.

### Data Ownership and Privacy
By default, Markdown files are stored locally on your machine, and you have full control over where and how they are backed up. This is a significant advantage over cloud-based solutions, where you are entrusting your data to a third party. It goes without saying that they are enriching themselves with your data. The cliche goes, 
> If you're not paying for the product, you are the product.

But embedded in that saying is the _admission that your data is really valuable_. 

So why should we produce our data in ways that _give it_ to corporations _for free_ _**by default**?_ 

I'm not saying that proprietary tools or cloud-based solutions don't have their place or should never be used, but I do advocate that we use some discretion and understand the tradeoffs of the tools we choose to use.

The takeaway is this: Writing content in markdown is for people who know they are producing valuable knowledge that will be beneficial in the future, either to themselves or others.

## Conclusion
Markdown offers a unique combination of simplicity, flexibility, and control that makes it an ideal choice for anyone looking to take their writing seriously. Its plain text nature ensures compatibility and durability, making it a reliable format for long-term knowledge preservation. The broad ecosystem of tools and its AI readiness further enhance its appeal, providing limitless options for writing, searching, and utilizing your content.

Ultimately, if you value the effort you put into your writing and recognize its long-term worth, Markdown offers a level of control and ownership that proprietary and cloud-based solutions simply can't match. Writing in Markdown is about respecting the value of your knowledge and ensuring that it remains accessible and useful for years to come.
