<!-- header:begin (generated from project metadata) -->
<h1 align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/seb5594/Home-Assistant-Renovate-App/main/renovate/dark_logo@2x.png">
    <img src="https://raw.githubusercontent.com/seb5594/Home-Assistant-Renovate-App/main/renovate/logo@2x.png" alt="Renovate" width="360" height="90">
  </picture>
</h1>

<p align="center">
  <a href="https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2Fseb5594%2FHome-Assistant-Apps"><img src="https://img.shields.io/static/v1?label=Home%20Assistant&amp;message=Add%20app%20repository&amp;color=18BCF2&amp;logo=homeassistant&amp;logoColor=white&amp;style=for-the-badge" alt="Home Assistant" height="28"></a><br>
  <a href="https://github.com/seb5594/Home-Assistant-Renovate-App/releases/tag/2026.11.22"><img src="https://img.shields.io/static/v1?label=app%20version&amp;message=2026.11.22&amp;color=1877A5&amp;style=for-the-badge" alt="app version" height="28"></a>
  <img src="https://img.shields.io/static/v1?label=image%20pulls&amp;message=65&amp;color=1877A5&amp;style=for-the-badge" alt="image pulls" height="28"><br>
  <img src="https://img.shields.io/static/v1?label=stage&amp;message=experimental&amp;color=2F855A&amp;style=flat" alt="stage" height="20">
  <img src="https://img.shields.io/static/v1?label=ingress&amp;message=enabled&amp;color=7C3AED&amp;style=flat" alt="ingress" height="20">
  <img src="https://img.shields.io/static/v1?label=arch%20%26%20size&amp;message=amd64%2077.5%20%C2%B7%20aarch64%2077.0%20%C2%B7%20armv7%2073.8%20%C2%B7%20armhf%2075.1%20%C2%B7%20i386%2076.9%20MiB&amp;color=157F71&amp;style=flat" alt="arch &amp; size" height="20">
  <a href="https://github.com/seb5594/home-assistant-base-multi-arch"><img src="https://img.shields.io/static/v1?label=base%20image&amp;message=3.24-2026.11.0&amp;color=1877A5&amp;style=flat" alt="base image" height="20"></a>
  <img src="https://img.shields.io/static/v1?label=mounts%20%28read-only%29&amp;message=addon_config%20%C2%B7%20ssl&amp;color=157F71&amp;style=flat" alt="mounts (read-only)" height="20"><br>
  <a href="https://github.com/seb5594/Home-Assistant-Renovate-App/actions/workflows/ci.yml"><img src="https://img.shields.io/github/actions/workflow/status/seb5594/Home-Assistant-Renovate-App/ci.yml?branch=main&amp;label=checks&amp;style=flat" alt="checks" height="20"></a>
  <img src="https://img.shields.io/static/v1?label=runtime%20tests&amp;message=120%20passed&amp;color=2F855A&amp;style=flat" alt="runtime tests" height="20">
  <a href="https://github.com/seb5594/Home-Assistant-Apps/issues"><img src="https://img.shields.io/github/issues/seb5594/Home-Assistant-Renovate-App?label=issues&amp;style=flat" alt="issues" height="20"></a><br>
  <a href="https://paypal.me/seb5594"><img src="https://img.shields.io/static/v1?label=Support&amp;message=PayPal&amp;color=0070BA&amp;logo=paypal&amp;logoColor=white&amp;style=for-the-badge" alt="PayPal" height="24"></a>
  <a href="https://buymeacoffee.com/seb5594"><img src="https://raw.githubusercontent.com/seb5594/Home-Assistant-Apps/473dc258f963096745aac327df54950eb9b59066/.github/assets/support-beer.svg" alt="Buy me a beer" height="24"></a><br>
  <a href="https://github.com/seb5594/Home-Assistant-Apps#license"><img src="https://img.shields.io/github/license/seb5594/Home-Assistant-Renovate-App?label=license&amp;style=flat" alt="license" height="20"></a>
</p>
<!-- header:end -->

**🇬🇧 English** · [🇩🇪 Deutsch](README.de.md)

> [!WARNING]
> **Experimental.** This app is new and has been tested against a mocked git server, a stand-in for Renovate and the configuration check of the real Renovate, but not yet on many real installations. Expect rough edges, and please report what you find.

Dependencies age quietly: a Docker tag here, a GitHub Action there, a Python package in your custom integration. **Renovate** watches your repositories and opens a pull request whenever something you use has a new version, so updates become a review instead of a chore. This app runs Renovate **on your own Home Assistant**, next to your own git server, with a web interface that needs no command line.

![Overview](docs/images/overview.png)

## Why this app

