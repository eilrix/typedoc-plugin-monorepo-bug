## typedoc-plugin-monorepo error reproduction case

```
npm i
npm run generate
```

Go to ./docs/classes  

There will be `test1.AnotherNormal.html` and `test1.Normal.html`, but no `test1.Problem.html`  

`Normal` will appear because it wasn't re-exported in `index.ts`. 
But it has exception: if a re-export goes alphabetically before file-exporter, then it will also appear.
`AnotherNormal` goes alphabetically before `index.ts`, so it will appear even it was re-exported.
`Problem` and `MoreProblem` won't show.  

Go to packages/test1/src/index.ts and remove line: `export * from './problem/Problem';`.  
After new generation `test1.Problem.html` will appear.