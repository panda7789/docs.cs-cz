---
title: Předběžné zpracování trénovacích dat s normalizers používané k zpracování dat – ML.NET
description: Další informace o použití normalizers se předběžně zpracovat trénovacích dat pro použití v modelu strojového učení, vytváření, trénování a vyhodnocování s ML.NET
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: c8b959904705e996c97bdcd8b3444e754d14d046
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297689"
---
# <a name="preprocess-training-data-with-normalizers-to-use-in-data-processing---mlnet"></a><span data-ttu-id="2ab26-103">Předběžné zpracování trénovacích dat s normalizers používané k zpracování dat – ML.NET</span><span class="sxs-lookup"><span data-stu-id="2ab26-103">Preprocess training data with normalizers to use in data processing - ML.NET</span></span>

<span data-ttu-id="2ab26-104">ML.NET zpřístupňuje řadu [algoritmy čištění a jiných ukazatelů](https://machinelearningmastery.com/parametric-and-nonparametric-machine-learning-algorithms/).</span><span class="sxs-lookup"><span data-stu-id="2ab26-104">ML.NET exposes a number of [parametric and non-parametric algorithms](https://machinelearningmastery.com/parametric-and-nonparametric-machine-learning-algorithms/).</span></span>

<span data-ttu-id="2ab26-105">Má **není** důležitosti které normalizátor zvolíte, protože je **použít** normalizátor při cvičení lineární nebo jiných ukazatelů modely.</span><span class="sxs-lookup"><span data-stu-id="2ab26-105">It's **not** as important which normalizer you choose as it is to **use** a normalizer when training linear or other parametric models.</span></span>

<span data-ttu-id="2ab26-106">Vždy zahrnovat normalizátor přímo v kanálu ML.NET learning, takže ho:</span><span class="sxs-lookup"><span data-stu-id="2ab26-106">Always include the normalizer directly in the ML.NET learning pipeline, so it:</span></span>

- <span data-ttu-id="2ab26-107">jenom se trénuje na trénovací data a ne na testovací data</span><span class="sxs-lookup"><span data-stu-id="2ab26-107">is only trained on the training data, and not on your test data,</span></span>
- <span data-ttu-id="2ab26-108">správně se použije na všechny nové příchozích dat, bez nutnosti další předběžné zpracování v době předpovědi.</span><span class="sxs-lookup"><span data-stu-id="2ab26-108">is correctly applied to all the new incoming data, without the need for extra pre-processing at prediction time.</span></span>

<span data-ttu-id="2ab26-109">Tady je fragment kódu, který ukazuje normalizace studium kanály.</span><span class="sxs-lookup"><span data-stu-id="2ab26-109">Here's a snippet of code that demonstrates normalization in learning pipelines.</span></span> <span data-ttu-id="2ab26-110">Předpokládá datovou sadu Iris:</span><span class="sxs-lookup"><span data-stu-id="2ab26-110">It assumes the Iris dataset:</span></span>

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Define the reader: specify the data columns and where to find them in the text file.
var reader = mlContext.Data.TextReader(new TextLoader.Arguments
{
    Column = new[] {
        // The four features of the Iris dataset will be grouped together as one Features column.
        new TextLoader.Column("Features", DataKind.R4, 0, 3),
        // Label: kind of iris.
        new TextLoader.Column("Label", DataKind.TX, 4),
    },
    // Default separator is tab, but the dataset has comma.
    Separator = ","
});

// Read the training data.
var trainData = reader.Read(dataPath);

// Apply all kinds of standard ML.NET normalization to the raw features.
var pipeline =
    mlContext.Transforms.Normalize(
        new NormalizingEstimator.MinMaxColumn("Features", "MinMaxNormalized", fixZero: true),
        new NormalizingEstimator.MeanVarColumn("Features", "MeanVarNormalized", fixZero: true),
        new NormalizingEstimator.BinningColumn("Features", "BinNormalized", numBins: 256));

// Let's train our pipeline of normalizers, and then apply it to the same data.
var normalizedData = pipeline.Fit(trainData).Transform(trainData);

// Inspect one column of the resulting dataset.
var meanVarValues = normalizedData.GetColumn<float[]>(mlContext, "MeanVarNormalized").ToArray();
```
