### Node Projects

```sh
npm install --save-dev eslint @slothfish/eslint-config eslint-plugin-import eslint-plugin-jest eslint-plugin-node eslint-plugin-promise eslint-plugin-you-dont-need-lodash-underscore
```

然后在package.json中设置ESLint配置:

```json
"eslintConfig": {
  "extends": "@slothfish/eslint-config/node"
}
```

如果你的项目没有package.json，也可以在根文件' .eslintrc '中:

```json
{
  "extends": "@slothfish/eslint-config/node"
}
```

或者在名为' .eslintrc.cjs '的根文件中:

```js
module.exports = {
  extends: "@slothfish/eslint-config/node",
};
```

### React Projects - Javascript

```sh
npm install --save-dev eslint @slothfish/eslint-config eslint-plugin-import eslint-plugin-jest eslint-plugin-promise eslint-plugin-you-dont-need-lodash-underscore eslint-plugin-jsx-a11y eslint-plugin-react eslint-plugin-react-hooks
```

然后在package.json中设置ESLint配置:

```json
"eslintConfig": {
  "extends": "@slothfish/eslint-config/browser-react"
}
```

如果你的项目没有package.json，也可以在根文件' .eslintrc '中:

```json
{
  "extends": "@slothfish/eslint-config/browser-react"
}
```

或者在名为' .eslintrc.cjs '的根文件中新增:
```js
module.exports = {
  extends: "@slothfish/eslint-config/browser-react",
};
```

### React Projects - Typescript

```sh
npm install --save-dev eslint @slothfish/eslint-config eslint-plugin-import eslint-plugin-promise eslint-plugin-you-dont-need-lodash-underscore eslint-plugin-jsx-a11y eslint-config-react-app @typescript-eslint/eslint-plugin @typescript-eslint/parser
```

然后在package.json中设置ESLint配置:

```json
"eslintConfig": {
  "extends": "@slothfish/eslint-config/browser-react-ts"
}
```

如果你的项目没有package.json，也可以在根文件“。eslintrc”中

```json
{
  "extends": "@slothfish/eslint-config/browser-react-ts"
}
```

或者修改 `.eslintrc.cjs`:

```js
module.exports = {
  extends: "@slothfish/eslint-config/browser-react-ts",
};
```

### Projects with Node and React
```json
{
  "extends": [
    "@slothfish/eslint-config/browser-react",
    "@slothfish/eslint-config/node"
  ]
}
```
### node.js
- `parser: "espree"`: 将 JavaScript 代码字符串转换成 AST，静态代码分析的基础设施，可以为代码质量检查、代码重构、代码转换等工具提供支持。
- `extends: []`: 用于继承其他 ESLint 配置。可以继承这些配置文件中的所有规则,可以更容易地编写符合规范的代码，同时也可以遵循最佳实践。
    - `plugin:jest/recommended`: 适用于 Jest 测试框架的推荐配置
    - `plugin:node/recommended`: 适用于 Node.js 环境的推荐配置
    - `plugin:promise/recommended`: 适用于 Promise 的推荐配置，包括了常见的 Promise 规则

  需要注意的是，在继承了多个插件的推荐配置时，可能会存在重复规则的情况。如果同一个规则在不同的插件配置中出现了，那么`它的值将取决于最后一个配置文件中定义的值`。因此，如果你想修改某个规则的默认值，你需要确保在最后一个配置文件中重新定义该规则。另外，当你继承多个配置文件时，你需要注意这些配置文件之间的依赖关系，以确保它们不会相互冲突或产生副作用。
- `env: {}`: 用于指定代码所运行的环境。
  - `es6: true`: 表示代码运行在 ECMAScript 6（即 ES2015）环境下，这意味着你可以使用 ES6 中新增的语言特性，例如箭头函数、类、const 和 let 变量声明等。通过设置这个选项，ESLint 将会预定义 ES6 中的全局变量和函数，例如 Promise、Map 和 Set 等。

  - `jest/globals: true`: 表示代码运行在 Jest 测试框架下，这意味着你可以使用 Jest 提供的全局函数和变量，例如 describe、test 和 expect。通过设置这个选项，ESLint 将会预定义 Jest 中的全局变量和函数。

  - `node: true`: 表示代码运行在 Node.js 环境下，这意味着你可以使用 Node.js 提供的全局变量和函数，例如 require、module 和 process。通过设置这个选项，ESLint 将会预定义 Node.js 中的全局变量和函数。

  在 ESLint 中，每个环境都有一组预定义的全局变量和函数，这些变量和函数在该环境下是可用的。

  例如，在 `Node.js` 环境下，你可以使用全局变量 `require`、`module` 和 `exports`，而在`浏览器环境`下，你可以使用全局变量 `document`、`window` 和 `navigator`。通过设置 `env 配置项`，你可以告诉 ESLint 代码所运行的环境，以便它正确地解析和检查你的代码。
