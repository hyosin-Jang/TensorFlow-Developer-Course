## Using keras APIs

- by setting this hyperparameter(num_words in Tokenizer), what the tokenizer will do is take the top 100 words by volume and just encode those.
- The tokenizer provides a word index property which returns a dictionary containing key value pairs, where the key is the word, and the value is the token for that word

![Untitled (49)](https://user-images.githubusercontent.com/71035113/151011744-d892f2e6-516b-4678-9703-7dd94d67f173.png)

## The reason why using tokenizer

- instead of having the words being trained in a neural network, you can actually have the number representing that word and it just makes your life a lot easier.

## The result of tokenizer

- you may have noticed that I have a lowercase i here and an uppercase I here.
- you'll see the exclamation from dog was removed.

## Text to sequence

- With new tokens for my new words like amazing, think, is, and do.
- At the bottom is my list of sentences that have been encoded into integer lists, with the tokens replacing the words.
- So for example, I love my dog becomes 4, 2, 1, 3.

## Looking more at the Tokenizer

- First of all, we really need a lot of training data to get a broad vocabulary or we could end up with sentences like, my dog my, like we just did.
- Secondly, in many cases, it's a good idea to instead of just ignoring unseen words, to put a special value in when an unseen word is encountered.
    - oov for outer vocabulary to be used for words that aren't in the word index.
    - but remember that it should be something unique and distinct that isn't confused with a real word.

## Padding

- As we do padding in classifying images, we also do padding in tokenizing texts.
- First, in order to use the padding functions you'll have to import `pad sequences` from `tensorflow.carastoppreprocessing.sequence`.

![Untitled (50)](https://user-images.githubusercontent.com/71035113/151011781-c4e76ec7-5dc6-4d72-acfc-08f7a004c01a.png)

- If we have maxlen parameters shorter than the longest sentences, you will lose from the beginning of the sentence.
- If you want to override this so that you lose from the end instead, you can do so with the truncating parameter.

### Sarcasm datasets by Rishabh Misra with details on Kaggle

- The first is sarcastic, is our label.
    - sarcastic: 1,  otherwise: 0
- The second is a headline
- the third is the link to the article that the headline describes.

![Untitled (51)](https://user-images.githubusercontent.com/71035113/151011786-5be1de7d-4cbd-4ba7-9492-21c75fafed67.png)
)
- So first you need to import JSON.
    - This allows you to load data in JSON format and automatically create a Python data structure from it.
- To do that you simply open the file, and pass it to json.load and you'll get a list containing lists of the three types of data: headlines, URLs, and is_sarcastic labels.
- Because I want the sentences as a list of their own to pass to the tokenizer, I can then create a list of sentences and later, if I want the labels for creating a neural network, I can create a list of them too.
- While I'm at it, I may as well do URLs even though I'm not going to use them here but you might want to

## extra test dataset

- [ML Resources - BBC Datasets (ucd.ie)](http://mlg.ucd.ie/datasets/bbc.html)
