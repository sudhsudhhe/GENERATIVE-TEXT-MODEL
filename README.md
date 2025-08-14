# GENERATIVE-TEXT-MODEL

"COMPANY": CODTECH IT SOLUTIONS

"NAME":M.V.SUDHEER BABU

"DOMAIN NAME":ARTIFICIAL INTELLIGENCE

"DURATION":6WEEKS

" Intern ID":CT06DY23

"MENTOR NAME":NEELA SANTOSH

Text generation is a branch of natural language processing (NLP) where a model learns patterns in text and produces coherent sequences based on an initial prompt. In this project, we implement a word-level Long Short-Term Memory (LSTM) neural network to generate coherent paragraphs from user-provided prompts.

LSTM networks are a special type of Recurrent Neural Network (RNN) designed to handle sequential data and capture long-term dependencies. Traditional RNNs suffer from the vanishing and exploding gradient problem, which limits their ability to remember information over long sequences. LSTMs solve this by using a gating mechanism — input, forget, and output gates — to control the flow of information and preserve relevant context over many time steps. This makes them well-suited for language modeling, where the meaning of a word often depends on many previous words.

In our implementation, we work at the word level rather than the character level. This means that the model’s vocabulary consists of unique words (plus special tokens like <pad>, <bos> for beginning-of-sequence, and <eos> for end-of-sequence). Working at the word level allows the model to learn semantic relationships between words, though it requires handling out-of-vocabulary words via an <unk> token.

The process begins with data preprocessing. We prepare a small sample corpus containing several short paragraphs on different topics (e.g., city life, nature, night sky). Each paragraph is tokenized into lowercase words and punctuation marks. We then build a vocabulary and map each token to a unique index. The text is converted into numerical sequences with added <bos> and <eos> markers. For training, we create input-target pairs, where the target sequence is simply the input sequence shifted by one word — this trains the model to predict the next word at each step.

The model architecture is straightforward:

Embedding Layer – Converts each token index into a dense vector representation, allowing the network to capture semantic relationships between words.

LSTM Layer – Processes the sequence of embeddings, maintaining a hidden state that carries context from earlier words.

Fully Connected Layer – Maps the LSTM output at each time step to a probability distribution over the vocabulary.

We train the model using Cross-Entropy Loss, ignoring <pad> tokens, and optimize with Adam for efficiency. Because the demo corpus is small, the model trains quickly (in under a minute for demonstration).

For text generation, we provide a prompt (e.g., “the city”), tokenize it, and feed it into the trained model. The model predicts the next word’s probability distribution, from which we sample using temperature scaling (to control randomness) and top-k sampling (to limit unlikely words). This process repeats until an <eos> token appears or a maximum length is reached.

The notebook also includes guidance on using pretrained GPT models from Hugging Face for higher-quality generation. GPT models, based on the Transformer architecture, can produce far more fluent and contextually rich paragraphs, especially when fine-tuned on specific topics.
