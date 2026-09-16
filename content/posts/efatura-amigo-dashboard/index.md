+++
date = '2026-09-16T14:15:28+01:00'
summary = 'Dashboard to visualise data that powers Efatura Amigo browser extension'
draft = false
title = 'Efatura Amigo Dashboard'
keywords = ["Lidl", "TypeScript", "Telegram", "Golang", "Parkside"]
tags = ["lidl", "telegram", "parkside", "typescript", "golang"]
categories = ["Projects"]
author = "Pedro Silva"
ShowBreadCrumbs = true
ShowReadingTime = true
ShowShareButtons = true

[cover]
image = "images/dashboard.png"
alt = "A Telegram bot that scrapes the Portuguese Lidl website to check for availability of Parkside products"
caption = "A Telegram bot that scrapes the Portuguese Lidl website to check for availability of Parkside products"
relative = true
+++
# 🚀 Quick Links

**GitHub Repository**: [efatura amigo dashboard source code]([https://github.com/PedroS11/parkside-notifier](https://github.com/PedroS11/efatura-amigo-fe))

---

After creating the browser extension and the backend that powers it, I found it annoying to login into AWS -> Dynamo ->
Explore items to view my saved companies + the Dynamo costs to read anything. So, createing a private dashboard where
I could easily do it seems like the next step.

# Architecture

## Backend
### Authentication
Since I'm running this on free tier services, the new endpoints must be behind authentication where I can control who can
access it.
To make it easier, Google authentication method was the quickest and easiest solution. The frontend would get a Google
Identification Token, send it the login endpoint and a host session cookie would be returned. 

The session cookies needed to be saved so we can control if the cookie is still valid, so it was between Dynamo or Redis.
Since I had all the structure to create multiple dynamos in my stack and I was the only accessing it, Dynamo was more than capable.

```
export type Session = {
  sub: string;
  email?: string;
  name?: string;
  expiresAt: number;
  id: string;
};
```
_Representation of a session item in the dynamo_

With a table to hold the sessions, then login endpoint would be responsible for:
- Validate if the identification belong to a valid Google account and generated using Efatura Amigo Dashboard Google Authentication client ID
- Generating a random session id
- Save the session in its table
- Return 200 with the cookie set in the headers

In order to protect all the private endpoints, I created an [aws lambda authorizer](https://github.com/PedroS11/efatura-amigo-be/blob/main/src/application/authorizer/index.ts) that would sit behind all and it would
get the session cookie, check in the dynamo if it exists and it's not expired. In case of success, return true with your Google info, if not, return false.

### Logout
The logout was a straigthforward lambda that would get the sessionId from the cookie, delete it from Dynamo and send back
a delete cookie header

### Me
In order to validate my session and get my information to display on dashboard, I created a new endpoint
that receives the session cookie, goes through the authorizer and, on sucess, returns the Google data.

### Search feature
I needed to quickly search the companies and needed to support name search so an indexer was what I needed, in this case,
I had a lot of experience with Algolia. Since it had a free tier service that would fit the load i needed, I decied with it.

So the data saved would have the same format as in dynamo:
``` 
export enum Categories {
  Saude,
  Ginasio,
  Educacao,
  Imoveis,
  Lares,
  Outros,
  "Reparacao Automovel",
  "Reparacao Motas",
  "Alimentacao/Hotelaria",
  Cabeleireiro,
  "Animais de Estimacao",
  Transportes,
  "Jornais e Revista",
  "Comercio a retalho de livros",
  "Atividades artisticas e literarias",
  "Atividades dos museus e monumentos historicos"
}

export interface Company {
  nif: number;
  name: string;
  category?: Categories;
  caeRev3?: string;
  updatedAt: number;
}
```

In Algolia, you can set which attributes are searchable so I decided for `nif` and `name`.

To feed Algolia with companies data, I needed to on every dynamo update also send to Algolia to guarantee consistency.

### Metadata

Nif-pt API has strict limits on the amount of calls i can do as explained in [here](https://blog.pedroosilva.dev/posts/efatura-amigo/#architecture-design). 
So having the amount of requests that i'm still able to do using the /credits endpoint will be a nice to have information displayed.

There's also more metadata that would be useful information to be displayed, the number of companies saved and to be processed.
Dynamos have a method called DescribeTable that returns this approximated data.

So having an endpoint that aggregates all these information would bring a lot of useful information to the dashboard

## Frontend

In order to build the UI I picked the most common and free technologies:
- [Vite](https://vite.dev/) for the react
- [tailwind](http://tailwindcss.com/)+[shadcn](https://ui.shadcn.com/) for the UI components
- [@react-oauth/google](https://github.com/MomenSherif/react-oauth) to handle the Google form and authentication flow
- Cloudflare pages to host the website
- Cloudflare workers to handle rate limits and forward requests

### Login
The dashboard would then have a Login page

<p align="center">
    <img src="images/login.png" alt="Companies table" style="width: 500px; height: auto; max-width: 100%;" />
    <br>
    <small>Login page</small>
</p>

### Dashboard

<p align="center">
    <img src="images/dashboard.png" alt="Companies table" style="width: 500px; height: auto; max-width: 100%;" />
    <br>
    <small>Dashboard page</small>
</p>

<p align="center">
    <img src="images/search.png" alt="Companies table" style="width: 500px; height: auto; max-width: 100%;" />
    <br>
    <small>Search results</small>
</p>


