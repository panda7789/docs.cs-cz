---
title: Předvídací předpovědi pomocí trénovaného modelu
description: Naučte se dělat předpovědi pomocí trénovaného modelu
ms.date: 09/18/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 182350cc5143155133385c6fd77986b271f6db91
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73977036"
---
# <a name="make-predictions-with-a-trained-model"></a><span data-ttu-id="7db94-103">Předvídací předpovědi pomocí trénovaného modelu</span><span class="sxs-lookup"><span data-stu-id="7db94-103">Make predictions with a trained model</span></span>

<span data-ttu-id="7db94-104">Naučte se používat trénovaný model k předpovědím</span><span class="sxs-lookup"><span data-stu-id="7db94-104">Learn how to use a trained model to make predictions</span></span>

## <a name="create-data-models"></a><span data-ttu-id="7db94-105">Vytváření datových modelů</span><span class="sxs-lookup"><span data-stu-id="7db94-105">Create data models</span></span>

### <a name="input-data"></a><span data-ttu-id="7db94-106">Vstupní data</span><span class="sxs-lookup"><span data-stu-id="7db94-106">Input data</span></span>

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

### <a name="output-data"></a><span data-ttu-id="7db94-107">Výstupní data</span><span class="sxs-lookup"><span data-stu-id="7db94-107">Output data</span></span>

<span data-ttu-id="7db94-108">Stejně `Features` `Label` jako názvy a vstupních sloupců má ML.NET výchozí názvy pro sloupce předpovídané hodnoty vytvořené modelem.</span><span class="sxs-lookup"><span data-stu-id="7db94-108">Like the `Features` and `Label` input column names, ML.NET has default names for the predicted value columns produced by a model.</span></span> <span data-ttu-id="7db94-109">V závislosti na úkolu se název může lišit.</span><span class="sxs-lookup"><span data-stu-id="7db94-109">Depending on the task the name may differ.</span></span>

<span data-ttu-id="7db94-110">Vzhledem k tomu, že algoritmus použitý v tomto vzorku je lineární `Score` regresní [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) algoritmus, výchozí název výstupního sloupce je definován atributem vlastnosti. `PredictedPrice`</span><span class="sxs-lookup"><span data-stu-id="7db94-110">Because the algorithm used in this sample is a linear regression algorithm, the default name of the output column is `Score` which is defined by the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute on the `PredictedPrice` property.</span></span>

```csharp
class HousingPrediction
{
    [ColumnName("Score")]
    public float PredictedPrice { get; set; }
}
```

## <a name="set-up-a-prediction-pipeline"></a><span data-ttu-id="7db94-111">Nastavení kanálu předpovědi</span><span class="sxs-lookup"><span data-stu-id="7db94-111">Set up a prediction pipeline</span></span>

<span data-ttu-id="7db94-112">Ať už vytváření jedné nebo dávky předpověď, předpověď kanálu musí být načtendo aplikace.</span><span class="sxs-lookup"><span data-stu-id="7db94-112">Whether making a single or batch prediction, the prediction pipeline needs to be loaded into the application.</span></span> <span data-ttu-id="7db94-113">Tento kanál obsahuje transformace před zpracováním dat i trénovaný model.</span><span class="sxs-lookup"><span data-stu-id="7db94-113">This pipeline contains both the data pre-processing transformations as well as the trained model.</span></span> <span data-ttu-id="7db94-114">Fragment kódu pod načte kanál předpovědi ze `model.zip`souboru s názvem .</span><span class="sxs-lookup"><span data-stu-id="7db94-114">The code snippet below loads the prediction pipeline from a file named `model.zip`.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Load Trained Model
DataViewSchema predictionPipelineSchema;
ITransformer predictionPipeline = mlContext.Model.Load("model.zip", out predictionPipelineSchema);
```

## <a name="single-prediction"></a><span data-ttu-id="7db94-115">Jednorázová předpověď</span><span class="sxs-lookup"><span data-stu-id="7db94-115">Single prediction</span></span>

<span data-ttu-id="7db94-116">Chcete-li vytvořit jednu [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) předpověď, vytvořte pomocí kanálu načtené předpovědi.</span><span class="sxs-lookup"><span data-stu-id="7db94-116">To make a single prediction, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) using the loaded prediction pipeline.</span></span>

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

<span data-ttu-id="7db94-117">Potom použijte [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) metodu a předat vstupní data jako parametr.</span><span class="sxs-lookup"><span data-stu-id="7db94-117">Then, use the [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) method and pass in your input data as a parameter.</span></span> <span data-ttu-id="7db94-118">Všimněte si, že pomocí [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) metody nevyžaduje [`IDataView`](xref:Microsoft.ML.IDataView)vstup být ).</span><span class="sxs-lookup"><span data-stu-id="7db94-118">Notice that using the [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) method does not require the input to be an [`IDataView`](xref:Microsoft.ML.IDataView)).</span></span> <span data-ttu-id="7db94-119">Důvodem je, že pohodlně internalizuje manipulaci s typem vstupních dat, takže můžete předat objekt vstupního datového typu.</span><span class="sxs-lookup"><span data-stu-id="7db94-119">This is because it conveniently internalizes the input data type manipulation so you can pass in an object of the input data type.</span></span> <span data-ttu-id="7db94-120">Navíc vzhledem `CurrentPrice` k tomu, že je cíl nebo popisek, který se pokoušíte předpovědět pomocí nových dat, předpokládá se, že pro něj v tuto chvíli neexistuje žádná hodnota.</span><span class="sxs-lookup"><span data-stu-id="7db94-120">Additionally, since `CurrentPrice` is the target or label you're trying to predict using new data, it's assumed there is no value for it at the moment.</span></span>

```csharp
// Input Data
HousingData inputData = new HousingData
{
    Size = 900f,
    HistoricalPrices = new float[] { 155000f, 190000f, 220000f }
};

