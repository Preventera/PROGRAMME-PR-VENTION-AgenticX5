# 🏗️ PROGRAMME-PRÉVENTION AgenticX5

> Architecture EDGY Native pour la gestion SST agentique au Québec

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![CNESST](https://img.shields.io/badge/CNESST-Conforme-green.svg)](https://www.cnesst.gouv.qc.ca/)
[![ISO 45001](https://img.shields.io/badge/ISO-45001:2018-blue.svg)](https://www.iso.org/iso-45001-occupational-health-and-safety.html)

## 📋 Description

Programme de Prévention SST entièrement modélisé avec les ontologies **EDGY Core** et **SafetyAgentic**, conforme aux exigences de la CNESST (LSST, LMRSST, RMPPCC) et ISO 45001:2018.

## 🎯 Caractéristiques

| Composant | Quantité |
|-----------|----------|
| **Acteurs SST** | 8 (Employeur, Travailleur, Superviseur, CoSS, RP, Membre CSS, Secouriste, Inspecteur) |
| **Rôles SST** | 8 avec bases légales LSST/CNESST |
| **Processus** | 9 (P1-P9 du programme de prévention) |
| **Agents IA** | 13 (Architecture AgenticX5 5 niveaux) |
| **Règles SHACL** | 30+ validations |
| **Triples RDF** | ~500 instances |

## 🏛️ Architecture EDGY
```
┌─────────────────────────────────────────────────────────────┐
│                    EDGY CORE                                │
├─────────────────────────────────────────────────────────────┤
│  Organization ─── Team ─── Person ─── Role                  │
│       │            │          │                             │
│       └──── Process ─── Task ─── RiskArea ─── DataFlow      │
└─────────────────────────────────────────────────────────────┘
                           │
                           ▼
┌─────────────────────────────────────────────────────────────┐
│                  SAFETY AGENTIC                             │
├─────────────────────────────────────────────────────────────┤
│  Agent (5 niveaux) ─── Task ─── RiskEvent ─── Mitigation    │
│  • PerceptionAgent     • NearMiss      • Preventive         │
│  • AnalysisAgent       • Incident      • Corrective         │
│  • DecisionAgent       • Accident                           │
│  • ActionAgent                                              │
│  • OrchestratorAgent                                        │
└─────────────────────────────────────────────────────────────┘
```

## 📦 Installation
```bash
# Cloner le repo
git clone https://github.com/Preventera/PROGRAMME-PR-VENTION-AgenticX5.git
cd PROGRAMME-PR-VENTION-AgenticX5

# Créer environnement virtuel
python -m venv venv
venv\Scripts\activate  # Windows

# Installer dépendances
pip install -r requirements.txt
```

## 🚀 Utilisation
```python
from rdflib import Graph
from pyshacl import validate

# Charger ontologies
graph = Graph()
graph.parse("ontologies/edgy_core.ttl", format="turtle")
graph.parse("ontologies/safety_agentic.ttl", format="turtle")
graph.parse("ontologies/programme_prevention_instances.ttl", format="turtle")

# Valider avec SHACL
shapes = Graph()
shapes.parse("ontologies/shacl_shapes.ttl", format="turtle")

conforms, results_graph, results_text = validate(
    graph, shacl_graph=shapes, inference='rdfs'
)
print(f"Conforme: {conforms}")
```

## 📊 Les 8 Acteurs SST

| # | Acteur | Base Légale | Responsabilités Clés |
|---|--------|-------------|----------------------|
| 1 | **Employeur** | LSST art. 51 | Responsable ultime SST |
| 2 | **Travailleur** | LSST art. 49 | Signaler dangers, porter EPI |
| 3 | **Superviseur** | LSST art. 51 | Application terrain |
| 4 | **CoSS** | LMRSST, RMPPCC | Programme prévention |
| 5 | **Représentant Prévention** | LSST art. 87-91 | Représenter travailleurs |
| 6 | **Membre Comité SST** | LSST art. 68-86 | Comité paritaire |
| 7 | **Secouriste** | Règl. premiers secours | Premiers soins |
| 8 | **Inspecteur CNESST** | LSST art. 177-193 | Conformité légale |

## 📈 Les 9 Processus du Programme

| # | Processus | Fréquence | Responsable |
|---|-----------|-----------|-------------|
| P1 | Élaboration programme prévention | Annuel | CoSS |
| P2 | Identification des risques | Mensuel | CoSS + Superviseur |
| P3 | Évaluation et priorisation | Mensuel | CoSS |
| P4 | Mise en place des contrôles | Continu | Superviseur |
| P5 | Formation et information | Continu | CoSS |
| P6 | Inspection et audit | Hebdomadaire | CoSS + RP |
| P7 | Gestion des incidents | Sur événement | CoSS |
| P8 | Surveillance médicale | Annuel | CoSS |
| P9 | Revue de direction | Trimestriel | Employeur |

## 🤖 Les 13 Agents IA (5 Niveaux)

### Niveau 1 - Collecte
- `IoTCollector` - Capteurs IoT (bruit, gaz, température)
- `VisionSafety` - Analyse vidéo (EPI, comportements)
- `DocumentScanner` - OCR documents SST

### Niveau 2 - Normalisation
- `DataValidator` - Validation SHACL
- `Harmonizer` - Fusion multi-sources

### Niveau 3 - Analyse
- `RiskAnalyzer` - Prédiction ML (94.7% précision)
- `ComplianceChecker` - Conformité CNESST/ISO
- `IncidentCorrelator` - Analyse causes profondes

### Niveau 4 - Recommandation
- `ActionRecommender` - Actions préventives/correctives
- `AlertManager` - Gestion alertes multi-canal
- `ReportGenerator` - Rapports automatisés

### Niveau 5 - Orchestration
- `Orchestrator` - Coordination multi-agents

## 🔗 Liens

- **EDGY-AgenticX5** : https://github.com/Preventera/EDGY-AgenticX5
- **GenAISafety** : https://genaisafety.ai
- **Preventera** : https://preventera.ai

## 📄 Licence

MIT License - © 2025 GenAISafety / Preventera

## 👤 Auteur

**Mario Deshaies**  
Founder Preventera | Chief AI Strategy Officer @ GenAISafety  
25+ années d'expérience IA × HSE