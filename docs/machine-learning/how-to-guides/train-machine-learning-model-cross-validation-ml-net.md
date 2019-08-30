---
title: Výuka modelu strojového učení pomocí vzájemného ověřování
description: Naučte se používat vzájemné ověřování k vytváření robustnějších modelů strojového učení v ML.NET. Křížové ověřování je technikou pro vyhodnocení školení a modelů, které rozdělí data do několika oddílů a navlakuje více algoritmů na těchto oddílech.
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to,title-hack-0625
ms.openlocfilehash: f29103d0cf59cdec10a641b05ce359bf95c01ccd
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169061"
---
# <a name="train-a-machine-learning-model-using-cross-validation"></a><span data-ttu-id="b2d2b-104">Výuka modelu strojového učení pomocí vzájemného ověřování</span><span class="sxs-lookup"><span data-stu-id="b2d2b-104">Train a machine learning model using cross validation</span></span>

<span data-ttu-id="b2d2b-105">Naučte se používat vzájemné ověřování k výuce robustnějších modelů strojového učení v ML.NET.</span><span class="sxs-lookup"><span data-stu-id="b2d2b-105">Learn how to use cross validation to train more robust machine learning models in ML.NET.</span></span> 

<span data-ttu-id="b2d2b-106">Křížové ověřování je technikou pro vyhodnocení školení a modelů, které rozdělí data do několika oddílů a navlakuje více algoritmů na těchto oddílech.</span><span class="sxs-lookup"><span data-stu-id="b2d2b-106">Cross-validation is a training and model evaluation technique that splits the data into several partitions and trains multiple algorithms on these partitions.</span></span> <span data-ttu-id="b2d2b-107">Tento postup zvyšuje odolnost modelu tím, že podrží data z procesu školení.</span><span class="sxs-lookup"><span data-stu-id="b2d2b-107">This technique improves the robustness of the model by holding out data from the training process.</span></span> <span data-ttu-id="b2d2b-108">Kromě zlepšení výkonu u nezpracovaných pozorování v prostředích s omezenými daty může být účinný nástroj pro školení modelů s menší datovou sadou.</span><span class="sxs-lookup"><span data-stu-id="b2d2b-108">In addition to improving performance on unseen observations, in data-constrained environments it can be an effective tool for training models with a smaller dataset.</span></span>

## <a name="the-data-and-data-model"></a><span data-ttu-id="b2d2b-109">Data a datový model</span><span class="sxs-lookup"><span data-stu-id="b2d2b-109">The data and data model</span></span>

