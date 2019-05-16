---
title: Vysvětlují modelu predikce na základě důležitosti funkce permutaci
description: Pochopení důležitosti funkce modelů s důležitostí permutaci funkce v ML.NET
ms.date: 05/02/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: 51ef4b55b1518381881e57d83fd43f8ec7f786c6
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645062"
---
# <a name="explain-model-predictions-using-permutation-feature-importance"></a><span data-ttu-id="2d319-103">Vysvětlují modelu predikce na základě důležitosti funkce permutaci</span><span class="sxs-lookup"><span data-stu-id="2d319-103">Explain model predictions using Permutation Feature Importance</span></span>

<span data-ttu-id="2d319-104">Zjistěte, jak popisují ML.NET strojového učení předpovědí modelu podle principy, které funkce příspěvek muset predikce na základě důležitosti funkce permutací (PFI).</span><span class="sxs-lookup"><span data-stu-id="2d319-104">Learn how to explain ML.NET machine learning model predictions by understanding the contribution features have to predictions using Permutation Feature Importance (PFI).</span></span>

<span data-ttu-id="2d319-105">Modely strojového učení se často představit jako černé skříňky, které se daly přijímat vstupy a generovat výstup.</span><span class="sxs-lookup"><span data-stu-id="2d319-105">Machine learning models are often thought of as black boxes that take inputs and generate an output.</span></span> <span data-ttu-id="2d319-106">Zprostředkující kroky nebo interakcí mezi funkcí, které ovlivňují výstupu jsou zřídka pochopitelné.</span><span class="sxs-lookup"><span data-stu-id="2d319-106">The intermediate steps or interactions among the features that influence the output are rarely understood.</span></span> <span data-ttu-id="2d319-107">Machine learning zavedeném do více aspektů každodenního života jako je například zdravotní péče, je naprosto pochopit, proč strojového učení rozhodnutí, která využívá model dělá.</span><span class="sxs-lookup"><span data-stu-id="2d319-107">As machine learning is introduced into more aspects of everyday life such as healthcare, it's of utmost importance to understand why a machine learning model makes the decisions it does.</span></span> <span data-ttu-id="2d319-108">Například pokud Diagnostika vyrábí celá modelu strojového učení, odborníci v oblasti zdravotní péče potřebovat způsob, jak prozkoumat faktory, které byly přidány do toho, že Diagnostika.</span><span class="sxs-lookup"><span data-stu-id="2d319-108">For example, if diagnoses are made by a machine learning model, healthcare professionals need a way to look into the factors that went into making that diagnoses.</span></span> <span data-ttu-id="2d319-109">Poskytuje správné diagnostiku dokonce vytvářet velký rozdíl na, jestli pacienta má rychlé obnovení, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="2d319-109">Providing the right diagnosis could make a great difference on whether a patient has a speedy recovery or not.</span></span> <span data-ttu-id="2d319-110">Čím vyšší stupeň explainability v modelu, větší jistotou pracovníky tudíž přijmout nebo odmítnout rozhodnutí modelem.</span><span class="sxs-lookup"><span data-stu-id="2d319-110">Therefore the higher the level of explainability in a model, the greater confidence healthcare professionals have to accept or reject the decisions made by the model.</span></span>

