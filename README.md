Example project to reproduce [lint-staged](https://github.com/okonet/lint-staged) stuck using [rubocop Server Mode](https://docs.rubocop.org/rubocop/1.50/usage/server.html).

### How to reproduce

```console
npm install
bundle install
touch foo && git add foo
git commit --allow-empty -m 'test'
bundle exec rubocop --start-server
touch bar && git add bar
git commit --allow-empty -m 'test2'
```

```console
❯ git commit --allow-empty -m 'test2'
✔ Preparing lint-staged...
❯ Running tasks for staged files...
  ❯ .lintstagedrc — 1 file
    ❯ * — 1 file
      ⠴ bundle exec rubocop --version
◼ Applying modifications from tasks...
◼ Cleaning up temporary files...
```

### Environment
- OS: macOS 13.3.1 (a)
- Node.js: v18.16.0
- lint-staged v13.2.2
- execa v7.1.1
- rubocop v1.50.2
