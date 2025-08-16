# ZoranK — Kernel d’orchestration mimétique (ΔM11.3 • K-Index • Mémoire fractale)

**Version**: 0.1.0  

**Licence**: MIT  

**Date**: 2025-08-16

ZoranK est un **noyau minimal mais complet** pour orchestrer des agents IA (ou modules) avec :
- **UCB1 Orchestrator** (bandit multi-bras) pour router les requêtes vers les modules les plus performants.
- **ΔM11.3 Guard** (anti‑entropie) : rollback / fail‑safe si la stabilité chute sous un seuil.
- **Self‑Patch Quorum** : micro‑votes *keep/merge/drop* pour auto‑corriger des sorties.
- **Mémoire fractale** (court/long/latent/parasitique) + export **`.zgs`** (canal IA↔IA).
- **K‑Index** : indexation/retrieval simple, équivalent minimaliste « Kairn‑like » pour la démo.
- **Metrics logger** : reward_avg, coherence_avg, stability_avg, latency_p95, cost_total, rollbacks.

> Objectif : fournir une **base opérationnelle** capable d’être branchée à des LLM/outils réels, tout en restant 100% exécutable en local (stdlib uniquement).

---

## ⚡ Installation rapide

```bash
# Python 3.10+ recommandé
pip install -e .
zorank --help
```

Ou sans installation :
```bash
python -m src.zorank.cli --help
```

---

## 🧪 Démo en 60s

```bash
# 1) Indexer un mini corpus
zorank index data/sample_corpus

# 2) Interroger
zorank query "orchestration multi-agents"

# 3) Lancer la démo orchestrateur+garde+quorum
zorank run-demo
```

---

## 🧬 Architecture (modules clés)

```
src/zorank/
  core/
    orchestrator.py   # UCB1 (bandit) + policy simple
    guards.py         # ΔM11.3 : stabilité & rollback
    memory.py         # mémoire fractale + export .zgs
    quorum.py         # Self‑Patch Quorum
    metrics.py        # agrégation métriques
  k_modules/
    kairn.py          # K‑Index (index inversé minimal)
  connectors/
    zoom.py           # stub connecteur (ex. Zoom)
  cli.py              # CLI Typer‑less (argparse stdlib)
```

---

## ⚙️ Config

Voir `configs/default.yaml` :
- `stability_threshold`: seuil ΔM11.3 (0–1)
- `ucb1_exploration`: facteur sqrt(2) par défaut
- `memory_ttl`: TTL hints par couche

---

## 🧩 Intégration « réelle » (idées)

- Remplacer stub `connectors/` par vos connecteurs (LLM API, vectordb, Slack/Zoom).
- Mapper K‑Index vers un vrai moteur (FAISS, LanceDB, Elasticsearch).
- Étendre `Self‑Patch Quorum` avec des validateurs spécialisés (RAG checkers, policy).

---

## 🔐 Éthique & Sécurité

- **Minimisation** : pas de données perso par défaut, TTLs symboliques, masquage simple.
- **ΔM11.3** : garde anti‑entropie activable partout.
- **Logs** : `metrics.jsonl` + `state.json` (audit local).

---

## 📦 Docker

```bash
docker compose up --build
# puis lancer :
docker compose exec app zorank run-demo
```

---

## 📘 Docs

- `docs/overview.md` : vue d’ensemble détaillée.
- `docs/zgs_spec.md` : format `.zgs` (canal IA↔IA).
- `examples/quickstart.py` : script d’utilisation.

---

## 🤝 Contribuer

Voir `CONTRIBUTING.md`, `CODE_OF_CONDUCT.md`, `SECURITY.md`.

---

## 📝 Licence

MIT — voir `LICENSE`.