- `parserOptions: {}`: 用于指定解析器的选项，告诉 ESLint 解析器如何解析和处理代码
  - `ecmaVersion: 2020`: 指定使用 ECMAScript 2020 版本的语法解析器。通过设置这个选项，ESLint 将会使用支持 ECMAScript 2020 语法的解析器来解析代码。这意味着你可以使用 ECMAScript 2020 中新增的语言特性，例如可选链式调用、nullish 合并、动态 import 等。

  - `ecmaFeatures: { impliedStrict: true }`: 启用 impliedStrict 模式。impliedStrict 模式是一种 JavaScript 严格模式的变种，它可以在代码中隐式地启用严格模式。具体来说，当你在代码中使用了严格模式中新增的语言特性，例如 let、const、class、箭头函数等，ESLint 将会自动启用严格模式。通过启用 impliedStrict 模式，你可以确保代码始终在严格模式下运行，从而避免一些常见的错误和不良实践，例如意外创建全局变量、不能删除不可删除的属性等。
- `plugins: []`: 用于加载 ESLint 插件(一组规则的集合)
  - `import`: 与模块导入和导出相关的插件，提供了一组模块导入和导出的规则，例如禁止未使用的导入、强制使用特定的导入方式等。

  - `jest`: 与 Jest 测试框架相关的插件，提供了一组用于编写 Jest 测试的规则，例如禁止使用 toBe 和 toEqual、鼓励使用 expect.assertions 等。

  - `promise`: 与 Promise 相关的插件，提供了一组用于编写 Promise 的规则，例如禁止使用 new Promise、鼓励使用 Promise.all 等。

  在 `ESLint` 中，插件是一组规则的集合，它们通常与具体的技术栈、框架或库有关。例如，`eslint-plugin-import` 插件提供了一组与模块导入和导出相关的规则，而 `eslint-plugin-jest` 插件提供了一组与 `Jest` 测试框架相关的规则。通过加载这些插件，你可以使用这些插件提供的规则，以便你可以更容易地编写符合规范的代码，同时也可以遵循最佳实践。
- `rules: {}`: 用于检查 JavaScript 代码的语法和风格是否符合一定的标准,这些规则按照 ESLint 的机制被分类为 "error"、"warn"、"off" 三种等级，分别表示错误、警告和关闭。
  1. `"array-bracket-spacing": ["error", "never"]`: 要求数组元素周围没有空格。
  2. `"array-callback-return": ["error", {allowImplicit: true}]`: 强制数组方法的回调函数中有 return 语句，并且允许隐式的 return 语句。
  3. `"arrow-body-style": ["error", "as-needed", {requireReturnForObjectLiteral: false}]`: 要求箭头函数体使用大括号并且不强制返回对象字面量。
  4. `"arrow-parens": ["error", "always", {requireForBlockBody: true}]`: 要求箭头函数的参数使用括号，并且在函数体是一个块时要求使用括号。
  5. `"arrow-spacing": ["error", {after: true, before: true}]`: 要求箭头函数的箭头前后有空格。
  6. `"block-scoped-var": "off"`: 禁止在块级作用域外部使用变量声明。
  7. `"block-spacing": ["error", "always"]`: 要求代码块前后有空格。
  8. `brace-style": ["error", "1tbs", {allowSingleLine: true}]`: 要求大括号的风格使用 "1tbs" 风格（即左大括号在代码块的同一行，右大括号在代码块末尾新起一行），并且允许单行代码块省略大括号。
  9. `"camelcase": ["error", {properties: "never"}]`: 要求使用驼峰式命名变量和属性，但允许属性名中包含下划线。
  10. `"comma-dangle": ["error", "always-multiline"]`: 要求多行代码中对象和数组最后一个元素后有逗号，但是单行代码中不允许有逗号。
  11. `"comma-spacing": ["error", {before: false, after: true}]`: 要求逗号前没有空格，逗号后有一个空格。
  12. `"comma-style": ["error", "last"]`: 要求逗号在行末。
  13. `"complexity": ["error", 20]`: 限制函数的复杂度不能超过 20（指的是函数中包含的独立路径的数量）。如果一个函数中包含的独立路径（分支）数量超过 20，就会被标记为错误。
  14. `"computed-property-spacing": ["error", "never"]`: 要求数组和对象中不使用空格。
  15. `"consistent-return": "off"`: 要求函数的返回值类型保持一致。在这个配置中，该规则被关闭。

  16. ...
