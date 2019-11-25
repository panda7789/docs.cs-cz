---
title: Vytvoření předpovědi s poučeným modelem
description: Naučte se vytvářet předpovědi s využitím trained model
ms.date: 09/18/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 182350cc5143155133385c6fd77986b271f6db91
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977036"
---
# <a name="make-predictions-with-a-trained-model"></a><span data-ttu-id="38a7b-103">Vytvoření předpovědi s poučeným modelem</span><span class="sxs-lookup"><span data-stu-id="38a7b-103">Make predictions with a trained model</span></span>

<span data-ttu-id="38a7b-104">Naučte se používat trained model k vytváření předpovědi</span><span class="sxs-lookup"><span data-stu-id="38a7b-104">Learn how to use a trained model to make predictions</span></span>

## <a name="create-data-models"></a><span data-ttu-id="38a7b-105">Vytváření datových modelů</span><span class="sxs-lookup"><span data-stu-id="38a7b-105">Create data models</span></span>

### <a name="input-data"></a><span data-ttu-id="38a7b-106">Vstupní data</span><span class="sxs-lookup"><span data-stu-id="38a7b-106">Input data</span></span>

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

### <a name="output-data"></a><span data-ttu-id="38a7b-107">Výstupní data</span><span class="sxs-lookup"><span data-stu-id="38a7b-107">Output data</span></span>

<span data-ttu-id="38a7b-108">Podobně jako u názvů vstupních sloupců `Features` a `Label` má ML.NET výchozí názvy pro předpovězené hodnoty sloupce vytvářené modelem.</span><span class="sxs-lookup"><span data-stu-id="38a7b-108">Like the `Features` and `Label` input column names, ML.NET has default names for the predicted value columns produced by a model.</span></span> <span data-ttu-id="38a7b-109">V závislosti na úloze se název může lišit.</span><span class="sxs-lookup"><span data-stu-id="38a7b-109">Depending on the task the name may differ.</span></span>

<span data-ttu-id="38a7b-110">Vzhledem k tomu, že algoritmus použitý v této ukázce je lineární regresní algoritmus, výchozí název výstupního sloupce je `Score`, který je definován atributem [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) vlastnosti `PredictedPrice`.</span><span class="sxs-lookup"><span data-stu-id="38a7b-110">Because the algorithm used in this sample is a linear regression algorithm, the default name of the output column is `Score` which is defined by the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute on the `PredictedPrice` property.</span></span>

```csharp
class HousingPrediction
{
    [ColumnName("Score")]
    public float PredictedPrice { get; set; }
}
```

## <a name="set-up-a-prediction-pipeline"></a><span data-ttu-id="38a7b-111">Nastavení kanálu předpovědi</span><span class="sxs-lookup"><span data-stu-id="38a7b-111">Set up a prediction pipeline</span></span>