- **Connecting takes a minute.** Pick your server and sign in the easiest way it allows: a short code for GitHub, your login for Gitea and Forgejo (the app creates a token with exactly the right permissions, your password is never stored), a sign-in on the server's own page for passkeys, YubiKeys and single sign-on, or a pre-filled token page. The Gitea app of Home Assistant is found automatically.
- **GitHub, GitLab, Gitea, Forgejo, Bitbucket, Azure DevOps, Gerrit and SCM-Manager** in one app, any number of accounts side by side. Self-hosted servers, GitHub Enterprise and Codeberg work too.
- **Safe to start.** A *preview run* shows what Renovate would do without changing anything. Repositories are switched on one by one, and Renovate's own "Configure Renovate" pull request has to be merged before it touches a repository.
- **Made for small machines.** One Node.js process that sleeps between runs, SQLite instead of a database server, runs in small batches with a memory limit and low CPU priority. A resource profile is chosen automatically from your memory, so a Raspberry Pi is as welcome as a mini PC.
- **Always the newest Renovate, pinned exactly.** The Renovate version is fixed in the image. A new Renovate release raises the pin and publishes a new app version by itself, so you get fresh versions without ever running an unpinned image.
- **You decide what merges by itself.** One setting per kind of update (major, minor, patch): a pull request for you, an automatic merge, a question first, or nothing. Four ready-made recipes cover the usual wishes, for example "merge everything except major updates". A built-in guide explains accounts, token permissions and what to do when nothing happens, see [updates and merging](renovate/DOCS.md#updates-what-is-merged-automatically).
- **Event driven when you want it.** Webhooks from your git server start a run a minute after you merge a pull request or tick a box in the Dependency Dashboard, instead of waiting for the schedule.
- **Part of Home Assistant.** Sensors (`sensor.renovate_status`, `sensor.renovate_open_pull_requests`, `sensor.renovate_last_run`), an event after every run and optional failure notifications fit into your automations.
- **Looks like it belongs.** Light and dark mode follow Home Assistant, the accent color is blue, follows your Home Assistant theme or is a color of your choice, and the interface speaks English and German.
- **Transparent.** Every run has a live log, a result per repository (new pull requests, updates found, problems) and plain-language hints for the usual failures: expired token, unreachable server, certificate, rate limit, too little memory.
- **Configurable down to the details.** Every setting is in the web interface *and* in the app configuration; a lock shows which one wins.

| | | |
| --- | --- | --- |
| ![Setup assistant](docs/images/wizard.png) | ![Run details](docs/images/run-detail.png) | ![Repositories, dark mode, German](docs/images/repositories-dark-de.png) |

## Supported git servers

| Server | Sign-in | Notes |
| --- | --- | --- |
| GitHub, GitHub Enterprise Server | Code (device flow) or token | The code sign-in needs an OAuth app, see [setting up the code sign-in](renovate/DOCS.md#sign-in-with-a-code-github) |
| GitLab, self-managed GitLab | Token (pre-filled page) or **browser sign-in** | The browser sign-in works with single sign-on; the app renews the short-lived tokens |
| Gitea | Password (creates a token), **browser sign-in (passkey, YubiKey, SSO)** or token | The Home Assistant Gitea app is detected |
| Forgejo, Codeberg | Password (creates a token), **browser sign-in** or token | |
| Bitbucket Cloud | User name and API token | Beta |
| Bitbucket Server / Data Center | HTTP access token | Beta |
| Azure DevOps (Services and Server) | Personal access token | Beta |
| Gerrit | User name and HTTP password | Beta, experimental in Renovate |
| SCM-Manager 3 | API key | Beta, experimental in Renovate |

The **browser sign-in** is the way for accounts that are protected by a passkey or a security key such as a YubiKey 5 NFC: you sign in on your server's own page, where those work exactly as usual, and the app never sees a password. It needs a one-time registration of the app on the server and no public address, see [Browser sign-in](renovate/DOCS.md#browser-sign-in-passkey-yubikey-sso).

The servers marked **Beta** were built from Renovate's documentation and tested against recorded API answers, not against real installations. Please report what does not work. They have no webhooks; the schedule starts their runs. AWS CodeCommit is not supported: its requests need AWS signatures, which would add a large dependency.

## Quick start

1. Add this repository to Home Assistant: **Settings → Apps → App store → ⋮ → Repositories**, then paste `https://github.com/seb5594/Home-Assistant-Apps`.
2. Install **Renovate**, start it and open the web interface (it also appears in the sidebar).
3. Press **Connect a git server** and follow the four steps.
4. Start with a **preview run**. When the result looks right, press **Run now**.
5. Open the "Configure Renovate" pull requests in your repositories and merge them. From then on Renovate keeps the repositories current.

The first run in a repository without configuration only opens the onboarding pull request. Nothing else changes before you merge it.

## How it relates to Mend Renovate CE

Mend publishes a "Community Edition" server of Renovate. This app deliberately does **not** wrap it, for reasons that matter to you:

| | Mend Renovate CE | This app (open-source Renovate) |
| --- | --- | --- |
| Git servers | GitHub, GitLab, Bitbucket Server | GitHub, GitLab, **Gitea, Forgejo**; Bitbucket and others possible |
| License | Proprietary, Mend terms of service, license key required | Renovate is AGPL-3.0, this app is MIT, no key |
| Redistribution | The image must not be bundled into other images | Bundled unmodified with the AGPL notices |
| Runs on | Debian based image | Alpine, tuned for Home Assistant |

The part that makes CE a "server" (schedule, job queue, webhooks, status) is what this app adds around the open-source Renovate, so you do not need two products. If you rely on Mend-only features (Merge Confidence, Mend Remediate), use Mend's own image.

## Performance and resources

| Profile | Chosen for | Parallel runs | Memory per run | Repositories per batch | CPU priority |
| --- | --- | --- | --- | --- | --- |
| Light | up to 2 GB RAM, Raspberry Pi | 1 | 512 MB | 3 | 15 (very polite) |
| Balanced | 2 to 6 GB | 1 | 1 GB | 10 | 10 |
| Performance | more than 6 GB | 2 | 2 GB | 25 | 5 |

- Between runs the app is a single idle Node.js process, roughly 80 MB. There is no polling: one timer waits for the next run.
- Renovate runs only while a run is active, in batches, so memory is given back after each batch. Every value can be overridden.
- The web interface has no framework and no build step: a few small files, compressed once and cached by the browser. Pages refresh only while visible, and only a running run keeps a live connection.
- The image is a few hundred MB, because Renovate itself is large even after development files are removed (about 185 MB of the installed package).

## Honest limits

- **Experimental.** See the notice at the top.
- **Architectures:** the app is built for amd64, aarch64, armv7, armhf and i386, like the base image. Only amd64 and aarch64 are used by the author; the 32-bit builds are untested, and Renovate needs a lot of memory, so expect them to be slow on small boards.
- **Pull requests come from the account you connect.** Use a dedicated "renovate" account for a clean history. A GitHub App or GitLab bot token can be pasted as a token as well.
- **Tokens from the browser sign-in expire** after an hour (Gitea) or two (GitLab). The app renews them before every run; if a server revokes the sign-in, the connection has to be added anew.
- **Lock files of non-JavaScript projects** need their tools. The image ships Node.js, npm and Git; add `python3`, `py3-pip`, `go` and others under *Extra system packages* when your repositories need them. Docker-in-Docker (`binarySource: docker`) is not available.
- **Regular expression safety net removed.** Renovate's optional `re2` engine is not part of the image, so Renovate uses the built-in engine. This only matters if you let untrusted people change the Renovate configuration of your repositories.
- **Webhooks need a reachable address.** Without a public URL (reverse proxy, tunnel) the schedule does the work, which is perfectly fine for most homes.
- **Sensors are not registry entities.** They disappear when Home Assistant restarts until the next update of the app, which happens within seconds of its start.
- **One user.** Access is controlled by Home Assistant (by default administrators only). There are no separate accounts in the app.
- **The server runs with the rights of the container.** Home Assistant keeps the app configuration readable for root only, and the app follows it live. Renovate itself, which runs package managers on your repositories, always starts as an unprivileged user.

## Updates and versions

Versions are calendar based: `YYYY.MM.DD` for the first build of a day, then `.1`, `.2`, and so on. The pinned Renovate version and the Alpine packages are updated automatically by the release pipeline; the [changelog](renovate/CHANGELOG.md) says what changed. Pre-built images are published to the GitHub container registry for both architectures.

## Documentation

The [app documentation](renovate/DOCS.md) lists every option and explains the sign-in methods, webhooks, certificates, extra tools and troubleshooting.

## Contributing

The code is small on purpose and written to be read:

```text
renovate/rootfs/opt/renovate-app/
  server/providers/     one file per git server
  server/runs/          queue, runner, resource profiles, report parsing
  server/settings/      the registry that drives validation, the interface and the configuration
  ui/                   the web interface (plain JavaScript modules, no build step)
tools/                  dev server with a fake Gitea, config and picture generators
.github/tests/unit/     tests (node --test), also run inside the built image
```

```bash
node --disable-warning=ExperimentalWarning --test '.github/tests/unit/*.test.mjs'
node --disable-warning=ExperimentalWarning tools/dev-server.mjs
```

`tools/sync-config.mjs` regenerates `config.yaml` and the translations from the settings registry; a test fails when they differ. New settings, texts and providers are described in the headers of the files they belong to.

<!-- support:begin (generated, shared text) -->
## Say thanks

All my projects are built in my spare time, just for the fun of it. Still, they take a lot of time and care, and many of the smart home gadgets I buy end up here because I want to make them cloud-free and smart-home ready. Every bit of support means a lot to me.

If my work helped you or turned out to be useful, show your appreciation with a hot drink for my next sleepless night.

[![PayPal](https://img.shields.io/static/v1?label=Support&message=PayPal&color=0070BA&logo=paypal&logoColor=white&style=for-the-badge)](https://paypal.me/seb5594) [![Buy me a beer](https://raw.githubusercontent.com/seb5594/Home-Assistant-Apps/473dc258f963096745aac327df54950eb9b59066/.github/assets/support-beer.svg)](https://buymeacoffee.com/seb5594)
<!-- support:end -->

<!-- license:begin (generated from the license file) -->
## License

[![license](https://img.shields.io/static/v1?label=license&message=MIT&color=5B6770&style=flat)](LICENSE)

Published under the [MIT License](LICENSE).
<!-- license:end -->
