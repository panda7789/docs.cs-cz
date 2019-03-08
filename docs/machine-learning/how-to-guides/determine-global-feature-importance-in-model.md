---
title: Určení funkcí důležitost modely s důležitostí permutaci funkce v ML.NET
description: Pochopení důležitosti funkce modelů s důležitostí permutaci funkce v ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: b0457bc07168579403e5a00383864c5612e1d17f
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675547"
---
# <a name="determine-the-feature-importance-of-models-with-permutation-feature-importance-in-mlnet"></a><span data-ttu-id="6cbc0-103">Určení funkcí důležitost modely s důležitostí permutaci funkce v ML.NET</span><span class="sxs-lookup"><span data-stu-id="6cbc0-103">Determine the feature importance of models with Permutation Feature Importance in ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="6cbc0-104">Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit.</span><span class="sxs-lookup"><span data-stu-id="6cbc0-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="6cbc0-105">Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="6cbc0-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="6cbc0-106">Aktuálně používáte této ukázky s postupy a související **ML.NET verze 0.10**.</span><span class="sxs-lookup"><span data-stu-id="6cbc0-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="6cbc0-107">Další informace najdete v tématu poznámky k verzi v [úložiště GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="6cbc0-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="6cbc0-108">Při vytváření modelů strojového učení, nestačí často stačí provést předpovědi.</span><span class="sxs-lookup"><span data-stu-id="6cbc0-108">When creating machine learning models, it is often not enough to simply make predictions.</span></span> <span data-ttu-id="6cbc0-109">Vývojáři, pracovníci s rozhodovací pravomocí a jsou ovlivněny modely strojového učení často, potřebujete pochopit, jak se rozhodovat modelů strojového učení a funkcí, které přispívají k jejich výkon.</span><span class="sxs-lookup"><span data-stu-id="6cbc0-109">Often, machine learning developers, decision makers, and those affected by the models need to understand how machine learning models make decisions and which features contribute to their performance.</span></span> <span data-ttu-id="6cbc0-110">`Permutation Feature Importance` (PFI) je nástroj explainability modelu, který se používá interně v Microsoftu, což vývojářům umožňuje machine learning lepší pochopení důležitosti funkce modelů.</span><span class="sxs-lookup"><span data-stu-id="6cbc0-110">`Permutation Feature Importance` (PFI) is a model explainability tool that is used internally at Microsoft to help machine learning developers better understand the feature importance of models.</span></span>

<span data-ttu-id="6cbc0-111">PFI je technika, chcete-li zjistit **globální funkce význam** v modelu trénovaného strojového učení, motivováno Breiman v ["Random doménových struktur" papír, část 10](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf).</span><span class="sxs-lookup"><span data-stu-id="6cbc0-111">PFI is a technique to determine **global feature importance** in a trained machine learning model, motivated by Breiman in the ["Random Forests" paper, section 10](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf).</span></span> <span data-ttu-id="6cbc0-112">PFI měří funkce význam položením otázky, "co vliv na model bude-li hodnoty pro funkci byly nastaveny na náhodnou \* hodnotu?".</span><span class="sxs-lookup"><span data-stu-id="6cbc0-112">PFI measures feature importance by asking the question, "What would the effect on the model be if the values for a feature were set to a random\* value?".</span></span> <span data-ttu-id="6cbc0-113">Výhodou PFI metody je, že je nezávislý na modelu – funguje to pro všechny modely, které lze vyhodnotit – a všech datových sadách, ne jenom cvičnou sadou, může použít k výpočtu důležité funkce.</span><span class="sxs-lookup"><span data-stu-id="6cbc0-113">The advantage of the PFI method is that it is model agnostic — it works with any model that can be evaluated — and it can use any dataset, not just the training set, to compute feature importance.</span></span> <span data-ttu-id="6cbc0-114">Vám pomůže PFI jako tak vytvořit importances funkci jako tento graf:</span><span class="sxs-lookup"><span data-stu-id="6cbc0-114">You can use PFI like so to produce feature importances like this graph:</span></span>

![Graf funkce význam permutaci](./media/determine-global-feature-importance-in-model/pfi-graph.png)

```csharp
// Compute the feature importance using PFI
var permutationMetrics = mlContext.Regression.PermutationFeatureImportance(model.LastTransformer, model.Transform(data), "MedianHomeValue");

// Get the feature names from the training set
var featureNames =
    data.Schema.AsEnumerable()
    .Select(column => column.Name) // Get the column names
    .Where(name => name != "MedianHomeValue") // Drop the Label
    .ToArray();

// Write out the feature names and their importance to the model's Mean R-squared value
for (int i = 0; i < featureNames.Length;i++)
{
    Console.WriteLine($"{featureNames[i]}\t{permutationMetrics[i].RSquared.Mean:G4}");
}
```

<span data-ttu-id="6cbc0-116">Příklad použití PFI k analýze funkce důležitost modelu, naleznete v tématu [úložiště GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/samples/Microsoft.ML.Samples/Dynamic/PermutationFeatureImportance).</span><span class="sxs-lookup"><span data-stu-id="6cbc0-116">For a sample using PFI to analyze the feature importance of a model, see [the dotnet/machinelearning GitHub repository](https://github.com/dotnet/machinelearning/tree/master/docs/samples/Microsoft.ML.Samples/Dynamic/PermutationFeatureImportance).</span></span>

<span data-ttu-id="6cbc0-117">/ \* I, ne náhodné přesně, ale permutovanou funkci mezi několik příkladů.</span><span class="sxs-lookup"><span data-stu-id="6cbc0-117">/\* Well, not random exactly, but permuted across the set of examples.</span></span>
