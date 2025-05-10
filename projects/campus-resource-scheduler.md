---
layout: project
type: project
image: img/crs.png
title: "Campus Resource Scheduler"
date: 2025
published: true
labels:
  - Final Project
  - Vercel
  - GitHub
summary: "A Campus Resource Scheduler website I contributed to in a group project for ICS 314."
---

<img class="img-fluid" src="../img/crs-about.png" style="display: block; margin: auto; height: auto; width: auto;">

In ICS 314, we were tasked with a final group project to develop a full-stack web application that would be genuinely useful to students, faculty, or administrators on campus. The result was the **Campus Resource Scheduler**, a tool designed to help users browse, borrow, and manage shared campus resources such as rooms and equipment. The project was built with modern web technologies, and it emphasized both functionality and usability.

My incredible teammates: **Zeyao Zhou, Ralph Uy, Sungwon Han, Eric Chae**, and I, **Arthur Acenas**, worked collaboratively from planning to deployment. We utilized GitHub Projects for agile-style issue tracking, conducted regular code reviews, and kept each other updated through group messaging on Discord and controlled commits to the main branch of our project. Our goal was to deliver a seamless scheduling experience tailored for academic environments.

<img class="img-fluid" src="../img/crs-equipment.png" style="display: block; margin: auto; height: auto; width: auto;">

I was primarily responsible for implementing the **Available Equipment** and **Available Rooms** pages. These pages dynamically display resources that are currently unclaimed, using filters to help users narrow down options by campus, location, or category. I wrote server-side logic to fetch and display only available resources, those whose `owner` is still set to `admin@foo.com` and implemented client-side components to reserve them. When a resource is borrowed, it disappears from the available list and appears in the borrower's personal "Your Resources" dashboard, where it can later be returned. This required tight integration between React components, API routes, Prisma database queries, and session-based access control.

<img class="img-fluid" src="../img/crs-rooms.png" style="display: block; margin: auto; height: auto; width: auto;">

We faced our fair share of challenges. One recurring issue was that resources were not syncing properly between the Available and Your Resources pages after being reserved or returned. This required a careful debugging process, especially with how we handled server actions, cache invalidation, and real-time UI updates. Another major challenge was enforcing project constraints, like limiting equipment reservations to five items per user, or allowing only one room reservation at a time. Each of these rules had to be reflected not only in the database but also in user-facing feedback and error handling.

In the end, the project came together beautifully. The final product was responsive, functional, and user-friendly. It reflected not only our technical skills, but also our growth as software engineers, working in a team, using version control effectively, writing maintainable code, and building something we could genuinely be proud of. The Campus Resource Scheduler represents one of my favorite experiences in the ICS 314 course, and a highlight of my development journey so far.

<hr>

Source: <a href="https://campus-resource-scheduler-project.github.io/"><i class="large github icon "></i>Campus Resource Scheduler</a>
