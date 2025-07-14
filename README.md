# 🔬 YOLOv13 Independent Validation Study

## 🎯 Objectif
Validation indépendante et transparente des performances de YOLOv13 par rapport à YOLOv12 et YOLO11 sur le dataset COCO, en réponse aux discordances identifiées dans [Ultralytics Issue #21243](https://github.com/ultralytics/ultralytics/issues/21243).

## 🚨 Problématique Identifiée
- **Discordance mAP** : YOLOv12x officiel = 55.2-55.4 vs YOLOv13 paper = 54.8
- **Latence** : YOLOv13 plus lent que YOLOv8 malgré les améliorations claims
- **Besoin** : Validation indépendante avec méthodologie standardisée

## 🔬 Méthodologie de Validation

### Dataset & Protocole
- **Dataset** : MS COCO 2017 validation set (5K images)
- **Métriques** : mAP50, mAP75, mAP50-95, temps d'inférence, usage mémoire
- **Hardware** : AMD Ryzen 9 7945HX + RTX 4060 (standardisé)
- **Reproductibilité** : Scripts automatisés + seeds fixes

### Modèles Comparés
| Modèle | Version | Source | Statut |
|--------|---------|--------|--------|
| YOLOv13-N/S/L/X | Latest | iMoonLab | 🔄 En cours |
| YOLOv12-N/S/L/X | Latest | sunsmarterjie | 🔄 En cours |
| YOLO11-N/S/L/X | Latest | Ultralytics | 🔄 En cours |

## 📊 Résultats Préliminaires

### Agricultural Dataset (Weeds-3) - Validé ✅
| Modèle | mAP50 | Recall | Amélioration |
|--------|-------|--------|--------------|
| YOLOv13 + SDPA | 82.9% | 73.5% | Baseline |
| YOLOv12 + SDPA | 76.7% | 66.4% | +6.2% pour YOLOv13 |

### COCO Validation - En Cours 🔄
| Modèle | mAP50-95 | mAP50 | mAP75 | Latence (ms) | Statut |
|--------|----------|-------|-------|--------------|--------|
| YOLOv13-N | - | - | - | - | ⏳ Planifié |
| YOLOv12-N | - | - | - | - | ⏳ Planifié |
| YOLO11-N | - | - | - | - | ⏳ Planifié |

*Résultats complets attendus : 7-10 jours*

## 🛠️ Quick Start

```bash
# Clone repository
git clone https://github.com/kennedy-kitoko/yolov13-validation-study.git
cd yolov13-validation-study

# Setup environment
conda create -n yolov13-val python=3.11
conda activate yolov13-val
pip install -r requirements.txt

# Run validation (après setup complet)
python scripts/run_validation.py --model yolov13n --dataset coco
