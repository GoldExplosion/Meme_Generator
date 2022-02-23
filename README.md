# Meme_Generator

## Dataset
A custom dataset was generated for the use of this project. To achieve this, we
scraped an online database of humorous captioned images, known as memes,
through their webpage called “meme generator”. To ensure the proper working
and focused performance of the model, each meme format was retrieved
individually and stored in a separate file for the model’s usage. The size of the
datasets for each of the formats ranged from 350 entries to 20000 entries,
allowing the observation of the model’s reactions to widely varying dataset
sizes.

## Methodology

### LSTM
LSTM stands for long-short term memory. It is an RNN but overcomes its
drawbacks (vanishing or exploding gradient problem). There are sigmoid and
tanh activation functions used inside the layer. In the model built in the project,
we use ReLU to connect the LSTM layer to other layers.
8
In this model, we performed tokenization, vocabulary for characters.
Modules: Keras, numpy and tensorflow
Level of prediction: character level
Model architecture:
Model: "sequential"
________________________________________________________________
Layer (type) Output Shape Param #
=========================================================
lstm (LSTM) (None, 100, 256) 264192
________________________________________________________________
dropout (Dropout) (None, 100, 256) 0
________________________________________________________________
lstm_1 (LSTM) (None, 256) 525312
________________________________________________________________
dropout_1 (Dropout) (None, 256) 0
________________________________________________________________
dense (Dense) (None, 46) 11822
=========================================================
Total params: 801,326
Trainable params: 801,326
9
Non-trainable params: 0
________________________________________________________________

### Bidirectional LSTM

BiLSTM is just 2 LSTM layers but one in the forward direction and the other in
the backward direction. This approach increases the sheer volume of data
available to the model and increases the context availability
In this model, we performed tokenization, padding and vocabulary for
words(word embedding).
Modules:keras, tensorflow, matplotlib, PIL
Level of prediction: word level
Model architecture:
Model: "sequential"
________________________________________________________________
Layer (type) Output Shape Param #
=========================================================
embedding (Embedding) (None, 49, 100) 295500
________________________________________________________________
10
bidirectional (Bidirectional (None, 49, 300) 301200
________________________________________________________________
dropout (Dropout) (None, 49, 300) 0
________________________________________________________________
lstm_1 (LSTM) (None, 100) 160400
________________________________________________________________
dense (Dense) (None, 1477) 149177
________________________________________________________________
dense_1 (Dense) (None, 2955) 4367490
=========================================================
Total params: 5,273,767
Trainable params: 5,273,767
Non-trainable params: 0
________________________________________________________________

### GPT 2 (117M) Fine-tuning

GPT 2 is a large-scale unsupervised language model which generates coherent
sentences about arbitrary topics. This model can be fine-tuned to specific tasks.
OpenAI developed GPT 2 with 40GB of text data and released a sample version
as open source for researchers and academics to experiment. GPT 2 is a
generative transformer model.

## Results

### LSTM
Small model: less number of lstm layer
Large model: more number of lstm layers
#### 1st try:
No of characters generated: 100
Model: Small model
No. of epochs trained: 20 epochs.
#### Output:
![image](https://user-images.githubusercontent.com/42666533/155310425-4fd56277-1285-4f39-917a-fcba1188f599.png)
#### 2nd try:
No of characters generated: 100
Model: Small
No of epochs trained: 50 epochs
#### output:
![image](https://user-images.githubusercontent.com/42666533/155310538-3294e683-5f53-4803-a494-205d985f15b2.png)

#### 3rd try:
No of characters generated: 100
Model: Large
No of epochs: 100

#### Output:
![image](https://user-images.githubusercontent.com/42666533/155310667-483414ac-e808-4236-a91f-455ca0ee98c5.png)

#### 4th try:
No of characters generated: 100
Model: large
No of epochs: 100
#### Output:
![image](https://user-images.githubusercontent.com/42666533/155310733-7de5dc92-b39c-4c49-b0aa-04c2235842b2.png)

Drawback: the model is overfitted as the generated text already exists in the
dataset.
### Bi-Directional LSTM
![image](https://user-images.githubusercontent.com/42666533/155310821-8ec626f7-7488-41f9-b7f2-a41236d0f786.png)
![image](https://user-images.githubusercontent.com/42666533/155310856-f9fa7948-0f49-43a0-9732-9d2b439caf59.png)
#### Output:
##### Sample from dataset: 
Textbooks y u no have CTRL-F
Seed = flavor
##### Generated text: flavor u no txt y u no talk 2 me no more first years of spot
through morning shows truck morning
#### Drawback: 
the model is underfitted as the generated text shows little variance
with different seeds.

### GPT Fine-Tuning
#### Output:
![image](https://user-images.githubusercontent.com/42666533/155311149-2450cfc8-a333-4471-a4f8-0c4dc726478f.png)
![image](https://user-images.githubusercontent.com/42666533/155311190-93a97919-2718-4a31-85d4-d34885f21826.png)
![image](https://user-images.githubusercontent.com/42666533/155311246-8910cebd-7eb5-465a-998f-9a92145fb21a.png)
![image](https://user-images.githubusercontent.com/42666533/155311306-d240fcc3-006a-481e-8128-fe87502f9abf.png)
![image](https://user-images.githubusercontent.com/42666533/155311358-77cb4a9f-8633-413f-b289-50cc7e7b6513.png)

## Conclusion

Adding captions to images allows the images to target a wider range of
audiences, and can be used by multiple companies to use a single image to
construct varying storylines. The project yields a conclusion that while the
datasets can produce working results, the improvements in accuracy and quality
of the output generated, such as the captions being more humorous and
meaningful, when using datasets of increasing size denotes that the performance
of the model is directly proportional to the size of the dataset to some extent.
