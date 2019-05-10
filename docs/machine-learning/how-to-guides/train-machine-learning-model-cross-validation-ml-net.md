---
title: Natrénování a vyhodnocení modelu strojového učení pomocí křížového ověření
description: Zjistěte, jak trénovat a vyhodnocovat u nich model strojového učení pomocí křížového ověření
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: a15dfbfcd563cf9df9c25779a5854a9f556523d1
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65066163"
---
# <a name="train-and-evaluate-a-machine-learning-model-using-cross-validation"></a><span data-ttu-id="785d6-103">Natrénování a vyhodnocení modelu strojového učení pomocí křížového ověření</span><span class="sxs-lookup"><span data-stu-id="785d6-103">Train and evaluate a machine learning model using cross validation</span></span>

<span data-ttu-id="785d6-104">Zjistěte, jak můžete vytvářet robustnější modely strojového učení v ML.NET křížového ověření.</span><span class="sxs-lookup"><span data-stu-id="785d6-104">Learn how to use cross validation to build more robust machine learning models in ML.NET.</span></span> 

<span data-ttu-id="785d6-105">Křížové ověření je školení a model hodnocení technika, která rozdělí data do několika oddílů a trénovat více algoritmy v těchto oddílech.</span><span class="sxs-lookup"><span data-stu-id="785d6-105">Cross-validation is a training and model evaluation technique that splits the data into several partitions and trains multiple algorithms on these partitions.</span></span> <span data-ttu-id="785d6-106">Tento postup zlepšuje odolnost modelu tím, že se data z procesu trénování.</span><span class="sxs-lookup"><span data-stu-id="785d6-106">This technique improves the robustness of the model by holding out data from the training process.</span></span> <span data-ttu-id="785d6-107">Kromě vylepšení výkonu na neviditelný pozorování, v prostředí omezené dat může být efektivní nástroj pro trénování modelů s menší datové sady.</span><span class="sxs-lookup"><span data-stu-id="785d6-107">In addition to improving performance on unseen observations, in data-constrained environments it can be an effective tool for training models with a smaller dataset.</span></span>

## <a name="the-data-and-data-model"></a><span data-ttu-id="785d6-108">Data a datový model</span><span class="sxs-lookup"><span data-stu-id="785d6-108">The data and data model</span></span>

