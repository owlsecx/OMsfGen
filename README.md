# 🦉 OMsfGen

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Linux-informational?style=flat-square&logo=linux&logoColor=white&color=0a0c10"/>
  <img src="https://img.shields.io/badge/Category-OAttack%20%2F%20Red%20Team-red?style=flat-square"/>
  <img src="https://img.shields.io/badge/Requires-Metasploit-blueviolet?style=flat-square"/>
  <img src="https://img.shields.io/badge/License-MIT-green?style=flat-square"/>
  <img src="https://img.shields.io/badge/Part%20of-OwlSec%20Toolkit-7b5ea7?style=flat-square"/>
  <img src="https://img.shields.io/badge/Version-1.0-cyan?style=flat-square"/>
</p>

> **OMsfGen** is a terminal frontend for `msfvenom` — configure payloads, encoders, and formats, generate output files, build `msfconsole` listener commands, and manage generation history, all from a clean interactive menu.

---

> ⚠️ **AUTHORISED RED TEAM USE ONLY** — Generating payloads without explicit written permission is illegal. Use only in authorised engagements.

---

## 📌 Overview

OMsfGen wraps `msfvenom` with a structured interactive interface — removing the need to memorise payload strings, encoder flags, or format options. Every generation is saved to a persistent history, and listener RC files can be exported directly for `msfconsole`.

---

## 🖥️ Menu

| Option | Description |
|--------|-------------|
| **[1] Generate Payload** | Run `msfvenom` with current settings — output file saved to `payloads/` |
| **[2] Build Listener** | Generate `msfconsole` one-liner and RC file for the active payload |
| **[3] Browse Payloads** | Browse all 20 payloads grouped by platform, select active payload |
| **[4] History** | View last 50 generations with payload, LHOST, LPORT, encoder, size |
| **[5] Export RC File** | Save a standalone `.rc` handler file for `msfconsole -r` |
| **[6] Fetch Local IPs** | Detect interface IP addresses and optionally set as LHOST |
| **[7] Settings** | Configure LHOST, LPORT, encoder, format, iterations, output directory |

---

## 🎯 Payload Library

### Windows
| Payload | Format |
|---------|--------|
| Windows (EXE) — reverse_tcp | `.exe` |
| Windows (EXE) — reverse_https | `.exe` |
| Windows x64 — reverse_tcp | `.exe` |
| Windows x64 — reverse_https | `.exe` |
| Windows — shell_reverse_tcp | `.exe` |
| Windows DLL — reverse_tcp | `.dll` |

### Linux
| Payload | Format |
|---------|--------|
| Linux (ELF) — reverse_tcp | `.elf` |
| Linux x64 (ELF) — reverse_tcp | `.elf` |
| Linux — shell_reverse_tcp | `.elf` |

### Android
| Payload | Format |
|---------|--------|
| Android (APK) — reverse_tcp | `.apk` |
| Android (APK) — reverse_https | `.apk` |

### macOS
| Payload | Format |
|---------|--------|
| macOS — shell_reverse_tcp | `.macho` |
| macOS x64 — reverse_tcp | `.macho` |

### Scripts
| Payload | Format |
|---------|--------|
| Python — reverse_tcp | `.py` |
| Python — shell_reverse_tcp | `.py` |
| PowerShell — reverse_tcp | `.ps1` |
| PowerShell — encoded | `.ps1` |
| Bash — shell_reverse_tcp | `.sh` |

---

## 🔧 Encoders

| Encoder |
|---------|
| none (no encoder) |
| x86/shikata_ga_nai |
| x86/xor_dynamic |
| x86/alpha_mixed |
| x86/countdown |
| x64/xor_dynamic |
| x64/zutto_dekiru |
| cmd/powershell_base64 |

---

## 📤 Output Formats

`exe` · `elf` · `apk` · `raw` · `py` · `ps1` · `psh` · `psh-cmd` · `sh` · `macho` · `dll` · `jar` · `war`

---

## 📋 Listener Builder

Generates a ready-to-run `msfconsole` handler for the active payload:

```bash
# One-liner
msfconsole -q -x "use exploit/multi/handler; set payload <payload>; set LHOST <ip>; set LPORT <port>; set ExitOnSession false; exploit -j -z"

# RC file
msfconsole -r handler_YYYYMMDD_HHMMSS.rc
```

RC files are saved to the configured output directory.

---

## 📁 History

Every successful generation is saved to `~/.omsfgen_history.json` (last 50 entries). Each entry records timestamp, payload string, LHOST, LPORT, encoder, format, output path, msfvenom exit code, and file size.

---

## ⚙️ Requirements

- **Linux** (any modern distro)
- **Metasploit Framework** — `msfvenom` must be installed and in `$PATH`
- **No Python installation needed** — runs as a standalone executable

```bash
# Install Metasploit (if needed)
curl https://raw.githubusercontent.com/rapid7/metasploit-omnibus/master/config/templates/metasploit-framework-wrappers/msfupdate.erb > msfinstall
chmod +x msfinstall && sudo ./msfinstall
```

---

## 🚀 Usage

```bash
./OMsfGen
```

---

## 📦 Part of OwlSec Toolkit

This tool is part of the **OwlSec** suite — a collection of 300+ security and privacy tools.

🔗 [owlsec.org](https://owlsec.org)

---

## ©️ License

MIT License — © Khaled S. Haddad

*Tools are distributed as pre-built executables. Source code is proprietary.*
