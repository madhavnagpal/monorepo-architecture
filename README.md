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
