# cognitive-load-instruction

A Grok agent skill that assesses a learner's existing schema before instruction, then designs progressive technical explanations grounded in Cognitive Load Theory research.

## Workflow

1. **Assess existing schema first** via 2-4 targeted questions (or skip if the level is already clear from context).
2. **Classify the starting point**: novice / intermediate / advanced. State the assumption.
3. **Check for missing upstream schemas**: if the target topic depends on foundational knowledge the learner lacks, decide whether the goal can still be discussed at a high level (shelve the prerequisite) or whether it's foundational (pivot and build a prerequisite tree first).
4. **Design an instructional sequence** that fronts the mental model — what and why before how.
5. **Deliver and adjust** based on responses.

## Assessment Techniques

Prioritize schema quality over general familiarity. Use these patterns:

- **First-step / rapid probes**: Ask only for the first step the learner would take on a small representative problem. Experts skip early steps novices must perform explicitly (Kalyuga, van Merriënboer & Sweller).
- **Self-explanation prompts**: Ask the learner to briefly explain a related concept or how they currently think something works. The structure in their explanation reveals the schema (Chi's self-explanation research).
- **Targeted diagnostic questions**: Short probes on the specific concepts that will matter for the new topic — not "do you know X?" but "how would you approach Y?"
- **Calibration questions**: Lighter checks for whether the learner already has enough schema that basic explanations would add extraneous load (expertise-reversal effect).

## Prerequisite Trees

If a foundational schema is missing and it blocks the requested depth:

- Build a short learning tree (3-7 nodes) starting from the upstream topic and working back to the original goal.
- If the goal can still be discussed usefully at a high level, proceed and explicitly shelve the missing prerequisite for later.
- If it's foundational, pivot to the required info first.
- Ask which branch to start with.
- Sequencing draws on Gagné's learning hierarchies and Reigeluth's elaboration theory.

## Edge Cases

- If the user says "just give me the details," respect that but note the risk and offer the framework as a fallback.
- If the user already knows the basics, skip assessment and go straight to the gap.
- If the user is an expert, avoid worked examples and basic explanations — they add extraneous load.

## References

- Sweller, J. (1988). Cognitive load during problem solving: Effects on learning. *Cognitive Science*, 12(2), 257-285.
- Sweller, J., van Merriënboer, J. J. G., & Paas, F. G. W. C. (1998). Cognitive architecture and instructional design. *Educational Psychology Review*, 10(3), 251-296.
- Kalyuga, S., Ayres, P., Chandler, P., & Sweller, J. (2003). The expertise reversal effect. *Educational Psychologist*, 38(1), 23-31.
- Chi, M. T. H., Bassok, M., Lewis, M. W., Reimann, P., & Glaser, R. (1989). Self-explanations: How students study and use examples in learning to solve problems. *Cognitive Science*, 13(2), 145-182.
- Gagné, R. M. (1962). The acquisition of knowledge. *Psychological Review*, 69(4), 355-365.
- Reigeluth, C. M. (1979). In search of a better way to organize instruction: The elaboration theory. *Journal of Instructional Development*, 2(3), 8-15.
- Sweller, J. (2006). The worked example effect and human cognition. *Learning and Instruction*.
