## typedoc-plugin-monorepo error reproduction case

```
npm i
npm run generate
```

Go to ./docs/classes

There will be `test1.AnotherNormal.html` and `test1.Normal.html`, but no `test1.Problem.html`

Go to packages/test1/src/index.ts and remove line: `export * from './problem/Problem';`.  
After new generation `test1.Problem.html` will appear.