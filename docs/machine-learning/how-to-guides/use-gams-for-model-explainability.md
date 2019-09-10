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
# <a name="use-generalized-additive-models-and-shape-functions-for-model-explainability-in-mlnet"></a><span data-ttu-id="2bcb6-103">Použití generalizované doplňkové modely a funkcí tvarů pro vyjasnění modelu v ML.NET</span><span class="sxs-lookup"><span data-stu-id="2bcb6-103">Use Generalized Additive Models and shape functions for model explainability in ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="2bcb6-104">Toto téma odkazuje na ML.NET, který je aktuálně ve verzi Preview, a materiál může být změněn.</span><span class="sxs-lookup"><span data-stu-id="2bcb6-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="2bcb6-105">Další informace najdete na stránce [ml.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) .</span><span class="sxs-lookup"><span data-stu-id="2bcb6-105">For more information, visit the [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) page.</span></span>

<span data-ttu-id="2bcb6-106">Tato ukázka s postupy a souvisejícími ukázkami aktuálně používá **ml.NET verze 0,10**.</span><span class="sxs-lookup"><span data-stu-id="2bcb6-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="2bcb6-107">Další informace najdete v poznámkách k verzi v [úložišti GitHub/Machinelearning GitHub](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="2bcb6-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="2bcb6-108">Při vytváření modelů strojového učení není často dost dělat předpovědi.</span><span class="sxs-lookup"><span data-stu-id="2bcb6-108">When creating machine learning models, it is often not enough to simply make predictions.</span></span> <span data-ttu-id="2bcb6-109">Vývojáři strojového učení, tvůrci rozhodování a oprávnění ovlivněné modely potřebují pochopit, jak modely strojového učení vytvářejí rozhodnutí a jaké funkce přispívají ke svému výkonu.</span><span class="sxs-lookup"><span data-stu-id="2bcb6-109">Often, machine learning developers, decision makers, and those affected by the models need to understand how machine learning models make decisions and which features contribute to their performance.</span></span> <span data-ttu-id="2bcb6-110">Model **generalizované doplňkové látky (GAMs)** se interně používá v Microsoftu, aby se usnadnilo vytváření modelů, které vývojářům strojového učení pomůžou vytvářet modely s vysokou kapacitou, které můžou snadno interpretovat jiní uživatelé.</span><span class="sxs-lookup"><span data-stu-id="2bcb6-110">**Generalized Additive Models (GAMs)** are used internally at Microsoft for model explainability to help machine learning developers create high-capacity models that can be easily interpreted by others.</span></span>

<span data-ttu-id="2bcb6-111">GAMs jsou třída **interpretované modely** , které jsou lineární modely, kde jsou tyto výrazy nelineární funkce, nazývané "funkce tvarů" jedné proměnné.</span><span class="sxs-lookup"><span data-stu-id="2bcb6-111">GAMs are a class of **interpretable models** that are linear models where the terms are nonlinear functions, called "shape functions" of a single variable.</span></span> <span data-ttu-id="2bcb6-112">Jako lineární modely jsou snadno interpretované, ale vzhledem k tomu, že modely se učí funkce funkcí místo jedné váhy, můžou modelovat složitější vztahy než jednoduchý lineární model.</span><span class="sxs-lookup"><span data-stu-id="2bcb6-112">As linear models, they are easily interpreted but because the models learn functions of features instead of a single weight, they can model more complex relationships than a simple linear model.</span></span> <span data-ttu-id="2bcb6-113">Výsledný prediktivní GAM má zachycený výraz, který představuje průměrnou předpověď v rámci sady školení a funkce tvarů, které představují odchylku od průměrného předpovědi.</span><span class="sxs-lookup"><span data-stu-id="2bcb6-113">The resulting GAM predictor has an intercept term that represents the average prediction over the training set, and shape functions that represent the deviation from the average prediction.</span></span> <span data-ttu-id="2bcb6-114">Funkce tvaru lze kontrolovat podle očí, aby bylo možné zobrazit odpověď modelu na různé hodnoty funkce a vizuálů jako následující graf, který je vytvořen na konci příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="2bcb6-114">The shape functions can be inspected by eye to see the response of the model to different values of a feature, and visualized like the following graph that is created at the end of the code example.</span></span> <span data-ttu-id="2bcb6-115">GAM Trainer v ML.NET je implementována pomocí nepřipojených stromů se zesílenými přechody (například stromu stumps) k získání funkcí neparametrového tvaru a je založena na metodě popsané v [srozumitelných modelech pro klasifikaci a regresi](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) pomocí Lou, Caruana a Gehrke.</span><span class="sxs-lookup"><span data-stu-id="2bcb6-115">The GAM trainer in ML.NET is implemented using shallow gradient boosted trees (for example tree stumps) to learn nonparametric shape functions, and is based on the method described in [Intelligible Models for Classification and Regression](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) by Lou, Caruana, and Gehrke.</span></span>

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

<span data-ttu-id="2bcb6-117">Ukázku toho, jak vytvořit model GAM a prozkoumat a interpretovat výsledky, najdete v [úložišti GitHub/Machinelearning GitHub](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs).</span><span class="sxs-lookup"><span data-stu-id="2bcb6-117">For a sample of how to train a GAM model and inspect and interpret the results, see [the dotnet/machinelearning GitHub repository](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs).</span></span>
