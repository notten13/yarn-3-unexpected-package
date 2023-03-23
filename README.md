# Unexpected package installed by Yarn 3

This is a minimal repository to try and reproduce an issue I spotted with Yarn 3.

The only dependency in this repository is `got@^9`. Neither this package nor any of its dependencies declare a dependency on the package `@types/keyv`, as can be seen in the `yarn.lock` file. However, `@types/keyv` is always installed by Yarn 3.

`yarn why -R @types/keyv` shows the following output:

```
└─ root-workspace-0b6124@workspace:.
   └─ got@npm:9.6.0 (via npm:^9)
      └─ @types/keyv@npm:3.1.4 (via npm:^3.1.1)
```

The extraneous package is not installed when using NPM or Yarn version 1.
