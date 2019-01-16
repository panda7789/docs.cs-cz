---
title: Použití PredictionEngine předpověď jeden po druhém - ML.NET
description: Další informace o použití ML.NET PredictionEngine předpověď jeden po druhém
ms.date: 01/15/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 0b3f60038fe7f49ffbff3c63fd2862ba67adb506
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333639"
---
# <a name="use-the-predictionengine-to-make-one-prediction-at-a-time---mlnet"></a>Použití PredictionEngine předpověď jeden po druhém - ML.NET 

Protože všechny modely ML.NET transformátoru, použijete `model.Transform` použít model, který má `DataView` k následné predikci. 

Více obvyklý případ, ale je, pokud není žádný parametr 'dataset', že chcete předpovědět na, ale místo toho obdržíte jedním z příkladů v čase. Například spusťte modelu jako součást vašeho webu technologie ASP.NET a muset udělat předpověď pro příchozí požadavek protokolu HTTP.

`PredictionEngine` Prostřednictvím kanálu pro predikce byla najednou spuštěna jedním z příkladů.

Tady je úplný příklad použití předem připravených Iris prediktivní model datové sady:

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Step one: read the data as an IDataView.
// First, we define the reader: specify the data columns and where to find them in the text file.
var reader = mlContext.Data.CreateTextReader(new TextLoader.Arguments
{
    Column = new[] {
        new TextLoader.Column("SepalLength", DataKind.R4, 0),
        new TextLoader.Column("SepalWidth", DataKind.R4, 1),
        new TextLoader.Column("PetalLength", DataKind.R4, 2),
        new TextLoader.Column("PetalWidth", DataKind.R4, 3),
        // Label: kind of iris.
        new TextLoader.Column("Label", DataKind.TX, 4),
    },
    // Default separator is tab, but the dataset has comma.
    Separator = ","
});

// Retrieve the training data.
var trainData = reader.Read(irisDataPath);

// Build the training pipeline.
var pipeline =
    // Concatenate all the features together into one column 'Features'.
    mlContext.Transforms.Concatenate("Features", "SepalLength", "SepalWidth", "PetalLength", "PetalWidth")
    // Note that the label is text, so it needs to be converted to key.
    .Append(mlContext.Transforms.Categorical.MapValueToKey("Label"), TransformerScope.TrainTest)
    // Use the multi-class SDCA model to predict the label using features.
    .Append(mlContext.MulticlassClassification.Trainers.StochasticDualCoordinateAscent())
    // Apply the inverse conversion from 'PredictedLabel' column back to string value.
    .Append(mlContext.Transforms.Conversion.MapKeyToValue(("PredictedLabel", "Data")));

// Train the model.
var model = pipeline.Fit(trainData);
```

Použití [pochopení schématu](https://github.com/dotnet/machinelearning/blob/master/docs/code/SchemaComprehension.md) predikcí, definovat dvojici třídy takto:

```csharp
private class IrisInput
{
    // Unfortunately, we still need the dummy 'Label' column to be present.
    [ColumnName("Label")]
    public string IgnoredLabel { get; set; }
    public float SepalLength { get; set; }
    public float SepalWidth { get; set; }
    public float PetalLength { get; set; }
    public float PetalWidth { get; set; }
}

private class IrisPrediction
{
    [ColumnName("Data")]
    public string PredictedClass { get; set; }
}
```

Predikce kód teď vypadá takto:

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Use the model for one-time prediction.
// Make the prediction function object. Note that, on average, this call takes around 200x longer
// than one prediction, so you might want to cache and reuse the prediction engine, instead of
// creating one per prediction.
var predictionEngine = model.CreatePredictionEngine<IrisInput, IrisPrediction>(mlContext);

// Obtain the prediction. Remember that 'Predict' is not reentrant. If you want to use multiple threads
// for simultaneous prediction, make sure each thread is using its own PredictionEngine.
var prediction = predictionEngine.Predict(new IrisInput
{
    SepalLength = 4.1f,
    SepalWidth = 0.1f,
    PetalLength = 3.2f,
    PetalWidth = 1.4f
});
```
