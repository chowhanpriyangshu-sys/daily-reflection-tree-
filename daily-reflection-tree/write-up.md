# Write-Up: Daily Reflection Tree
### Design Rationale — DT Fellowship Assignment

---

## 1. Why These Specific Questions

The assignment says the questions are the product. I spent most of my design time here.

The core challenge with all three axes is the same: the "wrong" end of each spectrum is invisible to the person holding it. Nobody thinks of themselves as a victim, entitled, or self-centred. Questions that name these things directly produce defensive or socially desirable answers. So every question in this tree is indirect — it asks about *behaviour* and *instinct*, not identity.

**Axis 1 (Locus of Control):** The opening question — *"How would you describe today in one word?"* — is deliberately broad. It captures the employee's initial emotional frame before they've had time to rationalise. Someone who says "Frustrating" and then answers *"I figured out what I could control"* is revealing internal locus despite a hard day. The follow-up question catches this and routes them to a deeper probe. I avoided questions like "Do you feel in control of your life?" because they're too transparent — based on Rotter's (1954) original scale, which uses behavioural scenarios rather than direct self-report.

**Axis 2 (Orientation):** Entitlement is defined by Campbell et al. (2004) as a stable, largely unconscious belief. The question *"Did you do something today that no one will notice or credit you for?"* surfaces it without naming it. A contribution-oriented person answers easily. An entitlement-oriented person either says no (they did only what was expected) or yes-but (they wished someone had noticed). The qualifier is the signal. This design follows Organ's (1988) OCB framework — discretionary, unrewarded effort is the clearest behavioural marker of contribution orientation.

**Axis 3 (Radius of Concern):** The question *"Whose face or situation comes to mind when you close the day?"* requires no reasoning — just noticing. Maslow's (1969) self-transcendence framework describes the shift from self-referential to other-referential concern as a developmental movement, not a moral judgement. The follow-up question (*"What stressed you most today?"*) probes whether stress was self-contained or diffused across others — a behavioural trace of perspective-taking capacity, per Batson (2011).

---

## 2. How I Designed the Branching

**The core trade-off was depth vs. maintainability.** A fully branched tree — every answer producing a unique path — would require exponentially more nodes and become unreadable as data. I chose a middle path: branch on the most diagnostic question per axis (the opener), then use a second question to refine, and route to one of two reflections per axis based on accumulated signals.

**Why signals instead of hard branches:** Each answer records a +1 tally for a pole (e.g. `axis1:internal`). The dominant pole at the end of each axis determines which reflection the employee sees. This handles ambiguous users gracefully — someone who gives one internal and one external answer gets the reflection that fits their lean, rather than hitting an arbitrary hard cutoff.

**Bridge nodes are reframes, not transitions.** The bridge after Axis 1 shifts the frame from *"what happened to you"* to *"what you gave"*. The bridge after Axis 2 shifts from *"your contribution"* to *"your circle of concern"*. Each bridge is slightly different depending on which reflection the employee just read, maintaining conversational coherence across the three axes.

**Options were designed to avoid false binaries.** On Axis 2, the option *"Yes — though I wish someone had noticed"* was deliberately included. It's an honest answer many people will choose, and it sits between pure contribution and pure entitlement. The tree captures this nuance and routes accordingly.

---

## 3. Psychological Sources

| Source | How it informed the design |
|--------|---------------------------|
| Rotter, J.B. (1954). *Social learning and clinical psychology* | Internal vs. external locus framing for Axis 1; behavioural scenario approach for question design |
| Dweck, C. (2006). *Mindset* | Effort-as-growth framing in Axis 1 follow-up questions |
| Organ, D.W. (1988). *Organizational Citizenship Behavior* | Discretionary, unrewarded effort as the behavioural marker for Axis 2 contribution pole |
| Campbell, W.K. et al. (2004). *Psychological entitlement* | Entitlement as unconscious and stable — shaped the indirect question design for Axis 2 |
| Maslow, A. (1969). *The farther reaches of human nature* | Self-transcendence as the peak above self-actualisation — theoretical core of Axis 3 |
| Batson, C.D. (2011). *Altruism in humans* | Perspective-taking as a cognitive act, distinct from sympathy — informed the radius framing |

---

## 4. What I Would Improve With More Time

**Softer option wording on Axis 2.** Some entitlement-branch options feel slightly loaded on reflection. *"I felt my effort wasn't being noticed"* may not resonate with someone who frames their entitlement differently. A better variant might be: *"I was keeping track of what I was putting in vs. getting back"* — behaviourally equivalent, less emotionally charged.

**Longitudinal pattern layer.** A single session tells you about one day. With session history (a lightweight local store, no LLM), the summary could say: *"This is the third time this week you've closed the day thinking about your own workload."* This would add significant value without violating the no-LLM constraint.

**More differentiation on Axis 3.** The radius axis currently has the least branching depth. With more time I'd write additional follow-up questions that probe *how* concern for others manifested — whether it was passive noticing or active response — to distinguish genuine altrocentrism from performed empathy.

**Real user testing.** The tree was designed and iterated using LLM persona roleplay. Actual employees at 7pm would surface gaps in the options — moments where none of the four choices feels honest. A round of hallway testing would sharpen the question design more than any amount of solo iteration.

---

*Node count: 36 total — 9 question, 10 decision, 6 reflection, 4 bridge, 2 summary, 1 start, 1 end, 3 null-routed shared nodes*
