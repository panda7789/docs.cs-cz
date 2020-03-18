---
title: Interpretovat ML.NET modely s důležitostí permutačních vlastností
description: Seznamte se s významem funkcí modelů s významem funkce permutace v ML.NET
ms.date: 01/30/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: c1163a41cd2feb0e8785ae9d4c6a71dfbedf3f12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77092613"
---
# <a name="interpret-model-predictions-using-permutation-feature-importance"></a><span data-ttu-id="7f899-103">Interpretovat předpovědi modelu pomocí důležitosti funkce permutace</span><span class="sxs-lookup"><span data-stu-id="7f899-103">Interpret model predictions using Permutation Feature Importance</span></span>

<span data-ttu-id="7f899-104">Pomocí důležitosti funkce permutace (PFI) se dozvíte, jak interpretovat ML.NET předpovědi modelu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="7f899-104">Using Permutation Feature Importance (PFI), learn how to interpret ML.NET machine learning model predictions.</span></span> <span data-ttu-id="7f899-105">PFI poskytuje relativní příspěvek každé funkce k predikci.</span><span class="sxs-lookup"><span data-stu-id="7f899-105">PFI gives the relative contribution each feature makes to a prediction.</span></span>

<span data-ttu-id="7f899-106">Modely strojového učení jsou často považovány za černé skříňky, které berou vstupy a generují výstup.</span><span class="sxs-lookup"><span data-stu-id="7f899-106">Machine learning models are often thought of as black boxes that take inputs and generate an output.</span></span> <span data-ttu-id="7f899-107">Mezilehlé kroky nebo interakce mezi funkcemi, které ovlivňují výstup, jsou zřídka pochopeny.</span><span class="sxs-lookup"><span data-stu-id="7f899-107">The intermediate steps or interactions among the features that influence the output are rarely understood.</span></span> <span data-ttu-id="7f899-108">Vzhledem k tomu, že strojové učení je zavedeno do dalších aspektů každodenního života, jako je zdravotní péče, je nanejvýš důležité pochopit, proč model strojového učení činí rozhodnutí, která činí.</span><span class="sxs-lookup"><span data-stu-id="7f899-108">As machine learning is introduced into more aspects of everyday life such as healthcare, it's of utmost importance to understand why a machine learning model makes the decisions it does.</span></span> <span data-ttu-id="7f899-109">Pokud jsou například diagnózy prováděny modelem strojového učení, potřebují zdravotničtí pracovníci způsob, jak se podívat na faktory, které byly provedeny při vytváření této diagnózy.</span><span class="sxs-lookup"><span data-stu-id="7f899-109">For example, if diagnoses are made by a machine learning model, healthcare professionals need a way to look into the factors that went into making that diagnoses.</span></span> <span data-ttu-id="7f899-110">Poskytnutí správné diagnózy by mohlo mít velký vliv na to, zda má pacient rychlé zotavení nebo ne.</span><span class="sxs-lookup"><span data-stu-id="7f899-110">Providing the right diagnosis could make a great difference on whether a patient has a speedy recovery or not.</span></span> <span data-ttu-id="7f899-111">Proto čím vyšší je úroveň vysvětlitelnosti v modelu, tím větší důvěra zdravotnických pracovníků musí přijmout nebo odmítnout rozhodnutí učiněná modelem.</span><span class="sxs-lookup"><span data-stu-id="7f899-111">Therefore the higher the level of explainability in a model, the greater confidence healthcare professionals have to accept or reject the decisions made by the model.</span></span>