// Get Prediction
HousingPrediction prediction = predictionEngine.Predict(inputData);
```

<span data-ttu-id="7db94-121">Pokud máte `Score` přístup k `prediction` vlastnostobjektu, měli byste `150079`získat hodnotu podobnou .</span><span class="sxs-lookup"><span data-stu-id="7db94-121">If you access the `Score` property of the `prediction` object, you should get a value similar to `150079`.</span></span>

## <a name="multiple-predictions"></a><span data-ttu-id="7db94-122">Více předpovědí</span><span class="sxs-lookup"><span data-stu-id="7db94-122">Multiple predictions</span></span>

<span data-ttu-id="7db94-123">Vzhledem k následujícím datům [`IDataView`](xref:Microsoft.ML.IDataView)je načtěte do .</span><span class="sxs-lookup"><span data-stu-id="7db94-123">Given the following data, load it into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="7db94-124">V tomto případě [`IDataView`](xref:Microsoft.ML.IDataView) je název `inputData`.</span><span class="sxs-lookup"><span data-stu-id="7db94-124">In this case, the name of the [`IDataView`](xref:Microsoft.ML.IDataView) is `inputData`.</span></span> <span data-ttu-id="7db94-125">Vzhledem k tomu, `CurrentPrice` že je cíl nebo popisek, který se pokoušíte předpovědět pomocí nových dat, předpokládá se, že pro něj v tuto chvíli neexistuje žádná hodnota.</span><span class="sxs-lookup"><span data-stu-id="7db94-125">Because `CurrentPrice` is the target or label you're trying to predict using new data, it's assumed there is no value for it at the moment.</span></span>

```csharp
// Actual data
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f, 175000f, 210000f }
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f }
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f }
    }
};
```

<span data-ttu-id="7db94-126">Potom použijte [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) metodu použít transformace dat a generovat předpovědi.</span><span class="sxs-lookup"><span data-stu-id="7db94-126">Then, use the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method to apply the data transformations and generate predictions.</span></span>

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

<span data-ttu-id="7db94-127">Zkontrolujte předpokládané hodnoty pomocí [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) metody.</span><span class="sxs-lookup"><span data-stu-id="7db94-127">Inspect the predicted values by using the [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method.</span></span>

```csharp
// Get Predictions
float[] scoreColumn = predictions.GetColumn<float>("Score").ToArray();
```

<span data-ttu-id="7db94-128">Předpovídané hodnoty ve sloupci skóre by měly vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="7db94-128">The predicted values in the score column should look like the following:</span></span>

| <span data-ttu-id="7db94-129">Pozorování</span><span class="sxs-lookup"><span data-stu-id="7db94-129">Observation</span></span> | <span data-ttu-id="7db94-130">Prediction (Předpověď)</span><span class="sxs-lookup"><span data-stu-id="7db94-130">Prediction</span></span> |
|---|---|
| <span data-ttu-id="7db94-131">1</span><span class="sxs-lookup"><span data-stu-id="7db94-131">1</span></span> | <span data-ttu-id="7db94-132">144638.2</span><span class="sxs-lookup"><span data-stu-id="7db94-132">144638.2</span></span> |
| <span data-ttu-id="7db94-133">2</span><span class="sxs-lookup"><span data-stu-id="7db94-133">2</span></span> | <span data-ttu-id="7db94-134">150079.4</span><span class="sxs-lookup"><span data-stu-id="7db94-134">150079.4</span></span> |
| <span data-ttu-id="7db94-135">3</span><span class="sxs-lookup"><span data-stu-id="7db94-135">3</span></span> | <span data-ttu-id="7db94-136">107789.8</span><span class="sxs-lookup"><span data-stu-id="7db94-136">107789.8</span></span> |
