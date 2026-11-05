<div align="center">


# Tale Tuners

**Enhancing sleep for kids with the soothing voice of their loved ones.**

<p align="center">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/python/python-original.svg" alt="Python" width="40" height="40" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/flask/flask-original.svg" alt="Flask" width="40" height="40" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/sqlite/sqlite-original.svg" alt="SQLite" width="40" height="40" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/html5/html5-original.svg" alt="HTML5" width="40" height="40" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/css3/css3-original.svg" alt="CSS3" width="40" height="40" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/javascript/javascript-original.svg" alt="JavaScript" width="40" height="40" />
  <img src="https://cdn.simpleicons.org/pythonanywhere/1D9FD7" alt="PythonAnywhere" width="40" height="40" />
</p>

Live Demo: https://suguna.pythonanywhere.com  
Built by Group 12, University of North Texas — 7 members. Suguna Garmidi was Scrum Master.

</div>

## Overview

Tale Tuners is a bedtime-story web app built by a 7-person UNT master's team. Children browse bedtime stories by genre, and a parent can read a story aloud and record it, so children can fall asleep to a familiar voice even when a parent is away.

This repository is the working Flask app that came out of that team project, deployed live on PythonAnywhere.

## How It Works

| 1️⃣ Create an account | 2️⃣ Pick a story | 3️⃣ Read & record |
|---|---|---|
| Sign up, then log in. | Choose a genre and a book. | Read aloud with the mic — play it back or download it. |

## ✨ Features

- **Accounts:** Signup, login, and logout with a SQLite users table.
- **Browse by genre:** Five genres — Adventure, Fantasy, Horror, Historical, Fiction.
- **Storybooks:** Nine public-domain books, hosted as PDFs on the site and linked per category.
- **Read and record:** Each book opens inside the app on a reader page, beside a mic record button — record while reading, then play back or download the recording. Recordings stay on the device; nothing is uploaded to the server.
- **Design:** A night-sky storybook theme across the signup, login, home, and category pages, with a cursor-chasing mouse on the home page and a ghost on the login and signup pages that covers its eyes while a password is typed.

## 📚 Storybooks

| Genre | Books |
|---|---|
| Adventure | *Treasure Island*, *The Adventures of Tom Sawyer* |
| Fantasy | *Alice's Adventures in Wonderland*, *The Wonderful Wizard of Oz* |
| Horror | *The Legend of Sleepy Hollow* |
| Historical | *Little Women*, *The Secret Garden* |
| Fiction | *Pinocchio*, *The Velveteen Rabbit* |

All nine books are free public-domain PDFs from Internet Archive (Gutenberg offers no PDF for these titles), hosted in `static/books/` and linked per category in the `STORYBOOKS` dict in `app.py`.

## Data Model

**Users table (SQLite):** `storytel.db`, created in `app.py` — `users (userid, firstname, lastname, email, pnnumber, password)`. This is the only database table in the app. The app was originally built on MySQL and moved to SQLite for the free PythonAnywhere tier, so it runs with no database server.

| Route | What it does |
|---|---|
| `/signup` | Creates a user in the users table (GET shows the form, POST inserts) |
| `/login` | Checks email and password, starts a session, shows the home page with the five genre categories |
| `/category` | Takes the selected genres (GET or POST) and returns the matching storybook PDFs hosted in `static/books/` |
| `/read/<filename>` | Opens the book's PDF inside the app, beside the mic record button |
| `/logout` | Ends the session and returns to login |
| `send_mail` | Login-notification email helper in `app.py` |

## Tech Stack

Python, Flask, SQLite, HTML, CSS, JavaScript, PythonAnywhere

## Project Structure

```
Tale-Tuners-Group-12/
├── app.py                  # Flask app: routes, SQLite setup, STORYBOOKS dict
├── assets/
│   └── banner.png          # README banner
├── static/
│   ├── books/              # The 9 storybook PDFs
│   ├── styles.css          # Original styles
│   ├── login.css           # Login page theme
│   ├── signup.css          # Signup page theme
│   ├── home.css            # Home page theme
│   ├── user.css            # Category page theme
│   ├── reader.css          # Reader page theme
│   ├── mouse.js            # Cursor-chasing mouse
│   ├── ghost.js            # Ghost that reacts to password typing and login results
│   └── reader.js           # Mic recording on the reader page
└── templates/
    ├── login.html
    ├── signup.html
    ├── home.html
    ├── userPage.html
    ├── reader.html
    └── forgot-password.html
```

## Getting Started

1. Clone the repository:
   ```
   git clone https://github.com/sugunagar/Tale-Tuners-Group-12.git
   ```
2. Install Flask (the app uses SQLite, which is built into Python — no database server needed):
   ```
   pip install flask
   ```
3. Run the app:
   ```
   python app.py
   ```
4. Open the signup page, create an account, log in, and pick a genre.

Try the live app at `https://suguna.pythonanywhere.com` — sign up, log in, and pick Fantasy to see *Alice's Adventures in Wonderland* and *The Wonderful Wizard of Oz*.

## Roadmap

Planned, not in this code yet: a favorites folder, a sleep timer, and story suggestions. Those were part of the original project vision and presentation.

**Known limitation:** the app has no page at its root address, so the entry point is login.

## Author

Suguna Garmidi — Data Analytics Engineer, Scrum Master for Group 12
Portfolio: `https://sugunagar.github.io`
