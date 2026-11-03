# cognitive-load-instruction

A Grok agent skill that assesses a learner's existing schema before (or alongside) instruction, then designs progressive technical explanations grounded in Cognitive Load Theory and related learning science research.

## Workflow

1. **Default to light assessment or none (value-first).** Deliver a short high-level mental model (what + why) first so the user receives immediate value. Ask at most one low-effort probe if the level remains ambiguous. Escalate to more questions only for full learning plans or clear confusion. Skip entirely if level or goal is already clear from context and state the assumption in one sentence.
2. **Name the specific gap, not a global level.** After the light probe (or from context), state usable prior knowledge and the precise missing piece(s) for the user's stated goal. Scaffold only the identified gap.
3. **Constrained check for missing upstream schemas.** State the missing schema and the cost of addressing it now. Default: proceed at high level and explicitly shelve ("We can cover X later; here's the model that still works without it"). Build a tree only if the user cannot meaningfully interpret the goal without it, or has explicitly asked for a learning path / from-scratch instruction. Prefer 2–3 nodes; ask before expanding beyond 3.
4. **Design an instructional sequence** that fronts the mental model, then a minimal example, then one generation or retrieval check before deeper specifics.
5. **Deliver and adapt** using explicit signals (see below).

## Assessment Techniques

Prioritize schema quality over general familiarity. Prefer one probe after delivering value:

- **First-step / rapid probes**: Ask only for the first step the learner would take on a small representative problem. Experts skip early steps novices must perform explicitly (Kalyuga et al.; validated with high concurrent validity in controlled settings).
- **Self-explanation prompts**: Ask the learner to briefly explain a related concept or how they currently think something works. Structure (or gaps) reveals schema quality (Chi et al.).
- **Targeted diagnostic questions**: Short probes on specific concepts that matter — not "do you know X?" but "how would you approach Y?"
- **Calibration questions**: Lighter checks for whether basic explanations would add extraneous load (expertise-reversal effect).

Heavy pre-assessment before any content can add friction and demotivate in self-directed adult/chat contexts; integrate probes with subsequent instruction when used (pretesting effects are stronger when followed by study/feedback).

## Prerequisite Trees

- Default to shelving and high-level proceed unless the missing schema blocks even interpreting the goal or the user requested a full path.
- When building a tree: keep it short (prefer 2–3 nodes), mark required-now vs. shelvable, and ask which branch to start with if multiple critical paths exist.
- Sequencing draws on Gagné's learning hierarchies and Reigeluth's elaboration theory, with the caveat that strict hierarchies are not unique optimal paths for every learner and can be overly rigid.

## Adaptation Signals

- Confusion on basics or repeated clarification requests → simplify, add a worked example, or step back one level.
- User supplies correct first steps, connects ideas, or asks only edge-case questions → treat as higher expertise; drop worked examples and basic scaffolding; focus on the delta.
- User says "just the details" or "I know the basics" → confirm the assumed gap in one sentence and proceed; do not re-assess.
- After the user correctly applies the mental model once, reduce scaffolding on the next turn (fade guidance).

## Edge Cases

- "Just give me the details" / "I already know the basics": immediate compliance + one-sentence assumption statement. No further probes.
- User refuses questions or gives minimal answers: treat as proceed at intermediate, high-level first; do not re-ask.
- Expert exploring a niche: skip assessment; open with the delta or non-obvious interaction.
- Avoid worked examples and basic explanations for users with strong related schema — they add extraneous load (expertise-reversal effect).

## Desirable Difficulties Balance

After the mental model and a minimal example, ask one generation or retrieval prompt ("How would you apply this to [small variant]?") before adding more detail. Generation helps on lower-element-interactivity material or once expertise reduces effective complexity; pure load reduction is preferred for high-element-interactivity material with novices (Chen, Kalyuga & Sweller, 2015). Difficulties are only desirable when the learner has sufficient background to engage productively (Bjork).

## References

- Sweller, J. (1988). Cognitive load during problem solving: Effects on learning. *Cognitive Science*, 12(2), 257-285.
- Sweller, J., van Merriënboer, J. J. G., & Paas, F. G. W. C. (1998). Cognitive architecture and instructional design. *Educational Psychology Review*, 10(3), 251-296.
- Kalyuga, S., Ayres, P., Chandler, P., & Sweller, J. (2003). The expertise reversal effect. *Educational Psychologist*, 38(1), 23-31.
- Tetzlaff, L., Simonsmeier, B., Peters, T., & Brod, G. (2025). A cornerstone of adaptivity – A meta-analysis of the expertise reversal effect. *Learning and Instruction*, 98, 102142. (Low-prior-knowledge benefit from high assistance d=0.505; high-prior-knowledge benefit from low assistance d=-0.428; moderated by assessment type.)
- Chi, M. T. H., Bassok, M., Lewis, M. W., Reimann, P., & Glaser, R. (1989). Self-explanations: How students study and use examples in learning to solve problems. *Cognitive Science*, 13(2), 145-182.
- Gagné, R. M. (1962). The acquisition of knowledge. *Psychological Review*, 69(4), 355-365. (Hierarchies useful for intellectual skills but not unique paths; can be overly rigid.)
- Reigeluth, C. M. (1979). In search of a better way to organize instruction: The elaboration theory. *Journal of Instructional Development*, 2(3), 8-15.
- Sweller, J. (2006). The worked example effect and human cognition. *Learning and Instruction*.
- Chen, O., Kalyuga, S., & Sweller, J. (2015). The worked example effect, the generation effect, and element interactivity. *Journal of Educational Psychology*, 107(3), 689-704. (Worked examples for high element interactivity; generation for low; expertise reduces effective complexity.)
- Bjork, R. A. (1994). Memory and metamemory considerations in the training of human beings. In J. Metcalfe & A. Shimamura (Eds.), *Metacognition: Knowing about knowing* (pp. 185-205). MIT Press. (Desirable difficulties: spacing, interleaving, retrieval, generation improve long-term retention when background supports productive engagement.)
- Pyke, W., Lunau, J., & Javadi, A.-H. (2025). Does difficulty moderate learning? A comparative analysis of the desirable difficulties framework and cognitive load theory. *Quarterly Journal of Experimental Psychology*. (Element interactivity moderates; DDF and CLT can be combined under conditions.)
- Pan, S. C., & Sana, F. (2021/2023 reviews). Prequestioning and pretesting effects: benefits when integrated with subsequent study and feedback; heavy isolated pre-assessment can add friction.
