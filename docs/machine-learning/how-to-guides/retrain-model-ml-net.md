---
title: Opakované trénování modelu
description: Zjistěte, jak programovém přeučení modelů v ML.NET
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 2f8f8c035166612aabede8a512485bdf296c5655
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557907"
---
# <a name="re-train-a-model"></a>Opakované trénování modelu

Zjistěte, jak přeučování v ML.NET model strojového učení.

Celém světě a data kolem něj změnit konstantní tempem. Modely proto nutné změnit a aktualizovat také. ML.NET poskytuje funkce pro znovu trénovací modely s využitím zjistili parametry modelu jako výchozí bod k průběžně sestavení na předchozí zkušenosti a nikoli pokaždé, když vytváříte od začátku.  

Tyto algoritmy jsou znovu trainable v ML.NET:

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

## <a name="load-pre-trained-model"></a>Načíst předem vytrénovaných model

Nejdřív načtěte předem natrénovaných modelů do vaší aplikace. Další informace o načítání trénovacích kanálů a modely, najdete v článku související [článek](./consuming-model-ml-net.md).

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define DataViewSchema of data prep pipeline and trained model
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data prepration pipeline
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip", out dataPrepPipelineSchema);

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("ogd_model.zip", out modelSchema);
```

## <a name="extract-pre-trained-model-parameters"></a>Extrahovat parametry předem vytrénovaných modelu

Po načtení modelu extrahovat parametry zjištěná modelu díky přístupu [ `Model` ](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) vlastnost předem natrénovaných modelů. Předem vytrénovaných model se trénuje pomocí trénování modelu lineární regrese [ `OnlineGradientDescentTrainer` ](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) vytváří[ `RegressionPredictionTransformer` ](xref:Microsoft.ML.Data.RegressionPredictionTransformer%601) , který vypíše [ `LinearRegressionModelParameters` ](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters). Tyto parametry modelu lineární regrese obsahovat zjištěná posun a váhy nebo koeficienty modelu. Tyto hodnoty se použije jako výchozí bod pro nové znovu trénovaného modelu.

```csharp
// Extract trained model parameters
LinearRegressionModelParameters originalModelParameters = 
    ((ISingleFeaturePredictionTransformer<object>)trainedModel).Model as LinearRegressionModelParameters;
```

## <a name="re-train-model"></a>Znovu trénování modelu

Proces přetrénování modelu se nijak neliší od u trénování modelu. Jediným rozdílem je, [ `Fit` ](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*) metoda kromě dat taky přijímá jako vstup původní zjistili parametry modelu a použije je jako počáteční bod v procesu znovu školení.  

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

## <a name="compare-model-parameters"></a>Porovnání parametry modelu

Jak poznáte, pokud znovu školení doopravdy stalo? Jedním ze způsobů je porovnat, zda parametry znovu trénovaného modelu se můžou lišit od těch, které původní model. Následující ukázka kódu porovná původní proti váhy znovu trénovaného modelu a vypíše do konzoly.

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

Následující tabulka ukazuje, jak může vypadat výstup. 

|Původní | Retrained | Rozdíl |
|---|---|---|
| 33039.86 | 56293.76 | -23253.9 |
| 29099.14 | 49586.03 | -20486.89 |
| 28938.38 | 48609.23 | -19670.85 |
| 30484.02 | 53745.43 | -23261.41 |
