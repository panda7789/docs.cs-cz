---
title: Ukládání a načítání vycvičených modelů
description: Naučte se ukládat a načítat školené modely.
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: e3cebe979b5c279ce8cb90db5510f8758c24c2b4
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976997"
---
# <a name="save-and-load-trained-models"></a>Ukládání a načítání vycvičených modelů

Naučte se, jak ukládat a načítat do vaší aplikace školený modely.

V průběhu procesu sestavování modelu je model umístěn v paměti a je přístupný v rámci životního cyklu aplikace. Pokud se ale aplikace zastaví, pokud se model neuloží místně nebo vzdáleně, už není přístupný. Modely jsou obvykle používány v určitém bodě po školení v jiných aplikacích, a to buď pro odvození nebo opětovné školení. Proto je důležité model Uložit. Pomocí kroků popsaných v následujících částech tohoto dokumentu uložte a načtěte modely při použití kanálů pro přípravu a školicí kanály pro přípravu dat, jako je tomu níže. I když tato ukázka používá model lineární regrese, stejný postup se vztahuje i na jiné algoritmy ML.NET.

```csharp
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 600f,
        HistoricalPrices = new float[] { 100000f, 125000f, 122000f },
        CurrentPrice = 170000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 200000f, 250000f, 230000f },
        CurrentPrice = 225000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 126000f, 130000f, 200000f },
        CurrentPrice = 195000f
    }
};

// Create MLContext
MLContext mlContext = new MLContext();

// Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(housingData);

// Define data preparation estimator
EstimatorChain<RegressionPredictionTransformer<LinearRegressionModelParameters>> pipelineEstimator =
    mlContext.Transforms.Concatenate("Features", new string[] { "Size", "HistoricalPrices" })
        .Append(mlContext.Transforms.NormalizeMinMax("Features"))
        .Append(mlContext.Regression.Trainers.Sdca());

// Train model
ITransformer trainedModel = pipelineEstimator.Fit(data);

// Save model
mlContext.Model.Save(trainedModel, data.Schema, "model.zip");
```

Vzhledem k tomu, že většina modelů a kanálů přípravy dat dědí ze stejné sady tříd, signatury metody Save a Load pro tyto komponenty jsou stejné. V závislosti na vašem případu použití můžete kombinovat kanál přípravy dat a model do jediného [`EstimatorChain`](xref:Microsoft.ML.Data.TransformerChain%601) , který by představoval výstup jednoho [`ITransformer`](xref:Microsoft.ML.ITransformer) nebo oddělit je tak, aby pro každý vytvořil samostatný [`ITransformer`](xref:Microsoft.ML.ITransformer) .

## <a name="save-a-model-locally"></a>Místní uložení modelu

Při ukládání modelu potřebujete dvě věci:

1. [`ITransformer`](xref:Microsoft.ML.ITransformer) modelu.
2. [`DataViewSchema`](xref:Microsoft.ML.DataViewSchema) očekávaného vstupu [`ITransformer`](xref:Microsoft.ML.ITransformer).

Po školení modelu použijte metodu [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) k uložení proučeného modelu do souboru s názvem `model.zip` pomocí `DataViewSchema` vstupních dat.

```csharp
// Save Trained Model
mlContext.Model.Save(trainedModel, data.Schema, "model.zip");
```

## <a name="load-a-model-stored-locally"></a>Načtení modelu místně uloženého

Místně uložené modely lze použít v jiných procesech nebo aplikacích, jako jsou `ASP.NET Core` a `Serverless Web Applications`. Další informace najdete v článcích [použití ml.NET ve webovém rozhraní API](./serve-model-web-api-ml-net.md) a [nasazení ml.NET webových aplikací bez serveru](./serve-model-serverless-azure-functions-ml-net.md) .

V samostatné aplikaci nebo procesu použijte metodu [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) společně s cestou k souboru, abyste získali vyškolený model do aplikace.

```csharp
//Define DataViewSchema for data preparation pipeline and trained model
DataViewSchema modelSchema;

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```

## <a name="load-a-model-stored-remotely"></a>Načtení modelu uloženého vzdáleně

Chcete-li načíst přípravné kanály a modely uložené ve vzdáleném umístění do vaší aplikace, použijte místo cesty k souboru v metodě [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) [`Stream`](xref:System.IO.Stream) .

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define DataViewSchema and ITransformers
DataViewSchema modelSchema;
ITransformer trainedModel;

// Load data prep pipeline and trained model
using (HttpClient client = new HttpClient())
{
    Stream modelFile = await client.GetStreamAsync("<YOUR-REMOTE-FILE-LOCATION>");

    trainedModel = mlContext.Model.Load(modelFile, out modelSchema);
}
```

## <a name="working-with-separate-data-preparation-and-model-pipelines"></a>Práce s oddělenými kanály pro přípravu a modelování dat

> [!NOTE]
> Práce s oddělenými kanály pro přípravu dat a výuku modelu je volitelná. Oddělení kanálů usnadňuje kontrolu zjištěných parametrů modelu. V případě předpovědi je snazší Uložit a načíst jeden kanál, který obsahuje operace školení pro přípravu a modelování dat.

Při práci se samostatnými kanály pro přípravu dat a modely se používá stejný postup jako u jednoho kanálu. s výjimkou toho je potřeba současně ukládat a načítat oba kanály.

Předané samostatné kanály pro přípravu a přípravu dat:

```csharp
// Define data preparation estimator
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", new string[] { "Size", "HistoricalPrices" })
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// Create data preparation transformer
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(data);

// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Pre-process data using data prep operations
IDataView transformedData = dataPrepTransformer.Transform(data);

// Train regression model
RegressionPredictionTransformer<LinearRegressionModelParameters> trainedModel = sdcaEstimator.Fit(transformedData);
```

### <a name="save-data-preparation-pipeline-and-trained-model"></a>Uložení kanálu přípravy dat a trained model

Pokud chcete uložit jak kanál pro přípravu dat, tak i školený model, použijte následující příkazy:

```csharp
// Save Data Prep transformer
mlContext.Model.Save(dataPrepTransformer, data.Schema, "data_preparation_pipeline.zip");

// Save Trained Model
mlContext.Model.Save(trainedModel, transformedData.Schema, "model.zip");
```

### <a name="load-data-preparation-pipeline-and-trained-model"></a>Načtení kanálu přípravy dat a trained model

V samostatném procesu nebo aplikaci načtěte následující kanál pro přípravu dat a školený model současně:

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define data preparation and trained model schemas
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline and trained model
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip",out dataPrepPipelineSchema);
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```
