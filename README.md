# Linux Essentials: My Journey Through Modules 1–3

**Author:** Emmanuella Odetsi Martey (Ella)
**Programme:** Akwannya Hub
**Modules covered:** Introduction to Linux · Operating Systems · Working in Linux

---

## Why I'm writing this

Over the past few weeks of weekly discussion sessions and personal study time, I went from barely knowing what a kernel was to being genuinely comfortable moving around a Linux system on the command line. This post is my reflection on that journey — what I learnt, how I learnt it, the commands I actually typed, and the moments that tripped me up along the way.

---

## Module 1: Introduction to Linux

### What Linux actually is

The biggest "yieyie" moment for me in this module was realising that **Linux, strictly speaking, is just the kernel** — not the whole operating system. The kernel is the part that sits between your applications and the physical hardware, deciding who gets CPU time, who gets memory, and who gets access to devices. Everything else people associate with "Linux" — the GNU tools, the desktop, the apps — is actually built on top of that kernel.

I found it easier to remember once I traced the lineage:
- **UNIX** (1970s) set out the original design philosophy.
- **GNU** (1983) built most of the free tools around that philosophy, but never had a popular kernel of its own.
- **Linus Torvalds** (1991) wrote the missing kernel.
- Put together, the two form what's technically called **GNU/Linux**.

### Open source and distributions

Because the source code is open, different groups packaged the kernel with different tools and defaults — which is why we end up with distributions like Ubuntu, Debian, Fedora and openSUSE. Understanding the "family tree" helped a lot: Ubuntu is built on Debian, and Fedora sits in the same family as Red Hat Enterprise Linux. It's not twenty unrelated operating systems — it's a handful of families, packaged differently.

**Key takeaway:** Linux isn't one thing — it's a kernel, a philosophy, and an ecosystem of communities building on top of it.

---

## Module 2: Operating Systems

### What an OS is actually doing

This module reframed how I think about my own laptop. Every time I have a browser, a music player, and a code editor open at once, they're all competing for the same CPU and memory — and the operating system is the one silently scheduling and sharing those resources so nothing collides.

### Choosing an OS is a business decision, not a preference

I learnt that the right OS depends on six factors: **role, function, life cycle, stability, compatibility, and cost.** The example that made this click for me was a hospital server — you would never run a hospital's critical systems on an exciting but untested release. Stability and support matter more than novelty.

### GUI vs CLI

I also compared the three ecosystems (Windows, macOS, Linux) and spent real time understanding *why* the command line matters so much in Linux culture. Doing the same task on fifty servers by clicking through menus fifty times versus running one command (or script) across all fifty — that's the entire argument for the CLI in one sentence.

**Key takeaway:** An operating system isn't chosen by looks. It's chosen by matching its strengths to the actual job it needs to do.

---

## Module 3: Working in Linux

This is where things stopped being theoretical and became hands-on.

### Commands I used, and what they actually do

| Command | What it does | Why I used it |
|---|---|---|
| `whoami` | Prints the username you're currently logged in as | First thing I ran to confirm which account I was operating under |
| `pwd` | Prints the current working directory (where you are in the filesystem) | Grounded me before running any other command |
| `ls` | Lists the contents of the current directory | Used constantly to see what files/folders exist before acting on them |
| `uname -a` | Prints system and kernel information (kernel name, version, architecture) | Helped me confirm exactly which Linux system and kernel version I was working on |
| `apt list --installed` | Lists all packages currently installed (Debian/Ubuntu family) | Used to audit what software was already on the system |
| `apt show <package>` | Shows details about a specific package (version, dependencies, description) | Used before installing anything, to understand what I was about to bring onto the system |
| `rpm -qa` | Lists all installed packages (Red Hat/Fedora family) | The RPM-family equivalent of `apt list --installed` |
| `dnf info <package>` | Shows details about a specific package (RPM family) | The RPM-family equivalent of `apt show` |

*(Screenshot below: terminal output from running `whoami`, `pwd`, `ls`, and `uname -a` in sequence.)*

`![whoami, pwd, ls, uname -a output](screenshots/basic-commands.png)`

*(Screenshot below: `apt list --installed` output and `apt show` on a chosen package.)*

`![apt package management output](screenshots/package-management.png)`

> **Note to self before publishing:** replace the two lines above with real `![alt text](path)` screenshots once the images are saved into a `screenshots/` folder in this repo.

### Processes, the kernel, and package management, in my own words

A **process** is just a running application, and it can't touch the CPU, memory, disk, or network directly — every single request goes through the kernel first, which is why the kernel is often described like an air-traffic controller managing many aircraft (processes) safely at once.

A **package manager** (`apt` on Debian-based systems, `dnf`/`rpm` on Red Hat-based systems) is what keeps software organised. Rather than me manually tracking what's installed and what each piece of software depends on, the package manager checks all of that automatically — install, update, remove, and dependency resolution, all handled for me.

I also learnt to be precise about three things I used to lump together: the **terminal** is just the window I type into; the **shell** (Bash) is the program actually interpreting my commands; and an **editor** (Vim, Nano) is a separate program I launch from the shell to change files directly — useful especially on servers with no graphical interface at all.

### Security and scaling

The final piece was realising that having power over a Linux system (especially root/admin access) comes with real responsibility: strong authentication, regular patching, least-privilege access, firewalls, and encryption all work as layers — each one catching what the layer before it might have missed. And at scale, that same Linux system can be virtualised (via a hypervisor into multiple VMs) or containerised (via tools like Docker, sharing one kernel) and deployed across public, private, or hybrid cloud infrastructure.

**Key takeaway:** Linux isn't just something you install — it's something you actively operate, secure, and scale.

---

## Challenges I ran into

- **Windows vs Linux syntax mismatches.** I work primarily on a Windows machine using PowerShell, so translating Linux commands (and things like heredoc syntax or path separators) into something that behaved the same way took real trial and error.
- **Keeping terminal, shell, and editor straight.** These three terms sound interchangeable at first, and it took deliberate repetition before the distinction actually stuck.
- **Remembering that the package-management commands change by distribution family.** I had to consciously map `apt`/`dpkg` (Debian) against `dnf`/`rpm` (Red Hat) rather than assuming one set of commands works everywhere.

## Key takeaways

1. Linux is the kernel — everything else is built on top of it.
2. Choosing an operating system (or a distribution) is about matching its strengths to the job, not personal preference.
3. The command line isn't intimidating once you see it as a tool for precision and repeatability, not a replacement for understanding.
4. Real competence came from typing the commands myself, not just reading about them.

---

*This write-up documents my personal progress through Modules 1–3 of the Akwannya Hub programme's Linux curriculum.*
