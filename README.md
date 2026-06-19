# Projet-Audio

Ce projet implémente une chaîne de traitement audio complète : de la transcription vocale (Speech-to-Text) à la génération de texte (Text-to-Text) et enfin à la synthèse vocale (Text-to-Speech).

### 1. Prérequis

Assurez-vous d'avoir les dépendances nécessaires installées. La première cellule du notebook (`!pip install ...`) s'en charge automatiquement.

### 2. Fichier Audio d'Entrée

Le projet utilise par défaut le fichier audio `testaudio.mp3` situé dans le répertoire `/content/`. Pour changer le fichier audio d'entrée, modifiez la variable `audio_path`:

```python
audio_path = '/content/testaudio.mp3' # Changez 'testaudio.mp3' par le nom de votre fichier
```

### 3. Fonctionnement des Étapes

*   **Récupération de l'Audio**: Charge le fichier `testaudio.mp3` et affiche ses propriétés (fréquence d'échantillonnage, durée).
*   **Speech-to-Text**: Utilise un modèle Whisper pour transcrire l'audio en texte. Le modèle `openai/whisper-small` est utilisé par défaut. Si votre audio est long (plus de 30 secondes), `return_timestamps=True` est activé pour gérer la transcription longue.
*   **Text-to-Text**: Prend le texte transcrit et utilise un modèle de génération de texte (`distilgpt2`) pour créer une réponse. Vous pouvez adapter le `prompt` pour guider la génération de texte.
*   **Text-to-Speech**: Convertit la réponse générée par le modèle de texte en un nouveau fichier audio (`generated_response.wav`) en utilisant un modèle de synthèse vocale (`facebook/mms-tts-eng`).
*   **Lecture de l'Audio**: Joue le fichier audio généré directement dans le notebook.

### 4. Personnalisation

*   **Modèles**: Vous pouvez expérimenter avec d'autres modèles Hugging Face pour chaque étape (Speech-to-Text, Text-to-Text, Text-to-Speech) en modifiant les noms des modèles dans les pipelines correspondants.
*   **Prompt LLM**: Ajustez le `prompt` dans l'étape Text-to-Text pour obtenir des types de réponses différents du LLM.

### 5. Exécution

Exécutez simplement les cellules du notebook séquentiellement pour voir le pipeline en action.
