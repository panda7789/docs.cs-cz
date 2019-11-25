---
title: Vysvětlete předpovědi modelů pomocí funkce permutace důležitost
description: Pochopení funkcí důležitosti modelů s funkcí permutace v ML.NET
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: 4bad8b0ed17a34ba290bf9c00d65cc3f000a2acf
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976690"
---
# <a name="explain-model-predictions-using-permutation-feature-importance"></a><span data-ttu-id="3c299-103">Vysvětlete předpovědi modelů pomocí funkce permutace důležitost</span><span class="sxs-lookup"><span data-stu-id="3c299-103">Explain model predictions using Permutation Feature Importance</span></span>

<span data-ttu-id="3c299-104">Naučte se vysvětlovat ML.NET Machine Learning model předpovědi tím, že porozumíte funkcím příspěvku předpovědi pomocí funkce permutace důležitost (PFI).</span><span class="sxs-lookup"><span data-stu-id="3c299-104">Learn how to explain ML.NET machine learning model predictions by understanding the contribution features have to predictions using Permutation Feature Importance (PFI).</span></span>

<span data-ttu-id="3c299-105">Modely strojového učení se často považovat za černé čtverečky, které přijímají vstupy a generují výstup.</span><span class="sxs-lookup"><span data-stu-id="3c299-105">Machine learning models are often thought of as black boxes that take inputs and generate an output.</span></span> <span data-ttu-id="3c299-106">Zprostředkující kroky nebo interakce mezi funkcemi, které ovlivňují výstup, se zřídka rozumí.</span><span class="sxs-lookup"><span data-stu-id="3c299-106">The intermediate steps or interactions among the features that influence the output are rarely understood.</span></span> <span data-ttu-id="3c299-107">Vzhledem k tomu, že je strojové učení zahrnuté do více aspektů každodenního života, jako je zdravotní péče, je velmi důležité pochopit, proč model strojového učení provádí rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="3c299-107">As machine learning is introduced into more aspects of everyday life such as healthcare, it's of utmost importance to understand why a machine learning model makes the decisions it does.</span></span> <span data-ttu-id="3c299-108">Například pokud jsou diagnostiky provedeny modelem strojového učení, odborníci na zdravotní péči potřebují způsob, jak se podívat na faktory, které se při diagnostikování prováděly.</span><span class="sxs-lookup"><span data-stu-id="3c299-108">For example, if diagnoses are made by a machine learning model, healthcare professionals need a way to look into the factors that went into making that diagnoses.</span></span> <span data-ttu-id="3c299-109">Poskytnutí správné diagnostiky by mohlo způsobit velký rozdíl na tom, jestli má pacient rychlejší obnovení.</span><span class="sxs-lookup"><span data-stu-id="3c299-109">Providing the right diagnosis could make a great difference on whether a patient has a speedy recovery or not.</span></span> <span data-ttu-id="3c299-110">Čím vyšší je úroveň vyjasnění v modelu, větší spolehlivé odborníky na zdravotní péči musí přijmout nebo odmítnout rozhodnutí učiněná modelem.</span><span class="sxs-lookup"><span data-stu-id="3c299-110">Therefore the higher the level of explainability in a model, the greater confidence healthcare professionals have to accept or reject the decisions made by the model.</span></span>

