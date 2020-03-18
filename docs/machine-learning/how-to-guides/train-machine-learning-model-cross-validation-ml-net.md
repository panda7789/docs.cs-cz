---
title: Trénování modelu strojového učení pomocí křížového ověřování
description: Naučte se používat křížové ověřování k vytváření robustnějších modelů strojového učení v ML.NET. Křížové ověřování je technika trénování a vyhodnocení modelu, která rozděluje data do několika oddílů a trénuje více algoritmů na těchto oddílech.
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to,title-hack-0625
ms.openlocfilehash: 87eae789478752423f3e682d4db6cead0391aa6e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73976927"
---
# <a name="train-a-machine-learning-model-using-cross-validation"></a><span data-ttu-id="ff844-104">Trénování modelu strojového učení pomocí křížového ověřování</span><span class="sxs-lookup"><span data-stu-id="ff844-104">Train a machine learning model using cross validation</span></span>

<span data-ttu-id="ff844-105">Naučte se používat křížové ověřování k trénování robustnějších modelů strojového učení v ML.NET.</span><span class="sxs-lookup"><span data-stu-id="ff844-105">Learn how to use cross validation to train more robust machine learning models in ML.NET.</span></span>

<span data-ttu-id="ff844-106">Křížové ověřování je technika trénování a vyhodnocení modelu, která rozděluje data do několika oddílů a trénuje více algoritmů na těchto oddílech.</span><span class="sxs-lookup"><span data-stu-id="ff844-106">Cross-validation is a training and model evaluation technique that splits the data into several partitions and trains multiple algorithms on these partitions.</span></span> <span data-ttu-id="ff844-107">Tato technika zlepšuje robustnost modelu tím, že podrží data z tréninkového procesu.</span><span class="sxs-lookup"><span data-stu-id="ff844-107">This technique improves the robustness of the model by holding out data from the training process.</span></span> <span data-ttu-id="ff844-108">Kromě zlepšení výkonu na neviditelné pozorování, v prostředí s omezenými daty může být účinným nástrojem pro trénování modelů s menší datovou sadou.</span><span class="sxs-lookup"><span data-stu-id="ff844-108">In addition to improving performance on unseen observations, in data-constrained environments it can be an effective tool for training models with a smaller dataset.</span></span>

## <a name="the-data-and-data-model"></a><span data-ttu-id="ff844-109">Datový a datový model</span><span class="sxs-lookup"><span data-stu-id="ff844-109">The data and data model</span></span>

<span data-ttu-id="ff844-110">Uvedená data ze souboru, který má následující formát:</span><span class="sxs-lookup"><span data-stu-id="ff844-110">Given data from a file that has the following format:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
620.00, 148330.32, 140913.81, 136686.39, 146105.37
550.00, 557033.46, 529181.78, 513306.33, 548677.95
1127.00, 479320.99, 455354.94, 441694.30, 472131.18
1120.00, 47504.98, 45129.73, 43775.84, 46792.41
```

<span data-ttu-id="ff844-111">Data mohou být modelována `HousingData` podle třídy, jako je, a načtena do . [`IDataView`](xref:Microsoft.ML.IDataView)</span><span class="sxs-lookup"><span data-stu-id="ff844-111">The data can be modeled by a class like `HousingData` and loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

```csharp
public class HousingData
{
    [LoadColumn(0)]
    public float Size { get; set; }

    [LoadColumn(1, 3)]
    [VectorType(3)]
    public float[] HistoricalPrices { get; set; }

