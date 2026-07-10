# 🎭 Scenario-based & Behavioral

[← Back to main README](../README.md)

> Scenario questions test research judgment and applied engineering thinking under realistic ambiguity — there's often no single "correct" answer, but strong answers show a clear, structured process and awareness of tradeoffs. Behavioral questions use the **STAR method** (Situation, Task, Action, Result) — the frameworks below are for structuring your *own* real experience, not for fabricating one.

---

### Q: "Design a text-to-3D asset generation pipeline for a game studio's production use, covering the path from a text prompt to a production-ready, texturable, riggable game asset. Walk me through your architecture and key design decisions."

**Answer (framework):**
Structure across the full pipeline discussed throughout this repo: (1) **Generation stage** — likely a multi-view-diffusion-then-reconstruction approach (per the diffusion and text-to-3D topics) for speed, given production use needs fast iteration, rather than slow per-scene SDS optimization. (2) **Geometry post-processing** — mesh extraction, remeshing for clean topology, and watertighting/self-intersection repair (per the mesh generation topic), since raw generated geometry is very unlikely to be production-ready as-is. (3) **Texture/material generation** — PBR-compatible texture generation with explicit de-lighting/intrinsic decomposition (per the texture topic) so assets work correctly under the game engine's own dynamic lighting, plus UV unwrapping if not natively handled. (4) **Rigging compatibility** — flag that clean, artist-standard topology (per the mesh topology discussion) is specifically important if assets need character rigging/animation, which may push toward explicit/autoregressive mesh generation approaches over pure implicit-extraction ones. (5) **Quality gating** — automated mesh quality checks (topology validity) before any asset reaches an artist, avoiding wasted manual review time on defective outputs. Close by acknowledging this is a multi-stage pipeline where each stage has its own quality bar, not a single end-to-end "prompt in, perfect asset out" system.

---

### Q: "You've trained a new text-to-3D model and it achieves a better (lower) FID score than the previous baseline, but your team's 3D artists say the outputs 'feel worse' in practice. How do you investigate this discrepancy?"

**Answer (framework):**
This tests exactly the automated-metric-versus-genuine-quality skepticism discussed throughout the evaluation topic. Structure: first verify the FID computation itself is genuinely comparable (same feature extractor, same reference distribution, same rendering/viewpoint sampling protocol between the two model comparisons — a subtle change in evaluation setup could produce a misleading FID improvement unrelated to genuine quality). Assuming the metric computation is sound, investigate what FID specifically does and doesn't capture (per the evaluation topic) — check if the new model exhibits **improved statistical/distributional similarity to training data on average while having specific, meaningful failure modes** (increased floaters, worse topology, Janus-problem-style inconsistency) that FID's aggregate, distribution-level computation wouldn't directly penalize but that artists would immediately notice and find frustrating in hands-on use. Run **targeted qualitative review across multiple viewpoints** (not just the single-view snapshots FID-style pipelines often use) and **explicit mesh-quality/topology checks** (per the mesh generation topic) on a batch of outputs from both models, looking specifically for artifacts a distributional metric wouldn't flag. This demonstrates the core research skill of not blindly trusting a single automated metric over direct, hands-on domain-expert feedback.

---

### Q: "A stakeholder wants your team to switch from a NeRF-based pipeline to Gaussian Splatting because 'it's what everyone's using now.' How do you evaluate whether this switch is actually warranted for your specific use case?"

**Answer (framework):**
Avoid either reflexively agreeing (chasing trends) or reflexively resisting (defending the status quo) — apply the structured tradeoff framework from the neural fields topic. Ask: what's the **actual current bottleneck** in the existing pipeline — is it rendering speed/interactivity (where Gaussian Splatting's advantage is most directly relevant), representation compactness/editability, or mesh-extraction quality for downstream use (where the comparison is less clear-cut and evolving)? Propose a **concrete, bounded pilot comparison** on the team's actual representative use cases and data, rather than deciding based on general community sentiment or benchmark results from unrelated use cases — measuring the specific metrics (speed, quality, downstream compatibility) that actually matter for this team's specific product/research needs. Be prepared to genuinely recommend staying with the current approach if the pilot doesn't show a clear, use-case-relevant benefit, even given the switch's popularity — this response demonstrates evidence-based technical judgment over trend-following.

