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

