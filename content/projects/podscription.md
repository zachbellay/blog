+++
title="Podscription: AI Generated Podcast Transcripts"
date=2023-02-08
extra.thumbnail="/assets/images/projects/podscription/landing-page.png"
extra.status="In Progress"
extra.description="A website that automatically transcribes podcasts."
extra.tools=["Python", "Django", "Celery", "TypeScript", "React", "TailwindCSS", "OpenAI Whisper", "Flowbite" ]
extra.toc = true
+++

<a href="https://www.podscription.app">
{{ img(path="/assets/images/projects/podscription/landing-page.png", center="True") }}
</a>

<center>The landing page for podscription.</center>

---

<center style="font-size:1.5em; color: #363636; font-weight: 600;">Check it out at</center>
<center style="font-size:1.5em; color: #363636; font-weight: 600;">➡️ <a href=http://www.podscription.app>www.podscription.app</a> ⬅️</center>

---

### What is podscription?

Podscription is a portmanteau of podcast and transcription. It is a website that uses AI to transcribes podcasts and makes them searchable.


### Why build it?

I am an avid podcast listener and sometimes remember certain conversations, but don't remember which podcast the conversation is from but would like to revisit it. So naturally, the idea to build a website that automatically transcribes podcasts and then make them publicly available to search seemed like a great solution.

I looked for existing solutions, but nothing super comprehensive really existed (or really exists).

Typically transcribing audio is fairly expensive. One existing website [podscribe.app](https://podscribe.app/) use Google Clouds Speech-to-text offering, which costs 96¢/1 hour episode. However, among the whirlwind of AI news, on [September 21st, 2022 OpenAI released Whisper](https://openai.com/research/whisper), a model that automatically transcribes audio with high performance and low cost. [OpenAI's Whisper API costs $0.006/minute](https://openai.com/blog/introducing-chatgpt-and-whisper-apis), which means a 60 minute podcast only costs $0.36 to transcribe, a 62% reduction in cost. This project was pretty much a non-starter before Whisper was released partially because of the cost, but also because with Whisper I can run it on my own gaming machine, which means it only costs me electricity and internet bandwidth.

### My Goals

- ✅ learn how to use Celery for asynchronous tasks
- ✅ get better at frontend development
    - ✅ improve my React and Typescript skills
    - ✅ try out TailwindCSS 
- ✅ use it to impress a potential employer to get a new job


### Technologies Used

- OpenAI Whisper
- Django
- Django Ninja
- Typescript + React
- TailwindCSS
- Flowbite Tailwind Component Library
- Celery
- Docker Compose 
- Nginx Proxy Manager
- ~~Apache Airflow~~


### Timeline

This project spanned from October 2022 to January 2023. 

The first 2 months or so was spent solely on getting the codebase setup. I also did spend a lot of time trying to use Apache Airflow for getting the podcasts, only to realize that Airflow was not the right tool for the task.

I landed my job at Rinse in late January 2023, and ever since have mostly stopped development. 

I showed this website to my current manager and I think it played a role in me getting hired. More of a cherry on top than anything, but I also learned a lot of the fundamental skills/tech stack to be qualified via this project in the first place.


### Demo & Tour


{{ video(path="/assets/images/projects/podscription/podscription-demo.mp4")}}

Here's me walking through the website as well as talking about some other competing websites.

---

{{ img(path="/assets/images/projects/podscription/all-podcasts.png", center="True") }}

The "All Podcasts" View.

---

{{ img(path="/assets/images/projects/podscription/light-mode-single-episode.png", center="True") }}

The "Single Episode" View, which shows the podcast maker, title of the episode, description, and the transcript. In light mode.

---

{{ img(path="/assets/images/projects/podscription/single-podcast.png", center="True") }}

The "Podcast" View, which shows information about the podcast, as well as all the available episodes.

---


{{ img(path="/assets/images/projects/podscription/search-results-both.png", center="True") }}

The Search View, has the top podcast results as well as top podcast episode results.

### Current Status

I've decided to slim the podcasts down just to podcasts I listen to and care about so that I can keep costs and maintenance low. 


### Going Forward 

I'm looking to move onto the next project, and while I had a lot of fun and learned a lot building this, it seems like there wasn't quite a product market fit. I am actively learning how to achieve product market fit and to actually solve real problems that people have. The advice I've got both in "Lean Startup" as well as from a coworker is to "get out of the house" and actually talk to people. It's tough for me mostly because I don't know where to start when it comes to searching for problems to solve.

I think the next step in my personal journey is to learn how to get better at customer discovery in addition to continuing to hone my tech skills. I'm thinking the next thing I build will be a mobile app, because most of Gen Z is almost always on their phone as opposed to website, and Apple/Google App Stores make it easy for customers to discover your app. We'll see what the next thing is!