    [LoadColumn(4)]
    [ColumnName("Label")]
    public float CurrentPrice { get; set; }
}
```

## <a name="prepare-the-data"></a><span data-ttu-id="ff844-112">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="ff844-112">Prepare the data</span></span>

<span data-ttu-id="ff844-113">Před zpracováním dat před jejich použitím k vytvoření modelu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="ff844-113">Pre-process the data before using it to build the machine learning model.</span></span> <span data-ttu-id="ff844-114">V této ukázce jsou sloupce `Size` a `HistoricalPrices` sloučeny do jednoho vektoru `Features` prvku, který je výstupem do nového sloupce nazývaného [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="ff844-114">In this sample, the `Size` and `HistoricalPrices` columns are combined into a single feature vector,  which is output to a new column called `Features` using the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method.</span></span> <span data-ttu-id="ff844-115">Kromě získávání dat do formátu očekávaného ML.NET algoritmy, zřetězení sloupců optimalizuje následné operace v kanálu použitím operace jednou pro zřetězený sloupec namísto každého ze samostatných sloupců.</span><span class="sxs-lookup"><span data-stu-id="ff844-115">In addition to getting the data into the format expected by ML.NET algorithms, concatenating columns optimizes subsequent operations in the pipeline by applying the operation once for the concatenated column instead of each of the separate columns.</span></span>

<span data-ttu-id="ff844-116">Jakmile jsou sloupce sloučeny do [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) jednoho vektoru, je `Size` `HistoricalPrices` použita na `Features` sloupec získat a ve stejném rozsahu mezi 0-1.</span><span class="sxs-lookup"><span data-stu-id="ff844-116">Once the columns are combined into a single vector, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) is applied to the `Features` column to get `Size` and `HistoricalPrices` in the same range between 0-1.</span></span>

```csharp
// Define data prep estimator
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", new string[] { "Size", "HistoricalPrices" })
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// Create data prep transformer
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(data);

