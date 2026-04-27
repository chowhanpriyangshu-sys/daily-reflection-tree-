# Daily Reflection Tree

A deterministic end-of-day reflection tool — DT Fellowship Assignment.

No LLM at runtime. No backend. No installation. Just open and reflect.

---

## How to Run

```bash
# Just open this file in any browser — that's it
frontend/daily-reflection-tree.html
```

Or serve locally:

```bash
cd frontend
python -m http.server 8000
# open http://localhost:8000/daily-reflection-tree.html
```

---

## Repository Structure

```
/tree/
  reflection-tree.tsv        ← Part A: full tree data (36 nodes)
  tree-diagram.md            ← Part A: Mermaid branch diagram

/agent/
  daily-reflection-tree.html ← Part B: working agent (loads tree, walks it, no LLM)

/transcripts/
  persona-1-transcript.md    ← Victim / Entitled / Self-centric path
  persona-2-transcript.md    ← Victor / Contributing / Altrocentric path

write-up.md                  ← Part A: design rationale (2 pages)
README.md                    ← This file
```

---

## Tree Format

The tree is stored in `tree/reflection-tree.tsv` — a tab-separated file readable without running any code.

| Column | Purpose |
|--------|---------|
| `id` | Unique node identifier |
| `parentId` | Parent node — builds the tree hierarchy |
| `type` | `start` `question` `decision` `reflection` `bridge` `summary` `end` |
| `text` | What the employee sees. `{NODE_ID.answer}` is replaced with their earlier answer |
| `options` | Pipe-separated fixed choices for question nodes. Decision nodes use routing rules here |
| `target` | Explicit jump target used by bridge nodes |
| `signal` | What this node tallies in state e.g. `axis1:internal` |

---

## Assignment Checklist

| Requirement | Minimum | Delivered |
|-------------|---------|-----------|
| Total nodes | 25+ | ✅ 36 |
| Question nodes | 8+ | ✅ 9 |
| Decision nodes | 4+ | ✅ 10 |
| Reflection nodes | 4+ | ✅ 6 |
| Bridge nodes | 2+ | ✅ 4 |
| All 3 axes in sequence | Yes | ✅ |
| Fixed options only | Yes | ✅ |
| Summary node | 1+ | ✅ 2 |
| No LLM at runtime | Yes | ✅ |
| Tree readable as data | Yes | ✅ TSV |
| Visual diagram | Yes | ✅ Mermaid |
| Write-up (max 2 pages) | Yes | ✅ |
| Working agent | Bonus | ✅ HTML |
| Two transcripts | Bonus | ✅ |
