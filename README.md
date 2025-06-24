# Medical Chatbot

This project implements a simple chatbot for providing medical information using natural language processing (NLP) and a neural network model. The chatbot is trained on a dataset of intents and patterns, and it features a graphical user interface (GUI) built with Tkinter.

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [File Structure](#file-structure)
- [How It Works](#how-it-works)
- [Training the Model](#training-the-model)
- [Running the Chatbot](#running-the-chatbot)
- [Contributing](#contributing)

## Overview
The Medical Chatbot is designed to respond to user queries related to medical information. It uses a neural network model trained on a dataset of intents (`intents.json`) to classify user input and generate appropriate responses. The GUI, built with Tkinter, allows users to interact with the chatbot in a user-friendly manner.

## Features
- **NLP Processing**: Tokenizes and lemmatizes user input to understand queries.
- **Neural Network Model**: Uses a Keras sequential model to predict intents based on user input.
- **GUI Interface**: A Tkinter-based GUI for user interaction.
- **Customizable Intents**: Easily extendable through the `intents.json` file.
- **Threshold-based Prediction**: Filters predictions to ensure reliable responses.

## Requirements
- Python 3.x
- Libraries:
  - `nltk`
  - `keras`
  - `tensorflow`
  - `numpy`
  - `pickle`
  - `tkinter` (usually included with Python)
- NLTK data:
  - `punkt`
  - `wordnet`

## Installation
1. **Clone the repository**:
   ```bash
   git clone https://github.com/bharathiprasad/Medical_chatbot.git
   cd <repository-directory>
   ```

2. **Install dependencies**:
   ```bash
   pip3 install nltk keras tensorflow numpy
   ```

3. **Download NLTK data**:
   ```python
   import nltk
   nltk.download('punkt')
   nltk.download('wordnet')
   ```

4. **Prepare the intents file**:
   Ensure the `intents.json` file is in the project directory with the appropriate structure (see [File Structure](#file-structure)).

## Usage
1. **Train the model**:
   Run the `train_chatbot.py` script to train the neural network model:
   ```bash
   python train_chatbot.py
   ```
   This will generate `words.pkl`, `classes.pkl`, and `chatbot_model.h5` files.

2. **Run the chatbot**:
   Start the GUI by running the `chatgui.py` script:
   ```bash
   python chatgui.py
   ```
   A window will open where you can type queries and receive responses from the chatbot.

## File Structure
- `train_chatbot.py`: Script to train the neural network model.
- `chatgui.py`: Script to run the Tkinter-based GUI for interacting with the chatbot.
- `intents.json`: JSON file containing the intents, patterns, and responses for the chatbot.
- `words.pkl`: Pickle file storing the vocabulary of lemmatized words.
- `classes.pkl`: Pickle file storing the list of intent classes.
- `chatbot_model.h5`: Trained Keras model for intent prediction.

## How It Works
1. **Training (`train_chatbot.py`)**:
   - Loads intents from `intents.json`.
   - Tokenizes and lemmatizes patterns to create a vocabulary (`words.pkl`) and intent classes (`classes.pkl`).
   - Creates a bag-of-words representation for each pattern.
   - Trains a Keras sequential model with three layers (128, 64, and output neurons) using stochastic gradient descent.
   - Saves the trained model to `chatbot_model.h5`.

2. **Chatbot GUI (`chatgui.py`)**:
   - Loads the trained model, vocabulary, and classes.
   - Processes user input by tokenizing and lemmatizing it, then creating a bag-of-words representation.
   - Predicts the intent using the trained model and filters predictions with a probability threshold of 0.25.
   - Selects a random response from the matched intent in `intents.json`.
   - Displays the conversation in a Tkinter GUI.

## Training the Model
To retrain the model (e.g., after updating `intents.json`):
1. Ensure `intents.json` is updated with new patterns and responses.
2. Run `train_chatbot.py` to generate new `words.pkl`, `classes.pkl`, and `chatbot_model.h5` files.

Example `intents.json` structure:
```json
{
  "intents": [
    {
      "tag": "greeting",
      "patterns": ["Hi", "Hello", "Hey"],
      "responses": ["Hello! How can I assist you?", "Hi there!"]
    },
    ...
  ]
}
```

## Running the Chatbot
1. Ensure all required files (`words.pkl`, `classes.pkl`, `chatbot_model.h5`, `intents.json`) are in the same directory as `chatgui.py`.
2. Run `chatgui.py` to open the GUI.
3. Type a message in the input box and click "Send" to interact with the chatbot.
4. The chatbot will display responses in the chat window.

## Contributing
Contributions are welcome! To contribute:
1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Make changes and test thoroughly.
4. Submit a pull request with a clear description of your changes.

