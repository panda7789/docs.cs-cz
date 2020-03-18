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
# <a name="make-predictions-with-a-trained-model"></a>Předvídací předpovědi pomocí trénovaného modelu

Naučte se používat trénovaný model k předpovědím

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

Stejně `Features` `Label` jako názvy a vstupních sloupců má ML.NET výchozí názvy pro sloupce předpovídané hodnoty vytvořené modelem. V závislosti na úkolu se název může lišit.

Vzhledem k tomu, že algoritmus použitý v tomto vzorku je lineární `Score` regresní [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) algoritmus, výchozí název výstupního sloupce je definován atributem vlastnosti. `PredictedPrice`

```csharp
class HousingPrediction
{
    [ColumnName("Score")]
    public float PredictedPrice { get; set; }
}
```

## <a name="set-up-a-prediction-pipeline"></a>Nastavení kanálu předpovědi

Ať už vytváření jedné nebo dávky předpověď, předpověď kanálu musí být načtendo aplikace. Tento kanál obsahuje transformace před zpracováním dat i trénovaný model. Fragment kódu pod načte kanál předpovědi ze `model.zip`souboru s názvem .

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Load Trained Model
DataViewSchema predictionPipelineSchema;
ITransformer predictionPipeline = mlContext.Model.Load("model.zip", out predictionPipelineSchema);
```

## <a name="single-prediction"></a>Jednorázová předpověď

Chcete-li vytvořit jednu [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) předpověď, vytvořte pomocí kanálu načtené předpovědi.

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

Potom použijte [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) metodu a předat vstupní data jako parametr. Všimněte si, že pomocí [`Predict`](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) metody nevyžaduje [`IDataView`](xref:Microsoft.ML.IDataView)vstup být ). Důvodem je, že pohodlně internalizuje manipulaci s typem vstupních dat, takže můžete předat objekt vstupního datového typu. Navíc vzhledem `CurrentPrice` k tomu, že je cíl nebo popisek, který se pokoušíte předpovědět pomocí nových dat, předpokládá se, že pro něj v tuto chvíli neexistuje žádná hodnota.

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

Pokud máte `Score` přístup k `prediction` vlastnostobjektu, měli byste `150079`získat hodnotu podobnou .

## <a name="multiple-predictions"></a>Více předpovědí

Vzhledem k následujícím datům [`IDataView`](xref:Microsoft.ML.IDataView)je načtěte do . V tomto případě [`IDataView`](xref:Microsoft.ML.IDataView) je název `inputData`. Vzhledem k tomu, `CurrentPrice` že je cíl nebo popisek, který se pokoušíte předpovědět pomocí nových dat, předpokládá se, že pro něj v tuto chvíli neexistuje žádná hodnota.

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

Potom použijte [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) metodu použít transformace dat a generovat předpovědi.

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

Zkontrolujte předpokládané hodnoty pomocí [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) metody.

```csharp
// Get Predictions
float[] scoreColumn = predictions.GetColumn<float>("Score").ToArray();
```

Předpovídané hodnoty ve sloupci skóre by měly vypadat takto:

| Pozorování | Prediction (Předpověď) |
|---|---|
| 1 | 144638.2 |
| 2 | 150079.4 |
| 3 | 107789.8 |