<span data-ttu-id="38a7b-112">Bez ohledu na to, jestli se provádí jedna nebo dávková předpověď, je potřeba do aplikace načíst kanál předpovědi.</span><span class="sxs-lookup"><span data-stu-id="38a7b-112">Whether making a single or batch prediction, the prediction pipeline needs to be loaded into the application.</span></span> <span data-ttu-id="38a7b-113">Tento kanál obsahuje transformaci předběžného zpracování dat i vyškolený model.</span><span class="sxs-lookup"><span data-stu-id="38a7b-113">This pipeline contains both the data pre-processing transformations as well as the trained model.</span></span> <span data-ttu-id="38a7b-114">Fragment kódu níže načte kanál předpovědi ze souboru s názvem `model.zip`.</span><span class="sxs-lookup"><span data-stu-id="38a7b-114">The code snippet below loads the prediction pipeline from a file named `model.zip`.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Load Trained Model
DataViewSchema predictionPipelineSchema;
ITransformer predictionPipeline = mlContext.Model.Load("model.zip", out predictionPipelineSchema);
```

## <a name="single-prediction"></a><span data-ttu-id="38a7b-115">Jedna předpověď</span><span class="sxs-lookup"><span data-stu-id="38a7b-115">Single prediction</span></span>

<span data-ttu-id="38a7b-116">Chcete-li vytvořit jedinou předpověď, vytvořte [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pomocí načteného kanálu předpovědi.</span><span class="sxs-lookup"><span data-stu-id="38a7b-116">To make a single prediction, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) using the loaded prediction pipeline.</span></span>

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

<span data-ttu-id="38a7b-117">Pak použijte metodu [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) a předejte vstupní data jako parametr.</span><span class="sxs-lookup"><span data-stu-id="38a7b-117">Then, use the [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) method and pass in your input data as a parameter.</span></span> <span data-ttu-id="38a7b-118">Všimněte si, že použití metody [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) nevyžaduje vstup jako [`IDataView`](xref:Microsoft.ML.IDataView)).</span><span class="sxs-lookup"><span data-stu-id="38a7b-118">Notice that using the [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) method does not require the input to be an [`IDataView`](xref:Microsoft.ML.IDataView)).</span></span> <span data-ttu-id="38a7b-119">Důvodem je to, že pohodlně internalizes manipulaci s datovým typem vstupu, takže můžete předat objekt vstupního datového typu.</span><span class="sxs-lookup"><span data-stu-id="38a7b-119">This is because it conveniently internalizes the input data type manipulation so you can pass in an object of the input data type.</span></span> <span data-ttu-id="38a7b-120">Vzhledem k tomu, že `CurrentPrice` je cílem nebo návěští, které se pokoušíte odhadnout pomocí nových dat, předpokládáme, že v tuto chvíli není k dispozici žádná hodnota.</span><span class="sxs-lookup"><span data-stu-id="38a7b-120">Additionally, since `CurrentPrice` is the target or label you're trying to predict using new data, it's assumed there is no value for it at the moment.</span></span>

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

<span data-ttu-id="38a7b-121">Pokud přistupujete k vlastnosti `Score` objektu `prediction`, měli byste získat hodnotu podobnou `150079`.</span><span class="sxs-lookup"><span data-stu-id="38a7b-121">If you access the `Score` property of the `prediction` object, you should get a value similar to `150079`.</span></span>

## <a name="multiple-predictions"></a><span data-ttu-id="38a7b-122">Několik předpovědi</span><span class="sxs-lookup"><span data-stu-id="38a7b-122">Multiple predictions</span></span>

<span data-ttu-id="38a7b-123">Když se dostanou následující data, načtou se do [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="38a7b-123">Given the following data, load it into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="38a7b-124">V tomto případě je název [`IDataView`](xref:Microsoft.ML.IDataView) `inputData`.</span><span class="sxs-lookup"><span data-stu-id="38a7b-124">In this case, the name of the [`IDataView`](xref:Microsoft.ML.IDataView) is `inputData`.</span></span> <span data-ttu-id="38a7b-125">Vzhledem k tomu, že `CurrentPrice` je cílem nebo návěští, které se pokoušíte odhadnout pomocí nových dat, předpokládá se, že v tuto chvíli není k dispozici žádná hodnota.</span><span class="sxs-lookup"><span data-stu-id="38a7b-125">Because `CurrentPrice` is the target or label you're trying to predict using new data, it's assumed there is no value for it at the moment.</span></span>

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

<span data-ttu-id="38a7b-126">Pak použijte metodu [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) pro použití transformace dat a generování předpovědi.</span><span class="sxs-lookup"><span data-stu-id="38a7b-126">Then, use the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method to apply the data transformations and generate predictions.</span></span>

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

<span data-ttu-id="38a7b-127">Zkontrolujte předpovězené hodnoty pomocí metody [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) .</span><span class="sxs-lookup"><span data-stu-id="38a7b-127">Inspect the predicted values by using the [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method.</span></span>

```csharp
// Get Predictions
float[] scoreColumn = predictions.GetColumn<float>("Score").ToArray();
```

<span data-ttu-id="38a7b-128">Předpovídané hodnoty ve sloupci skóre by měly vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="38a7b-128">The predicted values in the score column should look like the following:</span></span>

| <span data-ttu-id="38a7b-129">Příležitostný</span><span class="sxs-lookup"><span data-stu-id="38a7b-129">Observation</span></span> | <span data-ttu-id="38a7b-130">Předpovědi</span><span class="sxs-lookup"><span data-stu-id="38a7b-130">Prediction</span></span> |
|---|---|
| <span data-ttu-id="38a7b-131">první</span><span class="sxs-lookup"><span data-stu-id="38a7b-131">1</span></span> | <span data-ttu-id="38a7b-132">144638,2</span><span class="sxs-lookup"><span data-stu-id="38a7b-132">144638.2</span></span> |
| <span data-ttu-id="38a7b-133">odst</span><span class="sxs-lookup"><span data-stu-id="38a7b-133">2</span></span> | <span data-ttu-id="38a7b-134">150079,4</span><span class="sxs-lookup"><span data-stu-id="38a7b-134">150079.4</span></span> |
| <span data-ttu-id="38a7b-135">3</span><span class="sxs-lookup"><span data-stu-id="38a7b-135">3</span></span> | <span data-ttu-id="38a7b-136">107789,8</span><span class="sxs-lookup"><span data-stu-id="38a7b-136">107789.8</span></span> |
