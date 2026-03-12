# The Monolith  Phase B: *"Oh. So THAT'S what it does."*

> *"We ran the AI reverse engineering tool. We have documentation now. I'm not sure if that makes me feel better or worse."*

---

## What happened

So we took that terrifying 90,000-line C/Assembly monolith from Phase A and pointed an AI agent at it. Told it to figure out what's going on. And it did.

Turns out, the codebase is actually... kind of impressive? In a terrifying, 1996 kind of way.

## What we now know

After the reverse engineering (`/rev-eng`), we have a `specs/` folder with actual documentation:

- **`specs/prd.md`**  A product requirements document. Synthesized from code. The code now has a "vision". Wild.
- **`specs/features/`**  Feature documents for each major subsystem. There are... a lot of subsystems.
- **`specs/tasks/`**  Technical task breakdowns with actual file references. Every function, every module, mapped.
- **`specs/docs/architecture/`**  Architecture diagrams. The monolith has *layers*. Who knew.
- **`specs/docs/technology/`**  A full technology inventory. C, x86 Assembly, custom bytecode VM, platform-specific everything.

## What we learned

Things I did **not** expect to find in a 30-year-old codebase:

- A custom **virtual machine** with its own bytecode interpreter (`pr_exec.c`)
- An **entity-component system** before that was cool (edicts, `progdefs.h`)
- **Client-side prediction** for networking  in 1996!
- **Hand-written x86 assembly** for the software renderer (because GPUs were optional back then)
- Platform abstraction via `sys_*.c` files  DOS, Windows, Linux, Sun. *Sun.*
- A file called `gas2masm` that converts between two types of assembly. Because one type of assembly wasn't enough.

## The current state of things

```
Before reverse engineering:          After reverse engineering:
                                     
 "what is this?"                      "oh no, I understand it now"
 "who wrote this?"                    "it's actually kind of brilliant"
 "why is there assembly?"             "the assembly is the fast part"
 "is this even C?"                    "it's C, QuakeC, and vibes"
```

## So... now what?

Great question. I have documentation. I have architecture diagrams. I have feature specs.

But I also have:
- Zero tests
- `sprintf` everywhere (security people, look away)
- Build files for compilers that no longer exist
- Platform code for operating systems nobody runs anymore
- A codebase that assumes 8MB of RAM is generous

**The documentation tells me WHAT exists. It doesn't tell me WHAT TO DO about it.**

Do I... modernize it? Rewrite it? Containerize it? Deploy it to the cloud?
How do you even start? Where do you even begin with something like this?

I need a plan. A real plan. Not just docs.

---

*Phase A: "I don't know what this is."*
**Phase B: "I know what this is. I wish I didn't."**
*Phase C: Coming soon  maybe a plan?*