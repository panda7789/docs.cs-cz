---
title: Interpretace ML.NET modelů pomocí generalizovaných aditivních modelů
description: Použití generalizovaných aditivních modelů a funkcí tvarů pro interpretaci modelu v ML.NET
ms.date: 01/30/2020
ms.custom: mvc,how-to
ms.openlocfilehash: 29eac7a609ada57283a7c5b55b935e30709930dd
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243125"
---
# <a name="use-generalized-additive-models-and-shape-functions-for-model-interpretability-in-mlnet"></a><span data-ttu-id="40af6-103">Použití generalizovaných aditivních modelů a funkcí tvarů pro interpretaci modelu v ML.NET</span><span class="sxs-lookup"><span data-stu-id="40af6-103">Use Generalized Additive Models and shape functions for model interpretability in ML.NET</span></span>

<span data-ttu-id="40af6-104">Při vytváření modelů strojového učení často nestačí jednoduše vytvářet předpovědi.</span><span class="sxs-lookup"><span data-stu-id="40af6-104">When creating machine learning models, it is often not enough to simply make predictions.</span></span> <span data-ttu-id="40af6-105">Vývojáři strojového učení, osoby s rozhodovací pravomocí a ti, kterých se modely týkají, často potřebují pochopit, jak modely strojového učení rozhodují a které funkce přispívají k jejich výkonu.</span><span class="sxs-lookup"><span data-stu-id="40af6-105">Often, machine learning developers, decision makers, and those affected by the models need to understand how machine learning models make decisions and which features contribute to their performance.</span></span> <span data-ttu-id="40af6-106">**Generalizované aditivní modely (GAM)** se používají interně v Microsoftu pro interpretaci modelu, aby vývojáři strojového učení mohli vytvářet vysokokapacitní modely, které mohou snadno interpretovat ostatní uživatelé.</span><span class="sxs-lookup"><span data-stu-id="40af6-106">**Generalized Additive Models (GAMs)** are used internally at Microsoft for model interpretability to help machine learning developers create high-capacity models that can be easily interpreted by others.</span></span>

<span data-ttu-id="40af6-107">GAMs jsou třída **interpretovatelných modelů,** které jsou lineární modely, kde termíny jsou nelineární funkce, nazývané "tvarové funkce" jedné proměnné.</span><span class="sxs-lookup"><span data-stu-id="40af6-107">GAMs are a class of **interpretable models** that are linear models where the terms are nonlinear functions, called "shape functions" of a single variable.</span></span> <span data-ttu-id="40af6-108">Jako lineární modely jsou snadno interpretovány, ale protože se modely učí funkce funkcí namísto jedné hmotnosti, mohou modelovat složitější vztahy než jednoduchý lineární model.</span><span class="sxs-lookup"><span data-stu-id="40af6-108">As linear models, they are easily interpreted but because the models learn functions of features instead of a single weight, they can model more complex relationships than a simple linear model.</span></span> <span data-ttu-id="40af6-109">Výsledný gam prediktor má intercept termín, který představuje průměrnou předpověď přes trénovací sadu a tvar funkce, které představují odchylku od průměrné předpovědi.</span><span class="sxs-lookup"><span data-stu-id="40af6-109">The resulting GAM predictor has an intercept term that represents the average prediction over the training set, and shape functions that represent the deviation from the average prediction.</span></span> <span data-ttu-id="40af6-110">Funkce tvaru mohou být zkontrolovány okem, aby se zovírala odezva modelu na různé hodnoty prvku, a vizualizované jako následující graf, který je vytvořen na konci příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="40af6-110">The shape functions can be inspected by eye to see the response of the model to different values of a feature, and visualized like the following graph that is created at the end of the code example.</span></span> <span data-ttu-id="40af6-111">Gam trainer v ML.NET je implementován pomocí mělkého gradientu posílených stromů (například pařezů stromů) pro učení neparametrických funkcí tvaru a je založen na metodě popsané v [Intelligible Models for Classification and Regression](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) by Lou, Caruana a Gehrke.</span><span class="sxs-lookup"><span data-stu-id="40af6-111">The GAM trainer in ML.NET is implemented using shallow gradient boosted trees (for example tree stumps) to learn nonparametric shape functions, and is based on the method described in [Intelligible Models for Classification and Regression](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) by Lou, Caruana, and Gehrke.</span></span>

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

<span data-ttu-id="40af6-113">Příklad, jak trénovat model GAM a zkontrolovat a interpretovat výsledky, naleznete v [binární klasifikace trenér vzorku](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/Trainers/BinaryClassification/Gam.cs).</span><span class="sxs-lookup"><span data-stu-id="40af6-113">For an example of how to train a GAM model and inspect and interpret the results, see the [binary classification trainer sample](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/Trainers/BinaryClassification/Gam.cs).</span></span>
