---
title: Uložení a načtení trénovaných modelů
description: Přečtěte si, jak ukládat a načítat trénované modely
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: e3cebe979b5c279ce8cb90db5510f8758c24c2b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73976997"
---
# <a name="save-and-load-trained-models"></a>Uložení a načtení trénovaných modelů

Přečtěte si, jak ukládat a načítat trénované modely ve vaší aplikaci.

V průběhu procesu vytváření modelu modelu žije v paměti a je přístupný v průběhu celého životního cyklu aplikace. Však jakmile aplikace přestane běžet, pokud model není uložen někde místně nebo vzdáleně, je již přístupné. Obvykle modely se používají v určitém okamžiku po školení v jiných aplikacích buď pro odvození nebo re-školení. Proto je důležité uložit model. Uložte a načtěte modely pomocí kroků popsaných v následujících částech tohoto dokumentu při použití kanálů pro přípravu dat a model školení, jako je ten, který je popsán níže. Přestože tato ukázka používá lineární regresní model, stejný proces platí pro jiné ML.NET algoritmy.

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

Vzhledem k tomu, že většina modelů a kanály pro přípravu dat dědí ze stejné sady tříd, jsou podpisy metody ukládání a načítání pro tyto součásti stejné. V závislosti na případu použití můžete buď kombinovat kanál pro [`EstimatorChain`](xref:Microsoft.ML.Data.TransformerChain%601) přípravu dat [`ITransformer`](xref:Microsoft.ML.ITransformer) a model do [`ITransformer`](xref:Microsoft.ML.ITransformer) jednoho, který by výstup jeden nebo samostatné je a tím vytvořit samostatný pro každý.

## <a name="save-a-model-locally"></a>Místní uložení modelu

Při ukládání modelu potřebujete dvě věci:

1. Model. [`ITransformer`](xref:Microsoft.ML.ITransformer)
2. Očekávaný [`DataViewSchema`](xref:Microsoft.ML.DataViewSchema) vstup [`ITransformer`](xref:Microsoft.ML.ITransformer).

Po trénování [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) modelu použijte metodu k uložení `model.zip` trénovaného modelu do souboru volaného pomocí `DataViewSchema` vstupních dat.

```csharp
// Save Trained Model
mlContext.Model.Save(trainedModel, data.Schema, "model.zip");
```

## <a name="load-a-model-stored-locally"></a>Načtení modelu uloženého místně

Modely uložené lokálně lze použít v jiných `ASP.NET Core` `Serverless Web Applications`procesech nebo aplikacích, jako je a . Další informace najdete [v článku Použití ML.NET ve webovém rozhraní API](./serve-model-web-api-ml-net.md) a nasazení ML.NET článku s postupy webové aplikace Web App bez [serveru.](./serve-model-serverless-azure-functions-ml-net.md)

V samostatné aplikaci nebo [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) procesu použijte metodu spolu s cestou k souboru, abyste získali trénovaný model do aplikace.

```csharp
//Define DataViewSchema for data preparation pipeline and trained model
DataViewSchema modelSchema;

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```

## <a name="load-a-model-stored-remotely"></a>Načtení modelu uloženého na dálku

Chcete-li načíst kanály pro přípravu dat a [`Stream`](xref:System.IO.Stream) modely uložené ve vzdáleném umístění do aplikace, použijte místo cesty k souboru v metodě. [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*)

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

## <a name="working-with-separate-data-preparation-and-model-pipelines"></a>Práce se samostatnými datovými přípravami a kanály modelů

> [!NOTE]
> Práce se samostatnými kanály pro přípravu dat a modelškolení je volitelná. Oddělení potrubí usnadňuje kontrolu naučených parametrů modelu. Pro předpovědi je jednodušší uložit a načíst jeden kanál, který zahrnuje operace přípravy dat a model školení.

Při práci se samostatnými kanály a modely pro přípravu dat platí stejný proces jako jednotlivé kanály; s výjimkou nyní musí být oba kanály uloženy a načteny současně.

Vzhledem k tomu, samostatná příprava dat a model školení potrubí:

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

### <a name="save-data-preparation-pipeline-and-trained-model"></a>Uložení kanálu pro přípravu dat a trénovaného modelu

Chcete-li uložit kanál pro přípravu dat i trénovaný model, použijte následující příkazy:

```csharp
// Save Data Prep transformer
mlContext.Model.Save(dataPrepTransformer, data.Schema, "data_preparation_pipeline.zip");

// Save Trained Model
mlContext.Model.Save(trainedModel, transformedData.Schema, "model.zip");
```

### <a name="load-data-preparation-pipeline-and-trained-model"></a>Načtení kanálu pro přípravu dat a trénovaného modelu

V samostatném procesu nebo aplikaci načtěte kanál přípravy dat a trénovaný model současně následujícím způsobem:

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define data preparation and trained model schemas
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline and trained model
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip",out dataPrepPipelineSchema);
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```
