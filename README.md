# Affan Yousuf Siddiqui Portfolio

A personal portfolio website for Affan Yousuf Siddiqui, focused on Flutter development, mobile systems engineering, UAV ground control software, real-time telemetry, and cross-platform application development.

Live site:

```text
https://affanyousuf26.github.io/Affan-Portfolio/
```

## Overview

This is a single-page static portfolio built with plain HTML, CSS, and JavaScript. The visual design is inspired by UAV ground-control and telemetry dashboards, using a dark HUD-style interface with red accents, technical labels, animated details, and responsive sections.

## What It Includes

- Boot sequence and HUD-style header/status details
- Hero section with profile photo inside a phone frame and live intro animation
- Animated `pubspec.yaml` skills and technology stack
- Featured projects
- Interactive Zonaro app preview modal
- In-page drone dodge game
- Work experience timeline
- Education section
- Bottom tab navigation and contact bottom sheet
- Contact links for email, phone, LinkedIn, and GitHub
- Contact form using a `mailto:` fallback
- Responsive layout for desktop and mobile
- GitHub Pages deployment through GitHub Actions

## Featured Content

The portfolio highlights work around:

- Flutter and Dart application development
- UAV ground control systems
- MAVLink telemetry and payload control
- UDP, TCP, USB serial, and REST communication layers
- Real-time mobile systems
- Offline-first application workflows
- Firebase, PostgreSQL, Mapbox, H3, NestJS, and related tools

## Tech Stack

- HTML5
- CSS3
- JavaScript
- Google Fonts
- GitHub Actions
- GitHub Pages

## Project Structure

```text
.
├── index.html
├── images/
│   ├── affan.jpg
│   └── zonaro/
│       ├── icon.png
│       ├── onboarding.png
│       └── splash.png
├── .github/
│   └── workflows/
│       └── pages.yml
├── .nojekyll
└── README.md
```

## Local Preview

Open `index.html` directly in a browser. No build step, package installation, server, or backend is required.

## Deployment

The site is deployed with GitHub Pages using the workflow in:

```text
.github/workflows/pages.yml
```

Every push to the `main` branch triggers a new deployment.
