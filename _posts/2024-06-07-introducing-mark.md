---
layout: post
title:  "Introducing 'Mark', a Markdown CLI tool for GPT4o"
date:   2024-06-07 10:14:32 -0600
categories: markdown gpt4o cli
---

## Introduction
In this post, I want to introduce `Mark`, a simple CLI tool that uses Markdown and its syntax to interact naturally with the GPT4-vision/GPT4o models.

[https://github.com/relston/mark](https://github.com/relston/mark)

### Problem Statement
As a writer/manager/engineer/content creator, I need a tool that is effortlessly flexible and makes full use of the latest features of the GPT models. Something that let's me utilize GPT-4's image capabilities and also provides flexible yet predictable RAG retrieval mechanism for adding context to my GPT submissions. I can't spend time scripting together agentic frameworks through a series of isolated use cases that I may never see again. 

And I don't want my LLM interactions to be restricted by proprietary tools or stored by a centralized service. I want to keep track of my GPT threads in my own personal way. 

## What is Mark?
There are 3 things to know about `Mark`:

### In-Document Thread Builder
`Mark` is a CLI tool with an elegant design:
- It takes a path to a markdown file as its input, 
- Submit the content of that markdown file as a prompt to GPT.
- It appends the response from GPT back to the markdown file 

In essence, if you have a text file with a prompt like this:
```markdown
<!--- path/to/markdown.md -->
Tell me 5 facts about tigers! Respond in short bullet points.
```
Then run this command in your terminal:
```bash
# bash
mark path/to/markdown.md
```
This will update your markdown file like so:
```markdown
<!--- path/to/markdown.md -->
Tell me 5 facts about tigers! Respond in short bullet points.

# GPT Response (model: gpt-4o-2024-05-13, system: default)

## Five Facts About Tigers
- Tigers are the largest species of the cat family.
- They have distinctive striped coats that help with camouflage.
- Tigers are solitary animals, each having a large territory.
- They are strong swimmers and enjoy water.
- There are six subspecies of tigers, including the Bengal and Siberian tiger.

# User Response
```
You can add a follow-up message at the end of the `# User Response` and run the same command again in your terminal, essentially continuing the conversation within the markdown file. This is a very simple format to mimic the basic user experience of the official OpenAI GUI or any other web-based LLM tools right from your text editor.

### Simple RAG retrieval with image and link references
Any image and link references in the input markdown file are parsed out and handled in the following ways:
- Images references (local or remote) submitted with the user message prompt are processed according to the OpenAI API specifications.
- Links to local documents are read and submitted as context at the top of the system prompt.
- Links to web documents are scraped and also submitted as context at the top of the system prompt.

For example:
```markdown
Describe ![this image](https://www.animal.photos/mamm1/cat-tig1_files/bengal12.jpg) to me in one short sentence.

# GPT Response (model: gpt-4o-2024-05-13, system: default)
A Bengal tiger is walking on a sandy path with greenery in the background.

# User Response
List each section of content on [this page](https://en.wikipedia.org/wiki/Bengal_tiger)

# GPT Response (model: gpt-4o-2024-05-13, system: default)
## Sections of Content on the Bengal Tiger Wikipedia Page

1. **Taxonomy**
   - Genetic ancestry

2. **Characteristics**
   - Body weight and size

3. **Distribution and habitat**
   - India
   - Bangladesh
    ...
```

### Extensible scripting tool
You can also use standard input to pipe in content to Mark, and it will output the response to standard output. 
```bash
echo "Please explain this code: $(cat some_class.py)" | mark 
```
This feature is similar to other tools you can find and is not the primary focus of Mark, but it's still handy for many scripting use cases.

## Origin Story
### Why Markdown?
I love Markdown. It's an incredibly versatile way to write documents, and I have been using it every day for my professional note-taking as well as my personal journal. Anything written in Markdown is ultra-portable, flexible, and extensible in countless different use cases.
- At work, I have my own private repository where I take notes on all of my projects in Markdown format. Anything I work on, no matter how large or small, gets an entry. These notes keep records of Jira links, Confluence documentation and references, Slack messages, and code references. 
- In my personal life, I have a separate repository that serves as my personal journal. Here, I recount the events of the day, make plans about the future, share thoughts about personal projects, work through financial planning, and create travel itineraries.

Because I'm in my IDE all day, it's effortless and satisfying to use a tool I'm quite comfortable with to write content. It turns out IDEs are incredible writing tools. 

- Modern IDEs and text editors provide excellent support for Markdown, including syntax highlighting, preview panes, and support voice dictation.
- IDEs have extremely fast, indexable search across all of your text documents
- You can render your markdown into rich formatting, which can then be copied and pasted into other tools for publishing or sharing
- Markdown can be integrated with a variety of other tools and services, such as static site generators (e.g., Jekyll, Hugo), which can provide preview capabilities and publishing workflows.
- Markdown files can be easily converted to other formats (PDF, HTML, DOCX) using tools like Pandoc. This ensures that any work done in Markdown can be repurposed in multiple venues. I know that if I write everything in markdown first, it will be in its most reusable form going forward.

Markdown's compatibility with version control systems allows for efficient version tracking and collaboration so having my personal knowledge database as a Markdown repository is invaluable. This workflow has proven to be extremely powerful and flexible, and I don't think I can ever go back to a proprietary note-taking app.

## Why Markdown + GPT?
For a long time, I used a simple bash script to implement the in-document threaded conversation flow described above. You can see this [legacy project in my GitHub repo here](https://github.com/relston/gpt-cli). By doing this I learned that Markdown provides a powerful, flexible, and efficient medium to interact with LLMs. It's simplicity, combined with the richness of its features and compatibility with modern development tools, makes it uniquely suitable for optimizing the effectiveness of LLM interactions.

- **Semantic Structure**:
    - The simple formatting notation allows one to easily create prompts with structure that communicates a lot to the LLM while minimizing the input token count
    - Markdown's semantic elements like headers, blockquotes, and emphasis can help structure prompts in a way that guides the LLM through the task, emphasizing key parts and delineating sections logically. This can lead to more accurate understanding and processing by the LLM.
    - Markdown allows you to insert code blocks seamlessly within text. This is incredibly useful for creating and sharing code snippets or requests for code generation, maintenance, or documentation. The LLM can analyze the code context provided with the prose to give better responses.

- **Extensibility & Custom Syntax**:
    - Markdown can be extended with custom syntax, allowing for the inclusion of specialized elements such as task lists, diagrams (e.g., Mermaid.js for flowcharts), and more. This can provide additional context and directives to LLMs trained to parse such custom syntax.    
    - LLMs can provide responses structured as tables and lists, which are easily rendered in markdown

However, with the introduction of GPT4-vision, I felt the need to take advantage of Markdown's syntax for image references so that I could utilize GPT-4's vision capabilities within my existing workflow. I found the results to be quite impressive and quickly extended the functionality to link reference retrieval as well.

- **Image tags naturally provide visual context**:
  Not only are you working in a markdown document that can be rendered so that you can see the images but the Image references in Markdown files is a natural way to provide visual context to the LLM. 

- **Links are an easy, predictable and effective RAG medium**:
  Most RAG systems rely on embedding models and require setting up a database, which is time-consuming. They often include irrelevant content, bloating token counts and confusing the LLM.

  Markdown link tags offer explicit context and can be easily manipulated to provide the most relevant documents. In practice, these tags are _**WAY** more effective than many RAG solutions_ because they appear in the user message, referring back to the included documents. This dual reference provides clearer and more explicit instructions to the LLM, enhancing response quality.

All of this put together makes it clear to me that Markdown is the single best medium for interacting with LLMs. And `mark` allows you to use the latest LLM capabilities while maintaining a very simple user experience on par with the most polished web applications while leveraging the power and development potential of modern IDEs.

## Key Features
- **In-Document Thread Building**: Have a conversation with gpt, or simply incorporate its responses back into the document you're building.
- **GPT Vision with Image Tags**: The LLM sees your whole document, not just the text.
- **RAG using Links**: Simple, natural, intuitive, explicit and effective RAG retrieval mechanism.
- **Custom System Prompts**: Easily make use of all your existing prompts with `mark`.

## Installation
Prerequisites:
- OpenAI API key in the `OPENAI_API_KEY` environment variable
- Python 3.10 or higher
- [pipx](https://pipx.pypa.io/stable/installation/) 

```bash
pipx install git+https://github.com/relston/mark.git
```

## Getting Started
By default, `mark` will read a markdown file, extract any context references, and send them to the LLM. The responses are then appended to the markdown file.
```bash
mark path/to/markdown.md
```

### Custom system prompts
The system prompts folder is located at `~/.mark/system_prompts` and it includes a `default.md` prompt. You can add any additional system prompts you'd like to use in this folder and use them with the `--system` flag.
```bash
 ~/.mark/system_prompts/custom.md
mark path/to/markdown.md --system custom
```

### Scripting with Mark
Also supports `stdin` with `stdout` for piping GPT responses into other tools
```bash
cat path/to/markdown.md | mark 
 LLM response....
```

## Example Use Cases
### Extracting data from a screenshot into a markdown table
Take a screenshot of anything you want to extract data from, easilly paste it into a markdown file (VS Code or any modern IDE supports this feature), and run `mark` on the file. 

```markdown
Pull the flight information from this screenshot and output it as table

![alt text](image-1.png)

 GPT Response (model: gpt-4o-2024-05-13, system: default)
# Flight Information

| Direction          | Departure Time | Departure Location     | Arrival Time | Arrival Location | Duration | Airline           | Date       |
|--------------------|----------------|------------------------|--------------|------------------|----------|-------------------|------------|
| Denver → New York  | 4:15 PM        | Denver International (DEN) | 10:00 PM     | LaGuardia (LGA)  | 3h 45m   | Frontier Airlines | 07/05 (Fri)|
| New York → Denver  | 10:52 PM       | LaGuardia (LGA)        | 1:08 AM      | Denver International (DEN) | 4h 16m   | Frontier Airlines | 07/12 (Fri) - 07/13 (Sat)|
```

Turn diagrams from whiteboard sessions into Mermaid or PlantUML diagram syntax quickly and easily

### Get personalized coding help
Github CoPilot is great but it's just not GPT4. When you need a more then the stock solutions to standard development problems, `mark` can easilly pipe in all the context needed for GPT4 to give you a much more comprehensive solution.

```markdown
In my project, I have a [Config class](../mark/config.py) that is used by my [main CLI class](../mark/cli.py). Can you give me some ideas on how I can improve the interface for my Config class?

# GPT Response (model: gpt-4o-2024-05-13, system: default)
Certainly! Here are some ideas to enhance the interface for your `Config` class:

## 1. **Add Type Annotations**
Adding type annotations can help with readability and provide better support for....
```

### Scrape a web page for answers
Planning a night out? Researching a new topic? `mark` can scrape the web for you and provide you with the information you need.

```markdown
Give me a short list of all the vegetarian friendly items on [this menu](https://cochinotaco.com/englewood-cochino-taco-food-menu)

# GPT Response (model: gpt-4o-2024-05-13, system: default)
# Vegetarian-Friendly Items

## Snacks
- Cochino Elote
- Queso Dip (with Mushrooms or Beyond Meat)
- Mexican Egg Rolls (Mushroom & Corn)
- Green Chile Cheese Tots
- Cheeps & Salsa
```

# Conclusion
So thats `Mark`! A streamlined CLI tool that leverages Markdown to interact seamlessly with GPT-4. We highlighted key features like in-document thread building, GPT Vision with image references, and effective RAG retrieval using links, Mark offers a robust, flexible, and efficient solution for developers and writers. From installation to advanced usage, we've walked you through how to get started and maximize the tool's potential.

Mark transforms your Markdown workflow by incorporating GPT-4's powerful capabilities, making interactions smoother and more productive. Whether you're scripting complex tasks or simply generating content, Mark is designed to enhance your productivity and creativity effortlessly.

Give Mark a try today and see how it can revolutionize your Markdown and GPT-4 workflow! 🚀


