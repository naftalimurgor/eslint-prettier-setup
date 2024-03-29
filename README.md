# Introduction

What is **Linting?**: this is an automatic analysis of source code to find programmatic errors and stylistic errors.

What does prettier do? Prettier does exactly what the name suggests: it makes our code neat and with a consistent style.

Combining a linter(Eslint) and Prettier makes our code more cleaner and with fewer errors.
This makes our code read like prose and consistency.

Let's dive right in!

## Setup

Inside your project, run:

### 1. Install Eslint

```sh
npm i --save-dev eslint
```

### 2. Choose style

Generate the config(specify a desired style), or chose any popular style guide :wink:

```sh
npx eslint --init
```

Gives the following output in form of a prompt:

```sh
$ npx eslint --init
✔ How would you like to use ESLint? · style
✔ What type of modules does your project use? · none
✔ Which framework does your project use? · none
✔ Does your project use TypeScript? · No / Yes
✔ Where does your code run? · browser, node
✔ How would you like to define a style for your project? · prompt
✔ What format do you want your config file to be in? · JavaScript
✔ What style of indentation do you use? · 4
✔ What quotes do you use for strings? · single
✔ What line endings do you use? · unix
✔ Do you require semicolons? · No / Yes
The config that you've selected requires the following dependencies:

@typescript-eslint/eslint-plugin@latest @typescript-eslint/parser@latest
Installing @typescript-eslint/eslint-plugin@latest, @typescript-eslint/parser@latest
```

### 3. Prettier setup

Add `prettier`:

```sh
npm install -D prettier
```

Add the following devDependency to enable `Prettier` and `Eslint` to work together:

```sh
npm i --save-dev @typescript-eslint/parser
```

- Our `.prettierrc` config in the project root:

```javascript
// .pettierrc.json
{
  "semi": false, // Specify if you want to print semicolons at the end of statements
  "singleQuote": true, // If you want to use single quotes
  "arrowParens": "avoid", // Include parenthesis around a sole arrow function parameter
}
```

Add setup so Eslint can lint our code while `prettier` makes our code pretty as per the style chosen.

## DevDependencies- Eslint and prettier

1. `eslint`: ESLint core library
2. `@typescript-eslint/parser`: A parser that allows ESLint to understand TypeScript code
3. `@typescript-eslint/eslint-plugin`: Plugin with a set of recommended TypeScript rules
4. `prettier`: - this adds prettier to our project to be able to make our code cleaner

### 4. Integrate `Eslint` to whatever editor you are using:

1. Integrate `Eslint` with your code editor you are using, for Vscode, we use the [Eslint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) vscode extension.

2. Navigate to settings > edit `settings.json` and add the following to override the default JavaScript Formatter and use `Prettier` instead:

3. Add the prettier extenstion for Vscode, from [marketplace](https://open-vsx.org/extension/eamodio/gitlens)

```javascript
{
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true,
  ...
}
```

## Update `package.json`

```javascript
{
  scripts: {
    ...
    "build:module": "tsc -p tsconfig.module.json",
    "lint": "eslint --ext .ts . ",
    ...
  }
}
```

And we are good to go!
