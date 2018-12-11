---
title: Určení funkcí důležitost modely s důležitostí permutaci funkce v ML.NET
description: Pochopení důležitosti funkce modelů s důležitostí permutaci funkce v ML.NET
ms.date: 12/04/2018
ms.custom: mvc,how-to
ms.openlocfilehash: 4b93e085dbb99e7f6f5a0a839b863aad1c69c7ba
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155459"
---
# <a name="determine-the-feature-importance-of-models-with-permutation-feature-importance-in-mlnet"></a>Určení funkcí důležitost modely s důležitostí permutaci funkce v ML.NET

Při vytváření modelů strojového učení, nestačí často stačí provést předpovědi. Vývojáři, pracovníci s rozhodovací pravomocí a jsou ovlivněny modely strojového učení často, potřebujete pochopit, jak se rozhodovat modelů strojového učení a funkcí, které přispívají k jejich výkon. `Permutation Feature Importance` (PFI) je nástroj explainability modelu, který se používá interně v Microsoftu, což vývojářům umožňuje machine learning lepší pochopení důležitosti funkce modelů.

PFI je technika, chcete-li zjistit **globální funkce význam** v modelu trénovaného strojového učení, motivováno Breiman v ["Random doménových struktur" papír, část 10](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf). PFI měří funkce význam položením otázky, "co vliv na model bude-li hodnoty pro funkci byly nastaveny na náhodnou * hodnotu?". Výhodou PFI metody je, že je nezávislý na modelu – funguje to pro všechny modely, které lze vyhodnotit – a všech datových sadách, ne jenom cvičnou sadou, může použít k výpočtu důležité funkce. Vám pomůže PFI jako tak vytvořit importances funkci jako tento graf:

![Graf funkce význam permutaci](./media/determine-global-feature-importance-in-model/pfi-graph.png)

```csharp
// Compute the feature importance using PFI
var permutationMetrics = mlContext.Regression.PermutationFeatureImportance(model, data);
 
// Get the feature names from the training set
var featureNames = data.Schema.GetColumns()
                .Select(tuple => tuple.column.Name) // Get the column names
                .Where(name => name != labelName) // Drop the Label
                .ToArray();
 
// Write out the feature names and their importance to the model's R-squared value
for (int i = 0; i < featureNames.Length; i++)
  Console.WriteLine($"{featureNames[i]}\t{permutationMetrics[i].rSquared:G4}");
```

Příklad použití PFI k analýze funkce důležitost modelu, naleznete v tématu [úložiště GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/PermutationFeatureImportance.cs).

/ * I, ne náhodné přesně, ale permutovanou funkci mezi několik příkladů.
