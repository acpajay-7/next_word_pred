# 🧠 Next Word Prediction using RNN

> **An NLP & Deep Learning project that predicts the next word in a sentence using a Recurrent Neural Network (RNN), with an interactive Streamlit web application.**

---

## 🚀 Project Overview

**Next Word Prediction** is a Natural Language Processing (NLP) application designed to predict the most likely next word based on the text entered by the user.

The project uses a **Recurrent Neural Network (RNN)** to learn patterns from text sequences. The trained model is integrated with a **Streamlit** interface, allowing users to enter a sentence and instantly receive a predicted next word.

### 💡 Example

```text
Input:
I love machine

Prediction:
learning
```

The application takes the user's input, converts it into a numerical sequence using a trained tokenizer, pads the sequence to the required length, and passes it to the trained RNN model for prediction.

---

## ✨ Features

* 🧠 **RNN-based language model**
* ✍️ Interactive text input
* 🔮 Predicts the next word
* ⚡ Fast inference using a pre-trained model
* 🌐 Simple and interactive Streamlit interface
* 🔢 Automatic text tokenization
* 📏 Sequence padding for model input
* 💾 Uses saved model and preprocessing artifacts
* 🎯 Beginner-friendly NLP & Deep Learning project

---

## 🏗️ Project Architecture

```text
                 ┌──────────────────┐
                 │    User Input    │
                 │  "I love data"   │
                 └────────┬─────────┘
                          │
                          ▼
                 ┌──────────────────┐
                 │    Tokenizer     │
                 │  Text → Numbers  │
                 └────────┬─────────┘
                          │
                          ▼
                 ┌──────────────────┐
                 │ Sequence Padding │
                 │  Fixed Length    │
                 └────────┬─────────┘
                          │
                          ▼
                 ┌──────────────────┐
                 │   Trained RNN    │
                 │      Model       │
                 └────────┬─────────┘
                          │
                          ▼
                 ┌──────────────────┐
                 │ Next Word Index  │
                 └────────┬─────────┘
                          │
                          ▼
                 ┌──────────────────┐
                 │ Predicted Word   │
                 └──────────────────┘
```

---

## 🔄 How It Works

The application follows the following pipeline:

### 1️⃣ User enters text

The user enters a sentence through the Streamlit interface.

```text
Type a sentence here...
```

### 2️⃣ Tokenization

The input sentence is converted into numerical tokens using the trained tokenizer.

```python
sequence = tokenizer.texts_to_sequences([text])[0]
```

### 3️⃣ Sequence Padding

The numerical sequence is padded to the required input length.

```python
sequence = pad_sequences(
    [sequence],
    maxlen=max_len-1,
    padding='pre'
)
```

### 4️⃣ RNN Prediction

The processed sequence is passed to the trained RNN model.

```python
preds = model.predict(sequence, verbose=0)
```

### 5️⃣ Select Most Likely Word

The model produces prediction probabilities. The word with the highest predicted index is selected.

```python
predicted_index = np.argmax(preds)
```

### 6️⃣ Display Prediction

The predicted word is displayed through Streamlit.

```text
Predicted Next Word: learning
```

---

## 🧰 Technologies Used

| Technology            | Purpose                                       |
| --------------------- | --------------------------------------------- |
| 🐍 Python             | Programming language                          |
| 🧠 TensorFlow / Keras | Deep Learning & RNN model                     |
| 🔢 NumPy              | Numerical operations                          |
| 🌐 Streamlit          | Interactive web application                   |
| 📝 NLP                | Text preprocessing & prediction               |
| 💾 Pickle             | Saving/loading tokenizer & preprocessing data |

---

## 📁 Project Structure

```text
next_word_pred/
│
├── 📄 app.py
├── 🧠 rnn_model.h5
├── 🔤 tokenizer.pkl
├── 📏 max_len.pkl
├── 📓 word_prediction.ipynb
├── 📋 requirements.txt
└── 📖 README.md
```

### File Description

| File                    | Description                                          |
| ----------------------- | ---------------------------------------------------- |
| `app.py`                | Streamlit application and prediction logic           |
| `rnn_model.h5`          | Trained RNN deep learning model                      |
| `tokenizer.pkl`         | Saved tokenizer used for text-to-sequence conversion |
| `max_len.pkl`           | Saved maximum sequence length                        |
| `word_prediction.ipynb` | Notebook containing model development/training work  |
| `requirements.txt`      | Required Python dependencies                         |
| `README.md`             | Project documentation                                |

The Streamlit application loads the trained model, tokenizer, and maximum sequence length when the app starts.

---

## ⚙️ Installation

### 1. Clone the repository

```bash
git clone https://github.com/your-username/next_word_pred.git
```

### 2. Navigate to the project

```bash
cd next_word_pred
```

### 3. Create a virtual environment

```bash
python -m venv .venv
```

### 4. Activate the environment

