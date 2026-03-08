+++
date = '2026-03-04T10:40:12Z'
summary = 'My name is Pedro Silva, and here is everything you need to know about me.'
draft = false
title = 'Who am I?'
tags = ["it", "computer science", "dev"]
ShowBreadCrumbs = true
ShowReadingTime = true
ShowShareButtons = true
+++

My name is Pedro Silva, and I'm a software engineer at Mindera.

Ever since I was a kid, I spent countless hours playing video games, initially on a Gameboy Color. However, once my parents bought me a computer, I discovered a whole new world. My father always pushed me to learn more about how they worked, helping me understand different components through trial and error. Even though I didn't have early experience in software development, it always felt like my future career would involve computers.

## Education
In 2013, I enrolled at the Faculty of Engineering at the University of Porto (FEUP) to study Computer Science. At the time, the program was an integrated Master’s; five years later, I graduated with my Master's degree. I completed my thesis at Glintt, a Portuguese company that develops software for hospitals and pharmacies. My project focused on using machine learning to provide doctors with a list of possible medicines based on a patient's symptoms.

## Work Experience

### Glintt HS
I graduated with a final grade of 16 and began my career as a software engineer at Glintt. As often happens with corporate thesis projects, mine was shelved, and I began working on their core systems. Transitioning from "dummy" university projects to real-world software was an eye-opener.

I quickly realized that Portuguese health systems can be quite archaic, often built on outdated technologies and processes. Much of the code was written in PL/SQL directly within the database, lacking a proper IDE for debugging, and—worst of all—there was no version control system. Deployments were almost entirely manual.

Coming from a modern university ecosystem, I was a bit naive about how much legacy code exists in the industry. I learned that the primary hurdle is often financial; because private and public systems must communicate (often via SOAP or PL/SQL procedures), upgrading a single database requires every connected system to follow suit, which is costly and time-consuming.

Codewise, I spent my first six months working with PL/SQL (which I don’t particularly recommend!), before moving to .NET Core. My manager was very forward-thinking and pushed for new hires to adopt .NET Core and Docker. We became the first team to use Docker to build systems connecting third-party platforms to Glintt’s infrastructure.

One of my most significant projects involved validating medicines entering hospitals. Following EU mandates, laboratories must register every box of medicine produced. Our system scanned these barcodes, validated them against the EU database, and returned the status to the logistics team. After an intensive certification process, we became the first company in Portugal to have a certified medicine validation system.

Working at Glintt taught me how to handle legacy code, high-pressure environments, and tight deadlines. There was always a new "ASAP" feature or a critical system break that needed immediate attention. 

I spent two years there before deciding to move to Mindera.

### Mindera
I joined Mindera in 2020. A few friends already worked there and encouraged me to apply because the company had several openings for Node.js backend developers, a role I was very interested in.

I had worked with Node.js during university and loved it, but local job opportunities for it had been limited. When the chance arose at Mindera, I took it. I was placed with an e-commerce client where I still work today. My team builds systems to handle product, pricing, and stock data.

Joining Mindera highlighted just how much I had to learn about modern DevOps and Quality. Everything here is deployed to AWS (a shift from the on-premise hospital servers at Glintt). We prioritize quality; every bit of code requires, at least, unit tests and QA verification. I now use GitLab and GitLab CI/CD to automate deployments, supported by a dedicated platform team that makes the pipeline process as "plug-and-play" as possible for developers.

It has been a great and learning experience so far. Hope to keep learning and growing!