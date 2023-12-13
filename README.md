# Vue 3 + Vite

## Overview

This is a simple Vue 3 application showcasing my ability to structure and run a project using Vue 3 with Vite as the build tool. The app displays a greeting window with a joke and a punchline. Users can create new entries, delete existing entries, and fetch jokes from an external API. The project is configured to deploy on GitHub Pages.

## Technologies Used

- **Vue 3**: The JavaScript framework used for building the user interface.
- **Vite**: A fast build tool for Vue applications.
- **GitHub Pages**: Hosting platform for deploying the application.
- **Other Dependencies**: Axios for fetching API.

## Project Structure

`vue_app/
│
├── public/
│   ├── close.svg
│   └── ...
├── src/
│   ├── components/
│   │   ├── UI   
│   │   │   ├── MyButton.vue
│   │   │   └── MyModal.vue
│   │   ├── PostItem.vue
│   │   ├── PostList.vue
│   │   ├── PostForm.vue
│   │   └── ...
│   ├── App.vue
│   ├── main.js
│   └── ...
├── .gitignore
├── vite.config.js
├── package.json
├── README.md
└── ...`

## Features

- Greeting Window: Display a random joke and punchline.
- Modal Popup: Create new entries with a modal popup.
- Delete Functionality: Remove existing entries.
- API Integration: Fetch jokes from an external [Joke API](https://github.com/15Dkatz/official_joke_api).
- Loading Spinner: Animated spinner appears while content is loading.
