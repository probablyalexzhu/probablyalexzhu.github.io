---
title: "Tutorial: Learning Full-Stack Development With a Project"
tags: [projects, react, pocketbase, fullstack, tutorials]
date: 2023-06-30
showDate: false
showWordCount: true
showReadingTime: true

# summary: "Hi! My name is Alex Zhu."
showSummary: true
showAuthor: true
showTableOfContents: false
showComments: true
showPagination: true
invertPagination: true
showTaxonomies: true

draft: true
---
Project-based learning is one of the most enjoyable and effective ways to learn new skills. You get to develop something that you’re interested in, and the work is just challenging enough at the edge of your abilities to be fully engaging. Here’s how I learned full-stack dev by making a project.

1. Figuring out what to make

I wanted to learn front-end development, specifically React, as well as how to work with databases like SQL or MongoDB. This was a bit of a hole in my knowledge as I hadn’t been exposed to these technologies in the past, so I decided my project would include these technologies.

To turn this into a project, I could have made a stock project like a to-do list or notes app. However, this would a) not be fun because I don’t really care about making another notes app, and b) would look unimpressive to others because you could easily copy existing code to make something stock. Instead, I thought about what I actually wanted to make. I suck at remembering and deciding what to give people as gifts, so I decided to make a gift tracker to help people plan and think of gifts to give. This does exist already, but the few apps that do it are not very prominent. Ultimately, the important thing is that you came up with the idea and execute it yourself, even if it already exists in some form.

From the idea, I thought of a minimum viable product idea, which had just the four CRUD functions (create, read, update, delete). I sketched up a simple UI on my tablet, taking inspiration from Mobbin, a website for UI & UX research.

2. We do a little learning

Before jumping in headfirst, I read through the React docs https://react.dev/learn to learn some basics about how the software works. This taught me about crucial things that may have not occurred to me while developing, such as lifting state up, the difference between states and props, server vs client-side rendering, and how hooks work on a basic level. This general understanding helped massively while debugging code later, but I also didn’t spend infinite time on reading docs before jumping in (probably <10 hours reading docs total). After learning about half of everything I wanted to know to get started, I dived into the project as I would learn the rest as I went.

3. Getting started

For full-stack, I decided to build the front-end first and then add the back-end database later. I created a Next.js app since I planned on deploying to Vercel later and they work well together. I followed the documentation and YouTube tutorials to get set up with creating a Next app with the React framework. Unbeknownst to me, I ended up using the brand new Next.js 13 app router, so there was very little documentation available. This led to a few hiccups during development without a lot of help, but it ultimately turned out alright.

To save time making components that had some semblance of aesthetics, I used the component library Chakra UI. This was probably one of the best decisions I made in making the project; it probably saved me 50 hours of just designing components. Following the minimum design I sketched up earlier, I started putting components together and created the basic layout that the final app would have.

4. In the thick of it

Using Auth.js, formerly NextAuth.js, I made it so you would have to log in to view certain pages. I followed a tutorial on environment variables, and setting up Google Cloud for app authentication. https://www.youtube.com/watch?v=Eh3EpwqT4cM Along with that, I turned the one page application into a website with a home page and a separate page for the app to live on.

Now, it was time to set up a database. I had learned some SQL using Khan Academy, as I wanted to learn a relational database. From a Fireship video, I discovered Pocketbase, an open source SQLite backend that was super easy to set up. I ran the database locally on my computer first, then integrated it into my app making API requests as needed. This connection between front-end and database was super satisfying after a lot of debugging; like landing a rocket on another planet.

Once the connection was made, I was able to implement more features and test if they worked or not by interacting with the database. Eventually, I decided to scrap together a chat app really quickly to add to the project to demo the realtime and multi-user capabilities of the database. Finally, I cleaned up the app with some pretty front-end components and transitions.

5. Deploy

I’m a cheapstake when it comes to deploying things online. Pocketbase is entirely self-hosted, so I did it with the free resource allowances from Fly.io, and then deployed the Next.js front-end on Vercel + GitHub. In theory, the app should now run free forever, although something will prooobably go wrong :)

Honestly the whole process was easier than I anticipated and a ton of friend. I encourage anyone learning anything new to do it through an original project idea and to not be afraid to start; there are so many resources online nowadays to help with the process.