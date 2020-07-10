---
title: Interpretace ML.NET modelů se závažností funkcí permutace
description: Pochopení funkcí důležitosti modelů s funkcí permutace v ML.NET
ms.date: 01/30/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: ed0d6736f1f2e988d96a397cad77a7fc743489da
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174228"
---
# <a name="interpret-model-predictions-using-permutation-feature-importance"></a><span data-ttu-id="c5b5d-103">Interpretace předpovědi modelů pomocí funkce permutace důležitost</span><span class="sxs-lookup"><span data-stu-id="c5b5d-103">Interpret model predictions using Permutation Feature Importance</span></span>

<span data-ttu-id="c5b5d-104">Pomocí funkce permutace Feature důležitost (PFI) se dozvíte, jak interpretovat ML.NET předpovědi modelu Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="c5b5d-104">Using Permutation Feature Importance (PFI), learn how to interpret ML.NET machine learning model predictions.</span></span> <span data-ttu-id="c5b5d-105">PFI poskytuje relativní příspěvek, který každá funkce provede předpověď.</span><span class="sxs-lookup"><span data-stu-id="c5b5d-105">PFI gives the relative contribution each feature makes to a prediction.</span></span>

<span data-ttu-id="c5b5d-106">Modely strojového učení se často považovat za neprůhledná pole, která přijímají vstupy a generují výstup.</span><span class="sxs-lookup"><span data-stu-id="c5b5d-106">Machine learning models are often thought of as opaque boxes that take inputs and generate an output.</span></span> <span data-ttu-id="c5b5d-107">Zprostředkující kroky nebo interakce mezi funkcemi, které ovlivňují výstup, se zřídka rozumí.</span><span class="sxs-lookup"><span data-stu-id="c5b5d-107">The intermediate steps or interactions among the features that influence the output are rarely understood.</span></span> <span data-ttu-id="c5b5d-108">Vzhledem k tomu, že je strojové učení zahrnuté do více aspektů každodenního života, jako je zdravotní péče, je velmi důležité pochopit, proč model strojového učení provádí rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="c5b5d-108">As machine learning is introduced into more aspects of everyday life such as healthcare, it's of utmost importance to understand why a machine learning model makes the decisions it does.</span></span> <span data-ttu-id="c5b5d-109">Například pokud jsou diagnostiky provedeny modelem strojového učení, odborníci na zdravotní péči potřebují způsob, jak se podívat na faktory, které se při diagnostikování prováděly.</span><span class="sxs-lookup"><span data-stu-id="c5b5d-109">For example, if diagnoses are made by a machine learning model, healthcare professionals need a way to look into the factors that went into making that diagnoses.</span></span> <span data-ttu-id="c5b5d-110">Poskytnutí správné diagnostiky by mohlo způsobit velký rozdíl na tom, jestli má pacient rychlejší obnovení.</span><span class="sxs-lookup"><span data-stu-id="c5b5d-110">Providing the right diagnosis could make a great difference on whether a patient has a speedy recovery or not.</span></span> <span data-ttu-id="c5b5d-111">Čím vyšší je úroveň vyjasnění v modelu, větší spolehlivé odborníky na zdravotní péči musí přijmout nebo odmítnout rozhodnutí učiněná modelem.</span><span class="sxs-lookup"><span data-stu-id="c5b5d-111">Therefore the higher the level of explainability in a model, the greater confidence healthcare professionals have to accept or reject the decisions made by the model.</span></span>

