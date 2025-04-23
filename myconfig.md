# Station de Travail Ultra-Haut de Gamme (Linux Fedora Custom)

## 🧑‍💻 Utilisateur Final

- Interface fluide type macOS avec base GNOME 47 personnalisée
- Dock façon macOS, coins arrondis, flou, effets Wayland
- Gestes tactiles, raccourcis clavier Apple natifs
- Multi-workspaces sur 6 écrans UltraFine 5K

---

## 💻 Environnement Graphique

- **Wayland + GNOME 47 modifié**
- Layout type macOS
- Multi-écran Wayland (6 écrans Retina 5K)
- Support clavier Apple (⌘ = Super, Option = Alt)

---

## ⚙️ Système de Base

- Basé sur **Fedora** mixé avec du **MacOS**
- `dnf5`, `SELinux`, `Flatpak`, `systemd`
- Pilotes NVIDIA propriétaires (multi-GPU pris en charge)
- Logiciels préinstallés : **VS Code**, **GitHub**, **Google Chrome**

---

## 🐳 Environnement de Développement

- Isolation via **Docker uniquement**
- Conteneurs pour langages, LLM locaux, outils dev, monitoring
- GPUs adressables individuellement via `CUDA_VISIBLE_DEVICES`

---

## 🧬 Kernel Linux Optimisé

- Optimisations haute performance (NUMA, I/O schedulers, IRQ affinity)
- Pilotes réseau Ethernet 10 GbE et Wi-Fi 7 inclus

---

## 🧊 Système de Refroidissement Watercooling (Custom Loop)

| Composant | Modèle recommandé | Prix approximatif |
| --- | --- | --- |
| Waterblock CPU | EK-Quantum Velocity² sTRX5 | 200 € |
| Waterblocks GPU (×2) | EK-Quantum Vector² RTX 6000 Ada | 400 € ×2 |
| Radiateurs (×2) | EK-CoolStream 360 PE | 120 € ×2 |
| Pompe | EK-Loop D5 G3 PWM | 130 € |
| Réservoir | EK-RES X3 250 ou combo | 80–150 € |
| Tubes rigides (acrylique) | EK-HDC 12mm ou Corsair Hydro X | 50 € |
| Liquide de refroidissement | EK CryoFuel / Corsair HydroX | 25 € |
| Ventilateurs (×6) | Noctua NF-F12 / Phanteks T30 | 30 € ×6 = 180 € |

**💧 Total watercooling : ~1 400–1 500 €**

---

## 🛠️ Matériel (Hardware)

| Composant | Détail | Prix approximatif |
| --- | --- | --- |
| **Boîtier** | Lian Li PC-O11 Dynamic EVO XL | 250 € |
| **CPU** | AMD Threadripper Pro 7995WX (96 cœurs / 192 threads) | 9 000 € |
| **GPU** | 2 × NVIDIA RTX 6000 Ada (48 Go GDDR6 ECC) | 13 000 € |
| **RAM** | 512 Go DDR5 ECC REG (8 × 64 Go) | 4 000 € |
| **Stockage** | 2 × NVMe Gen5 4 To + carte d’extension RAID PCIe | 1 100 € |
| **Carte mère** | ASUS Pro WS WRX90E-SAGE SE | 1 000 € |
| **Alimentation** | Corsair AX1600i Platinum 1600W | 500 € |
| **Réseau** | Intel X550-T2 (Ethernet 10 GbE) + Wi-Fi 6E/7 PCIe | 350 € |

---

## 📺 Affichage – 6 Écrans LG UltraFine 5K

| Modèle | Détail | Prix unitaire | Total |
| --- | --- | --- | --- |
| LG UltraFine 5K 27MD5KL-B | 27”, 5120×2880, DCI-P3, USB-C + Thunderbolt | 1 300 € | 7 800 € |
- Connexion via adaptateurs USB-C actifs ou DisplayPort Alt Mode
- Résolution cumulée : **88 millions de pixels**

---

## 💵 Total Estimé Global : **~39 370 €**

---

## 🌟 Rendu Final de l’OS

### 🚟️ 1. Fenêtres flottantes & gestion visuelle

- Thème GTK + Shell à la macOS Ventura : coins arrondis, ombres, blur
- **Effets** : gélatine (wobbly), animations douces, flou GNOME/Wayfire
- Thèmes utilisés : `WhiteSur`, `Colloid`, `Mojave`

### 🧠 2. Dock intelligent

- Inspiré du dock macOS, centré, flou, effet de zoom icônes
- Masquage auto sauf contact souris bas écran
- Extensions : `Dash to Dock`, `Plank`, `Just Perfection`

### 🚀 3. Launchpad

- Vue grille façon Apple Launchpad via `gnome-shell-extension-arc-menu`

### 📂 4. Finder-like File Manager

- `Nautilus` modifié ou fork (gFiles), vue colonnes, tags, couleurs

### 🔋 5. Gestes Trackpad

