---
title: Pomocí funkcí tvar a zobecněn Additive modely pro model explainability
description: Pomocí funkcí tvar a zobecněn Additive modely pro model explainability v ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: ef56f737a2ad0cba616e32229ac3a395146fb6d2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662132"
---
# <a name="use-generalized-additive-models-and-shape-functions-for-model-explainability-in-mlnet"></a>Pomocí funkcí tvar a zobecněn Additive modely pro model explainability v ML.NET

> [!NOTE]
> Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit. Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Aktuálně používáte této ukázky s postupy a související **ML.NET verze 0.10**. Další informace najdete v tématu poznámky k verzi v [úložiště GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

Při vytváření modelů strojového učení, nestačí často stačí provést předpovědi. Vývojáři, pracovníci s rozhodovací pravomocí a jsou ovlivněny modely strojového učení často, potřebujete pochopit, jak se rozhodovat modelů strojového učení a funkcí, které přispívají k jejich výkon. **Generalizované Additive modely (GAMs)** se používají interně v Microsoftu pro model explainability, což vývojářům umožňuje machine learning vytvořit vysoké kapacity modely, které lze snadno interpretovat jinými.

GAMs jsou třídu **interpretovatelném modely** , které jsou lineární modely, kde jsou podmínky nelineárních funkce volána "obrazce funkce" jedné proměnné. Jako lineární model snadno jsou interpretovány, ale protože modely další funkce funkcí místo jednoho váha, jejich lze modelovat vztahy složitější než jednoduchý model lineární. Výsledný prediktivní GAM má zachycení termín, který představuje průměrný předpovědi trénovací sady a obrazec funkce, které představují odchylky od průměrné předpovědi. Obrazec funkce můžete prozkoumat oka zobrazíte odpověď model pro různé hodnoty, funkce a vizualizovat jako následující graf, který je vytvořen na konci v příkladu kódu. Trainer GAM v ML.NET je implementováno pomocí mělké barevného přechodu Posílený stromů (pro příklad stromu stumps) další funkce nonparametric tvar a vychází z metody popsané v [srozumitelné modely pro klasifikačních a regresních](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) Lou, Caruana a Gehrke.

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

![Zobecněný Additive modely obrazec funkce grafu](./media/use-gams-for-model-explainability/gam-shape-function-graph.png)

Ukázku toho, jak pro trénování modelu GAM, zkontrolujte a interpretovat výsledky najdete v tématu [úložiště GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs).
