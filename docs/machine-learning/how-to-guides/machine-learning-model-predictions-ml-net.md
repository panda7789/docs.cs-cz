---
title: Ujistěte se, předpovědi s trénovaného modelu
description: Naučte se vytvářet predikce na trénovaného modelu
ms.date: 06/20/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: ef2b22ff220d1fce1ec43f26c7d51f7e551e038d
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307401"
---
# <a name="make-predictions-with-a-trained-model"></a>Ujistěte se, předpovědi s trénovaného modelu

Další informace o použití trénovaný model k predikci

## <a name="create-data-models"></a>Vytvoření datových modelů

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

Podobně jako `Features` a `Label` vstupní sloupec názvy, ML.NET má výchozí názvy pro předpovězené hodnoty sloupce produkované modelu. V závislosti na úloze název se může lišit.

Protože algoritmus použitý v této ukázce se algoritmus lineární regrese, je výchozí název výstupního sloupce `Score` který je definován [ `ColumnName` ](xref:Microsoft.ML.Data.ColumnNameAttribute) atribut na `PredictedPrice` vlastnost.

```csharp
class HousingPrediction : HousingData
{
    [ColumnName("Score")]
    public float PredictedPrice { get; set; }
}
```

`HousingPrediction` Datový model dědí z `HousingData` snadno vizualizovat původní vstupní data společně s výstupem generovaných modelu.  

## <a name="set-up-a-prediction-pipeline"></a>Nastavení kanálu predikcí

Určuje, zda provedení jedné nebo predikcí služby batch, do predikce. kanál musí být načtena do aplikace. Tento kanál obsahuje transformace předběžného zpracování dat i trénovaného modelu. Následující fragment kódu načte kanálu předpovědi ze souboru s názvem `model.zip`.

```csharp
//Create MLContext 
MLContext mlContext = new MLContext();

// Load Trained Model
DataViewSchema predictionPipelineSchema;
ITransformer predictionPipeline = mlContext.Model.Load("model.zip", out predictionPipelineSchema);
```

## <a name="single-prediction"></a>Jeden predikcí

Chcete-li jeden predikcí, vytvořte [ `PredictionEngine` ](xref:Microsoft.ML.PredictionEngine%602) pomocí kanálu načíst předpovědi.

```csharp
// Create PredictionEngines
PredictionEngine<HousingData, HousingPrediction> predictionEngine = mlContext.Model.CreatePredictionEngine<HousingData, HousingPrediction>(predictionPipeline);
```

Potom použijte [ `Predict` ](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) metoda a předejte jí vstupní data jako parametr. Všimněte si, že při použití [ `Predict` ](xref:Microsoft.ML.PredictionEngineBase%602.Predict*) metoda nevyžaduje, aby vstupem bude [ `IDataView` ](xref:Microsoft.ML.IDataView)). Je to proto, že jednoduše internalizes manipulaci s typem vstupních dat, můžete předat objekt typu vstupní data. Kromě toho od `CurrentPrice` je cíl nebo popisek se snažíte předpovědět pomocí nových dat, se předpokládá, že neexistuje žádná hodnota pro něj v tuto chvíli.

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

Pokud přistupujete `Score` vlastnost `prediction` objekt, měli byste získat hodnotu podobný `150079`.

## <a name="batch-prediction"></a>Predikce služby batch

Daný následující data, načtení do [ `IDataView` ](xref:Microsoft.ML.IDataView). V tomto případě, název [ `IDataView` ](xref:Microsoft.ML.IDataView) je `inputData`. Protože `CurrentPrice` je cíl nebo popisek se snažíte předpovědět pomocí nových dat, se předpokládá, že neexistuje žádná hodnota pro něj v tuto chvíli.

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

Potom použijte [ `Transform` ](xref:Microsoft.ML.ITransformer.Transform*) metody pro použití transformace dat a generovat předpovědi.

```csharp
// Predicted Data
IDataView predictions = predictionPipeline.Transform(inputData);
```

Zkontrolujte predikované hodnoty pomocí [ `GetColumn` ](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) metody.

```csharp
// Get Predictions
float[] scoreColumn = predictions.GetColumn<float>("Score").ToArray();
```

Predikované hodnoty ve sloupci skóre by měl vypadat nějak takto:

| Zjišťování | Předpověď |
|---|---|
| 1 | 144638.2 |
| 2 | 150079.4 |
| 3 | 107789.8 |
