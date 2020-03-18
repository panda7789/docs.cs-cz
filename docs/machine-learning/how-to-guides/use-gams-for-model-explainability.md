---
title: Interpretace ML.NET modelů pomocí generalizovaných aditivních modelů
description: Použití generalizovaných aditivních modelů a funkcí tvarů pro interpretaci modelu v ML.NET
ms.date: 01/30/2020
ms.custom: mvc,how-to
ms.openlocfilehash: 6df19eff4fec98c5815a9f8f4d8e4e9a80cba6ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77092470"
---
# <a name="use-generalized-additive-models-and-shape-functions-for-model-interpretability-in-mlnet"></a>Použití generalizovaných aditivních modelů a funkcí tvarů pro interpretaci modelu v ML.NET

Při vytváření modelů strojového učení často nestačí jednoduše vytvářet předpovědi. Vývojáři strojového učení, osoby s rozhodovací pravomocí a ti, kterých se modely týkají, často potřebují pochopit, jak modely strojového učení rozhodují a které funkce přispívají k jejich výkonu. **Generalizované aditivní modely (GAM)** se používají interně v Microsoftu pro interpretaci modelu, aby vývojáři strojového učení mohli vytvářet vysokokapacitní modely, které mohou snadno interpretovat ostatní uživatelé.

GAMs jsou třída **interpretovatelných modelů,** které jsou lineární modely, kde termíny jsou nelineární funkce, nazývané "tvarové funkce" jedné proměnné. Jako lineární modely jsou snadno interpretovány, ale protože se modely učí funkce funkcí namísto jedné hmotnosti, mohou modelovat složitější vztahy než jednoduchý lineární model. Výsledný gam prediktor má intercept termín, který představuje průměrnou předpověď přes trénovací sadu a tvar funkce, které představují odchylku od průměrné předpovědi. Funkce tvaru mohou být zkontrolovány okem, aby se zovírala odezva modelu na různé hodnoty prvku, a vizualizované jako následující graf, který je vytvořen na konci příkladu kódu. Gam trainer v ML.NET je implementován pomocí mělkého gradientu posílených stromů (například pařezů stromů) pro učení neparametrických funkcí tvaru a je založen na metodě popsané v [Intelligible Models for Classification and Regression](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) by Lou, Caruana a Gehrke.

```csharp
// Train the Generalized Additive Model
var fitPipeline = pipeline.Fit(data);
var gamModel = fitPipeline.LastTransformer.Model;

// The intercept for Generalize Additive Models represent the average prediction for the training data
var intercept = gamModel.Intercept;
Console.WriteLine($"Average predicted cost: {intercept:0.00}");

// Get the column names from the training set
var columnNames = data.Schema.AsEnumerable()
    .Select(column => column.Name) // Get the column names
    .Where(name => name != "MedianHomeValue") // Drop the Label
    .ToArray();

// Get the index of a variable from the training data
var myFeatureIndex = columnNames.ToList().FindIndex(str => str.Equals("MyFeature"));

// The shape functions represent the deviation from the average prediction as a function of the feature value
// It is represented by a discrete set of bins
// First, get the array of bin upper bounds from the model for this feature
var myFeatureBins = gamModel.GetBinUpperBounds(myFeatureIndex);
// Then get the array of bin weights; these are the effect size for each bin
var myFeatureWeights = gamModel.GetBinEffects(myFeatureIndex);

// Write out the shape function for the feature (see the following figure for what this looks like)
for (int i = 0; i < myFeatureBins.Length; i++)
{
    Console.WriteLine($"x < {myFeatureBins[i]:0.00} => {myFeatureWeights[i]:0.000}");
}
```

![Graf funkce tvarových modelů generalizovaných aditivních modelů](./media/use-gams-for-model-explainability/gam-shape-function-graph.png)

Ukázku, jak trénovat model GAM a zkontrolovat a interpretovat výsledky, naleznete [v úložišti GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs).
