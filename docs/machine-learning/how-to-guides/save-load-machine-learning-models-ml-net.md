---
title: Uložení a načtení trénované modely
description: Zjistěte, jak uložit a načíst trénované modely
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: e3d4a51ceaf707d30c5072b91d7baf7fe02ef433
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65066169"
---
# <a name="save-and-load-trained-models"></a>Uložení a načtení trénované modely

Zjistěte, jak uložit a načíst trénované modely ve vaší aplikaci. 

V průběhu procesu vytváření modelu model je umístěn v paměti a je dostupný v průběhu životního cyklu aplikace. Po aplikaci se zastaví, pokud model není uložen někde místně nebo vzdáleně, je však již nebude dostupná. Modely se obvykle používají v určitém okamžiku po školení v jiných aplikacích, ať už pro odvození nebo znovu školení. Proto je důležité k ukládání modelu. Uložení a načtení modelů pomocí kroků popsaných v dalších částech tohoto dokumentu, při použití přípravy dat a modelu trénovacích kanálů stejný, jako je podrobně popsaný níže. I když tato ukázka používá model lineární regrese, stejný postup se vztahuje na jiné ML.NET algoritmy.

```csharp
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 600f,
        HistoricalPrices = new float[] { 100000f ,125000f ,122000f },
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

Protože většina modely a data přípravy kanály dědit z stejná sada tříd, uložit a načíst podpisy metod pro tyto součásti je stejný. V závislosti na vašemu případu použití, můžete buď kombinovat kanálu přípravy dat a modelu do jednoho [ `EstimatorChain` ](xref:Microsoft.ML.Data.TransformerChain%601) který by výstup jedné [ `ITransformer` ](xref:Microsoft.ML.ITransformer) nebo jim tak vytváření oddělení samostatné [ `ITransformer` ](xref:Microsoft.ML.ITransformer) pro každý. 

## <a name="save-a-model-locally"></a>Uložit model místně

Při ukládání modelu budete potřebovat dvě věci:

1. [ `ITransformer` ](xref:Microsoft.ML.ITransformer) Modelu.
2. [ `DataViewSchema` ](xref:Microsoft.ML.DataViewSchema) z [ `ITransformer` ](xref:Microsoft.ML.ITransformer)očekávaný vstup.

Po trénování modelu, použijte [ `Save` ](xref:Microsoft.ML.ModelOperationsCatalog.Save*) volá metodu pro uložení naučeného modelu do souboru `model.zip` pomocí `DataViewSchema` vstupní data. 

```csharp
// Save Trained Model
mlContext.Model.Save(trainedModel, data.Schema, "model.zip");
```

## <a name="load-a-model-stored-locally"></a>Načtení modelu ukládají místně

Modely se ukládají místně se dá použít v jiných procesů nebo aplikace, jako je `ASP.NET Core` a `Serverless Web Applications`. Zobrazit [ML.NET použití v rozhraní Web API](./serve-model-web-api-ml-net.md) a [nasazení ML.NET bez serveru webové aplikace](./serve-model-serverless-azure-functions-ml-net.md) články s postupy pro další informace. 

V samostatné aplikace nebo proces, použijte [ `Load` ](xref:Microsoft.ML.ModelOperationsCatalog.Load*) metoda spolu se cesta k souboru zobrazíte trénovaného modelu do vaší aplikace.

```csharp
//Define DataViewSchema for data preparation pipeline and trained model
DataViewSchema modelSchema;

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```

## <a name="load-a-model-stored-remotely"></a>Načtení modelu vzdáleně uložen

Chcete-li načíst kanálů přípravy dat a modely, které jsou uložené ve vzdáleném umístění do vaší aplikace, použijte [ `Stream` ](xref:System.IO.Stream) namísto cesty souboru v [ `Load` ](xref:Microsoft.ML.ModelOperationsCatalog.Load*) – metoda.

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

## <a name="working-with-separate-data-preparation-and-model-pipelines"></a>Práce s kanály modelu a samostatná data pro přípravu

> [!NOTE]
> Práce s kanály trénování modelu a samostatná data pro přípravu je volitelné. Oddělení kanály usnadňuje Zkontrolujte parametry zjištěná modelu. Pro predikcí je jednodušší pro uložení a načtení jeden kanál, který zahrnuje přípravy dat a operace trénování modelu.

Při práci s kanály samostatná data pro přípravu a modely, stejně jako jeden kanály platí; s výjimkou nyní obou kanálů je potřeba uložit a načíst současně.

Daný samostatná data pro přípravu a model trénovacích kanálů:

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

### <a name="save-data-preparation-pipeline-and-trained-model"></a>Uložení kanálu přípravy dat a trénovaného modelu

Uložení kanálu přípravy dat i trénovaného modelu, použijte následující příkazy:

```csharp
// Save Data Prep transformer
mlContext.Model.Save(dataPrepTransformer, data.Schema, "data_preparation_pipeline.zip");

// Save Trained Model
mlContext.Model.Save(trainedModel, transformedData.Schema, "model.zip");
```

### <a name="load-data-preparation-pipeline-and-trained-model"></a>Načíst kanálu přípravy dat a trénovaného modelu 

V samostatném procesu nebo v aplikaci načtěte kanálu přípravy dat a trénovaného modelu současně následujícím způsobem:

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define data preparation and trained model schemas
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline and trained model
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip",out dataPrepPipelineSchema);
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```
