# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

- **Run app:** `python app.py` (starts Flask dev server on port 5001)
- **Run tests:** `python -m pytest` (uses pytest-flask)
- **Activate venv:** `.venv\Scripts\activate` (Windows) or `source .venv/bin/activate` (macOS/Linux)
- **Install dependencies:** `pip install -r requirements.txt`

## Project Overview

**Spendly** is a personal expense tracker built with Flask. The app lets users log expenses, categorize spending, and view monthly summaries. It uses SQLite via raw SQL (no ORM) and Jinja2 server-side rendering.

This is an educational project with placeholder routes that students implement step by step.

## Architecture

- **`app.py`** — Flask app factory with all routes. Currently has stub placeholders for logout, profile, and expense CRUD that return plain text responses.
- **`database/db.py`** — Database module stub. Students implement `get_db()`, `init_db()`, and `seed_db()`. `database/__init__.py` is empty.
- **`templates/`** — Jinja2 templates extending `base.html`. `base.html` provides the nav bar, footer, and block sections (`content`, `head`, `scripts`). Auth forms (login/register) use `method="POST"` and display errors via the `error` template variable.
- **`static/css/style.css`** — Single stylesheet with CSS custom properties (DM Serif Display + DM Sans fonts, warm neutral palette). No CSS framework.
- **`static/js/main.js`** — Empty; students add JS incrementally.

## Key Patterns

- Routes return `render_template("page.html")` — no API/JSON endpoints.
- Auth forms POST to `/login` and `/register` with `email`, `password` (and `name` for register).
- DB module pattern: plain `sqlite3` with `row_factory = sqlite3.Row` and foreign keys enabled.
- The nav bar in `base.html` currently shows "Sign in" and "Get started" links — these need to switch to user menu when authenticated.
