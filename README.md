# 🎙️ Hindi ASR Fine-Tuning & Text Normalization Pipeline
*A comprehensive NLP & Speech Processing pipeline built as an assignment for the AI Researcher Intern role at Josh Talks.*

## 📌 Project Overview
This project tackles the complexities of Hindi Automatic Speech Recognition (ASR). It involves fine-tuning OpenAI's Whisper model, cleaning messy Hindi text outputs, classifying spelling errors, and implementing advanced Lattice-based WER calculations.

## 🚀 Key Features Implemented

* **1. Whisper Model Fine-Tuning (`transformers`):** * Fine-tuned `openai/whisper-small` on a custom Hindi conversational dataset.
  * Dynamically handled broken audio/JSON links and tracked both **WER (Word Error Rate)** and **CER (Character Error Rate)** to prevent overfitting.
* **2. Advanced Text Normalization:** * Converted spoken Hindi numbers to digits (including fractional numbers like *'डेढ़' -> 1.5*).
  * Safely masked semantic idioms (e.g., *'नौ दो ग्यारह'* remained untouched).
  * Automatically tagged English loanwords used in Devanagari script (`[EN]इंटरव्यू[/EN]`).
* **3. Spelling Classification & Auto-Correction:** * Scanned a 1.77 Lakh word corpus using strictly compiled Devanagari regex rules.
  * Implemented Levenshtein distance (`difflib`) to automatically suggest correct spellings for incorrect transliterations.
* **4. Lattice-Based WER Computation:** * Overcame the limitations of strict Reference Transcripts by building a dynamic **Word Lattice**.
  * Used multi-model agreement (Voting Threshold) to dynamically generate valid alternative bins, significantly reducing unfair WER penalties for models correctly predicting phonetic/formatting variations. Includes graph-based visualization (`networkx`).

## 🛠️ Tech Stack
* **Core:** Python 3.10
* **ML/DL:** Hugging Face `transformers`, `datasets`, `evaluate`, `jiwer`, `torch`
* **Data Processing:** `pandas`, `numpy`, `regex`
* **Visualization:** `networkx`, `matplotlib`

## 📂 Repository Contents
* `ASR_Pipeline.ipynb`: The main Google Colab notebook containing all 4 modular tasks.
* `FT_Result_Optimized.xlsx`: Output metrics containing WER/CER baseline comparisons.
* `Q3_Final_Classification_with_Suggestions.csv`: Classification results for 1.77 Lakh Hindi words.
* `Sample_Lattice_Graph.png`: Directed graph visualization of the multi-model Lattice.