<span data-ttu-id="3c299-111">K vysvětlení modelů, z nichž jeden je PFI, se používají různé techniky.</span><span class="sxs-lookup"><span data-stu-id="3c299-111">Various techniques are used to explain models, one of which is PFI.</span></span> <span data-ttu-id="3c299-112">PFI je technika, která se používá k vysvětlení klasifikací a regresních modelů, které jsou nechte inspirovaty pomocí [ *náhodných doménových struktur* Breiman](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) (viz oddíl 10).</span><span class="sxs-lookup"><span data-stu-id="3c299-112">PFI is a technique used to explain classification and regression models that is inspired by [Breiman's *Random Forests* paper](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) (see section 10).</span></span> <span data-ttu-id="3c299-113">Na nejvyšší úrovni je způsob, jakým funguje, náhodným pohybem dat pro celou datovou sadu a výpočtem množství metriky výkonu, které se v zájmu sníží.</span><span class="sxs-lookup"><span data-stu-id="3c299-113">At a high level, the way it works is by randomly shuffling data one feature at a time for the entire dataset and calculating how much the performance metric of interest decreases.</span></span> <span data-ttu-id="3c299-114">Čím větší je tato změna, tím důležitější je funkce.</span><span class="sxs-lookup"><span data-stu-id="3c299-114">The larger the change, the more important that feature is.</span></span>

<span data-ttu-id="3c299-115">Kromě toho zvýrazňováním nejdůležitějších funkcí se mohou tvůrci modelů soustředit na použití podmnožiny smysluplných funkcí, které mohou potenciálně snižovat dobu šumu a školení.</span><span class="sxs-lookup"><span data-stu-id="3c299-115">Additionally, by highlighting the most important features, model builders can focus on using a subset of more meaningful features which can potentially reduce noise and training time.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="3c299-116">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="3c299-116">Load the data</span></span>

<span data-ttu-id="3c299-117">Funkce v datové sadě používané pro tuto ukázku jsou ve sloupcích 1-12.</span><span class="sxs-lookup"><span data-stu-id="3c299-117">The features in the dataset being used for this sample are in columns 1-12.</span></span> <span data-ttu-id="3c299-118">Cílem je předpovědět `Price`.</span><span class="sxs-lookup"><span data-stu-id="3c299-118">The goal is to predict `Price`.</span></span>

| <span data-ttu-id="3c299-119">Kolo</span><span class="sxs-lookup"><span data-stu-id="3c299-119">Column</span></span> | <span data-ttu-id="3c299-120">Funkce</span><span class="sxs-lookup"><span data-stu-id="3c299-120">Feature</span></span> | <span data-ttu-id="3c299-121">Popis</span><span class="sxs-lookup"><span data-stu-id="3c299-121">Description</span></span>
| --- | --- | --- |
| <span data-ttu-id="3c299-122">první</span><span class="sxs-lookup"><span data-stu-id="3c299-122">1</span></span> | <span data-ttu-id="3c299-123">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="3c299-123">CrimeRate</span></span> | <span data-ttu-id="3c299-124">Sazba za trestných činů za hlavu</span><span class="sxs-lookup"><span data-stu-id="3c299-124">Per capita crime rate</span></span>
| <span data-ttu-id="3c299-125">odst</span><span class="sxs-lookup"><span data-stu-id="3c299-125">2</span></span> | <span data-ttu-id="3c299-126">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="3c299-126">ResidentialZones</span></span> | <span data-ttu-id="3c299-127">Místní zóny ve městě</span><span class="sxs-lookup"><span data-stu-id="3c299-127">Residential zones in town</span></span>
| <span data-ttu-id="3c299-128">3</span><span class="sxs-lookup"><span data-stu-id="3c299-128">3</span></span> | <span data-ttu-id="3c299-129">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="3c299-129">CommercialZones</span></span> | <span data-ttu-id="3c299-130">Jiné než místní zóny ve městě</span><span class="sxs-lookup"><span data-stu-id="3c299-130">Non-residential zones in town</span></span>
| <span data-ttu-id="3c299-131">4</span><span class="sxs-lookup"><span data-stu-id="3c299-131">4</span></span> | <span data-ttu-id="3c299-132">NearWater</span><span class="sxs-lookup"><span data-stu-id="3c299-132">NearWater</span></span> | <span data-ttu-id="3c299-133">Blízkost k tělo vody</span><span class="sxs-lookup"><span data-stu-id="3c299-133">Proximity to body of water</span></span>
| <span data-ttu-id="3c299-134">5</span><span class="sxs-lookup"><span data-stu-id="3c299-134">5</span></span> | <span data-ttu-id="3c299-135">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="3c299-135">ToxicWasteLevels</span></span> | <span data-ttu-id="3c299-136">Úrovně toxicity (PPM)</span><span class="sxs-lookup"><span data-stu-id="3c299-136">Toxicity levels (PPM)</span></span>
| <span data-ttu-id="3c299-137">6</span><span class="sxs-lookup"><span data-stu-id="3c299-137">6</span></span> | <span data-ttu-id="3c299-138">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="3c299-138">AverageRoomNumber</span></span> | <span data-ttu-id="3c299-139">Průměrný počet místností v domu</span><span class="sxs-lookup"><span data-stu-id="3c299-139">Average number of rooms in house</span></span>
| <span data-ttu-id="3c299-140">čl</span><span class="sxs-lookup"><span data-stu-id="3c299-140">7</span></span> | <span data-ttu-id="3c299-141">Domovská stránka</span><span class="sxs-lookup"><span data-stu-id="3c299-141">HomeAge</span></span> | <span data-ttu-id="3c299-142">Stáří domů</span><span class="sxs-lookup"><span data-stu-id="3c299-142">Age of home</span></span>
| <span data-ttu-id="3c299-143">8</span><span class="sxs-lookup"><span data-stu-id="3c299-143">8</span></span> | <span data-ttu-id="3c299-144">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="3c299-144">BusinessCenterDistance</span></span> | <span data-ttu-id="3c299-145">Vzdálenost k nejbližší obchodní oblasti</span><span class="sxs-lookup"><span data-stu-id="3c299-145">Distance to nearest business district</span></span>
| <span data-ttu-id="3c299-146">9</span><span class="sxs-lookup"><span data-stu-id="3c299-146">9</span></span> | <span data-ttu-id="3c299-147">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="3c299-147">HighwayAccess</span></span> | <span data-ttu-id="3c299-148">Blízkost k dálnicím</span><span class="sxs-lookup"><span data-stu-id="3c299-148">Proximity to highways</span></span>
| <span data-ttu-id="3c299-149">10pruhový</span><span class="sxs-lookup"><span data-stu-id="3c299-149">10</span></span> | <span data-ttu-id="3c299-150">TaxRate</span><span class="sxs-lookup"><span data-stu-id="3c299-150">TaxRate</span></span> | <span data-ttu-id="3c299-151">Daňová sazba vlastnosti</span><span class="sxs-lookup"><span data-stu-id="3c299-151">Property tax rate</span></span>
| <span data-ttu-id="3c299-152">odst</span><span class="sxs-lookup"><span data-stu-id="3c299-152">11</span></span> | <span data-ttu-id="3c299-153">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="3c299-153">StudentTeacherRatio</span></span> | <span data-ttu-id="3c299-154">Poměr studentů k učitelům</span><span class="sxs-lookup"><span data-stu-id="3c299-154">Ratio of students to teachers</span></span>
| <span data-ttu-id="3c299-155">12,5</span><span class="sxs-lookup"><span data-stu-id="3c299-155">12</span></span> | <span data-ttu-id="3c299-156">PercentPopulationBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="3c299-156">PercentPopulationBelowPoverty</span></span> | <span data-ttu-id="3c299-157">Procento populace žijících po chudobě</span><span class="sxs-lookup"><span data-stu-id="3c299-157">Percent of population living below poverty</span></span>
| <span data-ttu-id="3c299-158">13,5</span><span class="sxs-lookup"><span data-stu-id="3c299-158">13</span></span> | <span data-ttu-id="3c299-159">Cenové</span><span class="sxs-lookup"><span data-stu-id="3c299-159">Price</span></span> | <span data-ttu-id="3c299-160">Cena domovské stránky</span><span class="sxs-lookup"><span data-stu-id="3c299-160">Price of the home</span></span>

<span data-ttu-id="3c299-161">Ukázka datové sady je uvedena níže:</span><span class="sxs-lookup"><span data-stu-id="3c299-161">A sample of the dataset is shown below:</span></span>

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

<span data-ttu-id="3c299-162">Data v této ukázce lze modelovat podle třídy, jako je `HousingPriceData` a načtena do [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="3c299-162">The data in this sample can be modeled by a class like `HousingPriceData` and loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

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

## <a name="train-the-model"></a><span data-ttu-id="3c299-163">Výuka modelu</span><span class="sxs-lookup"><span data-stu-id="3c299-163">Train the model</span></span>

<span data-ttu-id="3c299-164">Následující ukázka kódu znázorňuje proces školení modelu lineární regrese k předvídání cen za domácnosti.</span><span class="sxs-lookup"><span data-stu-id="3c299-164">The code sample below illustrates the process of training a linear regression model to predict house prices.</span></span>

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

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a><span data-ttu-id="3c299-165">Vysvětlení modelu s funkcí permutace – důležitost (PFI)</span><span class="sxs-lookup"><span data-stu-id="3c299-165">Explain the model with Permutation Feature Importance (PFI)</span></span>

<span data-ttu-id="3c299-166">V ML.NET použijte metodu [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) pro příslušnou úlohu.</span><span class="sxs-lookup"><span data-stu-id="3c299-166">In ML.NET use the [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) method for your respective task.</span></span>

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance =
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

<span data-ttu-id="3c299-167">Výsledkem použití [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) v datové sadě školení je [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) objektů [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) .</span><span class="sxs-lookup"><span data-stu-id="3c299-167">The result of using [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) on the training dataset is an [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) of [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) objects.</span></span> <span data-ttu-id="3c299-168">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) poskytuje souhrnnou statistiku, například střední hodnotu a směrodatnou odchylku pro více pozorování [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) rovno počtu permutací určených parametrem `permutationCount`.</span><span class="sxs-lookup"><span data-stu-id="3c299-168">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) provides summary statistics like mean and standard deviation for multiple observations of [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) equal to the number of permutations specified by the `permutationCount` parameter.</span></span>

