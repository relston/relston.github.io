---
layout: post
title:  Agentic frameworks are a waste of time
date:   2024-09-18 10:14:32 -0600
categories: ai llm agents productivity tools
---

This is not click bate. Will not change my tone in this post. I will defend that statement and I will double down. Creating and using "Agents" for any personal LLM use cases is a waste of time. I will show you why and provide a simple alternative that is more effective, efficient, and we will all have a good laugh at the end.

# Agentic Frameworks?
I will admit, it is a cool idea. LLMs work well when given _personas_; and we're clearly seeing a trend of _specialization_ in AI models. So, like a team of individuals in a company, why not have LLMs work together as a team of `Agents`? Frameworks have popped up all over to help script togethers these types of workflows. There are plenty of anecdotal studies that show better results are possible when composing models like this. 

**Don't fall for it.**

There are NO credible professional use cases for this yet. [This excellent article by YourGPT](https://yourgpt.ai/blog/general/agentic-frameworks-limitations-business-automation) gets to the heart of this better than I can. But what about personal use cases?

# Let's create some agents
Consider this video from Mathew Berman, a popular AI influencer, who is trying to set up a "Team of AI agents" in [CrewAI](https://www.crewai.com/) to do the following task:

> I want to create a crew for personal use. Many ask about real-world uses for AI agents, and I'll show you today. I collect AI news links weekly and now produce a more frequent newsletter. I aim to have a crew that summarizes each article for my newsletter, saving me time.
      
Sounds great. Let's see how it goes.

<div class='center'>
    <iframe width="560" height="315" src="https://www.youtube.com/embed/8R7QOJgGyIQ?si=vMIEIQO0knmVanwL" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</div>

If you don't have time to watch the full hour video here is a summary with timestamps:

- 3:34 - Fumbling with dependency management
- 8:00 - Setting up personas for the writer and summarizer agents
- 12:00 - Defining the two tasks that make up the steps of the process
- 14:00 - First try at running the agents - oops the references tools for the agents are not defined
- 14:20 - "This isn't documented at all"
- 15:40 - Mathew not an expert with python import syntax
- 16:60 - It started, but still not configured right - lets look at some examples
- 18:00 - Examples have class structure - great, but not intuitive for non-programmers
- 21:00 - Wild copy pasting of code
- 25:30 - Running it - Oops, `dedent` not defined
- 27:47 - "I'm not quite sure this is going to work... I'm exposing my lack of experience with python here."
- 29:30 - Run it again - Agents not recognizing the tools
- 30:45 - Mattew pulls in **the founder of CrewAI** to help debug his script
- 34:20 - Founder: "The WebsiteSearch tool only searches the page... we don't have a tool for scraping a site yet" 
- 36:58 - I guess we are creating a custom tool for this
- 40:00 - He is seriously starting from scratch with Beautiful Soup to parse html
- 43:00 - Run again - Import errors, cool
- 45:30 - Site is blocking the request, lol - try setting a browser header? Still not working
- 48:32 - "This is getting more complex then I was hoping"
- 49:30 - New url works, hit the model token limit - scrapped too much content
        - He is hard coding tag id's to isolate the article content
- 53:40 - It's working, wow so easy!

First of all, let me say this: I love Mathew Berman! 

He is actually my favorite AI content creators, and one of the best sources for news and the latest AI tools on YouTube. If you haven't seen his channel you should check it out. What makes Mathew so relatable is that he is not an engineer, he is a power user. Seeking to leverage the latest AI tools to make his life easier. 

_That's the point, right?_

But wow, what a nightmare. You can tell that hour long video was cut way down, probably a solid work-day of time. And just to summarize a link. It's hilarious how simple the use case is and how quickly the task could be done with almost any other tool or process.

> But if it's automated, wont it save time over the long run eventually?

Sure. Reminds me of this XKCD comic...

<div class='center'>
    <img alt='Is it work your time?' src='https://imgs.xkcd.com/comics/is_it_worth_the_time.png'>
</div>

But those time savings are compared to what? Manually reading each article and writing a summary? Totally. But what if I told you there was a manual tool available that makes tasks like this so effortless, so natural, so intuitive, that using it each time would be faster then running a completed agentic script every time?

# Let's try [Mark](https://github.com/relston/mark) instead
Contrast the bloated agent framework with this drop dead, stupid simple command line tool. It just has one, very elegant design idea: 

> Use simple markdown syntax to naturally reference external data in your prompt

So how does that work in practice? How does it perform with a similar task?

For example, I was doing some product research for a side project. [alternativeto.net](https://alternativeto.net) is a nice way to tour though lots of similar products to find comparisons. I'm interested in Fromspree.io, a form submission service. But I want to know what else is out there. 

Here is my prompt 
> ```
> Collect the links of all the suggested services in this [page](https://alternativeto.net/software/formspree-io/?license=free) and create a bullet list with their names and links and a summary of any comments about them.
> ```

and the response from Mark:
```markdown
# GPT Response (model: gpt-4o, system: default)
## Suggested Service Links and Summaries

- **[FormSubmit](https://alternativeto.net/software/formsubmit/about/)**
  - Summary: Directly sends form submissions to your inbox without backend code or SMTP setup. Has a free API. 
  - Comment: Works as explained, but cannot send the form to multiple email addresses.

- **[Getform](https://alternativeto.net/software/getform/about/)**
  - Summary: Collects submissions, sends emails, and connects HTML forms with popular apps. Suitable for JAMStack and API-driven static websites.
  - Comment: No real free option as the free plan has a total submission limit, making it more of a free trial.

- **[Basin](https://alternativeto.net/software/basin/about/)**
  - Summary: Saves development time by providing backend support for web forms without needing backend coding.
  - Comment: Unlimited responses for free, and possible to receive form information in more than one email.

- **[Wufoo](https://alternativeto.net/software/wufoo/about/)**
  - Summary: Online form builder with cloud storage database.

- **[SmartForms](https://alternativeto.net/software/smartforms/about/)**
  - Summary: Feature-rich form backend with notifications via email, Slack, and Telegram.

- **[Formcarry](https://alternativeto.net/software/formcarry/about/)**
  - Summary: Provides a backend to collect form submissions without any backend coding.
  - Comments: User-friendly, simple interface. Powerful dashboard and excellent support. Missing validation support.

- **[Form2chat](https://alternativeto.net/software/form2chat/about/)**
  - Summary: Form backend for receiving submissions directly to chat platforms like Telegram, Viber, Facebook Messenger, etc.

- **[Fabform](https://alternativeto.net/software/fabform/about/)**
  - Summary: Anti-spam forms backend for static websites.

- **[Simple Form](https://alternativeto.net/software/simple-form/about/)**
  - Summary: Allows setup of forms with any kind of data.

- **[Airform](https://alternativeto.net/software/airform/about/)**
  - Summary: Provides control over forms without requiring servers.

- **[Submit JSON](https://alternativeto.net/software/submit-json/about/)**
  - Summary: Simplifies coding web forms by handling form submission notifications and more.

- **[Slapform](https://alternativeto.net/software/slapform/about/)**
  - Summary: Provides backend for forms and emails submissions to you and stores them securely.
```
Great! I have a list of services to check out. But those urls are't the offical sites. Let's change that.

```markdown
For each of those alternates listed, get the official link to the service in each of these pages

# GPT Response (model: gpt-4o, system: default)
## Official Links to Suggested Services

- **FormSubmit**
  - [Official Website](https://formsubmit.co/)

- **Getform**
  - [Official Website](http://getform.io)

- **Basin**
  - [Official Website](https://usebasin.com)

- **Wufoo**
  - [Official Website](https://www.wufoo.com)

- **SmartForms**
  - [Official Website](https://smartforms.dev)

- **Formcarry**
  - [Official Website](https://formcarry.com)

- **Form2chat**
  - [Official Website](https://form2chat.io)

- **Fabform**
  - [Official Website](https://fabform.io/)

- **Simple Form**
  - [Official Website](https://getsimpleform.com/)

- **Airform**
  - [Official Website](https://airform.io)

- **Submit JSON**
  - [Official Website](https://www.submitjson.com)

- **Slapform**
  - [Official Website](https://slapform.com)

```
You see what just happened there? In one thread, _just two short prompts_, we got Mark to get a dataset from one link and then iterate on that set. We parsed though a set of links to extract more specific information to get a report of content. I only wrote two sentences and I'm way past Mathew and his full day of debugging his agentic framework. 

Lets look at another example using Mark. 

# Local files   
Say your keeping a journal in a markdown files. Here are mine for September 2024:

```bash
find ./Journal/2024-09*
./Journal/2024-09-02-12-22-19.md
./Journal/2024-09-03-08-08-19.md
./Journal/2024-09-07-12-35-06.md
./Journal/2024-09-09-07-30-38.md
./Journal/2024-09-10-08-14-28.md
./Journal/2024-09-11-22-19-08.md
./Journal/2024-09-12-08-54-30.md
./Journal/2024-09-14-11-14-45.md
./Journal/2024-09-15-16-10-14.md
./Journal/2024-09-16-07-59-30.md
```
Cool. What happened this month so far? Let's find out!

```markdown
Summarize the major events from each of these journal entries, limit to the top 5 most significant events out of all the entries.
- [Entry](./Journal/2024-09-02-12-22-19.md)
- [Entry](./Journal/2024-09-03-08-08-19.md)
- [Entry](./Journal/2024-09-07-12-35-06.md)
- [Entry](./Journal/2024-09-09-07-30-38.md)
- [Entry](./Journal/2024-09-10-08-14-28.md)
- [Entry](./Journal/2024-09-11-22-19-08.md)
- [Entry](./Journal/2024-09-12-08-54-30.md)
- [Entry](./Journal/2024-09-14-11-14-45.md)
- [Entry](./Journal/2024-09-15-16-10-14.md)
- [Entry](./Journal/2024-09-16-07-59-30.md)


# GPT Response (model: gpt-4o, system: default)
## Significant Events

1. **Finished Paver Project**
   - On Monday, 2024-09-02, the paver project was finally completed. This was a significant task that had been ongoing and its completion marked a major milestone.

2. **Acquired Domain and Setup for Dishseeker.ai**
   - Progress on the Dishseeker.ai project included buying and setting up the domain, integrating Google Analytics, and making the contact form functional, as noted on Saturday, 2024-09-14.
....
```
So with a simple shell command (whose output can be quickly formatted into a markdown list in a few seconds) I was able to get a summary of the most significant events from my journal entries for any given time period. Notice how leveraging markdown syntax is a natural way to reference data external to the prompt.

# The simple tools are better
Agentic framworks are overkill for _personal use cases_ when they are:
- a) one off tasks
- b) frequent but simple tasks
- c) frequent, complex but the details change each time

