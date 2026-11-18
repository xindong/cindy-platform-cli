# cindy-platform-cli

Cindy Platform 管理命令行的公开发布仓库。这里只放发布包（见 [Releases](https://github.com/xindong/cindy-platform-cli/releases)），
源码在内部仓库维护，合入后自动发布到这里。使用需要 Cindy Platform 账号与相应权限。

Public release channel for the Cindy Platform admin CLI. This repository only hosts release
artifacts; they are published automatically from the internal source repository. Using the CLI
requires a Cindy Platform account with the relevant permissions.

## 安装 / Install

需要 Node.js 22+ / Requires Node.js 22+.

```bash
# 最新版本 / latest
npm install --global https://github.com/xindong/cindy-platform-cli/releases/latest/download/cindy-platform-cli.tgz

# 指定版本 / a specific version
npm install --global https://github.com/xindong/cindy-platform-cli/releases/download/v<version>/cindy-platform-cli-<version>.tgz

cindy-platform-cli --version
cindy-platform-cli --help
```

升级时重新执行同一条安装命令；卸载 / uninstall：`npm uninstall --global cindy-platform-cli`。

## 校验 / Verify

每个 Release 附 `SHA256SUMS`。Each release ships a `SHA256SUMS` file:

```bash
curl -LO https://github.com/xindong/cindy-platform-cli/releases/latest/download/cindy-platform-cli.tgz
curl -LO https://github.com/xindong/cindy-platform-cli/releases/latest/download/SHA256SUMS
shasum -a 256 -c SHA256SUMS --ignore-missing
npm install --global ./cindy-platform-cli.tgz
```

## 新版本提示 / Update notice

在交互终端中，有新版本时 CLI 会在命令结束后提示升级命令。它只读本地缓存，每天最多在后台查询一次本仓库的
latest release，不影响命令速度；CI、非交互输出时不检查，设置 `CINDY_PLATFORM_CLI_NO_UPDATE_CHECK=1` 可关闭。

In an interactive terminal the CLI prints a one-line upgrade hint when a newer release exists. It reads
a local cache and checks this repository's latest release in the background at most once a day; it never
runs in CI or for piped output. Set `CINDY_PLATFORM_CLI_NO_UPDATE_CHECK=1` to disable it.

## License

[MIT](./LICENSE) © XD Inc.