---

### Q: "You're three weeks into a research project pursuing a specific architectural idea for improving multi-view consistency, and initial results are unpromising — worse than your baseline. How do you decide whether to keep iterating on this idea, pivot to a different approach, or conclude it's a genuine negative result worth documenting and moving on from?"

**Answer (framework):**
This tests exactly the negative-result judgment discussed in the research methodology topic. Structure: first **rule out implementation bugs and unfair comparison** as the actual cause of the poor results (a surprisingly common root cause of apparently-negative results, per the paper reproduction discussion — is the baseline being fairly, thoroughly tuned; is there a subtle bug in the new architecture's implementation) before concluding the underlying idea itself is genuinely unpromising. If the implementation and comparison are verified sound, assess whether the **underlying hypothesis for why the idea should work still seems theoretically sound** given what's actually been observed — sometimes unpromising initial results reveal a genuine, informative flaw in the original hypothesis (worth documenting as a real negative-result finding), and sometimes they reveal an implementation/hyperparameter issue distinct from the core idea being wrong (worth further, more targeted iteration). Set an **explicit checkpoint/decision point** in advance (rather than open-endedly continuing indefinitely) — a reasonable additional time-boxed investigation to resolve the remaining ambiguity, after which a clear decision (continue, pivot, or document-and-conclude) should be made based on what's actually been learned, rather than sunk-cost-driven indefinite continuation.

---

### Q: "How would you approach explaining to a non-technical product stakeholder why your text-to-3D research prototype takes 30 seconds to generate an asset, while a competitor's product claims sub-second generation, without either dismissing the comparison or overpromising an unrealistic timeline for closing the gap?"

**Answer (framework):**
This tests the translation skill emphasized throughout this series. Structure: explain the underlying tradeoff in accessible terms (e.g., "our current approach does more careful, iterative refinement per generation, similar to a careful sketch-then-refine process, versus a faster, single-pass approach that trades some refinement for speed") rather than a purely technical explanation of diffusion sampling steps. Be **honest and specific about the actual technical gap** — is the competitor likely using a distilled/fast-sampling approach (per the diffusion topic's distillation discussion), a different architecture entirely, or accepting a different quality tradeoff — grounding the comparison in genuine technical understanding rather than vague reassurance. Propose a **concrete plan and realistic timeline** for closing the gap if warranted (e.g., "adopting distillation techniques is a well-established path with concrete precedent, and here's a realistic estimate of the engineering investment involved") rather than either dismissing the competitive pressure as unimportant or promising an unrealistic immediate fix — this combination of honest technical grounding and a credible improvement plan is what builds durable stakeholder trust.

---

### Q: "Tell me about a time you had to make a judgment call about the appropriate evaluation rigor for a research result, balancing thoroughness against a real deadline (a conference submission, a product launch decision)."

**Answer (framework):**
This tests practical research judgment under real constraints, echoing the research methodology topic's discussion of allocating limited time/compute. Structure: describe the specific evaluation tradeoff (which additional ablations, baselines, or evaluation dimensions you considered including but had to prioritize against given the time constraint), the **specific reasoning behind what you chose to prioritize** (e.g., prioritizing the ablations most central to substantiating the paper's core novel claim over comprehensive-but-less-critical additional comparisons), and how you **communicated the resulting evaluation scope's limitations honestly** (either in the paper's limitations section, or to stakeholders, per the honest-limitations-reporting theme from the research methodology topic) rather than either silently omitting evaluation gaps or claiming more comprehensive validation than was actually performed. Close with the outcome — did the prioritization prove sound, or did a reviewer/stakeholder later flag exactly the gap you'd deprioritized, and what you learned about evaluation-scoping judgment from the experience.

