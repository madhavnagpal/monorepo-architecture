# monorepo-architecture

scalable front end architecture

# App built process

1. Created 4 packages using create-react-app

```
npx create-react-app --template=typescript [package-name]
```

2. Delete node_modules and yarn.lock from each package

3. create package.json in root level

```
yarn init
```

4. Add workspace config in package.json

```
{
    "private": true,
    "workspaces": {
        "packages": [
            "packages/*",
        ]
    }
}
```

4. in root install packages

```
yarn install
```

5. Add team-a in main package.json
6. Add react-app-rewired , and react-app-rewire-babel-loader as dev dependincies
7. yarn install
8. replace react-scripts in scripts with react-app-rewired

9. from docs copy config-overrides.js

# Useful commands

1. yarn install
2. yarn workspace [workspace-name] [command-name]
   example

```
yarn workspace main start
```

3. yarn workspaces run [command-name]
   // Running same comman on all packages (example running tests)
4. yarn workspaces info
5. yarn why [package-name]
   to know why dependency in inside or at root level

### Till now we used yarn workspace to build our monorepo, now lets learn a new tool i.e lerna

in simple terms lerna makes managing monorepo easy (we can use yarn workspace and lerna together)

# Adding lerna

1. yarn add -WD lerna
   adding lerna as dev dependency in workspace root level

2. Add lerna.json

```
{
  "npmClient": "yarn",
  "packages": ["packages/*"],
  "version": "1.0.0"
}

```

# Benefits of using lerna over using yarn worspace alone

1. Lerna provides a number of commands that make it easier to manage your monorepo. For example, Lerna has commands for bootstrapping your monorepo, publishing your packages, and managing your versions.
2. Lerna can help you avoid common problems with monorepos, such as dependency conflicts and version mismatches. Lerna has a number of features that help to ensure that your packages are always using the correct versions of their dependencies.
3. Lerna can help you improve your workflow by making it easier to run tasks across all of your packages. For example, Lerna can help you run linters, tests, and builds across all of your packages with a single command.

# Lerna versioning

```
lerna version
```

Two types of versioning

1. locked (same version of each package, and main repo, on each update version of all updates)
2. independent (each package has independent versions)

```
// in locked
"version": "1.0.0" // add initial version, it will increment with each time you use lerna version
// in case of independent
"version": "independent"
```

## versioning based on convention commit

```
yarn lerna version --conventional-commits
```

1. fix -- patch
2. feat -- minor
3. BREAKING_CHANGE -- major

example if u use convention commit in 2 scenarios

### in core

1. if you have fix -> if will release patch of all (+ 0.0.1 to core, team-a, team-b, main)
2. if you add feature -> it will release (+ 0.1 - means release next minor of core, while next patch of team-a, team-b, main (which are dependent on core))

### in main

1. if you release feature -> only release next minor of main
2. if you release fix -> only release next patch of main

# Adding storybook and unit test in component library

In package component-library

1. npx storybook init

// in video needed to be done manually but with v7, its done automatically (step 2,3,4)

2. yarn add @storybook/react -D // basic storybook mechanism customized to react

3. yarn add @storybook/testing-library -D

4. yarn add @storybook/addon-links @storybook/addon-essentials @storybook/addon-interactions -D

on 8:06 mins in video of jack

# These were good, but even greater scalable monorepos are build by nx.dev
