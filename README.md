# Vite Multipage URL Bug

Multipage apps created with Vite have inconsistent URL behavior between the dev server and the build.

## Description

Using the following folder structure:

```
├── package.json
├── vite.config.js
├── index.html
└── nested
    └── index.html
```

### Expected

Both dev and build use the same URL to access the nested page; either:

1. `<root>/nested`
2. `<root>/nested/`
3. both of the above

### Actual

- Dev: `nested` page cannot be accessed without the trailing slash (`<root>/nested/`)
- Build: `nested` page can be accessed with or without trailing slash

## Steps to reproduce

1. Clone this repository.
2. Run `npm install` at the repository root.
3. Run `npm run dev` and attempt to navigate to `localhost:3000/nested`. You should see "Main Page". Navigating to `localhost:3000/nested/` produces the desired "Nested Page".
4. Run `npm run build` and `npm run preview`, then navigate to `localhost:5000/nested`. You should see "Nested Page". The same occurs when adding the trailing slash.