- 4 doigts droite/gauche : changer de bureau
- 4 doigts vers le haut : overview GNOME
- Outils : `libinput-gestures`, `touchegg`, `xdotool`, `wmctrl`

### 🧰 6. Compositing Wayland

- Wayland + Mutter modifié, flou, multi-écran 5K, blur my shell, arcmenu, etc.

### 🧪 7. Siri intégré

- Bouton orbe Siri
- 🔘 1. **Bouton Flottant "Siri-like"**
    - Bouton inspiré de l’orbe Siri de macOS Sonoma
    - Toujours visible dans un coin de l’écran (overlay via GNOME Shell Extension)
    - Clic = activation du microphone

> 🛠️ Technos : GNOME Shell Extension personnalisée (JS + Clutter) + gestion micro via PipeWire
> 

---

- 🎙️ 2. **Capture de la Voix**
    - Micro capté via **PipeWire** (`pw-cli`, `pactl`, etc.)
    - Audio au format PCM / FLAC / Opus → buffer
    - Bonus :
        - Détection automatique de la voix (VAD)
        - Activation possible via hotword (ex : *“Hey SuperPC”*)

> 🛠️ Librairies suggérées : vosk, whisper.cpp local (fallback), ou simple envoi brut du buffer audio
> 

---

- 📡 3. **Transmission au Coordinateur**
    - Le **Coordinateur local** reçoit l’audio (stream ou fichier temporaire) et le renvoie à un Mac Studio

> 🛠️ Protocoles : REST, WebSocket, gRPC ou ZeroMQ
> 

---

- 🔬 4. **Traitement sur Mac Studio**
    - Utilisation du **Neural Engine (ANE)** via Core ML pour :
        - **Transcription vocale** ultra rapide (ex : `Whisper` optimisé)
        - Analyse via LLM local (compréhension, réponse)
        - Synthèse vocale (`AVSpeechSynthesizer`, etc.)

> 🛠️ Tech stack Apple : Core ML, Metal, Swift, coremltools, pyobjc
> 

---

- ⏪ 5. **Retour & Affichage des Résultats**
    - Le coordinateur reçoit la réponse textuelle ou audio
    - Affichage dans une bulle visuelle stylée (overlay GNOME / notification)
    - En cas de réponse vocale : lecture via `speech-dispatcher` ou `espeak-ng`

---

- 💬 6. **Comportement de l’Interface**
    - 📋 A. Afichage
        - Liste des actions
            
            
            | Action | Comportement |
            | --- | --- |
            | Réponse vocale reçue | Affichage du **texte stylisé à gauche** du bouton |
            | Texte trop long | **Morphose fluide** : déformation, dispersion, disparition |
            | Nouvelle requête | Transition douce : remplacement de l’ancien texte |
            | Inactivité prolongée | Effacement automatique (ex : après 55 secondes) |
    - 🎨 B. **Style Visuel "Gemmini"**
        - **Police** : Manuscrite, douce et ronde (`Caveat`, `Pacifico`, ou sur mesure)
        - **Effets** :
        - Apparition du texte avec **pulsation douce** (scale + blur)
        - Couleurs pastel (blanc cassé, lavande)
        - Fond semi-transparent, flou arrière (GNOME / Wayfire)
        - Coins arrondis, animation non intrusive

> ✨ Objectif : élégance, futurisme doux, lisibilité maximale
> 

---

- 🔄 7. **Synchronisation Audio ↔ Texte**
    - **Début de la lecture vocale = apparition du texte**
    - Optionnel :
        - Affichage **mot à mot** synchronisé (live caption)
        - Ou effet de **révélation progressive** (type "machine à écrire")

---

## 🧰 Déchargement Dynamique vers 4 Mac Studio (M3 Ultra)

### ⚖️ Seuils et Taux de Déclenchement

| Ressource | Début transfert | Taux de transfert |
| --- | --- | --- |
| CPU | 95 cœurs | (2400/95) % = **25.26%** |
| GPU | 95% cœurs | (6400/95) % = **67.37%** |
| RAM | 450 Go | (12800/450) % = **28.44%** |
| Neural Engine | Immédiat | 100% |

### 🚀 Schéma Fonctionnel

- ✉️ Tâches dépassant les seuils → envoyées au **coordinateur** local
- 🧳 Coordinateur → dispatch sur les **4 Mac Studio (M3 Ultra)**
- 🛎️ Les résultats sont récupérés automatiquement

---

## 📊 Performance Matérielle Totale Estimée (PC + Mac Studio)

| Élément | Total estimé |
| --- | --- |
| **CPU** | 192 cœurs / 384 threads |
| **GPU** | 415-416 cœurs |
| **RAM** | 512 Go |
| **Stockage** | 12 To  |
| **Affichage** | 6 × 5K Retina (88 Mpx cumulés) |
| **Connectivité** | Ethernet 10 GbE, Wi-Fi 7 |
| **Watercooling** | Custom loop complet |
| **OS** | Fedora customisé GNOME 47 (style macOS) |
| **Docking / UI** | Dock, Launchpad, Finder-like, gestes multitouch, Siri button |