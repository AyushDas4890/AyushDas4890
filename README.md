<!--
THESIS: The profile renders as the thing Ayush actually builds — a multi-agent system — and now it *runs*. Every visual is a hand-authored animated SVG whose motion explains a real technical idea, not decoration.
OWN-WORLD: obsidian #07070F ground, electric blue #60A5FA, gold/amber #F59E0B signal accent; mono for system text, heavy tracked sans for the wordmark.
MOTION: one-shot entrances (boot, track-in, draw-on, odometer roll) + quiet ambient loops (flowing edges, breathing nodes, marquee, waveform). Every entrance settles on a fully legible frame; every SVG honors prefers-reduced-motion.
STORY: living agent graph → three-layer thesis → a packet actually running the critic loop → four project cards that each animate their key idea → stack marquee → typed sign-off.
FINISH: static README; every SVG validated with xmllint and frame-checked in headless Chromium; motion system documented in DESIGN.md.
-->

<div align="center">

<img src="assets/hero.svg" alt="Ayush Das — AI & Machine Learning Engineer" width="100%">

<br>

[![Portfolio](https://img.shields.io/badge/PORTFOLIO-07070F?style=for-the-badge&labelColor=07070F&color=60A5FA)](https://portfolio-website-zeta-topaz-84.vercel.app/)
[![LinkedIn](https://img.shields.io/badge/LINKEDIN-07070F?style=for-the-badge&labelColor=07070F&color=60A5FA)](https://linkedin.com/in/ayushdas4890)
[![Email](https://img.shields.io/badge/EMAIL-07070F?style=for-the-badge&labelColor=07070F&color=F59E0B)](mailto:ayushdas4890@gmail.com)

</div>

<br>

I build **autonomous agent systems** — the kind that plan, retrieve, critique their own output, and recover from being wrong. Most of my work starts as a paper and ends as something with a URL you can open right now. Below is how I think about the problem, then the systems themselves.

<br>

<img src="assets/section-01.svg" alt="01 — The problem I keep solving: a single LLM call is a guess" width="100%">

A single LLM call is a guess. It cannot tell you how confident it is, cannot go find what it's missing, and cannot notice it answered the wrong question. Every system here is an answer to that: **give the model a loop, an external memory, and something that grades it.**

<img src="assets/layers.svg" alt="Three layers — orchestration as a cyclic graph, retrieval as nearest-neighbour search over vector memory, verification as a prediction with a calibrated interval" width="100%">

| Layer | How I build it |
|:--|:--|
| **Orchestration** | Cyclic graphs over linear chains — agents that route, retry, and terminate on a condition rather than running a fixed sequence |
| **Retrieval** | Vector search as working memory, not a lookup table — episodic context scoped per run, semantic context that survives across them |
| **Verification** | Self-critique as an explicit node, conformal intervals, SHAP and cross-attention attributions — a model that shows its reasoning is auditable |

<br>

<img src="assets/section-02.svg" alt="02 — Topology: how the systems are wired" width="100%">

<div align="center">
<img src="assets/architecture.svg" alt="Agent topology: a packet runs planner → search → read → critic, is sent back along the amber self-critique loop for more evidence, then passes critic and is streamed out by write — all over a dual-layer ChromaDB memory" width="100%">
</div>

Watch the packet. The critic is the part that matters. A linear `plan → search → write` chain produces confident nonsense when retrieval comes back thin. Making critique a **routing node** instead of a post-processing step means the graph can send itself back for more evidence before it ever writes — the difference between a demo and something you'd let near real work.

<br>

<img src="assets/section-03.svg" alt="03 — Selected work: four systems, four live demos" width="100%">

<a href="https://github.com/AyushDas4890/AI-Research-Assistant-Pipeline"><img src="assets/project-research.svg" alt="AI Research Assistant Pipeline — blocking vs streamed output, 87% lower perceived latency" width="100%"></a>

### [AI Research Assistant Pipeline](https://github.com/AyushDas4890/AI-Research-Assistant-Pipeline)

Five-agent LangGraph system that plans, searches, reads, self-critiques, and writes structured research reports. Dual-layer memory via ChromaDB; results stream to the client over SSE rather than blocking on the full generation, reducing perceived latency by 87%.

**`LangGraph`** **`OpenAI`** **`ChromaDB`** **`FastAPI`** **`Tavily`**

[**→ Open the live demo**](https://ayushdas4890-ai-research-assistant-pipeline-app-1sjuvf.streamlit.app/)

<img src="assets/divider.svg" alt="" width="100%">

<a href="https://github.com/AyushDas4890/Legal-Conflict-Resolver"><img src="assets/project-legal.svg" alt="Legal-Financial Conflict Resolver — clauses aligned across two documents, one contradiction flagged with attention spans" width="100%"></a>

### [Legal-Financial Conflict Resolver](https://github.com/AyushDas4890/Legal-Conflict-Resolver)

Five-phase NLP pipeline that detects contradictions between legal documents. DeBERTa-v3-large for entailment, FAISS for clause alignment, and cross-attention heatmaps so a reviewer can see *which spans* drove the call — explainability being non-optional in a legal context.

**`DeBERTa-v3`** **`HuggingFace`** **`FAISS`** **`spaCy`** **`FastAPI`** **`React`**

[**→ Open the live demo**](https://website-orpin-chi-25.vercel.app)

<img src="assets/divider.svg" alt="" width="100%">

<a href="https://github.com/AyushDas4890/cancer-tf-dashboard"><img src="assets/project-atlas.svg" alt="Cancer TF Discovery Atlas — 19 lineage-specific transcription factors orbiting, HNF1B, GATA3 and NKX2-1 highlighted, 98.76% classifier accuracy" width="100%"></a>

### [Cancer TF Discovery Atlas](https://github.com/AyushDas4890/cancer-tf-dashboard)

Pan-cancer transcription-factor analysis over TCGA RNA-Seq data, surfaced as an interactive 3D dashboard. Identifies 19 lineage-specific transcription factors at **98.76%** classifier accuracy — and independently rediscovers known master regulators (HNF1B, GATA3, NKX2-1), which is the result that says the pipeline is finding biology rather than fitting noise.

**`Next.js`** **`Three.js`** **`scikit-learn`** **`Python`** **`Tailwind`**

[**→ Open the live demo**](https://cancer-tf-dashboard.vercel.app)

<img src="assets/divider.svg" alt="" width="100%">

<a href="https://github.com/AyushDas4890/Carbon_Footprint_Generator"><img src="assets/project-carbon.svg" alt="Carbon Footprint Generator — predictions drawn with conformal intervals beside SHAP attribution bars" width="100%"></a>

### [Carbon Footprint Generator — C4Future](https://github.com/AyushDas4890/Carbon_Footprint_Generator)

Production carbon-accounting platform: XGBoost predictions wrapped in **conformal intervals** (so the output carries a calibrated uncertainty range, not a bare point estimate), a RAG sustainability advisor over real LCA data, an agentic bill-of-materials decomposer, and SHAP attributions on every prediction.

**`Django`** **`XGBoost`** **`LangChain`** **`ChromaDB`** **`OpenAI`** **`Docker`**

[**→ Open the live demo**](https://ad074890-c4future.hf.space)

<br>

<img src="assets/section-04.svg" alt="04 — Stack: tools, sorted by the layer they serve" width="100%">

<img src="assets/stack.svg" alt="Stack by layer, scrolling: orchestration, retrieval, modeling, serving" width="100%">

<div align="center">

**Orchestration** — LangGraph · LangChain · agent routing, tool use, streaming<br>
**Retrieval** — ChromaDB · FAISS · embedding pipelines, hybrid ranking<br>
**Modeling** — PyTorch · Transformers · DeBERTa fine-tuning · XGBoost · SHAP<br>
**Serving** — FastAPI · Django · Streamlit · Docker · Vercel · HF Spaces

</div>

<br>

<img src="assets/footer.svg" alt="Currently building agentic systems — open to collaborating on hard ones" width="100%">

<div align="center">

[**ayushdas4890@gmail.com**](mailto:ayushdas4890@gmail.com) &nbsp;·&nbsp; [**LinkedIn**](https://linkedin.com/in/ayushdas4890) &nbsp;·&nbsp; [**Portfolio**](https://portfolio-website-zeta-topaz-84.vercel.app/)

</div>
