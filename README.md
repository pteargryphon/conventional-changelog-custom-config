<h1 align="center">conventional-changelog-custom-config</h1>
<p>
  <a href="https://github.com/pteargryphon/conventional-changelog-custom-config#readme">
    <img alt="Documentation" src="https://img.shields.io/badge/documentation-yes-brightgreen.svg" target="_blank" />
  </a>
  <a href="https://github.com/pteargryphon/conventional-changelog-custom-config/blob/master/LICENSE">
    <img alt="License: MIT" src="https://img.shields.io/badge/License-MIT-yellow.svg" target="_blank" />
  </a>
</p>

> This preset extends the [conventional-changelog-angular](https://github.com/conventional-changelog/conventional-changelog/blob/master/packages/conventional-changelog-angular/README.md) preset

### Differences to [conventional-changelog-angular](https://github.com/conventional-changelog/conventional-changelog/blob/master/packages/conventional-changelog-angular/README.md)

- 使用 **redmine** 或者其他工具管理项目，可以将 GitHub/GitLab 的 **issues** 地址替换成 **bugsUrl** 中的地址
- 显示 commit 对应的**提交人**及**邮箱地址**
- 使用 **emojis**

前置插件准备

- [commitizen](https://github.com/commitizen/cz-cli) 针对开发者简单的 commit 规范
- [cz-conventional-changelog](https://github.com/commitizen/cz-conventional-changelog) 使用 cz-conventional-changelog 的构建标准
- [conventional-changelog-cli](https://github.com/conventional-changelog/conventional-changelog/tree/master/packages/conventional-changelog-cli#readme) conventional-changelog 核心模块
- 这里我使用 [release-it](https://github.com/release-it/release-it#readme) 作为发布版本插件，也可以选择 [standard-version](https://github.com/conventional-changelog/standard-version)

```sh
npm i commitizen cz-conventional-changelog conventional-changelog-cli --save-dev

npm install --save-dev release-it
```

```sh
npm install conventional-changelog-custom-config --save-dev
```

## Configuration

在 package.json 中配置参数

### 不填配置的话则会按照 angular 的预设模版生成 CHANGELOG

```json
{
  "scripts": {
    "commit": "git-cz && git push",
    "release": "release-it",
    "changelog": "conventional-changelog -p custom-config -i CHANGELOG.md -s -r 0"
  },
  "repository": {
    "type": "git",
    "url": "https://github.com/example.git"
  },
  "config": {
    "commitizen": {
      "path": "cz-conventional-changelog"
    }
  },
  "changelog": {
    "bugsUrl": "https://redmine.example.com/issues/",
    "emojis": true,
    "authorName": true,
    "authorEmail": true
  }
}
```

**bugsUrl**

Type: `string` Default: `false`

当你需要将 issues URL 替换成其他 URL 时，使用该参数，例如使用 **redmine** 管理项目, `bugsUrl: 'https://redmine.example.com/issues/'`

如果不填 `bugsUrl` 则会根据 **package.json** 中的 `repository.url` 来作为 issues URL

如果你使用了第三方的协作系统（例如 **bitbucket**）， 推荐你使用这个插件 [conventional-changelog-angular-bitbucket](https://github.com/uglow/conventional-changelog-angular-bitbucket)

**emojis**

Type: `boolean` Default: `false`

### emojis types 参考 [gitmoji](https://gitmoji.carloscuesta.me/)

| Commit Type | Title                    | Description                                                                                                 | Emojis |
| ----------- | ------------------------ | ----------------------------------------------------------------------------------------------------------- | ------ |
| `feat`      | Features                 | A new feature                                                                                               | ✨      |
| `fix`       | Bug Fixes                | A bug Fix                                                                                                   | 🐛     |
| `docs`      | Documentation            | Documentation only changes                                                                                  | 📝     |
| `style`     | Styles                   | Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc)      | 💄     |
| `refactor`  | Code Refactoring         | A code change that neither fixes a bug nor adds a feature                                                   | ♻️     |
| `perf`      | Performance Improvements | A code change that improves performance                                                                     | ⚡️     |
| `test`      | Tests                    | Adding missing tests or correcting existing tests                                                           | ✅      |
| `build`     | Build                    | Changes that affect the build system or external dependencies (example scopes: gulp, broccoli, npm)         | 👷     |
| `ci`        | Continuous Integrations  | Changes to our CI configuration files and scripts (example scopes: Travis, Circle, BrowserStack, SauceLabs) | 🔧     |
| `chore`     | Chores                   | Other changes that don't modify src or test files                                                           | 🎫     |
| `revert`    | Reverts                  | Reverts a previous commit                                                                                   | ⏪      |

**authorName**

Type: `boolean` Default: `false`

在 CHANGELOG 中生成用户名

**authorEmail**

Type: `boolean` Default: `false`

在 CHANGELOG 中生成邮箱

## Usage

生成 CHANGELOG 之前得**先** commit，记得在 **master** **主分支**上发布版本，再生成 CHANGELOG，流程如下：

```sh
git add .

npm run commit

npm run release

npm run changelog
```

## Examples

![](https://raw.githubusercontent.com/pteargryphon/blog-img/master/img/vue-admin/20190710133722.png)

## Show your support

如果感觉不错，给个 Star 吧~

Give a ⭐️ if this project helped you!

## 📝 License

Copyright © 2019 [zengshunhao](https://github.com/pteargryphon).<br />
This project is [MIT](https://github.com/pteargryphon/conventional-changelog-custom-config/blob/master/LICENSE) licensed.

## Thanks

Thanks to [conventional-changelog](https://github.com/conventional-changelog/conventional-changelog)
