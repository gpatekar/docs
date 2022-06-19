React unit test setup

#### Quick links
https://app.pluralsight.com/course-player?clipId=1a8ce514-1e63-4bcc-be4b-9190b8ea467b<br />
https://javascript.plainenglish.io/setting-up-testing-library-and-redux-b80a699f0eda<br />
https://medium.com/@jorgeortega/react-forms-with-formik-and-unit-testing-with-react-testing-library-e2dda1a899db<br />
https://www.freecodecamp.org/news/8-simple-steps-to-start-testing-react-apps-using-react-testing-library-and-jest/<br />

## Jest

#### Installation
npm install -g jest-cli
npm install --save jest
<br />

#### Jest Configuration
- Add jest.config.js in test-config folder or root folder.<br />
- Update package.json script with following:<br />
`"jest": "jest --config jest.config.js"`<br />
**Link**: https://jestjs.io/docs/configuration<br />


## Store
Sometimes we have to mock the inital data coming from root store. Store could be redux or the React context library. Follow following steps to mock the server:
- Create test-helper folder in root of the application and add renderer.tsx(File name can be anything of your choice)
- Add following code.
- You will find description on following code here: https://dev.to/bonnie/getting-started-with-redux-and-testing-library-36ln

```
import React, { ReactElement, ReactNode } from 'react';
import { Store } from 'redux';
import { Provider } from 'react-redux';
import { TranslatorContext } from 'react-jhipster';
import { render as rtlRender, RenderOptions } from '@testing-library/react';

import initialize from '../config/store';

import { initialData } from './MockRootData';

interface IReduxRenderOptions {
  preloadedState?: any;
  store?: Store;
  renderOptions?: Omit<RenderOptions, 'wrapper'>;
}

const setTranslation = () => {
  TranslatorContext.registerTranslations('en', {});
};

async function render(
  ui: ReactElement,
  { preloadedState = { ...initialData }, store = initialize(preloadedState), ...renderOptions }: IReduxRenderOptions = {}
) {
  setTranslation();

  function Wrapper({ children }: { children?: ReactNode }): ReactElement {
    return <Provider store={store}>{children}</Provider>;
  }
  return rtlRender(ui, { wrapper: Wrapper, ...renderOptions });
}

// re-export everything
export * from '@testing-library/react';

// override render method
export { render };
```
<br />
<br />

## Mock service worker

#### Installation
npm install msw --dev

#### Setup
- setupTests.ts
Create setupTests.ts file under src folder and add following code<br />
```
// src/setupTests.js
import { server } from './mocks/server';
// Establish API mocking before all tests.
beforeAll(() => server.listen())

// Reset any request handlers that we may add during the tests,
// so they don't affect other tests.
afterEach(() => server.resetHandlers())

// Clean up after the tests are finished.
afterAll(() => server.close())
```
- Creat mocks folder under src folder and add two files **handlers.ts** and **server.ts**
**handlers.ts**
```
import { rest } from "msw";

const scoops = [
  {
    name: "Mint chip",
    imagePath: "/images/mint-chip.png",
  },
  {
    name: "Vanilla",
    imagePath: "/images/vanilla.png",
  },
];

const toppings = [
  {
    name: "M&Ms",
    imagePath: "/images/m-and-ms.png",
  },
  {
    name: "Hot fudge",
    imagePath: "/images/hot-fudge.png",
  },
];

export const handlers = [
  rest.get("http://localhost:3030/scoops", (req, res, ctx) => {
    return res(ctx.json(scoops));
  }),
  rest.get("http://localhost:3030/toppings", (req, res, ctx) => {
    return res(ctx.json(toppings));
  }),
];

```

**server.ts**
```
// src/mocks/server.js
import { setupServer } from 'msw/node'
import { handlers } from './handlers'

// This configures a request mocking server with the given request handlers.
export const server = setupServer(...handlers)
```
