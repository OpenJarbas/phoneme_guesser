# Phoneme Guesser

Utility to retrieve phonemes from text

This was developed for wake word detection automation using pocketsphinx, 
phonemes are retrieved from slightly processed .dict files in models 
from [sourceforge](https://sourceforge.net/projects/cmusphinx/files/Acoustic%20and%20Language%20Models/)

for `en` and `es`, out of vocab words will use an heuristic approach, for 
other languages out of vocab words will return closest match from known 
words

help wanted to implement heuristics for other languages

see supported languages in [this folder](./phoneme_guesser/res) 

# Install

```bash
pip install phoneme_guesser
```

# Usage

```python
from phoneme_guesser import get_phonemes

# if words are know, it is a simple dictionary lookup
en = "ok google"
print(get_phonemes(en, "en"))
# OW K EY . G UW G AH L

en = "hey andromeda"
print(get_phonemes(en, "en"))
# HH EY . AE N D R AA M AH D AH

pt = "ó ambrósio"
print(get_phonemes(pt, "pt-br"))
# O . a~ b r O z i u


# for en and es, out of vocab words will use an heuristic approach
# help wanted to implement heuristics for other languages

wakeword = "hey mycroft"
print(get_phonemes(wakeword, "en-us"))
# HH EH Y . M Y K R OW F T

print(get_phonemes(wakeword, "es-es"))
# e i . m y k r o f t


# when heuristics are not implemented
# out of vocab words will return closest match from known words

fr = "Bonjour firefox"  # notice firefox failure
print(get_phonemes(fr, "fr"))
# bb on jj ou rr . ff yy ai ff

it = "ciao google"
print(get_phonemes(it, "it"))
# k j a1 m o . d OO LL LL e

```