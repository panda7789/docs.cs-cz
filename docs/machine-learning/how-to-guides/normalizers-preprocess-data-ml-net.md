---
title: Předběžné zpracování trénovacích dat s normalizers používané k zpracování dat – ML.NET
description: Další informace o použití normalizers se předběžně zpracovat trénovacích dat pro použití v modelu strojového učení, vytváření, trénování a vyhodnocování s ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 2d18f7c19a51fd929ac6efb7f600cb1ac2733de8
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57676600"
---
# <a name="preprocess-training-data-with-normalizers-to-use-in-data-processing---mlnet"></a>Předběžné zpracování trénovacích dat s normalizers používané k zpracování dat – ML.NET

> [!NOTE]
> Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit. Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Aktuálně používáte této ukázky s postupy a související **ML.NET verze 0.10**. Další informace najdete v tématu poznámky k verzi v [úložiště GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

ML.NET zpřístupňuje řadu [algoritmy čištění a jiných ukazatelů](https://machinelearningmastery.com/parametric-and-nonparametric-machine-learning-algorithms/).

Má **není** důležitosti které normalizátor zvolíte, protože je **použít** normalizátor při cvičení lineární nebo jiných ukazatelů modely.

Vždy zahrnovat normalizátor přímo v kanálu ML.NET learning, takže ho:

- jenom se trénuje na trénovací data a ne na testovací data
- správně se použije na všechny nové příchozích dat, bez nutnosti další předběžné zpracování v době předpovědi.

Tady je fragment kódu, který ukazuje normalizace studium kanály. Předpokládá datovou sadu Iris:

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Define the reader: specify the data columns and where to find them in the text file.
var reader = mlContext.Data.CreateTextLoader(
    columns: new TextLoader.Column[]
    {
        // The four features of the Iris dataset will be grouped together as one Features column.
        new TextLoader.Column("Features",DataKind.R4,0,3),
        // Label: kind of iris.
        new TextLoader.Column("Label",DataKind.TX,4)
    },
    // Default separator is tab, but the dataset has comma.
    separatorChar: ',',
    // First line of the file is a header, not a data row.
    hasHeader: true
);

// Read the training data.
var trainData = reader.Read(dataPath);

// Apply all kinds of standard ML.NET normalization to the raw features.
var pipeline =
    mlContext.Transforms.Normalize(
            new NormalizingEstimator.MinMaxColumn(inputColumnName:"Features", outputColumnName:"MinMaxNormalized", fixZero: true),
            new NormalizingEstimator.MeanVarColumn(inputColumnName: "Features", outputColumnName: "MeanVarNormalized", fixZero: true),
            new NormalizingEstimator.BinningColumn(inputColumnName: "Features", outputColumnName: "BinNormalized", numBins: 256));

// Let's train our pipeline of normalizers, and then apply it to the same data.
var normalizedData = pipeline.Fit(trainData).Transform(trainData);

// Inspect one column of the resulting dataset.
var meanVarValues = normalizedData.GetColumn<float[]>(mlContext, "MeanVarNormalized").ToArray();
```
