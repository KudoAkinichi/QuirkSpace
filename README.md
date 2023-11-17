# Setup

Before getting started make sure to make an account in appwrite and set the schema in appwrite with exact name as in application to make it work.
make a .env.local file with this format:

VITE_APPWRITE_PROJECT_ID=

VITE_APPWRITE_URL=

VITE_APPWRITE_STORAGE_ID=

VITE_APPWRITE_DATABASE_ID=

VITE_APPWRITE_USER_COLLECTION_ID=

VITE_APPWRITE_POST_COLLECTION_ID=

VITE_APPWRITE_SAVES_COLLECTION_ID=

Run the following commands to get started:
1. npm install
2. npm run dev

### React + TypeScript + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

### Expanding the ESLint configuration

If you are developing a production application, we recommend updating the configuration to enable type aware lint rules:

- Configure the top-level `parserOptions` property like this:

```js
   parserOptions: {
    ecmaVersion: 'latest',
    sourceType: 'module',
    project: ['./tsconfig.json', './tsconfig.node.json'],
    tsconfigRootDir: __dirname,
   },
```

- Replace `plugin:@typescript-eslint/recommended` to `plugin:@typescript-eslint/recommended-type-checked` or `plugin:@typescript-eslint/strict-type-checked`
- Optionally add `plugin:@typescript-eslint/stylistic-type-checked`
- Install [eslint-plugin-react](https://github.com/jsx-eslint/eslint-plugin-react) and add `plugin:react/recommended` & `plugin:react/jsx-runtime` to the `extends` list
