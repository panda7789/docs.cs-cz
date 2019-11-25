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
# <a name="make-predictions-with-a-trained-model"></a>Vytvoření předpovědi s poučeným modelem

Naučte se používat trained model k vytváření předpovědi

## <a name="create-data-models"></a>Vytváření datových modelů

### <a name="input-data"></a>Vstupní data

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

### <a name="output-data"></a>Výstupní data

Podobně jako u názvů vstupních sloupců `Features` a `Label` má ML.NET výchozí názvy pro předpovězené hodnoty sloupce vytvářené modelem. V závislosti na úloze se název může lišit.

Vzhledem k tomu, že algoritmus použitý v této ukázce je lineární regresní algoritmus, výchozí název výstupního sloupce je `Score`, který je definován atributem [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) vlastnosti `PredictedPrice`.

```csharp
class HousingPrediction
{
    [ColumnName("Score")]
    public float PredictedPrice { get; set; }
}
```

## <a name="set-up-a-prediction-pipeline"></a>Nastavení kanálu předpovědi

Bez ohledu na to, jestli se provádí jedna nebo dávková předpověď, je potřeba do aplikace načíst kanál předpovědi. Tento kanál obsahuje transformaci předběžného zpracování dat i vyškolený model. Fragment kódu níže načte kanál předpovědi ze souboru s názvem `model.zip`.

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Load Trained Model
DataViewSchema predictionPipelineSchema;
ITransformer predictionPipeline = mlContext.Model.Load("model.zip", out predictionPipelineSchema);
```

## <a name="single-prediction"></a>Jedna předpověď

Chcete-li vytvořit jedinou předpověď, vytvořte [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pomocí načteného kanálu předpovědi.

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

Pak použijte metodu [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) a předejte vstupní data jako parametr. Všimněte si, že použití metody [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) nevyžaduje vstup jako [`IDataView`](xref:Microsoft.ML.IDataView)). Důvodem je to, že pohodlně internalizes manipulaci s datovým typem vstupu, takže můžete předat objekt vstupního datového typu. Vzhledem k tomu, že `CurrentPrice` je cílem nebo návěští, které se pokoušíte odhadnout pomocí nových dat, předpokládáme, že v tuto chvíli není k dispozici žádná hodnota.

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

Pokud přistupujete k vlastnosti `Score` objektu `prediction`, měli byste získat hodnotu podobnou `150079`.

## <a name="multiple-predictions"></a>Několik předpovědi

Když se dostanou následující data, načtou se do [`IDataView`](xref:Microsoft.ML.IDataView). V tomto případě je název [`IDataView`](xref:Microsoft.ML.IDataView) `inputData`. Vzhledem k tomu, že `CurrentPrice` je cílem nebo návěští, které se pokoušíte odhadnout pomocí nových dat, předpokládá se, že v tuto chvíli není k dispozici žádná hodnota.

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

Pak použijte metodu [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) pro použití transformace dat a generování předpovědi.

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

Zkontrolujte předpovězené hodnoty pomocí metody [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) .

```csharp
// Get Predictions
float[] scoreColumn = predictions.GetColumn<float>("Score").ToArray();
```

Předpovídané hodnoty ve sloupci skóre by měly vypadat takto:

| Příležitostný | Předpovědi |
|---|---|
| první | 144638,2 |
| odst | 150079,4 |
| 3 | 107789,8 |
