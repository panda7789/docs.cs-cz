---
title: Opakované trénování modelu
description: Informace o tom, jak přeškolit model v ML.NET
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 735782a4a0877a917b6e1885f009aa49d834170f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976967"
---
# <a name="re-train-a-model"></a>Opakované trénování modelu

Naučte se přeškolit model strojového učení v ML.NET.

Svět a data, která se pohybují, se mění při konstantním tempu. V takovém případě je potřeba, aby se modely změnily a aktualizovaly i. ML.NET poskytuje funkce pro opětovné školení modelů pomocí pořízených parametrů modelu jako výchozího bodu pro průběžné sestavování na předchozí prostředí a nikoli při každém neúplném psaní.

Následující algoritmy jsou znovu vlakové v ML.NET:

- [AveragedPerceptronTrainer](xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer)
- [FieldAwareFactorizationMachineTrainer](xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer)
- [LbfgsLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer)
- [LbfgsMaximumEntropyMulticlassTrainer](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer)
- [LbfgsPoissonRegressionTrainer](xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer)
- [LinearSvmTrainer](xref:Microsoft.ML.Trainers.LinearSvmTrainer)
- [OnlineGradientDescentTrainer](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer)
- [SgdCalibratedTrainer](xref:Microsoft.ML.Trainers.SgdCalibratedTrainer)
- [SgdNonCalibratedTrainer](xref:Microsoft.ML.Trainers.SgdNonCalibratedTrainer)
- [SymbolicSgdLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer)

## <a name="load-pre-trained-model"></a>Načíst předem trained model

Nejdřív načtěte předem vyškolený model do aplikace. Další informace o načítání školicích kanálů a modelů najdete v tématu [uložení a načtení trained model](save-load-machine-learning-models-ml-net.md).

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define DataViewSchema of data prep pipeline and trained model
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip", out dataPrepPipelineSchema);

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("ogd_model.zip", out modelSchema);
```

## <a name="extract-pre-trained-model-parameters"></a>Extrakce předučených parametrů modelu

Po načtení modelu rozbalte zjištěné parametry modelu tím, že získáte přístup k vlastnosti [`Model`](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) předučeného modelu. Předučený model byl vyškolený pomocí modelu lineární regrese [`OnlineGradientDescentTrainer`](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) , který vytvoří[`RegressionPredictionTransformer`](xref:Microsoft.ML.Data.RegressionPredictionTransformer%601) , které výstup [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters). Tyto parametry modelu lineární regrese obsahují zjištěné odchylky a váhy nebo koeficienty modelu. Tyto hodnoty budou použity jako výchozí bod pro nový znovu vyškolený model.

```csharp
// Extract trained model parameters
LinearRegressionModelParameters originalModelParameters =
    ((ISingleFeaturePredictionTransformer<object>)trainedModel).Model as LinearRegressionModelParameters;
```

## <a name="re-train-model"></a>Opětovné výuka modelu

Proces pro přeškolení modelu se neliší od školení modelu. Jediným rozdílem je, že metoda [`Fit`](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*) kromě dat také přijímá jako vstup původní naučené parametry modelu a používá je jako výchozí bod v procesu opětovného školení.

```csharp
// New Data
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f,175000f,210000f },
        CurrentPrice = 205000f
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f },
        CurrentPrice = 210000f
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f },
        CurrentPrice = 180000f
    }
};

//Load New Data
IDataView newData = mlContext.Data.LoadFromEnumerable<HousingData>(housingData);

// Preprocess Data
IDataView transformedNewData = dataPrepPipeline.Transform(newData);

// Retrain model
RegressionPredictionTransformer<LinearRegressionModelParameters> retrainedModel =
    mlContext.Regression.Trainers.OnlineGradientDescent()
        .Fit(transformedNewData, originalModelParameters);
```

## <a name="compare-model-parameters"></a>Porovnat parametry modelu

Jak zjistíte, jestli se vlastní školení skutečně stalo? Jedním ze způsobů je porovnat, jestli jsou parametry přeučeného modelu jiné než u původního modelu. Následující ukázka kódu porovnává původní váhu podle znovu vyškolených modelů a vypíše je do konzoly.

```csharp
// Extract Model Parameters of re-trained model
LinearRegressionModelParameters retrainedModelParameters = retrainedModel.Model as LinearRegressionModelParameters;

// Inspect Change in Weights
var weightDiffs =
    originalModelParameters.Weights.Zip(
        retrainedModelParameters.Weights, (original, retrained) => original - retrained).ToArray();

Console.WriteLine("Original | Retrained | Difference");
for(int i=0;i < weightDiffs.Count();i++)
{
    Console.WriteLine($"{originalModelParameters.Weights[i]} | {retrainedModelParameters.Weights[i]} | {weightDiffs[i]}");
}
```

Následující tabulka obsahuje informace o tom, jak může vypadat výstup.

|Původně | Přetrénovat | Rozdíl |
|---|---|---|
| 33039,86 | 56293,76 | -23253,9 |
| 29099,14 | 49586,03 | -20486,89 |
| 28938,38 | 48609,23 | -19670,85 |
| 30484,02 | 53745,43 | -23261,41 |
