name: CI Pipeline

on:
  push:
    branches:
      - main  # Trigger CI on pushes to the main branch
  pull_request:
    branches:
      - main  # Trigger CI when a pull request is opened or updated targeting the main branch

jobs:
  test:
    runs-on: ubuntu-latest  # Use the latest Ubuntu runner

    steps:
      - name: Checkout code
        uses: actions/checkout@v2  # Check out the repository code

      - name: Set up Node.js
        uses: actions/setup-node@v2
        with:
          node-version: '14'  # Use Node.js version 14 (change if using another language)

      - name: Install dependencies
        run: npm install  # Run npm install to set up dependencies

      - name: Run linting
        run: npm run lint  # Run linting script (e.g., ESLint)

      - name: Run tests
        run: npm test  # Run your test script (e.g., Jest)
