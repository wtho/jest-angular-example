# AngularJest

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 7.3.6.

# Setup

To create the project, the following commands were used:

```bash
ng new angular-jest
cd angular-jest
npm remove @types/jasmine @types/jasminewd2 jasmine-core jasmine-spec-reporter karma karma-chrome-launcher karma-coverage-istanbul-reporter karma-jasmine karma-jasmine-html-reporter protractor
npm install -D jest jest-preset-angular @types/jest
rm -r e2e
rm src/test.ts src/karma.conf.js
```

and the following files have to be created:

## `jest.config.js`
```ts
module.exports = {
  preset: 'jest-preset-angular',
  setupFilesAfterEnv: ['<rootDir>/src/setupJest.ts']
}
```

## `src/tsconfig.spec.json`
```json
{
  "extends": "../tsconfig.json",
  "compilerOptions": {
    "esModuleInterop": true,
    "types": [
      "jest",
      "node"
    ]
  },
  "include": [
    "**/*.spec.ts",
    "**/*.d.ts"
  ]
}
```

## `src/setupJest.ts`
```ts
import 'jest-preset-angular';
import './jestGlobalMocks';
```

## `src/jestGlobalMocks.ts`
```ts
Object.defineProperty(document.body.style, 'transform', {
  value: () => {
    return 
      enumerable: true,
      configurable: true,
    };
  },
});
```

Finally modify the scripts`package.json` to create a new job:
```json
{
  "scripts": {
    "ng": "ng",
    "start": "ng serve",
    "build": "ng build",
    "lint": "ng lint",
    "test": "jest"
  }
}
```

Now the jest can be run using `npm test`.