<span data-ttu-id="785d6-109">Zadaný data ze souboru, který má následující formát:</span><span class="sxs-lookup"><span data-stu-id="785d6-109">Given data from a file that has the following format:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
620.00, 148330.32, 140913.81, 136686.39, 146105.37
550.00, 557033.46, 529181.78, 513306.33, 548677.95
1127.00, 479320.99, 455354.94, 441694.30, 472131.18
1120.00, 47504.98, 45129.73, 43775.84, 46792.41
```

<span data-ttu-id="785d6-110">Data můžete modelovány pomocí třídy jako `HousingData`:</span><span class="sxs-lookup"><span data-stu-id="785d6-110">The data can be modeled by a class like `HousingData`:</span></span>

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

<span data-ttu-id="785d6-111">Načtení dat do do [ `IDataView` ](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="785d6-111">Load the data in into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="785d6-112">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="785d6-112">Prepare the data</span></span>

<span data-ttu-id="785d6-113">Předběžně zpracovat data před sestavením modelu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="785d6-113">Pre-process the data before using it to build the machine learning model.</span></span> <span data-ttu-id="785d6-114">V této ukázce `Size` a `HistoricalPrices` sloupce jsou sloučeny do jednoho funkce vektor, který je použita pro nový sloupec s názvem `Features` pomocí [ `Concatenate` ](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) metody.</span><span class="sxs-lookup"><span data-stu-id="785d6-114">In this sample, the `Size` and `HistoricalPrices` columns are combined into a single feature vector,  which is output to a new column called `Features` using the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method.</span></span> <span data-ttu-id="785d6-115">Kromě získávání dat do formátu očekávaném ML.NET algoritmy, zřetězení sloupce optimalizuje následné operace v kanálu použitím operace pro zřetězených sloupců místo jednotlivých samostatné sloupce.</span><span class="sxs-lookup"><span data-stu-id="785d6-115">In addition to getting the data into the format expected by ML.NET algorithms, concatenating columns optimizes subsequent operations in the pipeline by applying the operation once for the concatenated column instead of each of the separate columns.</span></span> 

<span data-ttu-id="785d6-116">Jakmile sloupce, které jsou sloučeny do jednoho vektoru [ `NormalizeMinMax` ](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) platí pro `Features` sloupce, chcete-li získat `Size` a `HistoricalPrices` ve stejném rozsahu od 0 – 1.</span><span class="sxs-lookup"><span data-stu-id="785d6-116">Once the columns are combined into a single vector, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) is applied to the `Features` column to get `Size` and `HistoricalPrices` in the same range between 0-1.</span></span> 

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

## <a name="train-model-with-cross-validation"></a><span data-ttu-id="785d6-117">Trénování modelu s křížové ověření</span><span class="sxs-lookup"><span data-stu-id="785d6-117">Train model with cross validation</span></span>

<span data-ttu-id="785d6-118">Jakmile byl předem zpracovaných dat, je čas pro trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="785d6-118">Once the data has been pre-processed, it's time to train the model.</span></span> <span data-ttu-id="785d6-119">Nejdřív vyberte algoritmus, který nejlépe odpovídá strojového učení úloh, která se má provést.</span><span class="sxs-lookup"><span data-stu-id="785d6-119">First, select the algorithm that most closely aligns with the machine learning task to be performed.</span></span> <span data-ttu-id="785d6-120">Protože předpovězené hodnoty je číselně průběžné hodnota, je úloha regrese.</span><span class="sxs-lookup"><span data-stu-id="785d6-120">Because the predicted value is a numerically continuous value, the task is regression.</span></span> <span data-ttu-id="785d6-121">Jeden z algoritmů regrese implementované ML.NET je [ `StochasticDualCoordinateAscentCoordinator` ](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) algoritmus.</span><span class="sxs-lookup"><span data-stu-id="785d6-121">One of the regression algorithms implemented by ML.NET is the [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) algorithm.</span></span> <span data-ttu-id="785d6-122">Pro trénování modelu s použitím křížového ověření [ `CrossValidate` ](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) metody.</span><span class="sxs-lookup"><span data-stu-id="785d6-122">To train the model with cross-validation use the [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) method.</span></span> 

> [!NOTE]
> <span data-ttu-id="785d6-123">I když tato ukázka používá model lineární regrese, CrossValidate se vztahuje na všechny ostatní strojového učení úkoly v ML.NET s výjimkou detekce anomálií.</span><span class="sxs-lookup"><span data-stu-id="785d6-123">Although this sample uses a linear regression model, CrossValidate is applicable to all other machine learning tasks in ML.NET except Anomaly Detection.</span></span>

```csharp
// Define StochasticDualCoordinateAscent algorithm estimator
IEstimator<ITransformer> sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Apply 5-fold cross validation
var cvResults = mlContext.Regression.CrossValidate(transformedData, sdcaEstimator, numberOfFolds: 5);
```

<span data-ttu-id="785d6-124">[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) provádí následující operace:</span><span class="sxs-lookup"><span data-stu-id="785d6-124">[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) performs the following operations:</span></span>

1. <span data-ttu-id="785d6-125">Rozděluje data do několika oddílů, které se rovná hodnotě zadané v `numberOfFolds` parametru.</span><span class="sxs-lookup"><span data-stu-id="785d6-125">Partitions the data into a number of partitions equal to the value specified in the `numberOfFolds` parameter.</span></span> <span data-ttu-id="785d6-126">Výsledek každý oddíl je [ `TrainTestData` ](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) objektu.</span><span class="sxs-lookup"><span data-stu-id="785d6-126">The result of each partition is a [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) object.</span></span>
1. <span data-ttu-id="785d6-127">Model se trénuje na všech oddílů pomocí zadaného strojového učení algoritmu odhaduje na trénovací datové sady.</span><span class="sxs-lookup"><span data-stu-id="785d6-127">A model is trained on each of the partitions using the specified machine learning algorithm estimator on the training data set.</span></span>
1. <span data-ttu-id="785d6-128">Každý model výkonu je vyhodnocen pomocí [ `Evaluate` ](xref:Microsoft.ML.RegressionCatalog.Evaluate*) metodu na testovací datové sady.</span><span class="sxs-lookup"><span data-stu-id="785d6-128">Each model's performance is evaluated using the [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) method on the test data set.</span></span> 
1. <span data-ttu-id="785d6-129">Model spolu s jeho metriky se vrátí pro každou modelů.</span><span class="sxs-lookup"><span data-stu-id="785d6-129">The model along with its metrics are returned for each of the models.</span></span>

<span data-ttu-id="785d6-130">Výsledek je uložen v `cvResults` je kolekce [ `CrossValidationResult` ](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult`1) objekty.</span><span class="sxs-lookup"><span data-stu-id="785d6-130">The result stored in `cvResults` is a collection of [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult`1) objects.</span></span> <span data-ttu-id="785d6-131">Tento objekt obsahuje trénovaného modelu, stejně jako metriky, které jsou obě přístupné formuláře [ `Model` ](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult`1.Model) a [ `Metrics` ](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult`1.Metrics) vlastnosti v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="785d6-131">This object includes the trained model as well as metrics which are both accessible form the [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult`1.Model) and [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult`1.Metrics) properties respectively.</span></span> <span data-ttu-id="785d6-132">V této ukázce `Model` vlastnost je typu [ `ITransformer` ](xref:Microsoft.ML.ITransformer) a `Metrics` vlastnost je typu [ `RegressionMetrics` ](xref:Microsoft.ML.Data.RegressionMetrics).</span><span class="sxs-lookup"><span data-stu-id="785d6-132">In this sample, the `Model` property is of type [`ITransformer`](xref:Microsoft.ML.ITransformer) and the `Metrics` property is of type [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics).</span></span> 

## <a name="extract-metrics"></a><span data-ttu-id="785d6-133">Extrahovat metriky</span><span class="sxs-lookup"><span data-stu-id="785d6-133">Extract metrics</span></span>

<span data-ttu-id="785d6-134">Metriky pro různé trénované modely přístupné prostřednictvím `Metrics` vlastnost jednotlivých [ `CrossValidationResult` ](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) objektu.</span><span class="sxs-lookup"><span data-stu-id="785d6-134">Metrics for the different trained models can be accessed through the `Metrics` property of the individual [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) object.</span></span> <span data-ttu-id="785d6-135">V takovém případě [spolehlivosti R metrika](https://en.wikipedia.org/wiki/Coefficient_of_determination) se často a ukládají v proměnné `rSquared`.</span><span class="sxs-lookup"><span data-stu-id="785d6-135">In this case, the [R-Squared metric](https://en.wikipedia.org/wiki/Coefficient_of_determination) is accessed and stored in the variable `rSquared`.</span></span> 

```csharp
IEnumerable<double> rSquared = 
    cvResults
        .Select(fold => fold.Metrics.RSquared);
```

<span data-ttu-id="785d6-136">Je-li si prohlédnout obsah `rSquared` proměnné, výstup by měl být pět hodnoty v rozsahu od 0-1, kde blíže 1 znamená, že nejlepší.</span><span class="sxs-lookup"><span data-stu-id="785d6-136">If you inspect the contents of the `rSquared` variable, the output should be five values ranging from 0-1 where closer to 1 means best.</span></span>

## <a name="select-the-best-performing-model"></a><span data-ttu-id="785d6-137">Výběr nejvýkonnějšího modelu</span><span class="sxs-lookup"><span data-stu-id="785d6-137">Select the best performing model</span></span>

<span data-ttu-id="785d6-138">Použití metrik, jako je spolehlivosti R, vyberte modelů z nejlepších nejhorší provádění.</span><span class="sxs-lookup"><span data-stu-id="785d6-138">Using metrics like R-Squared, select the models from best to worst performing.</span></span> <span data-ttu-id="785d6-139">Vyberte hlavní model k predikci nebo provádět další operace s.</span><span class="sxs-lookup"><span data-stu-id="785d6-139">Then, select the top model to make predictions or perform additional operations with.</span></span>

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
