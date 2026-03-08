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

# Education
In 2013, I enrolled at the Faculty of Engineering at the University of Porto (FEUP) to study Computer Science. At the time, the program was an integrated Master’s; five years later, I graduated with my Master's degree. I completed my thesis at Glintt, a Portuguese company that develops software for hospitals and pharmacies. My project focused on using machine learning to provide doctors with a list of possible medicines based on a patient's symptoms.

# Work Experience

## Glintt HS
I graduated with a final grade of 16 and began my career as a software engineer at Glintt. As often happens with corporate thesis projects, mine was shelved, and I began working on their core systems. Transitioning from "dummy" university projects to real-world software was an eye-opener.

I quickly realized that Portuguese health systems can be quite archaic, often built on outdated technologies and processes. Much of the code was written in PL/SQL directly within the database, lacking a proper IDE for debugging, and—worst of all—there was no version control system. Deployments were almost entirely manual.

Coming from a modern university ecosystem, I was a bit naive about how much legacy code exists in the industry. I learned that the primary hurdle is often financial; because private and public systems must communicate (often via SOAP or PL/SQL procedures), upgrading a single database requires every connected system to follow suit, which is costly and time-consuming.

Codewise, I spent my first six months working with PL/SQL (which I don’t particularly recommend!), before moving to .NET Core. My manager was very forward-thinking and pushed for new hires to adopt .NET Core and Docker. We became the first team to use Docker to build systems connecting third-party platforms to Glintt’s infrastructure.

One of my most significant projects involved validating medicines entering hospitals. Following EU mandates, laboratories must register every box of medicine produced. Our system scanned these barcodes, validated them against the EU database, and returned the status to the logistics team. After an intensive certification process, we became the first company in Portugal to have a certified medicine validation system.

Working at Glintt taught me how to handle legacy code, high-pressure environments, and tight deadlines. There was always a new "ASAP" feature or a critical system break that needed immediate attention. 

I spent two years there before deciding to move to Mindera.

## Mindera
I joined Mindera in 2020, encouraged by friends who spoke highly of the culture and the company's focus on Node.js—a technology I had grown to love during university but found limited opportunities for locally.

I was placed with a major e-commerce client and have been an integral part of that partnership ever since. 
My team builds and maintains the core systems handling product, pricing, and stock data.

### Technical Focus & Expertise
- **TypeScript**: I am a strong advocate of "types everywhere" ensuring our codebase remains clean and readable.

- **Search & Discovery**: I have experience working with Algolia for product indexing and recently work on the migration to Google Cloud Retail to optimize product data delivery.

- **Cloud Architecture**: I work daily within the AWS ecosystem, leveraging Lambdas, SNS, SQS, EventBridge, and DynamoDB, for example.

- **Modern DevOps**: Shifted from on-premise environments to the cloud and I now utilize GitLab CI/CD for automated deployments, collaborating with dedicated platform teams to keep our pipelines "plug-and-play."

- **Quality**: Every feature is backed by rigorous unit testing and QA verification.

It has been a great and learning experience so far. Hope to keep learning and growing!