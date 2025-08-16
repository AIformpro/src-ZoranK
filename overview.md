# ZoranK — Overview

ZoranK implémente un noyau d'orchestration minimal : UCB1, ΔM11.3, mémoire fractale, quorum, et K‑Index.
Chaque module est conçu pour être remplaçable par une implémentation plus avancée (plug‑in).

- **UCB1** : équilibre exploration/exploitation pour router vers les meilleurs modules.
- **ΔM11.3** : surveille la stabilité (proxy de dispersion), déclenche rollback local.
- **Mémoire fractale** : quatre couches + export `.zgs` pour IA↔IA.
- **Quorum** : agrégation simple de décisions (keep/merge/drop).
- **K‑Index** : index inversé minimal (tokenisation naïve) — utilisable hors LLM.

Audit : `metrics.jsonl` (append‑only), `state.json` (optionnel selon intégrations).
