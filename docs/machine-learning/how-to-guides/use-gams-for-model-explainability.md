---
title: Interpretace ML.NET modelů pomocí generalizované doplňkové modely
description: Použijte generalizované doplňkové modely a funkce tvarů pro výklad modelu v ML.NET
ms.date: 01/30/2020
ms.custom: mvc,how-to
ms.openlocfilehash: 6df19eff4fec98c5815a9f8f4d8e4e9a80cba6ed
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092470"
---
# <a name="use-generalized-additive-models-and-shape-functions-for-model-interpretability-in-mlnet"></a><span data-ttu-id="c3e25-103">Použijte generalizované doplňkové modely a funkce tvarů pro výklad modelu v ML.NET</span><span class="sxs-lookup"><span data-stu-id="c3e25-103">Use Generalized Additive Models and shape functions for model interpretability in ML.NET</span></span>

<span data-ttu-id="c3e25-104">Při vytváření modelů strojového učení není často dost dělat předpovědi.</span><span class="sxs-lookup"><span data-stu-id="c3e25-104">When creating machine learning models, it is often not enough to simply make predictions.</span></span> <span data-ttu-id="c3e25-105">Vývojáři strojového učení, tvůrci rozhodování a oprávnění ovlivněné modely potřebují pochopit, jak modely strojového učení vytvářejí rozhodnutí a jaké funkce přispívají ke svému výkonu.</span><span class="sxs-lookup"><span data-stu-id="c3e25-105">Often, machine learning developers, decision makers, and those affected by the models need to understand how machine learning models make decisions and which features contribute to their performance.</span></span> <span data-ttu-id="c3e25-106">**Generalizované doplňkové modely (GAMs)** se interně používají v Microsoftu, aby bylo možné modelovat, aby mohli vývojáři strojového učení vytvářet vysoce náročné modely, které můžou snadno interpretovat jiní uživatelé.</span><span class="sxs-lookup"><span data-stu-id="c3e25-106">**Generalized Additive Models (GAMs)** are used internally at Microsoft for model interpretability to help machine learning developers create high-capacity models that can be easily interpreted by others.</span></span>

<span data-ttu-id="c3e25-107">GAMs jsou třída **interpretované modely** , které jsou lineární modely, kde jsou tyto výrazy nelineární funkce, nazývané "funkce tvarů" jedné proměnné.</span><span class="sxs-lookup"><span data-stu-id="c3e25-107">GAMs are a class of **interpretable models** that are linear models where the terms are nonlinear functions, called "shape functions" of a single variable.</span></span> <span data-ttu-id="c3e25-108">Jako lineární modely jsou snadno interpretované, ale vzhledem k tomu, že modely se učí funkce funkcí místo jedné váhy, můžou modelovat složitější vztahy než jednoduchý lineární model.</span><span class="sxs-lookup"><span data-stu-id="c3e25-108">As linear models, they are easily interpreted but because the models learn functions of features instead of a single weight, they can model more complex relationships than a simple linear model.</span></span> <span data-ttu-id="c3e25-109">Výsledný prediktivní GAM má zachycený výraz, který představuje průměrnou předpověď v rámci sady školení a funkce tvarů, které představují odchylku od průměrného předpovědi.</span><span class="sxs-lookup"><span data-stu-id="c3e25-109">The resulting GAM predictor has an intercept term that represents the average prediction over the training set, and shape functions that represent the deviation from the average prediction.</span></span> <span data-ttu-id="c3e25-110">Funkce tvaru lze kontrolovat podle očí, aby bylo možné zobrazit odpověď modelu na různé hodnoty funkce a vizuálů jako následující graf, který je vytvořen na konci příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="c3e25-110">The shape functions can be inspected by eye to see the response of the model to different values of a feature, and visualized like the following graph that is created at the end of the code example.</span></span> <span data-ttu-id="c3e25-111">GAM Trainer v ML.NET je implementována pomocí nech stromů s omezeným přechodem (například stromu stumps) k získání funkcí neparametrového obrazce a je založena na metodě popsané v [srozumitelných modelech pro klasifikaci a regresi](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) pomocí Lou, Caruana a Gehrke.</span><span class="sxs-lookup"><span data-stu-id="c3e25-111">The GAM trainer in ML.NET is implemented using shallow gradient boosted trees (for example tree stumps) to learn nonparametric shape functions, and is based on the method described in [Intelligible Models for Classification and Regression](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) by Lou, Caruana, and Gehrke.</span></span>

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

<span data-ttu-id="c3e25-113">Ukázku toho, jak vytvořit model GAM a prozkoumat a interpretovat výsledky, najdete v [úložišti GitHub/Machinelearning GitHub](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs).</span><span class="sxs-lookup"><span data-stu-id="c3e25-113">For a sample of how to train a GAM model and inspect and interpret the results, see [the dotnet/machinelearning GitHub repository](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs).</span></span>
