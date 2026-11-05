# TikTok

## Skills

### huashu-motion

[huashu-motion](https://github.com/alchaincyf/huashu-motion) (MIT) makes motion graphics, launch films and explainers as editable HTML + GSAP code, renders them in your local Chrome, writes a score and sound effects, and lets you point at a frame in a browser studio to change it.

- Skill: `.claude/skills/huashu-motion` (a symlink, so Claude Code picks it up in this repo)
- Code: `vendor/huashu-motion`, vendored from upstream commit `52467f99c602b76ba86d511d37acdfe93fa1e16e` (v0.3.1, 2026-10-22). It holds what the npm package ships (`cli`, `studio`, `runtime`, `templates`, `fonts`, `examples`, `skills`) plus the license and READMEs. Upstream's `docs/` media, tests and site are left out.

The CLI is vendored because the npm release (`npx huashu-motion`, 0.1.1) is older than the skill. The skill's `bin/om` finds the vendored CLI on its own.

Ask Claude something like "make a 15 s 9:16 intro for my fishing channel with /huashu-motion", or run the CLI yourself:

```sh
.claude/skills/huashu-motion/bin/om doctor
.claude/skills/huashu-motion/bin/om demo
```

Requirements: Node 22+, Chrome/Chromium/Edge, FFmpeg. `om doctor` lists what is missing.

#### Updating

```sh
git clone --depth 1 https://github.com/alchaincyf/huashu-motion /tmp/huashu-motion
rm -rf vendor/huashu-motion && mkdir -p vendor/huashu-motion
git -C /tmp/huashu-motion archive HEAD cli studio runtime templates fonts examples skills LICENSE THIRD_PARTY.md package.json README.md README.en.md | tar -x -C vendor/huashu-motion
```

Then update the commit hash above.
