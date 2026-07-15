# pi-react-doctor

> React Doctor skill for Pi — your coding agent stops writing bad React.

[![npm](https://img.shields.io/npm/v/pi-react-doctor?color=blue)](https://www.npmjs.com/package/pi-react-doctor)
[![license](https://img.shields.io/npm/l/pi-react-doctor)](LICENSE)

## What it does

Adds the [React Doctor](https://github.com/millionco/react-doctor) skill to Pi. React Doctor deterministically scans your React codebase and catches issues across **state & effects, performance, architecture, security, and accessibility**. Works with Next.js, Vite, TanStack, React Native, Expo — anything React.

## Install

```bash
pi install npm:pi-react-doctor
```

Or locally for a single project:

```bash
pi install -l npm:pi-react-doctor
```

## Usage

The skill triggers when you:

- Type `/doctor` in a React project
- Ask Pi to "scan my React code" or "triage diagnostics"
- Finish a feature and want a regression check before committing

### Quick scan (changed files only)

Pi will run:

```bash
npx react-doctor@latest --verbose --scope changed
```

### Full cleanup pass

Say `/doctor` and Pi fetches the canonical local-triage playbook from [react.doctor](https://react.doctor) — a scan → filter → triage → fix → validate loop that edits the working tree directly.

### Rule management

Pi can also explain, disable, or tune individual rules:

```bash
npx react-doctor@latest rules explain react-doctor/no-array-index-as-key
npx react-doctor@latest rules disable react-doctor/no-array-index-as-key
npx react-doctor@latest rules set react-doctor/no-danger warn
```

## Requirements

- Pi coding agent
- Node.js ≥ 20.19.0 (react-doctor CLI is auto-fetched via `npx`)

## How it works

This package is a thin skill wrapper. It registers the `react-doctor` skill in Pi, which:

1. Detects React projects (presence of `react` in `package.json`)
2. Runs `npx react-doctor@latest` with the right flags
3. Fetches the canonical triage playbook from react.doctor for full passes
4. Surfaces diagnostics with fix recipes

The actual scanning engine lives in the [react-doctor](https://github.com/millionco/react-doctor) npm package — this wrapper handles Pi integration only.

## Credits

**React Doctor** is built and maintained by [Million.co](https://github.com/millionco). This package is an unofficial Pi skill wrapper — all scanning logic, rules, and playbooks belong to the upstream project. Huge thanks to the Million team for building an incredible tool.

If React Doctor saves your team hours, consider [sponsoring them on GitHub](https://github.com/millionco/react-doctor).

## Related

- [React Doctor](https://github.com/millionco/react-doctor) — the upstream CLI
- [react.doctor](https://react.doctor/docs) — docs and rule reference
- [pi.dev/packages](https://pi.dev/packages) — Pi package gallery

## License

MIT — same as upstream.
