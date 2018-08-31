Review on the paper 
"Neural Machine Translation by Jointly Learning to Align and Translate"
=======================================================================

In this paper Bahdanau et al. introduce a new neural machine translation 
approach using attention mechanism.

It is known that existing models proposed recently for neural machine 
translation often belong to a family of encoder-decoders and encode a source 
sentence into a fixed-lenght vector from which a decoder generates a 
translation. However recent reseaches show the use of a fixed-length vector can 
be a bottleneck in improving the performance of long sentences translation, 
especially those that are longer than the sentences in the training corpus.

The authors propose an extention to the encoder-decoder model which learns to 
align and translate jointly, particularly implementing a mechanism of attention 
in the decoder. The most important distinguishing feature of the proposed 
attention mechanism from the basic encoder-decoder is that it does not attempt 
to encode a whole input sentence of vectors into a single-length vector. 
Instead, it encodes the input sentence into a sequence of vectors called 
annotations and searches through, or, in other words, chooses a subset of these 
vectors adaptivly while decoding the translation, that allows a proposed model 
to cope better with long sentences.

In the paper was proposed a novel architecture for neural machine translation, 
consisting of bidirectional RNN as an encoder and a decoder that emulates 
searching through a source sentence during decoding a translation. 

The encoder reads the input sequence in two ways, forward and backward, and 
calculates a sequence of concatenations of the forward and backward RNN states 
called annotations. 

The decoder then generates new output word using a weighted sum of these 
annotations, while weights are computed as a softmax function of scores. The 
scores, in turn, represent how well the each input word and the output word 
match and are computed using an alignment model that is jointly trained with 
all the other components of the proposed system and which.

The authors show that each weight corresponding to an annotation can be 
understood as a propability that the target word is aligned to, or translated 
from, a source word.

There is an evaluation of the proposed approach along with the comparison with 
RNN Encoder-Decoder is provided in Section 5 using the same parallel 
English-French corpora provided by ACL WMT’14 for both models during 
experiments.

Obtained results of the experiments shown in the Sections 4 and 5 prove the 
proposed model outperformes the conventional architecture. Moreover, the 
proposed approach provides an intuitive way to inspect the (soft-)alignment 
between the words in a generated translation and those in a source sentences.  
Thus, for example, as adjectives and nouns are typically ordered differently 
between French and English, the model is able to align the words preserving 
language-specific word order.

An exhaustive description of the model and training process used in the 
experiments are provided in the Appendicies A and B.

However, there are some drawbacks of the proposed approach as well.
The one is the requirement of computing the annotation weight of every word in 
the source sentence for each word in the translation. Another challenge is to 
better handle unknown, or rare words.

In conclusion, the authors highlight that the proposed approach achieves, with 
a single model, a translation performance comparable, or close, to the 
conventional phrase-based system, finds a linguistically plausible 
(soft-)alignment between a source sentence and the corresponding target 
sentente. Furthermore the model can work on its own and generates a translation 
from a source sentences directly rather than using a neural network as a part 
of the existing system.
