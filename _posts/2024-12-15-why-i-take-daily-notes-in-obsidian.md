---
layout: post
title: Why I Take Daily Notes (And How I Do it in Obsidian)
date: 2024-12-15 23:11 -0600
categories:
  - Journaling
tags:
  - obsidian
  - journaling
  - productivity
---

In the chaotic adventure of life, it’s easy to get caught up in the whirlwind of daily tasks and forget the epic story we’re trying to tell. That’s where daily notes come in. For me, taking daily notes isn’t just a productivity hack—it’s a way to capture the narrative, track my quests, and reflect on the journey. Think of it as the adventurer’s journal you wish you’d always kept.

Here’s why I think daily notes are essential, why I’ve chosen [Obsidian](https://obsidian.md/) as my tool of choice, and how my fantasy-inspired daily note template keeps me motivated and (mostly) organized.

---

## Why Take Daily Notes? 📝
As someone who thrives on creating order out of chaos (I’m a software engineer, after all), daily notes serve a few critical purposes:

### 1. Personal Knowledge Management
Daily notes are a low-key brain dump where I can offload thoughts, ideas, and lessons. They’re my way of wrangling the mimic’s stash of random knowledge in my head.

### 2. Staying Grounded
Gratitude, inspiration, and mindfulness are part of my daily note template for a reason. They help me stay connected to the bigger picture.

### 3. Intention and Goal Setting
Each day is a chance to move forward on my quests, whether they’re small tasks or major life goals. Writing down my objectives keeps me focused on what matters.

### 4. Memory and Reminders
Let’s face it, I’m human (or at least a very intelligent NPC), and I forget things. My notes are my trusty NPC scribe, helping me recall important details.

### 5. Reflection and Retrospection
Every adventurer needs time to sit by the campfire and reflect. Daily notes help me learn from my wins, analyze my mistakes, and level up for the next day.

---

## Why I Chose Obsidian 🔐 
When I started looking for a note-taking tool years ago, I had a few requirements:

- **[Markdown-Friendly](https://github.com/chandlertee/obsidian-starter/blob/59f7dc14192b945be8509a3702f5b2d35279c435/Cheatsheets/Markdown%20Basics%20Cheatsheet.md)**: As a software engineer, I live in markdown already. Why reinvent the wheel?
- **Text Files**: I wanted my notes to remain portable and future-proof, not locked in some proprietary format.
- **Customizable**: I like tinkering, and Obsidian’s core and community plugins gave me infinite ways to level up. Check this [README](https://github.com/chandlertee/obsidian-starter/blob/59f7dc14192b945be8509a3702f5b2d35279c435/README.md) for more on the community plugins I've installed.
- **Cross-Device Sync**: Storing notes in a cloud drive lets me seamlessly access them from my laptop, tablet, or phone.
- **Static Site Integration**: With markdown notes, I can easily publish reflections on my Jekyll-powered blog. Meta, right?
- **Open Source**: I appreciate that Obsidian supports a thriving open-source ecosystem.

[Obsidian](https://obsidian.md/) checked all these boxes and then some. It’s the Bag of Holding of note-taking tools: versatile, compact, and full of surprises. I've been using Obsidian daily for several years now, and I decided it was time to update my Daily Note Template to keep the process feeling fresh.

---

## My Daily Note Template: A Walkthrough 
My [Daily Note Template](https://github.com/chandlertee/obsidian-starter/blob/c0a00e0570e973c809b4fa7ebad9386de13e79d1/Templates/Periodic/Daily%20Note%20Template.md) consists of three main sections:
1. **Campfire Prep 🔥** 
This is where I get ready for the day—the morning ritual that sets the tone.
2. **Field Notes 📝**
This is my space for jotting down random thoughts, meeting notes, or anything that pops up during the day. It’s my adventurer’s sketchbook.
3. **Long Rest 🌙**
Evenings are for reflecting on the day and preparing for tomorrow. This section helps me level up.

#### Why the Fantasy Theme? 🏰
Because why not make mundane tasks feel epic? The fantasy theme keeps me engaged and reminds me that every day is part of a larger adventure. Plus, who doesn’t want to feel like a hero slaying to-dos and collecting XP?

### Campfire Prep 🔥

#### Inspiration 📜
I use the community plugin Templater to pull in a random quote each day. It’s like starting with a bard’s song to inspire the adventurer in me.

#### Blessings ✨
Gratitude keeps me grounded. Writing down what I’m thankful for helps me see the treasure in my daily life.

#### This Week’s Quests
Using the community plugin Dataview, I pull tasks from my weekly note to ensure I’m aligned with the bigger picture. It’s like checking the party’s quest log.

#### Today’s Encounters 🏹
Here I list the day’s actionable tasks—the encounters I need to face. It’s my to-do list with a touch of adventuring flair.

#### Allies 🛡️
Who or what can support me today? This could be teammates, tools, or even a good cup of coffee. Allies are vital for any quest.

#### Traps 👹
What potential distractions or pitfalls do I need to avoid? Identifying these upfront helps me stay vigilant.

````md 
## Campfire Prep 🔥
#### Inspiration 📜
<% tp.web.daily_quote() %>
#### Blessings 🌟
**What am I grateful for today?**  
- <% tp.file.cursor() %>
#### This Week's Quests
```dataview
task 
from "Journal/Weekly/<% tp.date.now("YYYY-[W]ww", 0, tp.file.title, "YYYY-MM-DD") %>"
```
#### Today's Encounters 🏹
**What can I do today to advance this week's Quests?**  
  - [ ] 
#### Allies 🛡️
 **Who or what can help me today?**  
- 
#### Traps 👹
**What obstacles or distractions should I watch out for?**  
- 
````

---

### Field Notes 📝

```md
## Field Notes 📝
- 
```

---

### Long Rest 🌙

#### Wisdom 📚
What did I learn today? This is where I catalog the new lore or skills I’ve unlocked.

#### Boons ⚡
What gave me energy or supported me today? A great conversation? Exercise? I document my power-ups.

#### Loot 🏆
What were my wins? Big or small, these are the treasures I’ve earned.

#### Monsters 🐉
What were the toughest challenges I faced? How did I handle them? This section reminds me that even failures are part of the journey.

#### Growth 🌱
What can I improve tomorrow? This is my chance to reflect and set a course for better adventures ahead.

```md
## Long Rest 🌙
#### Wisdom 📚
**What did I learn today?**  
- 
#### Boons ⚡
**What gave me energy or helped me?**  
- 
#### Loot 🏆
**What were my wins today?**  
- 
#### Monsters 🐉
**What were the toughest challenges I faced? How did I handle them?**  
- 
#### Growth 🌱
**What can I improve tomorrow?**  
- 
```

---

### Template Plugin Integrations

#### Links to Related Daily and Weekly Notes
At the top of the template, I include code for the Templater community plugin to add the filename as the title of the note `# <% tp.file.title %>`. This is the default behavior for Obsidian, but I have turned off the default behavior as I prefer to not have the title in every note (especially when using Obsidian to write posts for a [Jekyll](https://jekyllrb.com/) static website, a subject for a different day). 

I also include code for the Templater community plugin to link to the previous and next day's note, as well as the weekly note. In short, `<% tp.date.now("YYYY-[W]ww", 0, tp.file.title, "YYYY-MM-DD") %>` takes the daily note filename `tp.file.title` (third parameter), which is in this date format `YYYY-MM-DD` (fourth parameter), adds the offset in days `0` (second parameter), and will convert the resulting date into the desired format `YYYY-[W]ww` (first parameter). This allows me to easily click the links to switch between the weekly and other daily notes using Obsidian's internal linking.

```md
# <% tp.file.title %>

**Prev Day:** **[[<% tp.date.now("YYYY-MM-DD", -1, tp.file.title, "YYYY-MM-DD") %>]]**  
**Next Day:** **[[<% tp.date.now("YYYY-MM-DD", +1, tp.file.title, "YYYY-MM-DD") %>]]**  
**Week:** **[[<% tp.date.now("YYYY-[W]ww", 0, tp.file.title, "YYYY-MM-DD") %>]]**  
```
#### **Notes Created Today**
I use a community plugin Dataview to query and list all my notes created during this specific day.

````md
## Notes Created Today
```dataview
list 
where file.cday = date("<% tp.file.title %>") and file.name != "<% tp.file.title %>"
sort file.ctime desc
```
````

---

## Final Thoughts 💭
Daily notes aren’t just about productivity for me—they’re a way to stay intentional, reflect on the journey, and have a little fun along the way. Whether you’re a fellow adventurer or just looking for a system to help you navigate your days, I hope this inspires you to create your own note-taking ritual. Remember: every great story starts with a single entry in the adventurer’s journal. 

[Full Daily Note Template](https://github.com/chandlertee/obsidian-starter/blob/c0a00e0570e973c809b4fa7ebad9386de13e79d1/Templates/Periodic/Daily%20Note%20Template.md)