<span data-ttu-id="3c299-169">Důležitost, nebo v tomto případě je absolutní průměrná míra snížení metriky R-čtverce vypočítaná pomocí [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) je pak možné seřadit od nejdůležitějších po nejméně důležité.</span><span class="sxs-lookup"><span data-stu-id="3c299-169">The importance, or in this case, the absolute average decrease in R-squared metric calculated by [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) can then be ordered from most important to least important.</span></span>

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

<span data-ttu-id="3c299-170">Tisk hodnot pro jednotlivé funkce v `featureImportanceMetrics` vygeneruje výstup podobný tomuto:.</span><span class="sxs-lookup"><span data-stu-id="3c299-170">Printing the values for each of the features in `featureImportanceMetrics` would generate output similar to that below.</span></span> <span data-ttu-id="3c299-171">Mějte na paměti, že byste měli očekávat, že byste měli zobrazit různé výsledky, protože tyto hodnoty se liší v závislosti na datech, která jsou uvedena.</span><span class="sxs-lookup"><span data-stu-id="3c299-171">Keep in mind that you should expect to see different results because these values vary based on the data that they are given.</span></span>

| <span data-ttu-id="3c299-172">Funkce</span><span class="sxs-lookup"><span data-stu-id="3c299-172">Feature</span></span> | <span data-ttu-id="3c299-173">Změnit na R-čtvercový</span><span class="sxs-lookup"><span data-stu-id="3c299-173">Change to R-Squared</span></span> |
|:--|:--:|
<span data-ttu-id="3c299-174">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="3c299-174">HighwayAccess</span></span>       |   <span data-ttu-id="3c299-175">-0,042731</span><span class="sxs-lookup"><span data-stu-id="3c299-175">-0.042731</span></span>
<span data-ttu-id="3c299-176">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="3c299-176">StudentTeacherRatio</span></span> |   <span data-ttu-id="3c299-177">-0,012730</span><span class="sxs-lookup"><span data-stu-id="3c299-177">-0.012730</span></span>
<span data-ttu-id="3c299-178">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="3c299-178">BusinessCenterDistance</span></span>| <span data-ttu-id="3c299-179">-0,010491</span><span class="sxs-lookup"><span data-stu-id="3c299-179">-0.010491</span></span>
<span data-ttu-id="3c299-180">TaxRate</span><span class="sxs-lookup"><span data-stu-id="3c299-180">TaxRate</span></span>             |   <span data-ttu-id="3c299-181">-0,008545</span><span class="sxs-lookup"><span data-stu-id="3c299-181">-0.008545</span></span>
<span data-ttu-id="3c299-182">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="3c299-182">AverageRoomNumber</span></span>   |   <span data-ttu-id="3c299-183">-0,003949</span><span class="sxs-lookup"><span data-stu-id="3c299-183">-0.003949</span></span>
<span data-ttu-id="3c299-184">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="3c299-184">CrimeRate</span></span>           |   <span data-ttu-id="3c299-185">-0,003665</span><span class="sxs-lookup"><span data-stu-id="3c299-185">-0.003665</span></span>
<span data-ttu-id="3c299-186">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="3c299-186">CommercialZones</span></span>     |   <span data-ttu-id="3c299-187">0,002749</span><span class="sxs-lookup"><span data-stu-id="3c299-187">0.002749</span></span>
<span data-ttu-id="3c299-188">Domovská stránka</span><span class="sxs-lookup"><span data-stu-id="3c299-188">HomeAge</span></span>             |   <span data-ttu-id="3c299-189">-0,002426</span><span class="sxs-lookup"><span data-stu-id="3c299-189">-0.002426</span></span>
<span data-ttu-id="3c299-190">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="3c299-190">ResidentialZones</span></span>    |   <span data-ttu-id="3c299-191">-0,002319</span><span class="sxs-lookup"><span data-stu-id="3c299-191">-0.002319</span></span>
<span data-ttu-id="3c299-192">NearWater</span><span class="sxs-lookup"><span data-stu-id="3c299-192">NearWater</span></span>           |   <span data-ttu-id="3c299-193">0,000203</span><span class="sxs-lookup"><span data-stu-id="3c299-193">0.000203</span></span>
<span data-ttu-id="3c299-194">PercentPopulationLivingBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="3c299-194">PercentPopulationLivingBelowPoverty</span></span>|    <span data-ttu-id="3c299-195">0,000031</span><span class="sxs-lookup"><span data-stu-id="3c299-195">0.000031</span></span>
<span data-ttu-id="3c299-196">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="3c299-196">ToxicWasteLevels</span></span>    |   <span data-ttu-id="3c299-197">-0,000019</span><span class="sxs-lookup"><span data-stu-id="3c299-197">-0.000019</span></span>

<span data-ttu-id="3c299-198">Podíváme se na pět nejdůležitějších funkcí pro tuto datovou sadu. cena na pracovišti, kterou tento model předpovídá, je ovlivněná jeho blízkostí vůči dálnicím, poměru učitelů v oblasti škol v oblasti, blízkost k hlavním pracovním centrům, daňové sazbě vlastností a Průměrný počet místností v domácnosti</span><span class="sxs-lookup"><span data-stu-id="3c299-198">Taking a look at the five most important features for this dataset, the price of a house predicted by this model is influenced by its proximity to highways, student teacher ratio of schools in the area, proximity to major employment centers, property tax rate and average number of rooms in the home.</span></span>
