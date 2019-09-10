---
title: Použití generalizované doplňkové modely a funkcí tvarů pro vyjasnění modelu
description: Použití generalizované doplňkové modely a funkcí tvarů pro vyjasnění modelu v ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: c58cf823007196c35da093fab7423c1e40ba1158
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855599"
---
# <a name="use-generalized-additive-models-and-shape-functions-for-model-explainability-in-mlnet"></a>Použití generalizované doplňkové modely a funkcí tvarů pro vyjasnění modelu v ML.NET

> [!NOTE]
> Toto téma odkazuje na ML.NET, který je aktuálně ve verzi Preview, a materiál může být změněn. Další informace najdete na stránce [ml.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) .

Tato ukázka s postupy a souvisejícími ukázkami aktuálně používá **ml.NET verze 0,10**. Další informace najdete v poznámkách k verzi v [úložišti GitHub/Machinelearning GitHub](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

Při vytváření modelů strojového učení není často dost dělat předpovědi. Vývojáři strojového učení, tvůrci rozhodování a oprávnění ovlivněné modely potřebují pochopit, jak modely strojového učení vytvářejí rozhodnutí a jaké funkce přispívají ke svému výkonu. Model **generalizované doplňkové látky (GAMs)** se interně používá v Microsoftu, aby se usnadnilo vytváření modelů, které vývojářům strojového učení pomůžou vytvářet modely s vysokou kapacitou, které můžou snadno interpretovat jiní uživatelé.

GAMs jsou třída **interpretované modely** , které jsou lineární modely, kde jsou tyto výrazy nelineární funkce, nazývané "funkce tvarů" jedné proměnné. Jako lineární modely jsou snadno interpretované, ale vzhledem k tomu, že modely se učí funkce funkcí místo jedné váhy, můžou modelovat složitější vztahy než jednoduchý lineární model. Výsledný prediktivní GAM má zachycený výraz, který představuje průměrnou předpověď v rámci sady školení a funkce tvarů, které představují odchylku od průměrného předpovědi. Funkce tvaru lze kontrolovat podle očí, aby bylo možné zobrazit odpověď modelu na různé hodnoty funkce a vizuálů jako následující graf, který je vytvořen na konci příkladu kódu. GAM Trainer v ML.NET je implementována pomocí nepřipojených stromů se zesílenými přechody (například stromu stumps) k získání funkcí neparametrového tvaru a je založena na metodě popsané v [srozumitelných modelech pro klasifikaci a regresi](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) pomocí Lou, Caruana a Gehrke.

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

![Graf funkcí obrazce generalizovaná doplňková](./media/use-gams-for-model-explainability/gam-shape-function-graph.png)

Ukázku toho, jak vytvořit model GAM a prozkoumat a interpretovat výsledky, najdete v [úložišti GitHub/Machinelearning GitHub](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs).
