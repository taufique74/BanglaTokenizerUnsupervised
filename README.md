# BanglaTokenizerUnsupervised
### This tokenizer is trained with Google's **SentencePiece**. ###
[SentencePiece](https://github.com/google/sentencepiece) is an unsupervised text tokenizer and detokenizer mainly for Neural Network-based text generation systems where the vocabulary size is predetermined prior to the neural model training. 

**It also seems like works well as a general purpose text tokenizer.**

To train this model, prothom alo bangla news corpus was used, scraped by [zabir-nabil](https://github.com/zabir-nabil). You can find the corpus [here](https://www.kaggle.com/furcifer/bangla-newspaper-dataset).

### Usage: ###
At first, install SentencePiece with pip 
> pip install sentencepiece

then,
```
>>>import sentencepiece as spm
>>>sp = spm.SentencePieceProcessor()
>>>sp.Load('./spiece_bangla.model')

>>>text = 'ক্রিকইনফো জানিয়েছে, আন্তর্জাতিক ম্যাচের চেয়ে ঘরোয়া ম্যাচে ‘জনসংখ্যাতাত্ত্বিক পরিচয়’ বেশি প্রভাব রাখে টিকিট ক্রয়ের ক্ষেত্রে—গবেষণায় তার প্রমাণ পেয়েছে ইংল্যান্ড ও ওয়েলস ক্রিকেট বোর্ড (ইসিবি)।'

>>>tokenized = sp.EncodeAsPieces(text)
>>>print(tokenized)
>['▁ক্রিকইনফো', '▁জানিয়েছে', ',', '▁আন্তর্জাতিক', '▁ম্যাচের', '▁চেয়ে', '▁ঘরোয়া', '▁ম্যাচে', '▁‘', 'জনসংখ্যা', 'তাত্ত্বিক', '▁পরিচয়', '’', '▁বেশি', '▁প্রভাব', '▁রাখে', '▁টিকিট', '▁ক্রয়ের', '▁ক্ষেত্রে', '—', 'গবেষণায়', '▁তার', '▁প্রমাণ', '▁পেয়েছে', '▁ইংল্যান্ড', '▁ও', '▁ওয়েলস', '▁ক্রিকেট', '▁বোর্ড', '▁(', 'ইসিবি', ')।']

>>>print([token.replace(u"\u2581", '') for token in tokenized])
['ক্রিকইনফো', 'জানিয়েছে', ',', 'আন্তর্জাতিক', 'ম্যাচের', 'চেয়ে', 'ঘরোয়া', 'ম্যাচে', '‘', 'জনসংখ্যা', 'তাত্ত্বিক', 'পরিচয়', '’', 'বেশি', 'প্রভাব', 'রাখে', 'টিকিট', 'ক্রয়ের', 'ক্ষেত্রে', '—', 'গবেষণায়', 'তার', 'প্রমাণ', 'পেয়েছে', 'ইংল্যান্ড', 'ও', 'ওয়েলস', 'ক্রিকেট', 'বোর্ড', '(', 'ইসিবি', ')।']
```
