# AI Newsletter Research Results – Research Papers

**Research Focus:** Agentic AI systems — tool use, planning, and skill reuse in LLM agents.

## 📄 Featured Research Papers

1. **PlanBench-XL: Evaluating Long-Horizon Planning of LLM Tool-Use Agents in Large-Scale Tool Ecosystems**
   * Publisher: arXiv (University of Illinois Urbana-Champaign), published June 21, 2026
   * Description: PlanBench-XL is a new benchmark that tests whether LLM agents can plan across long, multi-step tasks in an ecosystem of 1,665 tools, where agents must discover relevant tools rather than see them all upfront, infer hidden sub-goals, and cope with tools that silently fail or mislead. Across 327 tasks requiring roughly 25 turns each, ten frontier models (GPT-5.4, Gemini-3.1-Pro, Qwen3, Llama-3.3, DeepSeek-V4-Flash, and others) were evaluated, with even the best model (Gemini-3.1-Pro) reaching only 77% accuracy and most staying under 60%. When tool paths were deliberately disrupted, accuracy for top models dropped by 20+ points, and "silent" tool failures proved far more damaging than tools that returned clear errors.
   * Possible Impact: This benchmark exposes that today's agents struggle most with adaptive re-planning and recognizing untrustworthy tool output rather than simple tool discovery — a finding directly relevant to any team building production agents on real, imperfect APIs. It also gives the field a reusable, LLM-generated benchmark-construction pipeline and a potential reinforcement-learning training ground for building more resilient agents.
   * Download Link: [https://arxiv.org/abs/2606.22388](https://arxiv.org/abs/2606.22388)

2. **SoK: Agentic Skills — Beyond Tool Use in LLM Agents**
   * Publisher: arXiv (University of Technology Sydney & CSIRO Data61), published February 24, 2026
   * Description: This "Systematization of Knowledge" formalizes the emerging idea of reusable "agentic skills" — packaged, callable procedures that let an agent avoid re-deriving the same multi-step solution from scratch every time. Drawing on 65 papers and 24 real systems, the authors define a skill lifecycle (discovery → refinement → storage → retrieval → execution → evaluation), seven design patterns (from Claude Code-style metadata disclosure to marketplace-distributed skill packages), and a taxonomy of skill representation and scope. It also documents a real supply-chain attack, "ClawHavoc," in which over 1,184 malicious skills were found in a public skill registry, exposing serious governance gaps in the current skill ecosystem.
   * Possible Impact: As "skills" become a mainstream way to extend agent capability (mirroring Claude's own Skills feature), this paper gives builders a shared vocabulary, a security threat model, and evidence that curated skills can lift task success by 16+ percentage points — while warning that self-generated, unverified skills often hurt performance and open serious security holes.
   * Download Link: [https://arxiv.org/abs/2602.20867](https://arxiv.org/abs/2602.20867)

3. **Tool-R0: Self-Evolving LLM Agents for Tool-Learning from Zero Data**
   * Publisher: arXiv (University of Illinois Urbana-Champaign & ETH Zurich), published February 24, 2026
   * Description: Tool-R0 trains tool-calling agents using a self-play loop between two LLM roles — a "Generator" that invents progressively harder tool-use tasks and a "Solver" that learns to complete them — with zero human-labeled training data. Using reinforcement learning (GRPO) with reward signals for format correctness, task validity, and calibrated difficulty, the framework lifted a small Qwen2.5-1.5B model's tool-calling accuracy by nearly 93% relative improvement, matching or beating models trained on tens of thousands of human-curated examples.
   * Possible Impact: This shows a credible path to scaling agent training beyond expensive human-curated datasets, and the outsized gains on smaller models suggest cheaper, weaker LLMs could reach strong tool-use performance — a meaningful cost lever for teams deploying agents at scale.
   * Download Link: [https://arxiv.org/abs/2602.21320](https://arxiv.org/abs/2602.21320)
