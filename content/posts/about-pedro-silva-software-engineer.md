+++
date = '2026-03-04T10:40:12Z'
lastmod = '2026-03-25T12:00:00Z'
summary = 'Software engineer Pedro Silva shares his journey from Computer Science at FEUP to AWS TypeScript development at Mindera, including experience with .NET Core, PL/SQL, and e-commerce systems.'
description = 'Meet Pedro Silva, a software engineer working with AWS, TypeScript, and e-commerce systems. Learn about his career journey from healthcare software development to modern cloud architecture.'
draft = false
title = 'About Pedro Silva - Software Engineer'
keywords = ["Pedro Silva", "software engineer", "AWS developer", "TypeScript developer", "Mindera", "Glintt", "FEUP", "Computer Science", "cloud architecture", "e-commerce development"]
tags = ["software-engineer", "aws", "typescript", "career", "mindera", "glintt", "feup", "computer-science", "cloud-development", "e-commerce", "dotnet-core", "plsql", "gitlab-cicd", "algolia", "google-cloud-retail"]
categories = ["About", "Career"]
author = "Pedro Silva"
ShowBreadCrumbs = true
ShowReadingTime = true
ShowShareButtons = true
ShowToc = true
TocOpen = false
+++

My name is **Pedro Silva**, and I'm a **software engineer at Mindera** working with **AWS cloud architecture** and **TypeScript development**. With over 8 years of experience in software development, I've worked across various technologies from legacy systems to modern cloud-native applications.

Ever since I was a kid, I spent countless hours playing video games, initially on a Gameboy Color. However, once my parents bought me a computer, I discovered a whole new world. My father always pushed me to learn more about how they worked, helping me understand different components through trial and error. Even though I didn't have early experience in software development, it always felt like my future career would involve computers.

## Education & Academic Background
In 2013, I enrolled at the Faculty of Engineering at the University of Porto (FEUP) to study Computer Science. At the time, the program was an integrated Master’s; five years later, I graduated with my Master's degree. I completed my thesis at Glintt, a Portuguese company that develops software for hospitals and pharmacies. My project focused on using machine learning to provide doctors with a list of possible medicines based on a patient's symptoms.

## Professional Experience

### Glintt HS - Healthcare Software Development (2018-2020)
I graduated with a final grade of 16 and began my career as a software engineer at **Glintt**. As often happens with corporate thesis projects, mine was shelved, and I began working on their core systems. Transitioning from "dummy" university projects to real-world software was an eye-opener.

I quickly realized that Portuguese health systems can be quite archaic, often built on outdated technologies and processes. Much of the code was written in **PL/SQL** directly within the database, lacking a proper IDE for debugging, and—worst of all—there was no version control system. Deployments were almost entirely manual.

Coming from a modern university ecosystem, I was a bit naive about how much legacy code exists in the industry. I learned that the primary hurdle is often financial; because private and public systems must communicate (often via **SOAP** or **PL/SQL** procedures), upgrading a single database requires every connected system to follow suit, which is costly and time-consuming.

Codewise, I spent my first six months working with **PL/SQL** (which I don’t particularly recommend!), before moving to **.NET Core**. My manager was very forward-thinking and pushed for new hires to adopt **.NET Core** and **Docker**. We became the first team to use **Docker** to build systems connecting third-party platforms to Glintt’s infrastructure.

One of my most significant projects involved validating medicines entering hospitals. Following EU mandates, laboratories must register every box of medicine produced. Our system scanned these barcodes, validated them against the EU database, and returned the status to the logistics team. After an intensive certification process, we became the first company in Portugal to have a certified medicine validation system.

Working at Glintt taught me how to handle legacy code, high-pressure environments, and tight deadlines. There was always a new "ASAP" feature or a critical system break that needed immediate attention. 

I spent two years there before deciding to move to Mindera.

### Mindera - E-commerce & AWS Development (2020-Present)
I joined Mindera in 2020, encouraged by friends who spoke highly of the culture and the company's focus on Node.js—a technology I had grown to love during university but found limited opportunities for locally.

I was placed with a international e-commerce client and have been an integral part of that client ever since. 
My team is responsible for building and maintaining the core systems handling product, pricing, and stock data.

All the code is written in **TypeScript** and I'm one of the most enforcers of creating and adding meaningful types to our codebase, ensuring it remains clean and readable.
Putting `any` everywhere or not add the types to the function arguments and return values due to laziness, it's something I really hate because,
in the future, that will come back to haunt the team.

Back at **Glintt**, everything was deployed to servers in the hospitals whereas now, we use work daily with the **AWS** ecosystem, like Lambdas, SNS, SQS, EventBridge, and DynamoDB.
But we also use other third party services, for example, to have faster product searches we used to rely on **Algolia** for severly years.
Most recently, we migrated to **Google Cloud Retail** to optimize product data delivery.

Everything we write must be covered by unit tests and QA verification on the feature branches and quality environemnts before reaching production
For that, we utilize **GitLab** CI/CD for automated deployments, collaborating with dedicated platform teams to keep our pipelines "plug-and-play."

It has been a great and learning experience so far. Hope to keep learning and growing!

## Technical Skills & Expertise

**Cloud Platforms**: AWS (Lambda, SNS, SQS, EventBridge, DynamoDB)  
**Programming Languages**: TypeScript, JavaScript, C#, PL/SQL  
**Frameworks & Libraries**: Node.js, .NET Core, React  
**Tools & Services**: GitLab CI/CD, Docker, Algolia, Google Cloud Retail  
**Databases**: DynamoDB, MySQL, Oracle  

## Side Projects & Open Source

Beyond my professional work, I enjoy building tools that solve real problems. My most successful project is the [Twitch Live Extension](/posts/twitch-live-extension/), a browser extension that helps users track their favorite streamers and has grown to over 20,000 users across Chrome and Firefox.

## Let's Connect

I'm always interested in discussing software development, cloud architecture, and innovative projects. Feel free to reach out through my social media links or check out my other blog posts where I share technical insights and project experiences.