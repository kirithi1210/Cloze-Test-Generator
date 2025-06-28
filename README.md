# Cloze Test Generator

This tool helps you easily create **fill-in-the-blank quizzes** (also called cloze tests) from any English passage. It uses **spaCy** to understand grammar and **BERT** (a smart language model) to decide which words are most important to hide. It comes with a **simple web interface** using Gradio (recommended in **Colab**).

📎 🔗 [Try the live demo in Colaab]


---

## ✨ What It Can Do

| Main Features | Extras |
|---------------|--------|
| ✅ Auto-hide important words | ✅ Avoid hiding names and places |
| ✅ Choose difficulty (easy/medium/hard) | ✅ Save quiz as a JSON file |
| ✅ Target specific word types (nouns, verbs, adjectives) | |
| ✅ Pick how many blanks you want | |
| ✅ Keeps the sentence easy to understand | |
| ✅ Use via website (Gradio) – recommended in Colab | |

---

## 🏗️ Setup Instructions

Only use this in **Google Colab**.
Paste the following in a Colab cell to install everything:

```python
!pip install transformers spacy torch gradio
!python -m spacy download en_core_web_sm
```

---

## 🚀 How to Use (Colab Only)

### 1. Open the Gradio Web Interface

Paste and run this in a Colab cell:
```python
!python cloze_generator.py
```
This will open a shareable link. You can paste a paragraph, choose difficulty, and get a quiz + answers instantly.

---

## 📁 What’s Included

```
├── cloze_generator.py          # Main program code
├── cloze_generator_demo.ipynb # Colab notebook for demo
├── README.md                   # This file
├── examples/
│   ├── passage1.txt            # Sample paragraph
│   ├── quiz1.json              # Auto-generated quiz + answers
└── requirements.txt            # (optional) pinned versions
```

### 📘 Notebook Demo

Want a step-by-step version? Open the ready-to-run Colab notebook here:

🔗 [Open `cloze_generator_demo.ipynb` in Colab](sandbox:/mnt/data/README.md)

---

## 📋 Example Quiz

Input passage:
> *Artificial intelligence is transforming industries by enabling machines to learn from data and perform tasks that normally require human intelligence.*

Command:
```python
!python cloze_generator.py   --text examples/passage1.txt   --num_blanks 4 --difficulty hard --pos_targets nouns verbs
```
Result:
```json
{
  "quiz": "Artificial ___(1)___ is ___(2)___ industries by enabling machines to ___(3)___ from data and perform ___(4)___ that normally require human intelligence.",
  "answers": {
    "1": "intelligence",
    "2": "transforming",
    "3": "learn",
    "4": "tasks"
  }
}
```

---

## ✅ Testing Ideas

If you want to test your code:
- Make sure it hides the right number of words
- Verify the answers match the original text
- Try turning on/off named entity protection and check the effect

---

## 🙌 Built With

- [spaCy](https://spacy.io/) – grammar, part of speech, and named entity detection
- [HuggingFace Transformers](https://huggingface.co/) – BERT model to rank word importance
- [Gradio](https://gradio.app/) – for a quick and simple user interface
