# WordSenseEmbeddingsFromTranslationDictionaryCorrelationAnalysis

[![Build Status](https://travis-ci.org/oxinabox/WordSenseEmbeddingsFromTranslationDictionaryCorrelationAnalysis.jl.svg?branch=master)](https://travis-ci.org/oxinabox/WordSenseEmbeddingsFromTranslationDictionaryCorrelationAnalysis.jl)

[![Coverage Status](https://coveralls.io/repos/oxinabox/WordSenseEmbeddingsFromTranslationDictionaryCorrelationAnalysis.jl/badge.svg?branch=master&service=github)](https://coveralls.io/github/oxinabox/WordSenseEmbeddingsFromTranslationDictionaryCorrelationAnalysis.jl?branch=master)

[![codecov.io](http://codecov.io/github/oxinabox/WordSenseEmbeddingsFromTranslationDictionaryCorrelationAnalysis.jl/coverage.svg?branch=master)](http://codecov.io/github/oxinabox/WordSenseEmbeddingsFromTranslationDictionaryCorrelationAnalysis.jl?branch=master)


This is kind of related to http://anthology.aclweb.org/E/E14/E14-1049.pdf


Here is the idea: ripped straight from facebook discussion about it.
(Maximum casual tier)

Lyndon 'Frames' White
Crazy midnight idea.
Start with a set of word embeddings for every word in every language in babelnet (or some other translators dictionary).
For each word translation group (/group/multi-language set of synonyms) convert them into set of aligned pairs (n-tuples where n is number of languages being supported), by appending random vectors to each word vetor so each alignment is unique.
Applies CCA (gCCA for >1 language).
Now your vectors from all languages are in one space.
Also you've gone from word vectors to word sense vectors kinda sneaky like. (Though I think detecting word sense existances using translators dictionaries is fairly standard)
I think this idea is cute.

Kimberley Larking
I don't fully understand this, but if it's what I think, it sounds like a great idea! You could do a lot of interesting things with it.

Roland Kerr
I try to stay on top of your area at a surface level, but I'm not sure why you would want to add random vectors in this case. Isn't that decreasing your semantic accuracy?

Lyndon 'Frames' White
CCA maps 2 vector spaces (gCCA maps any number of vector spaces) into 1 shared vector space.
It does this because you feed it a set of pairs of vectors form each of the original space and it tries to align them in the new common space, so they are proj...See more

Roland Kerr
Okay, so the random vector is like, as small as possible.

Lyndon 'Frames' White
nah?
like it would be a hyper-parameter to tune.
But the random vector doesn't exist anymore in the projected space.
It is projected to a nonrandom point,
because the CCA finds the (coincidental) corrections in the random vector.
The random vector is where the capacity for this to model word-senses instead of just words comes from.
It probably wants to be like 10%-50% the size of the word vector, at a guess.



