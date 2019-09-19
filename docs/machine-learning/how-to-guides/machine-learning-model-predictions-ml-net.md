---
title: Vytvoření předpovědi s poučeným modelem
description: Naučte se vytvářet předpovědi s využitím trained model
ms.date: 09/18/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 33e0cb74342ca3e82ff5f108453d63e022d63d20
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118013"
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

Podobně jako vstupní `Label` názvy sloupců aml.NETmávýchozínázvypropředpovězenéhodnotysloupcevytvářenémodelem.`Features` V závislosti na úloze se název může lišit.

Vzhledem k tomu, že algoritmus použitý v této ukázce je lineární regresní algoritmus, výchozí název výstupního sloupce `Score` je definován [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) atributem `PredictedPrice` vlastnosti.

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

Chcete-li udělat jednu předpověď, vytvořte [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pomocí načteného kanálu předpovědi.

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

Pak použijte [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) metodu a předejte vstupní data jako parametr. Všimněte si, že [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) použití metody nevyžaduje vstup [`IDataView`](xref:Microsoft.ML.IDataView)jako). Důvodem je to, že pohodlně internalizes manipulaci s datovým typem vstupu, takže můžete předat objekt vstupního datového typu. Vzhledem `CurrentPrice` k tomu, že se jedná o cíl nebo popisek, který se pokoušíte odhadnout pomocí nových dat, předpokládáme, že v tuto chvíli není k dispozici žádná hodnota.

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

Pokud přistupujete `Score` k vlastnosti `prediction` objektu, měli byste `150079`získat hodnotu podobnou.

## <a name="multiple-predictions"></a>Několik předpovědi

Když jsou uvedena následující data, načtěte je [`IDataView`](xref:Microsoft.ML.IDataView)do. V tomto případě [`IDataView`](xref:Microsoft.ML.IDataView) je `inputData`název. Vzhledem `CurrentPrice` k tomu, že se jedná o cíl nebo popisek, který se pokoušíte odhadnout pomocí nových dat, předpokládá se, že v tuto chvíli není k dispozici žádná hodnota.

```csharp
// Actual data
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f,175000f,210000f }
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

Pak použijte [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) metodu pro použití transformace dat a generování předpovědi.

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

Zkontrolujte předpovězené hodnoty pomocí [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) metody.

```csharp
// Get Predictions
float[] scoreColumn = predictions.GetColumn<float>("Score").ToArray();
```

Předpovídané hodnoty ve sloupci skóre by měly vypadat takto:

| Příležitostný | Předpověď |
|---|---|
| 1 | 144638,2 |
| 2 | 150079,4 |
| 3 | 107789,8 |