---

### Q: "Describe a time you had to reproduce or build directly on top of another team's or another paper's published method, and it didn't work as well as claimed when you actually implemented/tested it. How did you handle this?"

**Answer (framework):**
Structure: describe the specific discrepancy (be concrete — what specific metric/quality gap you observed versus the original claims), your **systematic investigation process** (checking for implementation differences from underspecified details, per the paper reproduction discussion, verifying your evaluation protocol matched the original, checking whether the gap was specific to certain data/scenarios or a general shortfall), and how you ultimately resolved or explained the discrepancy — did you identify a genuine implementation gap on your end (a valuable, if sometimes deflating, learning experience), did you identify that the original claims depended on favorable conditions/data not representative of your actual use case, or did you conclude the original result genuinely doesn't reproduce as claimed (worth carefully documenting and potentially communicating back to the original authors or your own team). This demonstrates the rigorous, non-defensive investigative process that distinguishes genuine research engineering skill from either blind trust in published claims or reflexive skepticism without careful verification.

---

### Q: "How do you balance pursuing ambitious, higher-risk research directions (that could produce a significant breakthrough but might also not pan out) against more incremental, lower-risk improvements that are more likely to deliver reliable, if modest, progress?"

**Answer (framework):**
This tests research portfolio judgment. A strong answer avoids a one-size-fits-all stance ("always be ambitious" or "always be incremental") and instead describes a **deliberate portfolio approach** — allocating most effort toward reliable, incremental progress (which keeps a project/team delivering steady, valuable results) while reserving a smaller, bounded portion of time/compute for higher-risk, higher-reward exploration, with **explicit checkpoints** to assess whether a higher-risk direction is showing enough early promise to warrant continued investment (tying back to the negative-result decision-making discussed earlier) — describe a specific example from your own experience of making this kind of allocation decision, what informed the specific risk/reward balance you chose for that particular context (team/project stage, available runway, what the stakeholders' actual risk tolerance was), and the outcome.

---

### Q: "Where do you see generative 3D research heading over the next few years, and how are you positioning your own skills and research interests for that?"

**Answer (framework):**
Interviewers want genuine, informed perspective, not generic AI-hype enthusiasm. A strong answer discusses **specific, concrete trends** you've actually thought carefully about — e.g., the continued maturation of fast, feed-forward (rather than per-scene-optimization) generation approaches closing the speed gap needed for genuinely interactive creative tools, growing emphasis on generating production-ready assets (clean topology, proper PBR materials, per the mesh/texture topics) rather than just visually-impressive renders, the ongoing challenge of 3D data scarcity and how the field continues finding creative ways to leverage 2D priors, or growing interest in 4D/dynamic and physically-simulatable generative 3D content — and connects this to a **concrete, specific plan for developing your own relevant skills**, showing genuine, active engagement with a field that's evolving rapidly rather than treating your current knowledge as a fixed, finished destination.

---

### Q: "Describe your experience (or how you'd approach) collaborating with 3D artists or game/film production teams who may be skeptical that generative AI tools can actually meet their professional quality bar, rather than just producing impressive-looking demos."

**Answer (framework):**
This tests the ability to build genuine trust with a skeptical, quality-bar-conscious professional audience, echoing the task-based evaluation discussion from the evaluation topic. Good structure: describe how you'd **ground conversations in concrete, production-relevant metrics** (time saved on actual cleanup work, per the task-based user study discussion, rather than abstract quality scores) instead of impressive-looking but potentially cherry-picked demo reels. Describe how you'd **actively seek out and incorporate artist feedback into the research direction** (e.g., prioritizing clean topology/PBR compatibility specifically because artists flagged these as the actual blockers to using generated assets in production, rather than the research team unilaterally deciding what to prioritize based on academic benchmark performance alone) — genuine collaborative trust-building, similar to the cross-discipline collaboration themes emphasized throughout this series of repos, comes from demonstrably incorporating domain-expert feedback into the actual research priorities, not just presenting research results to them after the fact.

---
