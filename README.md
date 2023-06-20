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