<span data-ttu-id="c5b5d-112">K vysvětlení modelů, z nichž jeden je PFI, se používají různé techniky.</span><span class="sxs-lookup"><span data-stu-id="c5b5d-112">Various techniques are used to explain models, one of which is PFI.</span></span> <span data-ttu-id="c5b5d-113">PFI je technika, která se používá k vysvětlení klasifikací a regresních modelů, které jsou nechte inspirovaty pomocí [ *náhodných doménových struktur* Breiman](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) (viz oddíl 10).</span><span class="sxs-lookup"><span data-stu-id="c5b5d-113">PFI is a technique used to explain classification and regression models that is inspired by [Breiman's *Random Forests* paper](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) (see section 10).</span></span> <span data-ttu-id="c5b5d-114">Na nejvyšší úrovni je způsob, jakým funguje, náhodným pohybem dat pro celou datovou sadu a výpočtem množství metriky výkonu, které se v zájmu sníží.</span><span class="sxs-lookup"><span data-stu-id="c5b5d-114">At a high level, the way it works is by randomly shuffling data one feature at a time for the entire dataset and calculating how much the performance metric of interest decreases.</span></span> <span data-ttu-id="c5b5d-115">Čím větší je tato změna, tím důležitější je funkce.</span><span class="sxs-lookup"><span data-stu-id="c5b5d-115">The larger the change, the more important that feature is.</span></span>

<span data-ttu-id="c5b5d-116">Kromě toho zvýrazňováním nejdůležitějších funkcí se mohou tvůrci modelů soustředit na použití podmnožiny smysluplných funkcí, které mohou potenciálně snižovat dobu šumu a školení.</span><span class="sxs-lookup"><span data-stu-id="c5b5d-116">Additionally, by highlighting the most important features, model builders can focus on using a subset of more meaningful features which can potentially reduce noise and training time.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="c5b5d-117">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="c5b5d-117">Load the data</span></span>

<span data-ttu-id="c5b5d-118">Funkce v datové sadě používané pro tuto ukázku jsou ve sloupcích 1-12.</span><span class="sxs-lookup"><span data-stu-id="c5b5d-118">The features in the dataset being used for this sample are in columns 1-12.</span></span> <span data-ttu-id="c5b5d-119">Cílem je předpovědět `Price` .</span><span class="sxs-lookup"><span data-stu-id="c5b5d-119">The goal is to predict `Price`.</span></span>

| <span data-ttu-id="c5b5d-120">Sloupec</span><span class="sxs-lookup"><span data-stu-id="c5b5d-120">Column</span></span> | <span data-ttu-id="c5b5d-121">Funkce</span><span class="sxs-lookup"><span data-stu-id="c5b5d-121">Feature</span></span> | <span data-ttu-id="c5b5d-122">Popis</span><span class="sxs-lookup"><span data-stu-id="c5b5d-122">Description</span></span>
| --- | --- | --- |
| <span data-ttu-id="c5b5d-123">1</span><span class="sxs-lookup"><span data-stu-id="c5b5d-123">1</span></span> | <span data-ttu-id="c5b5d-124">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="c5b5d-124">CrimeRate</span></span> | <span data-ttu-id="c5b5d-125">Sazba za trestných činů za hlavu</span><span class="sxs-lookup"><span data-stu-id="c5b5d-125">Per capita crime rate</span></span>
| <span data-ttu-id="c5b5d-126">2</span><span class="sxs-lookup"><span data-stu-id="c5b5d-126">2</span></span> | <span data-ttu-id="c5b5d-127">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="c5b5d-127">ResidentialZones</span></span> | <span data-ttu-id="c5b5d-128">Místní zóny ve městě</span><span class="sxs-lookup"><span data-stu-id="c5b5d-128">Residential zones in town</span></span>
| <span data-ttu-id="c5b5d-129">3</span><span class="sxs-lookup"><span data-stu-id="c5b5d-129">3</span></span> | <span data-ttu-id="c5b5d-130">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="c5b5d-130">CommercialZones</span></span> | <span data-ttu-id="c5b5d-131">Jiné než místní zóny ve městě</span><span class="sxs-lookup"><span data-stu-id="c5b5d-131">Non-residential zones in town</span></span>
| <span data-ttu-id="c5b5d-132">4</span><span class="sxs-lookup"><span data-stu-id="c5b5d-132">4</span></span> | <span data-ttu-id="c5b5d-133">NearWater</span><span class="sxs-lookup"><span data-stu-id="c5b5d-133">NearWater</span></span> | <span data-ttu-id="c5b5d-134">Blízkost k tělo vody</span><span class="sxs-lookup"><span data-stu-id="c5b5d-134">Proximity to body of water</span></span>
| <span data-ttu-id="c5b5d-135">5</span><span class="sxs-lookup"><span data-stu-id="c5b5d-135">5</span></span> | <span data-ttu-id="c5b5d-136">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="c5b5d-136">ToxicWasteLevels</span></span> | <span data-ttu-id="c5b5d-137">Úrovně toxicity (PPM)</span><span class="sxs-lookup"><span data-stu-id="c5b5d-137">Toxicity levels (PPM)</span></span>
| <span data-ttu-id="c5b5d-138">6</span><span class="sxs-lookup"><span data-stu-id="c5b5d-138">6</span></span> | <span data-ttu-id="c5b5d-139">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="c5b5d-139">AverageRoomNumber</span></span> | <span data-ttu-id="c5b5d-140">Průměrný počet místností v domu</span><span class="sxs-lookup"><span data-stu-id="c5b5d-140">Average number of rooms in house</span></span>
| <span data-ttu-id="c5b5d-141">7</span><span class="sxs-lookup"><span data-stu-id="c5b5d-141">7</span></span> | <span data-ttu-id="c5b5d-142">Domovská stránka</span><span class="sxs-lookup"><span data-stu-id="c5b5d-142">HomeAge</span></span> | <span data-ttu-id="c5b5d-143">Stáří domů</span><span class="sxs-lookup"><span data-stu-id="c5b5d-143">Age of home</span></span>
| <span data-ttu-id="c5b5d-144">8</span><span class="sxs-lookup"><span data-stu-id="c5b5d-144">8</span></span> | <span data-ttu-id="c5b5d-145">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="c5b5d-145">BusinessCenterDistance</span></span> | <span data-ttu-id="c5b5d-146">Vzdálenost k nejbližší obchodní oblasti</span><span class="sxs-lookup"><span data-stu-id="c5b5d-146">Distance to nearest business district</span></span>
| <span data-ttu-id="c5b5d-147">9</span><span class="sxs-lookup"><span data-stu-id="c5b5d-147">9</span></span> | <span data-ttu-id="c5b5d-148">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="c5b5d-148">HighwayAccess</span></span> | <span data-ttu-id="c5b5d-149">Blízkost k dálnicím</span><span class="sxs-lookup"><span data-stu-id="c5b5d-149">Proximity to highways</span></span>
| <span data-ttu-id="c5b5d-150">10</span><span class="sxs-lookup"><span data-stu-id="c5b5d-150">10</span></span> | <span data-ttu-id="c5b5d-151">TaxRate</span><span class="sxs-lookup"><span data-stu-id="c5b5d-151">TaxRate</span></span> | <span data-ttu-id="c5b5d-152">Daňová sazba vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c5b5d-152">Property tax rate</span></span>
| <span data-ttu-id="c5b5d-153">11</span><span class="sxs-lookup"><span data-stu-id="c5b5d-153">11</span></span> | <span data-ttu-id="c5b5d-154">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="c5b5d-154">StudentTeacherRatio</span></span> | <span data-ttu-id="c5b5d-155">Poměr studentů k učitelům</span><span class="sxs-lookup"><span data-stu-id="c5b5d-155">Ratio of students to teachers</span></span>
| <span data-ttu-id="c5b5d-156">12</span><span class="sxs-lookup"><span data-stu-id="c5b5d-156">12</span></span> | <span data-ttu-id="c5b5d-157">PercentPopulationBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="c5b5d-157">PercentPopulationBelowPoverty</span></span> | <span data-ttu-id="c5b5d-158">Procento populace žijících po chudobě</span><span class="sxs-lookup"><span data-stu-id="c5b5d-158">Percent of population living below poverty</span></span>
| <span data-ttu-id="c5b5d-159">13</span><span class="sxs-lookup"><span data-stu-id="c5b5d-159">13</span></span> | <span data-ttu-id="c5b5d-160">Cena</span><span class="sxs-lookup"><span data-stu-id="c5b5d-160">Price</span></span> | <span data-ttu-id="c5b5d-161">Cena domovské stránky</span><span class="sxs-lookup"><span data-stu-id="c5b5d-161">Price of the home</span></span>

<span data-ttu-id="c5b5d-162">Ukázka datové sady je uvedena níže:</span><span class="sxs-lookup"><span data-stu-id="c5b5d-162">A sample of the dataset is shown below:</span></span>

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

<span data-ttu-id="c5b5d-163">Data v této ukázce lze modelovat podle třídy, jako je `HousingPriceData` a načtena do [`IDataView`](xref:Microsoft.ML.IDataView) .</span><span class="sxs-lookup"><span data-stu-id="c5b5d-163">The data in this sample can be modeled by a class like `HousingPriceData` and loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

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

## <a name="train-the-model"></a><span data-ttu-id="c5b5d-164">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="c5b5d-164">Train the model</span></span>

<span data-ttu-id="c5b5d-165">Následující ukázka kódu znázorňuje proces školení modelu lineární regrese k předvídání cen za domácnosti.</span><span class="sxs-lookup"><span data-stu-id="c5b5d-165">The code sample below illustrates the process of training a linear regression model to predict house prices.</span></span>

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

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a><span data-ttu-id="c5b5d-166">Vysvětlení modelu s funkcí permutace – důležitost (PFI)</span><span class="sxs-lookup"><span data-stu-id="c5b5d-166">Explain the model with Permutation Feature Importance (PFI)</span></span>

<span data-ttu-id="c5b5d-167">V ML.NET použijte [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) metodu pro příslušnou úlohu.</span><span class="sxs-lookup"><span data-stu-id="c5b5d-167">In ML.NET use the [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) method for your respective task.</span></span>

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance =
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

<span data-ttu-id="c5b5d-168">Výsledkem použití [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) v datové sadě školení je [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) objekt.</span><span class="sxs-lookup"><span data-stu-id="c5b5d-168">The result of using [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) on the training dataset is an [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) of [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) objects.</span></span> <span data-ttu-id="c5b5d-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics)poskytuje souhrnnou statistiku, například střední hodnotu a směrodatnou odchylku pro více pozorování [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) rovnající se počtu permutací určených `permutationCount` parametrem.</span><span class="sxs-lookup"><span data-stu-id="c5b5d-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) provides summary statistics like mean and standard deviation for multiple observations of [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) equal to the number of permutations specified by the `permutationCount` parameter.</span></span>

