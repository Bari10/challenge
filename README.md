# tf1-thumbnail

This repository demonstrates the implementation of a thumbnail component across web, Storybook, Stencil, React Native, and documentation for feature demonstration and integration.

- [tf1-thumbnail](#tf1-thumbnail)
  - [Component Library](#component-library)
    - [Prerequisites](#prerequisites)
    - [Setup component-library and run thumbnail component in Storybook locally](#setup-component-library-and-run-thumbnail-component-in-storybook-locally)
    - [Troubleshooting](#troubleshooting)
  - [Documentation Site](#documentation-site)
    - [To run locally](#to-run-locally)


## Component Library

### Prerequisites
- Node.js `18.19.0` - Install via [nvm](https://github.com/nvm-sh/nvm) or [Node.js downloads](https://nodejs.org/)
- yarn - `4.2.2`
- corepack - Included with node 16+

### Setup component-library and run thumbnail component in Storybook locally

1. `cd component-library/packages/web-components/`
   1. `yarn install`
   2. `yarn build`
   3. `yarn watch:stencil` (optional)
2. `cd ../core/`
   1. `yarn install`
   2. `yarn build`
3. `cd ../mobile-components/`
   1. `yarn install`
   2. `yarn storybook`

This will allow you to run Storybook locally to view and develop components at `http://localhost:6006/`, where you can see the thumbnail component in action.

### Troubleshooting

If you encounter errors related to Yarn versions, ensure Corepack is enabled and using the correct Yarn version:

```
corepack enable
corepack prepare yarn@4.2.2 --activate
```

If issues persist, check your Node version:
```
node -v
```

If using nvm, switch to the correct Node version:
```
nvm use 18.19.0
```

Then try running the install again:
```
yarn install
```

##  Documentation Site

### To run locally

Tested using `node` v18.19.0 and `yarn` v1.22.19

1. **Install dependencies**

   ```
   $ cd vets-design-system-documentation
   $ yarn install (only once)
   ```

2. **[Install Jekyll](https://jekyllrb.com/docs/installation/)**

   **NOTE:** This repo works with Ruby version 3.0.2.

3. **Install Ruby gems**

   ```
   $ bundle install
   ```

4. **Build and start the Jekyll server**

   ```
   $ yarn start
   ```

5. **Verify in browser: [localhost:4000](http://localhost:4000/)**

6. **Start the Storybook server for component previews**

In a new terminal window, navigate to the `storybook` directory and run:

   ```
   $ cd ../component-library/packages/storybook
   $ yarn install (only once)
   $ yarn static-storybook-server
   ```

8. **Verify Storybook is running: [localhost:8080](http://localhost:8080/)**