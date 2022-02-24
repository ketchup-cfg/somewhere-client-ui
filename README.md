# Forum-UI

A front-end user interface for the forum-api application created using Svelte.js.

## Building

This application is build with Svelte.js and uses Tailwind CSS for styling.

In order to build this application, first run the following command to build the CSS for the application:

```bash
npx tailwindcss -i ./public/global.css -o ./public/build/bundle.css
```

Then run this command to build the application with the built CSS applied to it:

```bash
npm run build
```