Yeah, that's **all of them**. Only some business processes are ever `frequent`, `complex` and `consistent` and Agents have failed to deliver in this arena so far. _Agents_ are a **_waste of time_**.

# And now, the kicker
Oh, and by the way... You know, you can script with [Mark](https://github.com/relston/mark) too, right?  It is not only possible, but objectively better than the CrewAI agentic framework example in the Mathew Burman video. Don't believe me?  Try it yourself. 

_It will only take a few seconds._


Just define a few system prompts vaguely similar to the ones in the video
```bash
echo "
role: Summarizer of Websites
goal: Go to a given website, scrape the content, and provide a summary of the article on the website
backstory: You work at a leading tech think tank. Your expertise lies in identifying emerging trends. You have a knack for taking complex AI topics and explaining them clearly and succinctly, with a bit of wit.
task: Take a list of websites that contain AI content, read/scrape the content and then pass it to the writer agent
" > ~/.mark/system_prompts/test_summarizer.md

echo "
role: Tech Content Summarizer and Writer
goal: Craft compelling short-form content on AI advancements
backstory: You are a renowned Content Creator, known for your insightful and engaging articles. You transform complex concepts into compelling narratives
task: Using the text provided by the scraper agent, develop a short and compelling/interesting short-form summary of the text provided to you about AI
" > ~/.mark/system_prompts/test_writer.md
```
Adding a system prompts is as simple as creating a markdown file in the `~/.mark/system_prompts/` directory.

Cool.. you're set up.

So now you can just script them together like this:
```bash
echo "[the web page](https://www.axios.com/2024/02/06/runway-ai-venture-capital-fund)" | mark -s test_summarizer - | mark -s test_writer -
```
The output

> AI startup Runway, famed for its innovative work in generative AI for images and videos, is stepping into venture capitalism with a new $10 million fund aimed at early-stage AI startups. This strategic move, disclosed in an SEC filing, is designed to broaden their influence within the AI industry. It's a savvy trend, reflecting how emerging tech sectors, much like cryptocurrency, often see startups incubating other startups. Notably, Runway's fresh fund will not tap into its existing resources, a relief for current investors. Having already secured over $250 million from industry giants like Alphabet and Nvidia, Runway's silence on the matter leaves room for speculation and anticipation.

That is a **one. line. command.** Simple linux piping to chain the two Mark request commands together. It does the EXACT same thing as the CrewAI example. Not only was it set up in two commands but it runs in a fraction of the time. 

# Conclusion
I hope you can appreciate how hilarious this Agentic Frameworks demo was so me. As an engineer, one of my pet peeves is _over-engineering_: Building out complex systems, but only solving simple problems. 

Agents are toys. They are fun ideas to play with. You could get some interesting results out of them. They are not for anyone who is serious about getting things done.

[Mark](https://github.com/relston/mark) is the tool for that. It is the most effective way to interact with LLMs for personal use cases. It is simple, elegant, and powerful.
Get the LLM output you want, be in total control of the input, and get it done in seconds. 