<span data-ttu-id="c5b5d-170">Důležitost, nebo v tomto případě je absolutní průměrná míra snížení metriky R-čtverce vypočítaná pomocí [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) lze seřadit od nejdůležitějších po nejméně důležité.</span><span class="sxs-lookup"><span data-stu-id="c5b5d-170">The importance, or in this case, the absolute average decrease in R-squared metric calculated by [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) can then be ordered from most important to least important.</span></span>

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

<span data-ttu-id="c5b5d-171">Tisk hodnot pro jednotlivé funkce v nástroji `featureImportanceMetrics` by vygeneroval výstup podobný tomuto:.</span><span class="sxs-lookup"><span data-stu-id="c5b5d-171">Printing the values for each of the features in `featureImportanceMetrics` would generate output similar to that below.</span></span> <span data-ttu-id="c5b5d-172">Mějte na paměti, že byste měli očekávat, že byste měli zobrazit různé výsledky, protože tyto hodnoty se liší v závislosti na datech, která jsou uvedena.</span><span class="sxs-lookup"><span data-stu-id="c5b5d-172">Keep in mind that you should expect to see different results because these values vary based on the data that they are given.</span></span>

| <span data-ttu-id="c5b5d-173">Funkce</span><span class="sxs-lookup"><span data-stu-id="c5b5d-173">Feature</span></span> | <span data-ttu-id="c5b5d-174">Změnit na R-čtvercový</span><span class="sxs-lookup"><span data-stu-id="c5b5d-174">Change to R-Squared</span></span> |
|:--|:--:|
<span data-ttu-id="c5b5d-175">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="c5b5d-175">HighwayAccess</span></span>       |   <span data-ttu-id="c5b5d-176">-0,042731</span><span class="sxs-lookup"><span data-stu-id="c5b5d-176">-0.042731</span></span>
<span data-ttu-id="c5b5d-177">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="c5b5d-177">StudentTeacherRatio</span></span> |   <span data-ttu-id="c5b5d-178">-0,012730</span><span class="sxs-lookup"><span data-stu-id="c5b5d-178">-0.012730</span></span>
<span data-ttu-id="c5b5d-179">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="c5b5d-179">BusinessCenterDistance</span></span>| <span data-ttu-id="c5b5d-180">-0,010491</span><span class="sxs-lookup"><span data-stu-id="c5b5d-180">-0.010491</span></span>
<span data-ttu-id="c5b5d-181">TaxRate</span><span class="sxs-lookup"><span data-stu-id="c5b5d-181">TaxRate</span></span>             |   <span data-ttu-id="c5b5d-182">-0,008545</span><span class="sxs-lookup"><span data-stu-id="c5b5d-182">-0.008545</span></span>
<span data-ttu-id="c5b5d-183">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="c5b5d-183">AverageRoomNumber</span></span>   |   <span data-ttu-id="c5b5d-184">-0,003949</span><span class="sxs-lookup"><span data-stu-id="c5b5d-184">-0.003949</span></span>
<span data-ttu-id="c5b5d-185">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="c5b5d-185">CrimeRate</span></span>           |   <span data-ttu-id="c5b5d-186">-0,003665</span><span class="sxs-lookup"><span data-stu-id="c5b5d-186">-0.003665</span></span>
<span data-ttu-id="c5b5d-187">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="c5b5d-187">CommercialZones</span></span>     |   <span data-ttu-id="c5b5d-188">0,002749</span><span class="sxs-lookup"><span data-stu-id="c5b5d-188">0.002749</span></span>
<span data-ttu-id="c5b5d-189">Domovská stránka</span><span class="sxs-lookup"><span data-stu-id="c5b5d-189">HomeAge</span></span>             |   <span data-ttu-id="c5b5d-190">-0,002426</span><span class="sxs-lookup"><span data-stu-id="c5b5d-190">-0.002426</span></span>
<span data-ttu-id="c5b5d-191">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="c5b5d-191">ResidentialZones</span></span>    |   <span data-ttu-id="c5b5d-192">-0,002319</span><span class="sxs-lookup"><span data-stu-id="c5b5d-192">-0.002319</span></span>
<span data-ttu-id="c5b5d-193">NearWater</span><span class="sxs-lookup"><span data-stu-id="c5b5d-193">NearWater</span></span>           |   <span data-ttu-id="c5b5d-194">0,000203</span><span class="sxs-lookup"><span data-stu-id="c5b5d-194">0.000203</span></span>
<span data-ttu-id="c5b5d-195">PercentPopulationLivingBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="c5b5d-195">PercentPopulationLivingBelowPoverty</span></span>|    <span data-ttu-id="c5b5d-196">0,000031</span><span class="sxs-lookup"><span data-stu-id="c5b5d-196">0.000031</span></span>
<span data-ttu-id="c5b5d-197">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="c5b5d-197">ToxicWasteLevels</span></span>    |   <span data-ttu-id="c5b5d-198">-0,000019</span><span class="sxs-lookup"><span data-stu-id="c5b5d-198">-0.000019</span></span>

<span data-ttu-id="c5b5d-199">Podíváme se na pět nejdůležitějších funkcí této datové sady. cena na pracovišti, kterou tento model předpovídá, je ovlivněná jeho blízkostí vůči dálnicím, poměru učitelů v oblasti škol v oblasti, blízkost k hlavním pracovním centrům, daňové sazbě vlastností a průměrnému počtu místností na domovské stránce.</span><span class="sxs-lookup"><span data-stu-id="c5b5d-199">Taking a look at the five most important features for this dataset, the price of a house predicted by this model is influenced by its proximity to highways, student teacher ratio of schools in the area, proximity to major employment centers, property tax rate and average number of rooms in the home.</span></span>
