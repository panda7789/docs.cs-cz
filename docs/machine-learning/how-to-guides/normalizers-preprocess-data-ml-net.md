---
title: Předběžné zpracování trénovacích dat s normalizers používané k zpracování dat – ML.NET
description: Další informace o použití normalizers se předběžně zpracovat trénovacích dat pro použití v modelu strojového učení, vytváření, trénování a vyhodnocování s ML.NET
ms.date: 02/06/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 28d358cd381f71b4116e1dd25d847fc51835f09e
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56093044"
---
# <a name="preprocess-training-data-with-normalizers-to-use-in-data-processing---mlnet"></a>Předběžné zpracování trénovacích dat s normalizers používané k zpracování dat – ML.NET

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
