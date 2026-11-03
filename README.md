# coding-lessons

Engineering lessons that outlive any one project — how work goes wrong, and what to do differently —
kept as a [Scatterhoard](https://github.com/jtcours/scatterhoard) memory set, so that a coding agent can recall the right
one at the moment it is about to make the mistake.

A lesson belongs here when it would hold on a different codebase: testing and verification technique,
debugging method, design judgement, tooling behaviour. Each records a mistake made at real cost, with
its reasoning. Many carry **triggers**: short memories describing what a session is about to write
when that mistake happens, phrased the way a session would phrase it, so that a recall made just
before writing finds them.

## Using it

**1. Take the set on** from a checkout of this repository. In a session with the Scatterhoard tools:

```
hoard_sets  action: "create", name: "coding-lessons"
hoard_sets  action: "import", scope: "shared:coding-lessons", directory: "<path to this checkout>"
hoard_sets  action: "mint", scope: "shared:coding-lessons", author: "<the name you publish under>"
```

`hoard_sets` action `status` should then list `shared:coding-lessons` with its memories. The set is
yours to write to: lessons your projects teach you go into it, and `hoard_sets` action `export` with
the same `directory` writes them into the checkout's memory file, where `git diff` shows them. To take
in other people's lessons, pull this repository and run the import again.

**2. Put this paragraph in your project's `AGENTS.md`** (or `CLAUDE.md`), exactly as written:

```
This project draws on the `coding-lessons` memory set, if `hoard_sets` status lists it. Before each
change that adds or alters behaviour — a new function, file, data format, check, refusal or test,
but not a rename, a reformat or moved code — write one sentence saying what you are about to write,
and recall it once: `hoard_recall` with that sentence as `query`, no `scope`, `ignore_floor: true`,
`detail: "summary"` and `limit: 5`. Where a returned line is a lesson or a trigger for what you are
about to do, look it up with `hoard_lookup` and write accordingly. When you find a mistake that a
lesson covers, or that one should, recall the keyword `coding-lessons-adoption-guide` and do what
it says. If the set is not loaded, work without it and say so once, so the user can decide whether
to add it.
```

**Why it goes in `AGENTS.md` rather than being looked up.** A file of instructions stays in front of
the agent for the whole session; a looked-up guide is read once and scrolls away. Measured on the
project this set came from, sessions that read the habit from a recalled guide recalled before nearly
every change on the first day, and before about one change in eight three sessions later. The
paragraph also has to read correctly where the set is absent, because `AGENTS.md` travels with every
clone and the set does not.

**Why each setting.** No `scope`, so a speculative query does not drag down this set's calibrated
non-match floor; `ignore_floor`, because triggers are short and score below a floor calibrated on
long lessons; `detail: "summary"` and a small limit, because five one-line summaries cost little and
the one worth reading is fetched whole. Once per change, never per edit: a habit that fires on every
edit gets skipped.

## When a mistake turns up

The paragraph above sends the agent to the adoption guide, stored in this set under
`coding-lessons-adoption-guide`. In short: check whether the habit would have found the lesson, and if
not, add a trigger so that next time it does. If no lesson fits and the mistake would happen on any
codebase, write one. Both go into this set; a trigger phrased in your own project's nouns goes in your
project's set instead, linked to the lesson.

## Contributing

What your sessions add reaches everyone else by pull request: export, commit the change to
`scatterhoard_mem/coding-lessons.json`, and offer it here. The set's charter — its
`hoard-scope-topics` memory — is the test a new memory has to pass, and review is where that is
checked. Nothing about a particular person, machine or set of working preferences belongs here, and
nothing project-specific: those belong in a personal or project set.

## What is in the file

`scatterhoard_mem/coding-lessons.json` is a Scatterhoard memory file: a header line declaring the
format version and the set, then one memory per line, ordered by id. Each memory carries its claim,
its reasoning, a handle for where it came from, keywords, and links.

The rules a memory has to meet live in the set itself, where an agent reads them: what belongs, and
how triggers and examples link to a lesson, in the charter (`hoard_recall` with keywords
`["hoard-scope-topics"]` and scope `shared:coding-lessons`); how to tag what you write, in part 3 of
`coding-lessons-adoption-guide`.

The set's history is in [HISTORY.md](HISTORY.md).