<span data-ttu-id="b2d2b-110">Zadaná data ze souboru, který má následující formát:</span><span class="sxs-lookup"><span data-stu-id="b2d2b-110">Given data from a file that has the following format:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
620.00, 148330.32, 140913.81, 136686.39, 146105.37
550.00, 557033.46, 529181.78, 513306.33, 548677.95
1127.00, 479320.99, 455354.94, 441694.30, 472131.18
1120.00, 47504.98, 45129.73, 43775.84, 46792.41
```

<span data-ttu-id="b2d2b-111">Data lze modelovat podle třídy, jako `HousingData` je a načtena [`IDataView`](xref:Microsoft.ML.IDataView)do.</span><span class="sxs-lookup"><span data-stu-id="b2d2b-111">The data can be modeled by a class like `HousingData` and loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

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

## <a name="prepare-the-data"></a><span data-ttu-id="b2d2b-112">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="b2d2b-112">Prepare the data</span></span>

<span data-ttu-id="b2d2b-113">Předem zpracujte data před jejich použitím k sestavení modelu Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="b2d2b-113">Pre-process the data before using it to build the machine learning model.</span></span> <span data-ttu-id="b2d2b-114">V této ukázce `Size` jsou sloupce a `HistoricalPrices` sloučeny do jediného vektoru funkce, který je výstupem do [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) nového sloupce s `Features` názvem pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="b2d2b-114">In this sample, the `Size` and `HistoricalPrices` columns are combined into a single feature vector,  which is output to a new column called `Features` using the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method.</span></span> <span data-ttu-id="b2d2b-115">Kromě získání dat do formátu očekávaného algoritmy ML.NET optimalizuje sloupce následné operace v kanálu, a to použitím operace jednou pro zřetězený sloupec místo každého samostatného sloupce.</span><span class="sxs-lookup"><span data-stu-id="b2d2b-115">In addition to getting the data into the format expected by ML.NET algorithms, concatenating columns optimizes subsequent operations in the pipeline by applying the operation once for the concatenated column instead of each of the separate columns.</span></span> 

<span data-ttu-id="b2d2b-116">Jakmile jsou sloupce zkombinovány do jednoho vektoru, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) je použita `Features` na sloupec pro získání `Size` a `HistoricalPrices` ve stejném rozsahu mezi 0-1.</span><span class="sxs-lookup"><span data-stu-id="b2d2b-116">Once the columns are combined into a single vector, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) is applied to the `Features` column to get `Size` and `HistoricalPrices` in the same range between 0-1.</span></span> 

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

## <a name="train-model-with-cross-validation"></a><span data-ttu-id="b2d2b-117">Výuka modelu pomocí vzájemného ověřování</span><span class="sxs-lookup"><span data-stu-id="b2d2b-117">Train model with cross validation</span></span>

<span data-ttu-id="b2d2b-118">Jakmile jsou data předem zpracovaná, je čas je vyškolit.</span><span class="sxs-lookup"><span data-stu-id="b2d2b-118">Once the data has been pre-processed, it's time to train the model.</span></span> <span data-ttu-id="b2d2b-119">Nejdřív vyberte algoritmus, který nejlépe odpovídá úloze strojového učení, která se má provést.</span><span class="sxs-lookup"><span data-stu-id="b2d2b-119">First, select the algorithm that most closely aligns with the machine learning task to be performed.</span></span> <span data-ttu-id="b2d2b-120">Vzhledem k tomu, že předpokládaná hodnota je numericky souvislá hodnota, je úkol regresní.</span><span class="sxs-lookup"><span data-stu-id="b2d2b-120">Because the predicted value is a numerically continuous value, the task is regression.</span></span> <span data-ttu-id="b2d2b-121">Jedním z regresních algoritmů implementovaných pomocí ml.NET [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) je algoritmus.</span><span class="sxs-lookup"><span data-stu-id="b2d2b-121">One of the regression algorithms implemented by ML.NET is the [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) algorithm.</span></span> <span data-ttu-id="b2d2b-122">Pro výuku modelu pomocí křížového ověřování použijte [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) metodu.</span><span class="sxs-lookup"><span data-stu-id="b2d2b-122">To train the model with cross-validation use the [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) method.</span></span> 

> [!NOTE]
> <span data-ttu-id="b2d2b-123">I když tato ukázka používá model lineární regrese, CrossValidate se vztahuje na všechny ostatní úlohy strojového učení v ML.NET s výjimkou detekce anomálií.</span><span class="sxs-lookup"><span data-stu-id="b2d2b-123">Although this sample uses a linear regression model, CrossValidate is applicable to all other machine learning tasks in ML.NET except Anomaly Detection.</span></span>

```csharp
// Define StochasticDualCoordinateAscent algorithm estimator
IEstimator<ITransformer> sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Apply 5-fold cross validation
var cvResults = mlContext.Regression.CrossValidate(transformedData, sdcaEstimator, numberOfFolds: 5);
```

<span data-ttu-id="b2d2b-124">[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*)provede následující operace:</span><span class="sxs-lookup"><span data-stu-id="b2d2b-124">[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) performs the following operations:</span></span>

1. <span data-ttu-id="b2d2b-125">Rozdělí data do několika oddílů, které se rovnají hodnotě zadané v `numberOfFolds` parametru.</span><span class="sxs-lookup"><span data-stu-id="b2d2b-125">Partitions the data into a number of partitions equal to the value specified in the `numberOfFolds` parameter.</span></span> <span data-ttu-id="b2d2b-126">Výsledkem každého oddílu je [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) objekt.</span><span class="sxs-lookup"><span data-stu-id="b2d2b-126">The result of each partition is a [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) object.</span></span>
1. <span data-ttu-id="b2d2b-127">Model se vystavuje na každém oddílu pomocí zadaného algoritmu strojového učení Estimator v sadě školicích dat.</span><span class="sxs-lookup"><span data-stu-id="b2d2b-127">A model is trained on each of the partitions using the specified machine learning algorithm estimator on the training data set.</span></span>
1. <span data-ttu-id="b2d2b-128">Výkon každého modelu se vyhodnocuje pomocí [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) metody v sadě testovacích dat.</span><span class="sxs-lookup"><span data-stu-id="b2d2b-128">Each model's performance is evaluated using the [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) method on the test data set.</span></span> 
1. <span data-ttu-id="b2d2b-129">Model spolu s jeho metrikami se vrátí pro každý model.</span><span class="sxs-lookup"><span data-stu-id="b2d2b-129">The model along with its metrics are returned for each of the models.</span></span>

<span data-ttu-id="b2d2b-130">Výsledek uložený v `cvResults` je [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) kolekce objektů.</span><span class="sxs-lookup"><span data-stu-id="b2d2b-130">The result stored in `cvResults` is a collection of [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) objects.</span></span> <span data-ttu-id="b2d2b-131">Tento objekt zahrnuje trained model a také metriky, které jsou přístupné ve [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) formě vlastností a. [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics)</span><span class="sxs-lookup"><span data-stu-id="b2d2b-131">This object includes the trained model as well as metrics which are both accessible form the [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) and [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics) properties respectively.</span></span> <span data-ttu-id="b2d2b-132">V této ukázce `Model` je vlastnost typu [`ITransformer`](xref:Microsoft.ML.ITransformer) a `Metrics` vlastnost je typu [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics).</span><span class="sxs-lookup"><span data-stu-id="b2d2b-132">In this sample, the `Model` property is of type [`ITransformer`](xref:Microsoft.ML.ITransformer) and the `Metrics` property is of type [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics).</span></span> 

## <a name="evaluate-the-model"></a><span data-ttu-id="b2d2b-133">Vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="b2d2b-133">Evaluate the model</span></span>

<span data-ttu-id="b2d2b-134">Metriky pro různé vyškolené modely jsou dostupné prostřednictvím `Metrics` vlastnosti jednotlivého [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) objektu.</span><span class="sxs-lookup"><span data-stu-id="b2d2b-134">Metrics for the different trained models can be accessed through the `Metrics` property of the individual [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) object.</span></span> <span data-ttu-id="b2d2b-135">V tomto případě je k dispozici [metrika R-kvadrát](https://en.wikipedia.org/wiki/Coefficient_of_determination) , která je uložena v `rSquared`proměnné.</span><span class="sxs-lookup"><span data-stu-id="b2d2b-135">In this case, the [R-Squared metric](https://en.wikipedia.org/wiki/Coefficient_of_determination) is accessed and stored in the variable `rSquared`.</span></span> 

```csharp
IEnumerable<double> rSquared = 
    cvResults
        .Select(fold => fold.Metrics.RSquared);
```

<span data-ttu-id="b2d2b-136">Pokud provedete kontrolu obsahu `rSquared` proměnné, výstup by měl mít pět hodnot od 0-1, kde blíže k 1 znamená nejlepší.</span><span class="sxs-lookup"><span data-stu-id="b2d2b-136">If you inspect the contents of the `rSquared` variable, the output should be five values ranging from 0-1 where closer to 1 means best.</span></span> <span data-ttu-id="b2d2b-137">Pomocí metrik, jako je R-kvadrát, vyberte modely od nejvyšších po nejhorší výkon.</span><span class="sxs-lookup"><span data-stu-id="b2d2b-137">Using metrics like R-Squared, select the models from best to worst performing.</span></span> <span data-ttu-id="b2d2b-138">Pak vyberte horní model, který bude předpovědi, nebo proveďte další operace s.</span><span class="sxs-lookup"><span data-stu-id="b2d2b-138">Then, select the top model to make predictions or perform additional operations with.</span></span>

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