<span data-ttu-id="7f899-112">Různé techniky se používají k vysvětlení modelů, z nichž jeden je PFI.</span><span class="sxs-lookup"><span data-stu-id="7f899-112">Various techniques are used to explain models, one of which is PFI.</span></span> <span data-ttu-id="7f899-113">PFI je technika používaná k vysvětlení klasifikačních a regresních modelů, která je [inspirována Breimanovým *papírem Random Forests* ](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) (viz oddíl 10).</span><span class="sxs-lookup"><span data-stu-id="7f899-113">PFI is a technique used to explain classification and regression models that is inspired by [Breiman's *Random Forests* paper](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) (see section 10).</span></span> <span data-ttu-id="7f899-114">Na vysoké úrovni, způsob, jakým to funguje, je náhodným mícháním dat po jedné funkci pro celou datovou sadu a výpočtem, o kolik se snižuje metrika výkonu zájmu.</span><span class="sxs-lookup"><span data-stu-id="7f899-114">At a high level, the way it works is by randomly shuffling data one feature at a time for the entire dataset and calculating how much the performance metric of interest decreases.</span></span> <span data-ttu-id="7f899-115">Čím větší je změna, tím důležitější je tato funkce.</span><span class="sxs-lookup"><span data-stu-id="7f899-115">The larger the change, the more important that feature is.</span></span>

<span data-ttu-id="7f899-116">Kromě toho zvýrazněním nejdůležitějších funkcí se tvůrci modelů mohou zaměřit na použití podmnožiny smysluplnějších funkcí, které mohou potenciálně snížit hluk a dobu školení.</span><span class="sxs-lookup"><span data-stu-id="7f899-116">Additionally, by highlighting the most important features, model builders can focus on using a subset of more meaningful features which can potentially reduce noise and training time.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="7f899-117">Načtení dat</span><span class="sxs-lookup"><span data-stu-id="7f899-117">Load the data</span></span>

<span data-ttu-id="7f899-118">Funkce v datové sadě používané pro tuto ukázku jsou ve sloupcích 1-12.</span><span class="sxs-lookup"><span data-stu-id="7f899-118">The features in the dataset being used for this sample are in columns 1-12.</span></span> <span data-ttu-id="7f899-119">Cílem je předpovědět `Price`.</span><span class="sxs-lookup"><span data-stu-id="7f899-119">The goal is to predict `Price`.</span></span>

| <span data-ttu-id="7f899-120">Sloupec</span><span class="sxs-lookup"><span data-stu-id="7f899-120">Column</span></span> | <span data-ttu-id="7f899-121">Funkce</span><span class="sxs-lookup"><span data-stu-id="7f899-121">Feature</span></span> | <span data-ttu-id="7f899-122">Popis</span><span class="sxs-lookup"><span data-stu-id="7f899-122">Description</span></span>
| --- | --- | --- |
| <span data-ttu-id="7f899-123">1</span><span class="sxs-lookup"><span data-stu-id="7f899-123">1</span></span> | <span data-ttu-id="7f899-124">Míra kriminality</span><span class="sxs-lookup"><span data-stu-id="7f899-124">CrimeRate</span></span> | <span data-ttu-id="7f899-125">Míra kriminality na obyvatele</span><span class="sxs-lookup"><span data-stu-id="7f899-125">Per capita crime rate</span></span>
| <span data-ttu-id="7f899-126">2</span><span class="sxs-lookup"><span data-stu-id="7f899-126">2</span></span> | <span data-ttu-id="7f899-127">Obytné zóny</span><span class="sxs-lookup"><span data-stu-id="7f899-127">ResidentialZones</span></span> | <span data-ttu-id="7f899-128">Obytné zóny ve městě</span><span class="sxs-lookup"><span data-stu-id="7f899-128">Residential zones in town</span></span>
| <span data-ttu-id="7f899-129">3</span><span class="sxs-lookup"><span data-stu-id="7f899-129">3</span></span> | <span data-ttu-id="7f899-130">Komerční zóny</span><span class="sxs-lookup"><span data-stu-id="7f899-130">CommercialZones</span></span> | <span data-ttu-id="7f899-131">Nebytové zóny ve městě</span><span class="sxs-lookup"><span data-stu-id="7f899-131">Non-residential zones in town</span></span>
| <span data-ttu-id="7f899-132">4</span><span class="sxs-lookup"><span data-stu-id="7f899-132">4</span></span> | <span data-ttu-id="7f899-133">V blízkostiVoda</span><span class="sxs-lookup"><span data-stu-id="7f899-133">NearWater</span></span> | <span data-ttu-id="7f899-134">Blízkost vodního útvaru</span><span class="sxs-lookup"><span data-stu-id="7f899-134">Proximity to body of water</span></span>
| <span data-ttu-id="7f899-135">5</span><span class="sxs-lookup"><span data-stu-id="7f899-135">5</span></span> | <span data-ttu-id="7f899-136">Toxické odpadyÚrovně</span><span class="sxs-lookup"><span data-stu-id="7f899-136">ToxicWasteLevels</span></span> | <span data-ttu-id="7f899-137">Úrovně toxicity (PPM)</span><span class="sxs-lookup"><span data-stu-id="7f899-137">Toxicity levels (PPM)</span></span>
| <span data-ttu-id="7f899-138">6</span><span class="sxs-lookup"><span data-stu-id="7f899-138">6</span></span> | <span data-ttu-id="7f899-139">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="7f899-139">AverageRoomNumber</span></span> | <span data-ttu-id="7f899-140">Průměrný počet pokojů v domě</span><span class="sxs-lookup"><span data-stu-id="7f899-140">Average number of rooms in house</span></span>
| <span data-ttu-id="7f899-141">7</span><span class="sxs-lookup"><span data-stu-id="7f899-141">7</span></span> | <span data-ttu-id="7f899-142">Domácí věk</span><span class="sxs-lookup"><span data-stu-id="7f899-142">HomeAge</span></span> | <span data-ttu-id="7f899-143">Věk domova</span><span class="sxs-lookup"><span data-stu-id="7f899-143">Age of home</span></span>
| <span data-ttu-id="7f899-144">8</span><span class="sxs-lookup"><span data-stu-id="7f899-144">8</span></span> | <span data-ttu-id="7f899-145">Vzdálenost businesscentra</span><span class="sxs-lookup"><span data-stu-id="7f899-145">BusinessCenterDistance</span></span> | <span data-ttu-id="7f899-146">Vzdálenost do nejbližší obchodní čtvrti</span><span class="sxs-lookup"><span data-stu-id="7f899-146">Distance to nearest business district</span></span>
| <span data-ttu-id="7f899-147">9</span><span class="sxs-lookup"><span data-stu-id="7f899-147">9</span></span> | <span data-ttu-id="7f899-148">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="7f899-148">HighwayAccess</span></span> | <span data-ttu-id="7f899-149">Blízkost dálnic</span><span class="sxs-lookup"><span data-stu-id="7f899-149">Proximity to highways</span></span>
| <span data-ttu-id="7f899-150">10</span><span class="sxs-lookup"><span data-stu-id="7f899-150">10</span></span> | <span data-ttu-id="7f899-151">Daňová sazba</span><span class="sxs-lookup"><span data-stu-id="7f899-151">TaxRate</span></span> | <span data-ttu-id="7f899-152">Sazba daně z nemovitých věcí</span><span class="sxs-lookup"><span data-stu-id="7f899-152">Property tax rate</span></span>
| <span data-ttu-id="7f899-153">11</span><span class="sxs-lookup"><span data-stu-id="7f899-153">11</span></span> | <span data-ttu-id="7f899-154">StudentUčitelRatio</span><span class="sxs-lookup"><span data-stu-id="7f899-154">StudentTeacherRatio</span></span> | <span data-ttu-id="7f899-155">Poměr studentů k učitelům</span><span class="sxs-lookup"><span data-stu-id="7f899-155">Ratio of students to teachers</span></span>
| <span data-ttu-id="7f899-156">12</span><span class="sxs-lookup"><span data-stu-id="7f899-156">12</span></span> | <span data-ttu-id="7f899-157">PercentPopulationBelowChudoba</span><span class="sxs-lookup"><span data-stu-id="7f899-157">PercentPopulationBelowPoverty</span></span> | <span data-ttu-id="7f899-158">Procento obyvatel žijících pod hranicí chudoby</span><span class="sxs-lookup"><span data-stu-id="7f899-158">Percent of population living below poverty</span></span>
| <span data-ttu-id="7f899-159">13</span><span class="sxs-lookup"><span data-stu-id="7f899-159">13</span></span> | <span data-ttu-id="7f899-160">Price</span><span class="sxs-lookup"><span data-stu-id="7f899-160">Price</span></span> | <span data-ttu-id="7f899-161">Cena domu</span><span class="sxs-lookup"><span data-stu-id="7f899-161">Price of the home</span></span>

<span data-ttu-id="7f899-162">Ukázka datové sady je uvedena níže:</span><span class="sxs-lookup"><span data-stu-id="7f899-162">A sample of the dataset is shown below:</span></span>

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

<span data-ttu-id="7f899-163">Data v této ukázce mohou `HousingPriceData` být modelována podle třídy jako a načtena do . [`IDataView`](xref:Microsoft.ML.IDataView)</span><span class="sxs-lookup"><span data-stu-id="7f899-163">The data in this sample can be modeled by a class like `HousingPriceData` and loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

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

## <a name="train-the-model"></a><span data-ttu-id="7f899-164">Trénování modelu</span><span class="sxs-lookup"><span data-stu-id="7f899-164">Train the model</span></span>

<span data-ttu-id="7f899-165">Níže uvedený příklad kódu ilustruje proces školení lineárníregresní model předpovědět ceny domů.</span><span class="sxs-lookup"><span data-stu-id="7f899-165">The code sample below illustrates the process of training a linear regression model to predict house prices.</span></span>

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

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a><span data-ttu-id="7f899-166">Vysvětlete model s důležitostí permutačních vlastností (PFI)</span><span class="sxs-lookup"><span data-stu-id="7f899-166">Explain the model with Permutation Feature Importance (PFI)</span></span>

<span data-ttu-id="7f899-167">V ML.NET [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) použijte metodu pro příslušný úkol.</span><span class="sxs-lookup"><span data-stu-id="7f899-167">In ML.NET use the [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) method for your respective task.</span></span>

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance =
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

<span data-ttu-id="7f899-168">Výsledkem použití [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) na trénovací [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) datové sady je objekty.</span><span class="sxs-lookup"><span data-stu-id="7f899-168">The result of using [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) on the training dataset is an [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) of [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) objects.</span></span> <span data-ttu-id="7f899-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics)poskytuje souhrnné statistiky, jako je střední [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) a směrodatná odchylka `permutationCount` pro více pozorování rovnající se počtu permutací určených parametrem.</span><span class="sxs-lookup"><span data-stu-id="7f899-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) provides summary statistics like mean and standard deviation for multiple observations of [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) equal to the number of permutations specified by the `permutationCount` parameter.</span></span>