// Transform data
IDataView transformedData = dataPrepTransformer.Transform(data);
```

## <a name="train-model-with-cross-validation"></a><span data-ttu-id="ff844-117">Model vlaku s křížovou validací</span><span class="sxs-lookup"><span data-stu-id="ff844-117">Train model with cross validation</span></span>

<span data-ttu-id="ff844-118">Jakmile jsou data předem zpracována, je čas trénovat model.</span><span class="sxs-lookup"><span data-stu-id="ff844-118">Once the data has been pre-processed, it's time to train the model.</span></span> <span data-ttu-id="ff844-119">Nejprve vyberte algoritmus, který je nejvíce v souladu s úlohou strojového učení, která má být provedena.</span><span class="sxs-lookup"><span data-stu-id="ff844-119">First, select the algorithm that most closely aligns with the machine learning task to be performed.</span></span> <span data-ttu-id="ff844-120">Vzhledem k tomu, že předpovídaná hodnota je číselně souvislá hodnota, úkol je regrese.</span><span class="sxs-lookup"><span data-stu-id="ff844-120">Because the predicted value is a numerically continuous value, the task is regression.</span></span> <span data-ttu-id="ff844-121">Jedním z regresních algoritmů implementovaných [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) ML.NET je algoritmus.</span><span class="sxs-lookup"><span data-stu-id="ff844-121">One of the regression algorithms implemented by ML.NET is the [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) algorithm.</span></span> <span data-ttu-id="ff844-122">Chcete-li trénovat model s [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) křížovým ověřením, použijte metodu.</span><span class="sxs-lookup"><span data-stu-id="ff844-122">To train the model with cross-validation use the [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) method.</span></span>

> [!NOTE]
> <span data-ttu-id="ff844-123">Přestože tato ukázka používá lineární regresní model, CrossValidate se vztahuje na všechny ostatní úlohy strojového učení v ML.NET s výjimkou detekce anomálií.</span><span class="sxs-lookup"><span data-stu-id="ff844-123">Although this sample uses a linear regression model, CrossValidate is applicable to all other machine learning tasks in ML.NET except Anomaly Detection.</span></span>

```csharp
// Define StochasticDualCoordinateAscent algorithm estimator
IEstimator<ITransformer> sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Apply 5-fold cross validation
var cvResults = mlContext.Regression.CrossValidate(transformedData, sdcaEstimator, numberOfFolds: 5);
```

<span data-ttu-id="ff844-124">[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*)provádí následující operace:</span><span class="sxs-lookup"><span data-stu-id="ff844-124">[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) performs the following operations:</span></span>

1. <span data-ttu-id="ff844-125">Rozdělí data do počtu oddílů rovnající se hodnotě zadané v parametru. `numberOfFolds`</span><span class="sxs-lookup"><span data-stu-id="ff844-125">Partitions the data into a number of partitions equal to the value specified in the `numberOfFolds` parameter.</span></span> <span data-ttu-id="ff844-126">Výsledkem každého oddílu [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) je objekt.</span><span class="sxs-lookup"><span data-stu-id="ff844-126">The result of each partition is a [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) object.</span></span>
1. <span data-ttu-id="ff844-127">Model je trénovaný na každém z oddílů pomocí zadaný odhad algoritmu strojového učení na trénovací datové sady.</span><span class="sxs-lookup"><span data-stu-id="ff844-127">A model is trained on each of the partitions using the specified machine learning algorithm estimator on the training data set.</span></span>
1. <span data-ttu-id="ff844-128">Výkon každého modelu je vyhodnocen pomocí metody na [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) testovací datové sadě.</span><span class="sxs-lookup"><span data-stu-id="ff844-128">Each model's performance is evaluated using the [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) method on the test data set.</span></span>
1. <span data-ttu-id="ff844-129">Model spolu s jeho metriky jsou vráceny pro každý z modelů.</span><span class="sxs-lookup"><span data-stu-id="ff844-129">The model along with its metrics are returned for each of the models.</span></span>

<span data-ttu-id="ff844-130">Výsledek uložený `cvResults` v je [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="ff844-130">The result stored in `cvResults` is a collection of [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) objects.</span></span> <span data-ttu-id="ff844-131">Tento objekt zahrnuje trénovaný model, stejně [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) jako [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics) metriky, které jsou přístupné z a vlastnosti v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ff844-131">This object includes the trained model as well as metrics which are both accessible form the [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) and [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics) properties respectively.</span></span> <span data-ttu-id="ff844-132">V této `Model` ukázce [`ITransformer`](xref:Microsoft.ML.ITransformer) je `Metrics` vlastnost typu [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics)a vlastnost je typu .</span><span class="sxs-lookup"><span data-stu-id="ff844-132">In this sample, the `Model` property is of type [`ITransformer`](xref:Microsoft.ML.ITransformer) and the `Metrics` property is of type [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics).</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="ff844-133">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="ff844-133">Evaluate the model</span></span>

<span data-ttu-id="ff844-134">Metriky pro různé trénované modely `Metrics` lze přistupovat prostřednictvím vlastnosti jednotlivého [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) objektu.</span><span class="sxs-lookup"><span data-stu-id="ff844-134">Metrics for the different trained models can be accessed through the `Metrics` property of the individual [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) object.</span></span> <span data-ttu-id="ff844-135">V tomto případě [r-kvadrát metrika](https://en.wikipedia.org/wiki/Coefficient_of_determination) je `rSquared`přístupná a uloženy v proměnné .</span><span class="sxs-lookup"><span data-stu-id="ff844-135">In this case, the [R-Squared metric](https://en.wikipedia.org/wiki/Coefficient_of_determination) is accessed and stored in the variable `rSquared`.</span></span>

```csharp
IEnumerable<double> rSquared =
    cvResults
        .Select(fold => fold.Metrics.RSquared);
```

<span data-ttu-id="ff844-136">Pokud zkontrolujete obsah `rSquared` proměnné, výstup by měl být pět hodnot v rozsahu od 0-1, kde blíže k 1 znamená nejlepší.</span><span class="sxs-lookup"><span data-stu-id="ff844-136">If you inspect the contents of the `rSquared` variable, the output should be five values ranging from 0-1 where closer to 1 means best.</span></span> <span data-ttu-id="ff844-137">Pomocí metrik, jako je R-Squared, vyberte modely od nejlepšího po nejhorší.</span><span class="sxs-lookup"><span data-stu-id="ff844-137">Using metrics like R-Squared, select the models from best to worst performing.</span></span> <span data-ttu-id="ff844-138">Potom vyberte nejvyšší model, chcete-li předpovědět nebo provést další operace s.</span><span class="sxs-lookup"><span data-stu-id="ff844-138">Then, select the top model to make predictions or perform additional operations with.</span></span>

```csharp
// Select all models
ITransformer[] models =
    cvResults
        .OrderByDescending(fold => fold.Metrics.RSquared)
        .Select(fold => fold.Model)
        .ToArray();

// Get Top Model
ITransformer topModel = models[0];
```