<span data-ttu-id="2d319-111">Různých technik vytváření slouží k vysvětlení modelů, z nichž jeden je PFI.</span><span class="sxs-lookup"><span data-stu-id="2d319-111">Various techniques are used to explain models, one of which is PFI.</span></span> <span data-ttu-id="2d319-112">PFI je technika, použít k vysvětlení klasifikačních a regresních modelů, které se [společnosti Breiman *doménových struktur Random* papíru](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf)(viz část 10).</span><span class="sxs-lookup"><span data-stu-id="2d319-112">PFI is a technique used to explain classification and regression models that is inspired by [Breiman's *Random Forests* paper](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf)(see section 10).</span></span> <span data-ttu-id="2d319-113">Na vysoké úrovni je způsob, jakým funguje tak, že náhodně přesouvání dat jednu funkci současně pro celou datovou sadu a výpočtu, kolik metrika výkonu zájmu snižuje.</span><span class="sxs-lookup"><span data-stu-id="2d319-113">At a high level, the way it works is by randomly shuffling data one feature at a time for the entire dataset and calculating how much the performance metric of interest decreases.</span></span> <span data-ttu-id="2d319-114">Čím větší změny, důležitější, je tato funkce.</span><span class="sxs-lookup"><span data-stu-id="2d319-114">The larger the change, the more important that feature is.</span></span> 

<span data-ttu-id="2d319-115">Kromě toho zvýrazněním nejdůležitější funkce tvůrci modelu soustředit se na pomocí některé podsady lépe vystihuje funkcí, které může potenciálně snížit šum a čas školení.</span><span class="sxs-lookup"><span data-stu-id="2d319-115">Additionally, by highlighting the most important features, model builders can focus on using a subset of more meaningful features which can potentially reduce noise and training time.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="2d319-116">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="2d319-116">Load the data</span></span>

<span data-ttu-id="2d319-117">Funkce v datové sadě, se používají pro tuto ukázku se ve sloupcích 1 – 12.</span><span class="sxs-lookup"><span data-stu-id="2d319-117">The features in the dataset being used for this sample are in columns 1-12.</span></span> <span data-ttu-id="2d319-118">Cílem je možnost předvídat `Price`.</span><span class="sxs-lookup"><span data-stu-id="2d319-118">The goal is to predict `Price`.</span></span> 

| <span data-ttu-id="2d319-119">Sloupec</span><span class="sxs-lookup"><span data-stu-id="2d319-119">Column</span></span> | <span data-ttu-id="2d319-120">Funkce</span><span class="sxs-lookup"><span data-stu-id="2d319-120">Feature</span></span> | <span data-ttu-id="2d319-121">Popis</span><span class="sxs-lookup"><span data-stu-id="2d319-121">Description</span></span> 
| --- | --- | --- |
| <span data-ttu-id="2d319-122">1</span><span class="sxs-lookup"><span data-stu-id="2d319-122">1</span></span> | <span data-ttu-id="2d319-123">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="2d319-123">CrimeRate</span></span> | <span data-ttu-id="2d319-124">Za hlavu crime</span><span class="sxs-lookup"><span data-stu-id="2d319-124">Per capita crime rate</span></span>
| <span data-ttu-id="2d319-125">2</span><span class="sxs-lookup"><span data-stu-id="2d319-125">2</span></span> | <span data-ttu-id="2d319-126">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="2d319-126">ResidentialZones</span></span> | <span data-ttu-id="2d319-127">Domácí zón ve městě</span><span class="sxs-lookup"><span data-stu-id="2d319-127">Residential zones in town</span></span>
| <span data-ttu-id="2d319-128">3</span><span class="sxs-lookup"><span data-stu-id="2d319-128">3</span></span> | <span data-ttu-id="2d319-129">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="2d319-129">CommercialZones</span></span> | <span data-ttu-id="2d319-130">Domácí bez zón ve městě</span><span class="sxs-lookup"><span data-stu-id="2d319-130">Non-residential zones in town</span></span>
| <span data-ttu-id="2d319-131">4</span><span class="sxs-lookup"><span data-stu-id="2d319-131">4</span></span> | <span data-ttu-id="2d319-132">NearWater</span><span class="sxs-lookup"><span data-stu-id="2d319-132">NearWater</span></span> | <span data-ttu-id="2d319-133">Blízkosti textu vody</span><span class="sxs-lookup"><span data-stu-id="2d319-133">Proximity to body of water</span></span>
| <span data-ttu-id="2d319-134">5</span><span class="sxs-lookup"><span data-stu-id="2d319-134">5</span></span> | <span data-ttu-id="2d319-135">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="2d319-135">ToxicWasteLevels</span></span> | <span data-ttu-id="2d319-136">Toxicity úrovně (PPM)</span><span class="sxs-lookup"><span data-stu-id="2d319-136">Toxicity levels (PPM)</span></span>
| <span data-ttu-id="2d319-137">6</span><span class="sxs-lookup"><span data-stu-id="2d319-137">6</span></span> | <span data-ttu-id="2d319-138">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="2d319-138">AverageRoomNumber</span></span> | <span data-ttu-id="2d319-139">Průměrný počet místnosti interně</span><span class="sxs-lookup"><span data-stu-id="2d319-139">Average number of rooms in house</span></span>
| <span data-ttu-id="2d319-140">7</span><span class="sxs-lookup"><span data-stu-id="2d319-140">7</span></span> | <span data-ttu-id="2d319-141">HomeAge</span><span class="sxs-lookup"><span data-stu-id="2d319-141">HomeAge</span></span> | <span data-ttu-id="2d319-142">Stáří Domovská stránka</span><span class="sxs-lookup"><span data-stu-id="2d319-142">Age of home</span></span>
| <span data-ttu-id="2d319-143">8</span><span class="sxs-lookup"><span data-stu-id="2d319-143">8</span></span> | <span data-ttu-id="2d319-144">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="2d319-144">BusinessCenterDistance</span></span> | <span data-ttu-id="2d319-145">Vzdálenost do nejbližší oblasti podnikání</span><span class="sxs-lookup"><span data-stu-id="2d319-145">Distance to nearest business district</span></span>
| <span data-ttu-id="2d319-146">9</span><span class="sxs-lookup"><span data-stu-id="2d319-146">9</span></span> | <span data-ttu-id="2d319-147">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="2d319-147">HighwayAccess</span></span> | <span data-ttu-id="2d319-148">Blízkosti dálnice</span><span class="sxs-lookup"><span data-stu-id="2d319-148">Proximity to highways</span></span>
| <span data-ttu-id="2d319-149">10</span><span class="sxs-lookup"><span data-stu-id="2d319-149">10</span></span> | <span data-ttu-id="2d319-150">TaxRate</span><span class="sxs-lookup"><span data-stu-id="2d319-150">TaxRate</span></span> | <span data-ttu-id="2d319-151">Sazba daně vlastnost</span><span class="sxs-lookup"><span data-stu-id="2d319-151">Property tax rate</span></span>
| <span data-ttu-id="2d319-152">11</span><span class="sxs-lookup"><span data-stu-id="2d319-152">11</span></span> | <span data-ttu-id="2d319-153">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="2d319-153">StudentTeacherRatio</span></span> | <span data-ttu-id="2d319-154">Poměr studentů pro učitele</span><span class="sxs-lookup"><span data-stu-id="2d319-154">Ratio of students to teachers</span></span>
| <span data-ttu-id="2d319-155">12</span><span class="sxs-lookup"><span data-stu-id="2d319-155">12</span></span> | <span data-ttu-id="2d319-156">PercentPopulationBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="2d319-156">PercentPopulationBelowPoverty</span></span> | <span data-ttu-id="2d319-157">Procento naplnění žijete pod chudoby</span><span class="sxs-lookup"><span data-stu-id="2d319-157">Percent of population living below poverty</span></span>
| <span data-ttu-id="2d319-158">13</span><span class="sxs-lookup"><span data-stu-id="2d319-158">13</span></span> | <span data-ttu-id="2d319-159">Cena</span><span class="sxs-lookup"><span data-stu-id="2d319-159">Price</span></span> | <span data-ttu-id="2d319-160">Cena Domovská stránka</span><span class="sxs-lookup"><span data-stu-id="2d319-160">Price of the home</span></span>

<span data-ttu-id="2d319-161">Ukázkové datové sady, která je zobrazena níže:</span><span class="sxs-lookup"><span data-stu-id="2d319-161">A sample of the dataset is shown below:</span></span>

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

<span data-ttu-id="2d319-162">Data v této ukázce můžete modelovány pomocí třídy jako `HousingPriceData`:</span><span class="sxs-lookup"><span data-stu-id="2d319-162">The data in this sample can be modeled by a class like `HousingPriceData`:</span></span>

```csharp
class HousingPriceData
{
    [LoadColumn(0)]
    public float CrimeRate { get; set; }

    [LoadColumn(1)]
    public float ResidentialZones { get; set; }

    [LoadColumn(2)]
    public float CommercialZones { get; set; }

    [LoadColumn(3)]
    public float NearWater { get; set; }

    [LoadColumn(4)]
    public float ToxicWasteLevels { get; set; }

    [LoadColumn(5)]
    public float AverageRoomNumber { get; set; }

    [LoadColumn(6)]
    public float HomeAge { get; set; }

    [LoadColumn(7)]
    public float BusinessCenterDistance { get; set; }

    [LoadColumn(8)]
    public float HighwayAccess { get; set; }

    [LoadColumn(9)]
    public float TaxRate { get; set; }

    [LoadColumn(10)]
    public float StudentTeacherRatio { get; set; }

    [LoadColumn(11)]
    public float PercentPopulationBelowPoverty { get; set; }

    [LoadColumn(12)]
    [ColumnName("Label")]
    public float Price { get; set; }
}
```

<span data-ttu-id="2d319-163">Načtení dat do [ `IDataView` ](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="2d319-163">Load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

## <a name="train-the-model"></a><span data-ttu-id="2d319-164">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="2d319-164">Train the model</span></span>

<span data-ttu-id="2d319-165">Následující vzorový kód ukazuje procesu trénování modelu lineární regrese k předvídání cen organizace.</span><span class="sxs-lookup"><span data-stu-id="2d319-165">The code sample below illustrates the process of training a linear regression model to predict house prices.</span></span>

```csharp
// 1. Get the column name of input features.
string[] featureColumnNames = 
    data.Schema
        .Select(column => column.Name)
        .Where(columnName => columnName != "Label").ToArray();

// 2. Define estimator with data pre-processing steps
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", featureColumnNames)
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// 3. Create transformer using the data pre-processing estimator
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(data);

// 4. Pre-process the training data
IDataView preprocessedTrainData = dataPrepTransformer.Transform(data);

// 5. Define Stochastic Dual Coordinate Ascent machine learning estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// 6. Train machine learning model
var sdcaModel = sdcaEstimator.Fit(preprocessedTrainData);
```

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a><span data-ttu-id="2d319-166">Vysvětlují modelu s permutaci funkce význam (PFI)</span><span class="sxs-lookup"><span data-stu-id="2d319-166">Explain the model with Permutation Feature Importance (PFI)</span></span>

<span data-ttu-id="2d319-167">Používá ML.NET [ `PermutationFeatureImportance` ](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) metodu pro příslušné úlohy.</span><span class="sxs-lookup"><span data-stu-id="2d319-167">In ML.NET use the [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) method for your respective task.</span></span>

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance = 
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

<span data-ttu-id="2d319-168">Výsledek použití [ `PermutationFeatureImportance` ](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) na trénovací datové sady je [ `ImmutableArray` ](xref:System.Collections.Immutable.ImmutableArray) z [ `RegressionMetricsStatistics` ](xref:Microsoft.ML.Data.RegressionMetricsStatistics) objekty.</span><span class="sxs-lookup"><span data-stu-id="2d319-168">The result of using [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) on the training dataset is an [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) of [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) objects.</span></span> <span data-ttu-id="2d319-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) poskytuje souhrnné statistiky, jako je průměr a směrodatné odchylky pro více pozorování [ `RegressionMetrics` ](xref:Microsoft.ML.Data.RegressionMetrics) rovna počtu permutací určené `permutationCount` parametru.</span><span class="sxs-lookup"><span data-stu-id="2d319-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) provides summary statistics like mean and standard deviation for multiple observations of [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) equal to the number of permutations specified by the `permutationCount` parameter.</span></span>

<span data-ttu-id="2d319-170">Význam, nebo v tomto případě absolutní průměrná snížení spolehlivosti R metrika vypočte tak, že [ `PermutationFeatureImportance` ](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) lze pak provést řazení z vašich nejdůležitějších a nejméně důležitá.</span><span class="sxs-lookup"><span data-stu-id="2d319-170">The importance, or in this case, the absolute average decrease in R-squared metric calculated by [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) can then be ordered from most important to least important.</span></span>  

```csharp
// Order features by importance
var featureImportanceMetrics =
    permutationFeatureImportance
        .Select((metric, index) => new { index, metric.RSquared })
        .OrderByDescending(myFeatures => Math.Abs(myFeatures.RSquared.Mean));

Console.WriteLine("Feature\tPFI");

foreach (var feature in featureImportanceMetrics)
{
    Console.WriteLine($"{featureColumnNames[feature.index],-20}|\t{feature.RSquared.Mean:F6}");
}
```

<span data-ttu-id="2d319-171">Tisk hodnoty pro každé z těchto funkcí v `featureImportanceMetrics` vygenerují výstup podobný tomu níže.</span><span class="sxs-lookup"><span data-stu-id="2d319-171">Printing the values for each of the features in `featureImportanceMetrics` would generate output similar to that below.</span></span> <span data-ttu-id="2d319-172">Mějte na paměti, která by se měl zobrazit odlišné výsledky vzhledem k tomu, že tyto hodnoty se liší podle data, která jsou uvedeny.</span><span class="sxs-lookup"><span data-stu-id="2d319-172">Keep in mind that you should expect to see different results because these values vary based on the data that they are given.</span></span>  

| <span data-ttu-id="2d319-173">Funkce</span><span class="sxs-lookup"><span data-stu-id="2d319-173">Feature</span></span> | <span data-ttu-id="2d319-174">Změnit na spolehlivosti R</span><span class="sxs-lookup"><span data-stu-id="2d319-174">Change to R-Squared</span></span> |
|:--|:--:|
<span data-ttu-id="2d319-175">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="2d319-175">HighwayAccess</span></span>       |   <span data-ttu-id="2d319-176">-0.042731</span><span class="sxs-lookup"><span data-stu-id="2d319-176">-0.042731</span></span>
<span data-ttu-id="2d319-177">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="2d319-177">StudentTeacherRatio</span></span> |   <span data-ttu-id="2d319-178">-0.012730</span><span class="sxs-lookup"><span data-stu-id="2d319-178">-0.012730</span></span>
<span data-ttu-id="2d319-179">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="2d319-179">BusinessCenterDistance</span></span>| <span data-ttu-id="2d319-180">-0.010491</span><span class="sxs-lookup"><span data-stu-id="2d319-180">-0.010491</span></span>
<span data-ttu-id="2d319-181">TaxRate</span><span class="sxs-lookup"><span data-stu-id="2d319-181">TaxRate</span></span>             |   <span data-ttu-id="2d319-182">-0.008545</span><span class="sxs-lookup"><span data-stu-id="2d319-182">-0.008545</span></span>
<span data-ttu-id="2d319-183">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="2d319-183">AverageRoomNumber</span></span>   |   <span data-ttu-id="2d319-184">-0.003949</span><span class="sxs-lookup"><span data-stu-id="2d319-184">-0.003949</span></span>
<span data-ttu-id="2d319-185">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="2d319-185">CrimeRate</span></span>           |   <span data-ttu-id="2d319-186">-0.003665</span><span class="sxs-lookup"><span data-stu-id="2d319-186">-0.003665</span></span>
<span data-ttu-id="2d319-187">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="2d319-187">CommercialZones</span></span>     |   <span data-ttu-id="2d319-188">0.002749</span><span class="sxs-lookup"><span data-stu-id="2d319-188">0.002749</span></span>
<span data-ttu-id="2d319-189">HomeAge</span><span class="sxs-lookup"><span data-stu-id="2d319-189">HomeAge</span></span>             |   <span data-ttu-id="2d319-190">-0.002426</span><span class="sxs-lookup"><span data-stu-id="2d319-190">-0.002426</span></span>
<span data-ttu-id="2d319-191">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="2d319-191">ResidentialZones</span></span>    |   <span data-ttu-id="2d319-192">-0.002319</span><span class="sxs-lookup"><span data-stu-id="2d319-192">-0.002319</span></span>
<span data-ttu-id="2d319-193">NearWater</span><span class="sxs-lookup"><span data-stu-id="2d319-193">NearWater</span></span>           |   <span data-ttu-id="2d319-194">0.000203</span><span class="sxs-lookup"><span data-stu-id="2d319-194">0.000203</span></span>
<span data-ttu-id="2d319-195">PercentPopulationLivingBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="2d319-195">PercentPopulationLivingBelowPoverty</span></span>|    <span data-ttu-id="2d319-196">0.000031</span><span class="sxs-lookup"><span data-stu-id="2d319-196">0.000031</span></span>
<span data-ttu-id="2d319-197">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="2d319-197">ToxicWasteLevels</span></span>    |   <span data-ttu-id="2d319-198">-0.000019</span><span class="sxs-lookup"><span data-stu-id="2d319-198">-0.000019</span></span>

<span data-ttu-id="2d319-199">A podívejte se na pět nejdůležitější funkce pro tuto datovou sadu, cena house předpovídané pomocí tohoto modelu je ovlivněno umístění v blízkosti dálnice, studenty, vyučující poměr školy v oblasti, blízkosti hlavní zaměstnání centra, sazba daně vlastnost a Průměrný počet místnosti na domovské stránce.</span><span class="sxs-lookup"><span data-stu-id="2d319-199">Taking a look at the the five most important features for this dataset, the price of a house predicted by this model is influenced by its proximity to highways, student teacher ratio of schools in the area, proximity to major employment centers, property tax rate and average number of rooms in the home.</span></span>
