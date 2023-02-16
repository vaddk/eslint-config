# @vaddk/eslint-config

- Одинарные кавычки, без точки запятой
- Автоматическое форматирование кода при сохранении (предназначено для использования)
- Разработан для работы с Vue + Typescript (есть fallback под js)
- Lint json, yaml, markdown
- Сортировка импортов, висячие запятые

## Установка

```bash
pnpm add -D eslint @vaddk/eslint-config
```

## Конфиг `.eslintrc`

```json
{
  "extends": "@vaddk/eslint-config"
}
```

> `.eslintignore` не нужен, настройки учтены в конфиге.

## Добавление скрипта в package.json

```json
{
  "scripts": {
    "lint": "eslint .",
    "lint:fix": "eslint . --fix"
  }
}
```

## Настройка VS Code

Необходимо установить [VS Code ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) и создать `.vscode/settings.json` в корне проекта.

```json
{
  "prettier.enable": false,
  "editor.formatOnSave": false,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  }
}
```

## Изменение правил TypeScript

Изменить правила линтинга TypeScript можно, добавив файл `tsconfig.eslint.json` в корень проекта, и указав в нем необходимые правила. Если вы хотите использовать более строгие правила линтинга TypeScript, не создавая файл `tsconfig.eslint.json`, вы можете изменить переменную окружения `ESLINT_TSCONFIG`, указав в ней название текущего конфигурационного файла ts. 

```js
// .eslintrc.js
process.env.ESLINT_TSCONFIG = 'tsconfig.json'

module.exports = {
  extends: '@vaddk/eslint-config'
}
```