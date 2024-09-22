# How to Update npm packages

To update all your packages to their latest versions, you can use the `npm-check-updates` package. Here are the steps:

1. Install the `npm-check-updates` package globally by running the following command:

```bash
npm install -g npm-check-updates
```

2. Run the following command to update all your packages to their latest versions:

```bash
ncu -u
```

3. Finally, run the following command to install the updated packages:

```bash
npm install
```

This will update your package.json with the latest versions of all dependencies and install them.
