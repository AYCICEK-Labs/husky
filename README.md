# husky

The Git hooks of AYÇİÇEK Labs Node projects, run by [Husky](https://typicode.github.io/husky).

| Hook                | What it does                                                                                             |
| ------------------- | -------------------------------------------------------------------------------------------------------- |
| `.husky/pre-commit` | Runs [lint-staged](https://github.com/AYCICEK-Labs/lint-staged): formats the staged files with Prettier. |
| `.husky/commit-msg` | Checks the message with [commitlint](https://github.com/AYCICEK-Labs/commitlint).                        |

Projects without a `package.json` have no hooks; their commits are checked in CI.

## Use it in a Node project

The hooks need the configurations of [`prettier`](https://github.com/AYCICEK-Labs/prettier), [`commitlint`](https://github.com/AYCICEK-Labs/commitlint) and [`lint-staged`](https://github.com/AYCICEK-Labs/lint-staged) in the project.

```sh
base=https://raw.githubusercontent.com/AYCICEK-Labs/husky/main/.husky
mkdir -p .husky
curl -fsSL "$base/pre-commit" -o .husky/pre-commit
curl -fsSL "$base/commit-msg" -o .husky/commit-msg
npm install --save-dev husky
npm pkg set scripts.prepare=husky
npx husky
```

`npm install` runs `prepare`, so the hooks are active in every clone after installing.

## License

[MIT](LICENSE) © Yunus Emre AYÇİÇEK
