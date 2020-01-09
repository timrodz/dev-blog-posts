# Hacktoberfest: From Decision To Completion

¡Hola/Hello/Kia Ora everyone! 👋

📖 **Table of Contents**
1. [Making A Decision & Sticking To It 🚀](#part-1)
2. [Tackling The Challenge 👨🏽‍💻](#part-2)
3. [Exploring The Web! 🌐](#part-3)
  - [DEV](#dev)
  - [DeckDeckGo](#deckdeckgo)
  - [Making A VS Code Extension](#lightswitch)
4. [Lessons Learned, A Retrospective ❤️](#part-4)

---

I'm always looking for ways to learn and improve who I am, personally and career-wise. This year I completed my first ever Hacktoberfest — It felt great! Now that I've completed it and have stayed active with contributions, I wonder: 
- What **inspired** me? 
- How can I stay **motivated** to work on more open source projects?
- How can I **encourage** others to do the same?

![Hacktoberfest pull request status](https://thepracticaldev.s3.amazonaws.com/i/14bbn7cgrbgxtzu3n2zy.png)

---

# Making A Decision & Sticking To It 🚀 <a name="part-1"></a>

This year I made the switch from game programming to Full-stack. Before the switch, I had only been coding in languages such as `C++`, `C#`, `Lua`, and using game engines such as `Unreal Engine 4` and `Unity3D`. I've been discovering and working with technologies like `JavaScript`, `Python`, and `SQL` to name a few. The breadth of tools, frameworks, libraries, APIs out there are tremendous - I can get why it might be so hard to get into this!

### Impostor Syndrome Kicks In

> Alright, I know how to code. Or do I? Surely I can work on a small issue and solve it, right? How about data structures? I've forgotten to implement a `B-Tree` yet again...

Impostor Syndrome accompanies those who work or have worked in the Games Industry, and it has decided to stay. To prove myself that I am a capable programmer (and more importantly, that I'm more than willing to overcome obstacles), I started creating side-projects to work on.

But if you're like me, you tend to come up with lots of side-projects, only to never work on them again. And that's fine - Some of these projects have a specific purpose, and they may have taught you the thing you wanted to know. Time to move on!

Since I'm also now working on web technologies, I wanted to expand portfolio with projects that were more relevant to my job - All I had were games and a couple of websites.

### How Open Source Helped

I was looking for a way to publish an old blog post I wrote on my website - First I tried Medium, but I generally dislike Medium. It feels like it was [not meant for developers](https://dev.to/devteam/medium-was-never-meant-to-be-a-part-of-the-developer-ecosystem-25a0). That lead me to discover DEV, and with it, a post talking about Hacktoberfest — I was sold immediately after!

When I discovered Open Source, I noticed the following:

- An infinite amount of **projects** to work on. If I can't do one, I might simply jump onto another - Great for someone like myself.
- A **community** of passionate, friendly developers collaborating and communicating together.
- Barriers ranging from short to very tall - There are issues for those with **any level of experience**. *Woohoo!*
- "Remote Work" vibes, where the maintainers of a project act as project leads. They ensure collaborators stay in tune with the project's vision and are **happy to help** out.
I was convinced. Time to give this a try! Working on multiple ones would keep my mind agile, constantly looking at new horizons.

---

# Tackling The Challenge 👨🏽‍💻 <a name="part-2"></a>

With any kind of programming task, I focus on creating an MVP (Minimum Viable Product) first —You don't learn variables and start writing classes right away— Instead, I ask myself questions i.e.:

- What are the requirements needed to complete this task?
- Do I need to create a complex input handler this early?
- Have I made a plan on how to tackle this? Flow Charts, UML Diagrams, Notes, etc.

These were the steps I followed to complete my first Hacktoberfest:

### 1. Learning How Open Source Actually Works

Projects like [First Contributions](https://github.com/firstcontributions/first-contributions) and Hacktoberfest's [Getting Started](https://hacktoberfest.digitalocean.com/details) guide are great for newcomers like me. They teach you the basics of open source, where to find projects, and best practices.

> Note on commit signature verification:
> Some projects will require you to verify your commits. This means you will have to create and register a GPG signature (I had to do this). Learn more: [GitHub Signature Verification](https://help.github.com/en/articles/about-commit-signature-verification)

### 2. Working with `Markdown`

Spanish is my first language, so I decided to put my translation skills to test. For this PR, I found this project and added a Spanish version:

[useful-dev-tools pull](https://github.com/lucasnaja/useful-dev-tools/pull/6)

### 3. Working With `HTML`, `CSS` & `JavaScript`

`HTML` and `CSS` are great programming languages for beginners. They provide us with beautiful sites and power the web.

[emojiscreen pull](https://github.com/brittanyrw/emojiscreen/pull/399)

`JavaScript` empowers our web, granting it the ability to do amazing things! I went for basic concepts: Working with an `object` and editing text inside it.

[emojiscreen pull](https://github.com/brittanyrw/emojiscreen/pull/400)

### Learning By Example; Developing A Habit

After finishing these tasks, I felt confident enough to tackle more difficult ones. I decided to work on codebases with unfamiliar technologies. It was time to [explore the web!](#part-3)

---

# Exploring The Web! 🌐 <a name="part-3"></a>

After finishing these basic tasks, I felt confident enough to tackle more difficult ones.

### 🌈 DEV <a name="dev"></a>

To begin, I decided to work on DEV, as I'm loving this site! It was my first time trying `Ruby`, so you can imagine the confusion I had with the syntax. DEV's codebase is huge, so I wanted to make changes that I knew weren't going to destroy the site. I approached this with the following mindset:

- Learn basic Ruby: [TutorialsPoint](https://www.tutorialspoint.com/ruby/ruby_syntax.htm)
- Find out how the Ruby ecosystem works. This article from [stuartellis](https://www.stuartellis.name/articles/erb/) helped me understand the basics of *Embedded Ruby Templating* (ERB)
- Hack code around and see what the output gives

[Dev.to pull](https://github.com/thepracticaldev/dev.to/pull/4137)

> Plus: Contributing to DEV gives you a cool badge!
> ![DEV Contributor Badge](https://thepracticaldev.s3.amazonaws.com/i/dwyvrlntc1ddtc7q4slp.png)

**Contribute to DEV**: 

[POST](https://dev.to/devteam/how-to-contribute-to-dev-this-hacktoberfest-5b91)

### 📊 DeckDeckGo <a name="deckdeckgo"></a>

[DeckDeckGo](https://deckdeckgo.com/) is an open-source presentation editor - And a very powerful one! It was also my first time using `StencilJS`. This was my approach:

- Learn the core concepts for Stencil JS: [Stencil Documentation](https://stenciljs.com/docs/introduction)
- Ask proactive questions to the project maintainer (lead):
  - What do they expect from a hypothetical PR? i.e. Acceptance Criteria
  - Ask questions on how to approach the PR
- Ask what the project structure is. How do files talk to each other? I find this helped me understand the code more than anything for this case!

[DeckDeckGo pull](https://github.com/deckgo/deckdeckgo/pull/406).

**Learn more about DeckDeckGo**:

[POST](https://dev.to/daviddalbusco/we-are-developing-an-open-source-editor-for-presentations-1bng)

### 🛠 Making A VS Code Extension <a name="lightswitch"></a>

I started [LightSwitch](https://github.com/timrodz/vscode-light_switch) a couple of weeks ago. I decided to write a DEV post about it:

[POST](https://dev.to/timrodz/hacktoberfest-let-s-build-a-vs-code-extension-1pn8)

Turns out, it was a success! I started by creating my own issues (After having implemented and pushed the MVP out), adding labels such as `hacktoberfest`, `help wanted`, `good first issue` — Last thing I knew, awesome folks were contributing to the project! ❤️

**Learn more about Light Switch**:

[Light Switch](https://github.com/timrodz/vscode-light_switch no-readme)

---

# Lessons Learned, A Retrospective ❤️ <a name="part-4"></a>

Working with Open Source software has taught me how to become a better developer, and how to approach problems through a new lens. I have actioned my learning into the following areas:

- Communication
  - Writing commit messages and summaries that are more **descriptive and contextual**.
  - Focusing on words that can express your thoughts **clearly**.
  - Asking better, smaller questions and being open to **clarify** them.
- Learning new technologies:
  - Web technologies, as complex as they may seem, **don't have to be**. Try different approaches like toying with code, watching tutorials, taking a course, etc.
- There are many ways to solve a problem - have an **open mind** when working with Open Source.

### If you're still in doubt...

...We all are at some point, no matter how experienced some may seem! Getting into Open Source can seem daunting, especially if you're just getting started with tech. The first steps are the hardest to give - **Start small, grow big**.

*Photo by [Jukan Tateisi](https://unsplash.com/@tateisimikito?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)*
