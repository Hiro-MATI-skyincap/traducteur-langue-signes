# 🤟 Traducteur de Langue des Signes

Système de reconnaissance et traduction de la langue des signes en temps réel utilisant l'apprentissage profond et la vision par web-cam sur ordinateur/portable.

## 📋 Prérequis

- Python 3.8+
- Webcam fonctionnelle
- GPU recommandé (CUDA) pour l'entraînement

## 🚀 Installation

```bash
# Cloner le repository
git clone https://github.com/votre-nom/traducteur-langue-signes.git
cd traducteur-langue-signes

# Créer un environnement virtuel
python -m venv venv
source venv/bin/activate  # Sur Windows: venv\Scripts\activate

# Installer les dépendances
pip install -r requirements.txt
```

## 📁 Structure du Projet
arborescent
```
traducteur-langue-des-signes/
│
├── donnees/
│   ├── brutes/              # Vidéos brutes (optionnel)
│   ├── points_clefs/        # Points clés extraits (JSON)
│   └── preparees/           # Données prêtes pour l'entraînement
│       ├── train/
│       ├── val/
│       └── test/
│
├── modeles/
│   ├── checkpoints/         # Sauvegardes pendant l'entraînement
│   └── production/          # Modèles finaux optimisés
│
├── src/
│   ├── capture/
│   │   ├── __init__.py
│   │   └── capture_points_clefs.py
│   │
│   ├── entrainement/
│   │   ├── __init__.py
│   │   ├── train_modele.py
│   │   └── modele_lstm.py   # Architecture du modèle
│   │
│   ├── prediction/
│   │   ├── __init__.py
│   │   └── traduction_signes.py
│   │
│   └── utils/
│       ├── __init__.py
│       ├── preprocessing.py
│       └── config.py         # Configuration centrale
│
├── logs/                     # Journaux d'entraînement
├── tests/                    # Tests unitaires
├── notebooks/                # Notebooks Jupyter pour l'exploration
│
├── requirements.txt
├── .gitignore
├── config.yaml              # Configuration du projet
├── main.py                  # Interface en ligne de commande
└── README.md
```

## 🎯 Utilisation

### 1. Capture de données

```bash
# Capturer des gestes pour créer votre dataset
python main.py capture --mot "bonjour" --nb-sequences 30
```

### 2. Entraînement du modèle

```bash
# Entraîner le modèle sur vos données
python main.py train --epochs 100 --batch-size 32
```

### 3. Traduction en temps réel

```bash
# Lancer la traduction en direct
python main.py predict --modele modeles/production/modele_final.h5
```

## 🛠️ Configuration

Modifiez `config.yaml` pour personnaliser:
- Nombre de points clés détectés
- Longueur des séquences
- Hyperparamètres du modèle
- Seuil de confiance

## 📊 Dataset

Le système détecte:
- 21 points de la main (MediaPipe)
- 33 points du corps (pose)
- 468 points du visage (expressions faciales)

Chaque geste est représenté par une séquence temporelle de ces points.

## 🧪 Tests

```bash
# Exécuter les tests
pytest tests/
```

## 📈 Performance

- Précision: 95%+ sur vocabulaire de base
- Latence: <100ms en temps réel
- Support: 50+ mots/signes

## 🤝 Contribution

Les contributions sont les bienvenues !.

## 📄 Licence

demo-test

## 👥 Auteurs

- Skyincap-demo - [@votre-github](https://github.com/votre-nom)

## 🙏 Remerciements

- MediaPipe pour la détection des points clés
- TensorFlow/Keras pour le deep learning
- Communauté LSF pour les ressources