#### Windows

```powershell
.venv\Scripts\activate
```

#### Linux / macOS

```bash
source .venv/bin/activate
```

### 5. Install dependencies

```bash
pip install -r requirements.txt
```

The project requires:

```text
streamlit
numpy
tensorflow
```

---

## ▶️ Run the Application

Start the Streamlit application using:

```bash
streamlit run app.py
```

After starting the application, Streamlit will provide a local URL such as:

```text
http://localhost:8501
```

Open the URL in your browser.

---

## 🖥️ Application Interface

The application provides a simple interface where users can enter text and click **Predict Next Word**.

```text
┌──────────────────────────────────────┐
│     🧠 Next Word Prediction (RNN)    │
│                                      │
│ Enter a sentence:                    │
│ ┌──────────────────────────────────┐ │
│ │ I love machine                   │ │
│ └──────────────────────────────────┘ │
│                                      │
│       [ Predict Next Word ]          │
│                                      │
│  Predicted Next Word: learning       │
└──────────────────────────────────────┘
```

The current application uses a centered Streamlit layout and displays the prediction as a success message.

---

## 🧪 Example Predictions

Try entering text similar to the language patterns present in the training data.

| Input              | Possible Output |
| ------------------ | --------------- |
| `I love machine`   | `learning`      |
| `data science is`  | `interesting`   |
| `deep learning is` | `powerful`      |
| `I am learning`    | `Python`        |

> ⚠️ Actual predictions depend on the vocabulary and training data used to train the model.

---

## 🧠 Deep Learning Concepts Used

This project demonstrates several important concepts in NLP and Deep Learning:

### 🔹 Natural Language Processing

Text is converted into a numerical representation that can be processed by a neural network.

### 🔹 Tokenization

Words are mapped to numerical indices.

```text
"I love data"
       ↓
[12, 7, 45]
```

### 🔹 Sequence Modeling

The model learns relationships between words in a sequence.

```text
I → love → machine → learning
```

### 🔹 Recurrent Neural Network

RNNs are designed to work with sequential data and can learn patterns from previous elements in a sequence.

### 🔹 Padding

Sequences are converted into a consistent length before being passed to the model.

### 🔹 Softmax / Probability Prediction

The model predicts probabilities for possible words, and the highest-scoring prediction is selected.

---

## 🎯 Learning Objectives

Through this project, I explored:

* Natural Language Processing
* Text preprocessing
* Tokenization
* Sequence generation
* Padding sequences
* RNN architecture
* Deep Learning model training
* Model inference
* Saving/loading trained models
* Streamlit application development
* Integrating a Deep Learning model into a web application

---

## 🌍 Real-World Applications

Next Word Prediction is an important concept behind many modern applications.

### 💬 Smart Keyboards

Suggesting the next word while typing.

### 📧 Email Assistance

Helping users complete sentences and write emails faster.

### 🔎 Search Engines

Predicting what a user is likely to type next.

### 🤖 Chatbots

Improving conversational text generation.

### ✍️ Writing Assistants

Helping users complete sentences and generate text.

---

## 📈 Future Improvements

The current application predicts a single next word. It can be improved in several ways:

### 🔮 Multiple Word Suggestions

Instead of returning only one word:

```text
machine → learning
         → vision
         → translation
```

### 📊 Top-K Predictions

Display the top 3 or top 5 predictions with probabilities.

### 🧠 LSTM / GRU

Replace the basic RNN with:

* LSTM
* GRU
* Bidirectional LSTM

to improve sequence learning.

### 🎨 Improved UI

Add:

* Custom CSS
* Prediction cards
* Probability bars
* Dark mode
* Example buttons

### 📚 Larger Dataset

Train the model on a much larger text corpus to improve vocabulary and prediction quality.

### 🚀 Deployment

Deploy the Streamlit application so it can be accessed through a public URL.

---

## ⚠️ Limitations

* Prediction quality depends heavily on the training dataset.
* The model can only predict words available in its learned vocabulary.
* A basic RNN may struggle with long-term dependencies.
* Predictions may not always be grammatically or semantically correct.
* The current application predicts only one next word.

---

## 📌 Important Note

The trained model and preprocessing files must be available in the expected project directory for the Streamlit application to work correctly.

The application loads:

```text
rnn_model.h5
tokenizer.pkl
max_len.pkl
```

and uses them during prediction.

---

## 💼 Skills Demonstrated

This project demonstrates practical experience with:

```text
Python
│
├── Natural Language Processing
├── Deep Learning
├── Recurrent Neural Networks
├── TensorFlow / Keras
├── NumPy
├── Text Tokenization
├── Sequence Processing
├── Model Inference
├── Streamlit
└── Machine Learning Deployment Concepts
```

---

## 👨‍💻 Author

### **Ajay**

**Aspiring Data Scientist | Data Analyst | Machine Learning Engineer**

📍 India

---