<span data-ttu-id="7f899-170">Důležitost nebo v tomto případě absolutní průměrný pokles metriky R-kvadrát vypočítaný lze [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) pak seřadit z nejdůležitějšího na nejméně důležitý.</span><span class="sxs-lookup"><span data-stu-id="7f899-170">The importance, or in this case, the absolute average decrease in R-squared metric calculated by [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) can then be ordered from most important to least important.</span></span>

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

<span data-ttu-id="7f899-171">Tisk hodnot pro každou z `featureImportanceMetrics` funkcí v in by generovat výstup podobný níže.</span><span class="sxs-lookup"><span data-stu-id="7f899-171">Printing the values for each of the features in `featureImportanceMetrics` would generate output similar to that below.</span></span> <span data-ttu-id="7f899-172">Mějte na paměti, že byste měli očekávat, že se zobrazí různé výsledky, protože tyto hodnoty se liší v závislosti na datech, která jsou uvedena.</span><span class="sxs-lookup"><span data-stu-id="7f899-172">Keep in mind that you should expect to see different results because these values vary based on the data that they are given.</span></span>

| <span data-ttu-id="7f899-173">Funkce</span><span class="sxs-lookup"><span data-stu-id="7f899-173">Feature</span></span> | <span data-ttu-id="7f899-174">Změnit na R-Squared</span><span class="sxs-lookup"><span data-stu-id="7f899-174">Change to R-Squared</span></span> |
|:--|:--:|
<span data-ttu-id="7f899-175">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="7f899-175">HighwayAccess</span></span>       |   <span data-ttu-id="7f899-176">-0.042731</span><span class="sxs-lookup"><span data-stu-id="7f899-176">-0.042731</span></span>
<span data-ttu-id="7f899-177">StudentUčitelRatio</span><span class="sxs-lookup"><span data-stu-id="7f899-177">StudentTeacherRatio</span></span> |   <span data-ttu-id="7f899-178">-0.012730</span><span class="sxs-lookup"><span data-stu-id="7f899-178">-0.012730</span></span>
<span data-ttu-id="7f899-179">Vzdálenost businesscentra</span><span class="sxs-lookup"><span data-stu-id="7f899-179">BusinessCenterDistance</span></span>| <span data-ttu-id="7f899-180">-0.010491</span><span class="sxs-lookup"><span data-stu-id="7f899-180">-0.010491</span></span>
<span data-ttu-id="7f899-181">Daňová sazba</span><span class="sxs-lookup"><span data-stu-id="7f899-181">TaxRate</span></span>             |   <span data-ttu-id="7f899-182">-0.008545</span><span class="sxs-lookup"><span data-stu-id="7f899-182">-0.008545</span></span>
<span data-ttu-id="7f899-183">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="7f899-183">AverageRoomNumber</span></span>   |   <span data-ttu-id="7f899-184">-0.003949</span><span class="sxs-lookup"><span data-stu-id="7f899-184">-0.003949</span></span>
<span data-ttu-id="7f899-185">Míra kriminality</span><span class="sxs-lookup"><span data-stu-id="7f899-185">CrimeRate</span></span>           |   <span data-ttu-id="7f899-186">-0.003665</span><span class="sxs-lookup"><span data-stu-id="7f899-186">-0.003665</span></span>
<span data-ttu-id="7f899-187">Komerční zóny</span><span class="sxs-lookup"><span data-stu-id="7f899-187">CommercialZones</span></span>     |   <span data-ttu-id="7f899-188">0.002749</span><span class="sxs-lookup"><span data-stu-id="7f899-188">0.002749</span></span>
<span data-ttu-id="7f899-189">Domácí věk</span><span class="sxs-lookup"><span data-stu-id="7f899-189">HomeAge</span></span>             |   <span data-ttu-id="7f899-190">-0.002426</span><span class="sxs-lookup"><span data-stu-id="7f899-190">-0.002426</span></span>
<span data-ttu-id="7f899-191">Obytné zóny</span><span class="sxs-lookup"><span data-stu-id="7f899-191">ResidentialZones</span></span>    |   <span data-ttu-id="7f899-192">-0.002319</span><span class="sxs-lookup"><span data-stu-id="7f899-192">-0.002319</span></span>
<span data-ttu-id="7f899-193">V blízkostiVoda</span><span class="sxs-lookup"><span data-stu-id="7f899-193">NearWater</span></span>           |   <span data-ttu-id="7f899-194">0.000203</span><span class="sxs-lookup"><span data-stu-id="7f899-194">0.000203</span></span>
<span data-ttu-id="7f899-195">PercentPopulationLivingPodchudoba</span><span class="sxs-lookup"><span data-stu-id="7f899-195">PercentPopulationLivingBelowPoverty</span></span>|    <span data-ttu-id="7f899-196">0.000031</span><span class="sxs-lookup"><span data-stu-id="7f899-196">0.000031</span></span>
<span data-ttu-id="7f899-197">Toxické odpadyÚrovně</span><span class="sxs-lookup"><span data-stu-id="7f899-197">ToxicWasteLevels</span></span>    |   <span data-ttu-id="7f899-198">-0.000019</span><span class="sxs-lookup"><span data-stu-id="7f899-198">-0.000019</span></span>

<span data-ttu-id="7f899-199">Podíváme-li se na pět nejdůležitějších prvků pro tuto datovou sadu, cena domu předpovídaná tímto modelem je ovlivněna jeho blízkostí k dálnicím, poměrem studentů škol v této oblasti, blízkostí k hlavním pracovním centrům, sazbou daně z nemovitosti a průměrný počet pokojů v domácnosti.</span><span class="sxs-lookup"><span data-stu-id="7f899-199">Taking a look at the five most important features for this dataset, the price of a house predicted by this model is influenced by its proximity to highways, student teacher ratio of schools in the area, proximity to major employment centers, property tax rate and average number of rooms in the home.</span></span>
