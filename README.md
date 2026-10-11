# updates

Public downloads and update feeds for Kirill Prudnikov's Mac apps (Dictum, Textum, Cliplark, Shotlark, Note Calc).
No source code here — only release builds, update feeds and the signed licensing policy. Served by GitHub Pages at
`https://updates.kvp-projects.com/` (the `CNAME` file).

| Path | What it is |
|---|---|
| `<app>/appcast.xml` | [Sparkle](https://sparkle-project.org) update feed of a Swift app (`dictum`, `textum`, `cliplark`, `shotlark`) |
| `note-calc/latest.json` | Note Calc's update feed (Tauri updater) |
| `policy.json` + `policy.json.sig` | the licensing policy every app reads once a day (status of each app: beta / paid, revoked keys), signed with the shelf's Ed25519 key |
| `CNAME`, `index.html`, `.nojekyll` | GitHub Pages settings and a placeholder page |

Builds are the **Releases** of this repository, tagged `<app>-<version>` (e.g. `dictum-0.3.0`): a notarized DMG and
the update archive. Every update is signed with the apps' update key (checked by Sparkle / the Tauri updater) and
with Apple's Developer ID, notarized by Apple.

`policy.json` is never edited by hand alone: any change must be signed again (`license-tool sign-policy` /
`license-tool revoke` in the private `mac-app-kit`), otherwise the apps ignore it. Its `serial` grows with every edit; an app never goes back to a smaller one.
