# Changelog

## 2026.11.24

* 📦 Update renovatebot/renovate to 44.260.3 (was 44.258.1).

## 2026.11.23

* 📦 Update renovatebot/renovate to 44.258.1 (was 44.257.9).

## 2026.11.22

* 📦 Update renovatebot/renovate to 44.257.9 (was 44.257.8).

## 2026.11.21.2

* 📦 Update renovatebot/renovate to 44.257.8 (was 44.256.1).

## 2026.11.21.1

* 🗑️ Removed: the "Connections" list of the app configuration. Connections are created in the web interface; connections that came from the list stay as ordinary ones. ✨ New: a guide section and documentation for one setup for many repositories (shared preset, recommended settings) and an explanation why a schedule in a repository (for example before 6am on monday) shows issues but no pull requests.

## 2026.11.21

* ✨ New: choose per kind of update (major, minor, patch) whether Renovate opens a pull request, merges it by itself, asks first or skips it, with four ready-made recipes (Settings → Updates and merging). A guide in the web interface explains the account for commits and pull requests, token permissions, moving from the Mend Renovate app and what to do when issues appear but no pull requests. Runs now say why updates were held back. Emojis in the web interface. 🐛 Fixed: pull requests changed by someone else were counted as updated, and the default of Renovate (two new pull requests per hour) held back most updates between runs hours apart; the limit is now off by default. Pull requests of the Mend Renovate app are taken over.

## 2026.11.20.3

* ✨ New: Bitbucket Cloud, Bitbucket Server, Azure DevOps, Gerrit and SCM-Manager (beta), and sign-in through the browser for Gitea, Forgejo and GitLab (passkey, YubiKey, SSO) with automatic renewal of the short-lived tokens. 🐛 Fixed: the app configuration was ignored because Home Assistant keeps it readable for root only; the server now runs with the container's rights and Renovate as an unprivileged user, and an unreadable configuration is reported. The log time no longer wraps on phones, the webhook port is now 5594, and the groups of the configuration page are in a new order.

## 2026.11.20.2

* 🐛 Fixed: the mobile layout was wider than the screen. The resource profile box showed the old profile after a change. Changes in the app configuration now apply within seconds without a restart, and connections that cannot be applied are shown with the reason. New: Settings → App configuration → Compare now, and a "Restart needed" hint for extra packages and certificates.

## 2026.11.20.1

* 🐛 Fixed: the app did not start ("unable to open database file"). The database now lives in its own folder that the app user can write to.

## 2026.11.20

- ✨ First release (experimental). Renovate 44.256.1 with a web interface inside Home Assistant: connect GitHub, GitLab, Gitea or Forgejo, choose repositories, run on a schedule or on webhooks, follow every run live.
