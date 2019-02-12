---
title: Pomocí funkcí tvar a zobecněn Additive modely pro model explainability v ML.NET
description: Pomocí funkcí tvar a zobecněn Additive modely pro model explainability v ML.NET
ms.date: 02/06/2019
ms.custom: mvc,how-to
ms.openlocfilehash: c6f30a8cc5c07d97c62ded065f1e18a4f0523617
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56093109"
---
# <a name="use-generalized-additive-models-and-shape-functions-for-model-explainability-in-mlnet"></a><span data-ttu-id="e31f3-103">Pomocí funkcí tvar a zobecněn Additive modely pro model explainability v ML.NET</span><span class="sxs-lookup"><span data-stu-id="e31f3-103">Use Generalized Additive Models and shape functions for model explainability in ML.NET</span></span>

<span data-ttu-id="e31f3-104">Při vytváření modelů strojového učení, nestačí často stačí provést předpovědi.</span><span class="sxs-lookup"><span data-stu-id="e31f3-104">When creating machine learning models, it is often not enough to simply make predictions.</span></span> <span data-ttu-id="e31f3-105">Vývojáři, pracovníci s rozhodovací pravomocí a jsou ovlivněny modely strojového učení často, potřebujete pochopit, jak se rozhodovat modelů strojového učení a funkcí, které přispívají k jejich výkon.</span><span class="sxs-lookup"><span data-stu-id="e31f3-105">Often, machine learning developers, decision makers, and those affected by the models need to understand how machine learning models make decisions and which features contribute to their performance.</span></span> <span data-ttu-id="e31f3-106">**Generalizované Additive modely (GAMs)** se používají interně v Microsoftu pro model explainability, což vývojářům umožňuje machine learning vytvořit vysoké kapacity modely, které lze snadno interpretovat jinými.</span><span class="sxs-lookup"><span data-stu-id="e31f3-106">**Generalized Additive Models (GAMs)** are used internally at Microsoft for model explainability to help machine learning developers create high-capacity models that can be easily interpreted by others.</span></span>

<span data-ttu-id="e31f3-107">GAMs jsou třídu **interpretovatelném modely** , které jsou lineární modely, kde jsou podmínky nelineárních funkce volána "obrazce funkce" jedné proměnné.</span><span class="sxs-lookup"><span data-stu-id="e31f3-107">GAMs are a class of **interpretable models** that are linear models where the terms are nonlinear functions, called "shape functions" of a single variable.</span></span> <span data-ttu-id="e31f3-108">Jako lineární model snadno jsou interpretovány, ale protože modely další funkce funkcí místo jednoho váha, jejich lze modelovat vztahy složitější než jednoduchý model lineární.</span><span class="sxs-lookup"><span data-stu-id="e31f3-108">As linear models, they are easily interpreted but because the models learn functions of features instead of a single weight, they can model more complex relationships than a simple linear model.</span></span> <span data-ttu-id="e31f3-109">Výsledný prediktivní GAM má zachycení termín, který představuje průměrný předpovědi trénovací sady a obrazec funkce, které představují odchylky od průměrné předpovědi.</span><span class="sxs-lookup"><span data-stu-id="e31f3-109">The resulting GAM predictor has an intercept term that represents the average prediction over the training set, and shape functions that represent the deviation from the average prediction.</span></span> <span data-ttu-id="e31f3-110">Obrazec funkce můžete prozkoumat oka zobrazíte odpověď model pro různé hodnoty, funkce a vizualizovat jako následující graf, který je vytvořen na konci v příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="e31f3-110">The shape functions can be inspected by eye to see the response of the model to different values of a feature, and visualized like the following graph that is created at the end of the code example.</span></span> <span data-ttu-id="e31f3-111">Trainer GAM v ML.NET je implementováno pomocí mělké barevného přechodu Posílený stromů (pro příklad stromu stumps) další funkce nonparametric tvar a vychází z metody popsané v [srozumitelné modely pro klasifikačních a regresních](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) Lou, Caruana a Gehrke.</span><span class="sxs-lookup"><span data-stu-id="e31f3-111">The GAM trainer in ML.NET is implemented using shallow gradient boosted trees (for example tree stumps) to learn nonparametric shape functions, and is based on the method described in [Intelligible Models for Classification and Regression](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) by Lou, Caruana, and Gehrke.</span></span>

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

<span data-ttu-id="e31f3-113">Ukázku toho, jak pro trénování modelu GAM, zkontrolujte a interpretovat výsledky najdete v tématu [úložiště GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs).</span><span class="sxs-lookup"><span data-stu-id="e31f3-113">For a sample of how to train a GAM model and inspect and interpret the results, see [the dotnet/machinelearning GitHub repository](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs).</span></span>
