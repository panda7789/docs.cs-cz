---
title: Použijte vytváření funkcí k tréninku modelu na textová data - ML.NET
description: Zjistěte, jak použít vytváření funkcí k tréninku modelu na textová data s ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: e26a4b293869b7cdad3c439237bd0145cafa314a
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57844354"
---
# <a name="apply-feature-engineering-for-machine-learning-model-training-on-textual-data-with-mlnet"></a>Použít vytváření funkcí pro strojové učení cvičení modelu na textová data s ML.NET

> [!NOTE]
> Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit. Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Aktuálně používáte této ukázky s postupy a související **ML.NET verze 0.10**. Další informace najdete v tématu poznámky k verzi v [úložiště GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

Je potřeba převést všechna data bez typu float pro `float` datové typy od všech ML.NET `learners` očekávat funkce, jako je `float vector`.

Další informace o textových dat, musíte extrahovat text funkce. ML.NET má některé základní text funkce extrakce mechanismy:

- `Text normalization` (odebrání interpunkční znaménka, diakritiky přepnutí na malá písmena atd.)
- `Separator-based tokenization`.
- `Stopword` odebrání.
- `Ngram` a `skip-gram` extrakce.
- `TF-IDF` změny měřítka.
- `Bag of words` převod.

Následující příklad ukazuje ML.NET textové funkce extrakce mechanismy pomocí [Wikipedia detox dataset](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv):

<!-- markdownlint-disable MD010 -->
```console
Sentiment   SentimentText
1   Stop trolling, zapatancas, calling me a liar merely demonstartes that you arer Zapatancas. You may choose to chase every legitimate editor from this site and ignore me but I am an editor with a record that isnt 99% trolling and therefore my wishes are not to be completely ignored by a sockpuppet like yourself. The consensus is overwhelmingly against you and your trolling lover Zapatancas,  
1   ::::: Why are you threatening me? I'm not being disruptive, its you who is being disruptive.   
0   " *::Your POV and propaganda pushing is dully noted. However listing interesting facts in a netral and unacusitory tone is not POV. You seem to be confusing Censorship with POV monitoring. I see nothing POV expressed in the listing of intersting facts. If you want to contribute more facts or edit wording of the cited fact to make them sound more netral then go ahead. No need to CENSOR interesting factual information. "
0   ::::::::This is a gross exaggeration. Nobody is setting a kangaroo court. There was a simple addition concerning the airline. It is the only one disputed here.   
```
<!-- markdownlint-enable MD010 -->

```csharp
// Define the reader: specify the data columns and where to find them in the text file.
var reader = mlContext.Data.CreateTextLoader(new[] 
    {
        new TextLoader.Column("IsToxic", DataKind.BL, 0),
        new TextLoader.Column("Message", DataKind.TX, 1),
    },
    hasHeader: true
);

// Read the data.
var data = reader.Read(dataPath);

// Inspect the message texts that are read from the file.
var messageTexts = data.GetColumn<string>(mlContext, "Message").Take(20).ToArray();

// Apply various kinds of text operations supported by ML.NET.
var pipeline =
    // One-stop shop to run the full text featurization.
    mlContext.Transforms.Text.FeaturizeText("TextFeatures", "Message")

    // Normalize the message for later transforms
    .Append(mlContext.Transforms.Text.NormalizeText("NormalizedMessage", "Message"))

    // NLP pipeline 1: bag of words.
    .Append(new WordBagEstimator(mlContext, "BagOfWords", "NormalizedMessage"))

    // NLP pipeline 2: bag of bigrams, using hashes instead of dictionary indices.
    .Append(new WordHashBagEstimator(mlContext, "BagOfBigrams","NormalizedMessage", 
                ngramLength: 2, allLengths: false))

    // NLP pipeline 3: bag of tri-character sequences with TF-IDF weighting.
    .Append(mlContext.Transforms.Text.TokenizeCharacters("MessageChars", "Message"))
    .Append(new NgramExtractingEstimator(mlContext, "BagOfTrichar", "MessageChars", 
                ngramLength: 3, weighting: NgramExtractingEstimator.WeightingCriteria.TfIdf))

    // NLP pipeline 4: word embeddings.
    .Append(mlContext.Transforms.Text.TokenizeWords("TokenizedMessage", "NormalizedMessage"))
    .Append(mlContext.Transforms.Text.ExtractWordEmbeddings("Embeddings", "TokenizedMessage",
                WordEmbeddingsExtractingTransformer.PretrainedModelKind.GloVeTwitter25D));

// Let's train our pipeline, and then apply it to the same data.
// Note that even on a small dataset of 70KB the pipeline above can take up to a minute to completely train.
var transformedData = pipeline.Fit(data).Transform(data);

// Inspect some columns of the resulting dataset.
var embeddings = transformedData.GetColumn<float[]>(mlContext, "Embeddings").Take(10).ToArray();
var unigrams = transformedData.GetColumn<float[]>(mlContext, "BagOfWords").Take(10).ToArray();
```
