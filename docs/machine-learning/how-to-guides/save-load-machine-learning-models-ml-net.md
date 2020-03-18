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
# <a name="save-and-load-trained-models"></a><span data-ttu-id="15e4b-103">Uložení a načtení trénovaných modelů</span><span class="sxs-lookup"><span data-stu-id="15e4b-103">Save and load trained models</span></span>

<span data-ttu-id="15e4b-104">Přečtěte si, jak ukládat a načítat trénované modely ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="15e4b-104">Learn how to save and load trained models in your application.</span></span>

<span data-ttu-id="15e4b-105">V průběhu procesu vytváření modelu modelu žije v paměti a je přístupný v průběhu celého životního cyklu aplikace.</span><span class="sxs-lookup"><span data-stu-id="15e4b-105">Throughout the model building process, a model lives in memory and is accessible throughout the application's lifecycle.</span></span> <span data-ttu-id="15e4b-106">Však jakmile aplikace přestane běžet, pokud model není uložen někde místně nebo vzdáleně, je již přístupné.</span><span class="sxs-lookup"><span data-stu-id="15e4b-106">However, once the application stops running, if the model is not saved somewhere locally or remotely, it's no longer accessible.</span></span> <span data-ttu-id="15e4b-107">Obvykle modely se používají v určitém okamžiku po školení v jiných aplikacích buď pro odvození nebo re-školení.</span><span class="sxs-lookup"><span data-stu-id="15e4b-107">Typically models are used at some point after training in other applications either for inference or re-training.</span></span> <span data-ttu-id="15e4b-108">Proto je důležité uložit model.</span><span class="sxs-lookup"><span data-stu-id="15e4b-108">Therefore, it's important to store the model.</span></span> <span data-ttu-id="15e4b-109">Uložte a načtěte modely pomocí kroků popsaných v následujících částech tohoto dokumentu při použití kanálů pro přípravu dat a model školení, jako je ten, který je popsán níže.</span><span class="sxs-lookup"><span data-stu-id="15e4b-109">Save and load models using the steps described in subsequent sections of this document when using data preparation and model training pipelines like the one detailed below.</span></span> <span data-ttu-id="15e4b-110">Přestože tato ukázka používá lineární regresní model, stejný proces platí pro jiné ML.NET algoritmy.</span><span class="sxs-lookup"><span data-stu-id="15e4b-110">Although this sample uses a linear regression model, the same process applies to other ML.NET algorithms.</span></span>

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

<span data-ttu-id="15e4b-111">Vzhledem k tomu, že většina modelů a kanály pro přípravu dat dědí ze stejné sady tříd, jsou podpisy metody ukládání a načítání pro tyto součásti stejné.</span><span class="sxs-lookup"><span data-stu-id="15e4b-111">Because most models and data preparation pipelines inherit from the same set of classes, the save and load method signatures for these components is the same.</span></span> <span data-ttu-id="15e4b-112">V závislosti na případu použití můžete buď kombinovat kanál pro [`EstimatorChain`](xref:Microsoft.ML.Data.TransformerChain%601) přípravu dat [`ITransformer`](xref:Microsoft.ML.ITransformer) a model do [`ITransformer`](xref:Microsoft.ML.ITransformer) jednoho, který by výstup jeden nebo samostatné je a tím vytvořit samostatný pro každý.</span><span class="sxs-lookup"><span data-stu-id="15e4b-112">Depending on your use case, you can either combine the data preparation pipeline and model into a single [`EstimatorChain`](xref:Microsoft.ML.Data.TransformerChain%601) which would output a single [`ITransformer`](xref:Microsoft.ML.ITransformer) or separate them thus creating a separate [`ITransformer`](xref:Microsoft.ML.ITransformer) for each.</span></span>

## <a name="save-a-model-locally"></a><span data-ttu-id="15e4b-113">Místní uložení modelu</span><span class="sxs-lookup"><span data-stu-id="15e4b-113">Save a model locally</span></span>

<span data-ttu-id="15e4b-114">Při ukládání modelu potřebujete dvě věci:</span><span class="sxs-lookup"><span data-stu-id="15e4b-114">When saving a model you need two things:</span></span>

1. <span data-ttu-id="15e4b-115">Model. [`ITransformer`](xref:Microsoft.ML.ITransformer)</span><span class="sxs-lookup"><span data-stu-id="15e4b-115">The [`ITransformer`](xref:Microsoft.ML.ITransformer) of the model.</span></span>
2. <span data-ttu-id="15e4b-116">Očekávaný [`DataViewSchema`](xref:Microsoft.ML.DataViewSchema) vstup [`ITransformer`](xref:Microsoft.ML.ITransformer).</span><span class="sxs-lookup"><span data-stu-id="15e4b-116">The [`DataViewSchema`](xref:Microsoft.ML.DataViewSchema) of the [`ITransformer`](xref:Microsoft.ML.ITransformer)'s expected input.</span></span>

<span data-ttu-id="15e4b-117">Po trénování [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) modelu použijte metodu k uložení `model.zip` trénovaného modelu do souboru volaného pomocí `DataViewSchema` vstupních dat.</span><span class="sxs-lookup"><span data-stu-id="15e4b-117">After training the model, use the [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) method to save the trained model to a file called `model.zip` using the `DataViewSchema` of the input data.</span></span>

```csharp
// Save Trained Model
mlContext.Model.Save(trainedModel, data.Schema, "model.zip");
```

## <a name="load-a-model-stored-locally"></a><span data-ttu-id="15e4b-118">Načtení modelu uloženého místně</span><span class="sxs-lookup"><span data-stu-id="15e4b-118">Load a model stored locally</span></span>

<span data-ttu-id="15e4b-119">Modely uložené lokálně lze použít v jiných `ASP.NET Core` `Serverless Web Applications`procesech nebo aplikacích, jako je a .</span><span class="sxs-lookup"><span data-stu-id="15e4b-119">Models stored locally can be used in other processes or applications like `ASP.NET Core` and `Serverless Web Applications`.</span></span> <span data-ttu-id="15e4b-120">Další informace najdete [v článku Použití ML.NET ve webovém rozhraní API](./serve-model-web-api-ml-net.md) a nasazení ML.NET článku s postupy webové aplikace Web App bez [serveru.](./serve-model-serverless-azure-functions-ml-net.md)</span><span class="sxs-lookup"><span data-stu-id="15e4b-120">See [Use ML.NET in Web API](./serve-model-web-api-ml-net.md) and [Deploy ML.NET Serverless Web App](./serve-model-serverless-azure-functions-ml-net.md) how-to articles to learn more.</span></span>

<span data-ttu-id="15e4b-121">V samostatné aplikaci nebo [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) procesu použijte metodu spolu s cestou k souboru, abyste získali trénovaný model do aplikace.</span><span class="sxs-lookup"><span data-stu-id="15e4b-121">In a separate application or process, use the [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) method along with the file path to get the trained model into your application.</span></span>

```csharp
//Define DataViewSchema for data preparation pipeline and trained model
DataViewSchema modelSchema;

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```

## <a name="load-a-model-stored-remotely"></a><span data-ttu-id="15e4b-122">Načtení modelu uloženého na dálku</span><span class="sxs-lookup"><span data-stu-id="15e4b-122">Load a model stored remotely</span></span>

<span data-ttu-id="15e4b-123">Chcete-li načíst kanály pro přípravu dat a [`Stream`](xref:System.IO.Stream) modely uložené ve vzdáleném umístění do aplikace, použijte místo cesty k souboru v metodě. [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*)</span><span class="sxs-lookup"><span data-stu-id="15e4b-123">To load data preparation pipelines and models stored in a remote location into your application, use a [`Stream`](xref:System.IO.Stream) instead of a file path in the [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) method.</span></span>

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

## <a name="working-with-separate-data-preparation-and-model-pipelines"></a><span data-ttu-id="15e4b-124">Práce se samostatnými datovými přípravami a kanály modelů</span><span class="sxs-lookup"><span data-stu-id="15e4b-124">Working with separate data preparation and model pipelines</span></span>

> [!NOTE]
> <span data-ttu-id="15e4b-125">Práce se samostatnými kanály pro přípravu dat a modelškolení je volitelná.</span><span class="sxs-lookup"><span data-stu-id="15e4b-125">Working with separate data preparation and model training pipelines is optional.</span></span> <span data-ttu-id="15e4b-126">Oddělení potrubí usnadňuje kontrolu naučených parametrů modelu.</span><span class="sxs-lookup"><span data-stu-id="15e4b-126">Separation of pipelines makes it easier to inspect the learned model parameters.</span></span> <span data-ttu-id="15e4b-127">Pro předpovědi je jednodušší uložit a načíst jeden kanál, který zahrnuje operace přípravy dat a model školení.</span><span class="sxs-lookup"><span data-stu-id="15e4b-127">For predictions, it's easier to save and load a single pipeline that includes the data preparation and model training operations.</span></span>

<span data-ttu-id="15e4b-128">Při práci se samostatnými kanály a modely pro přípravu dat platí stejný proces jako jednotlivé kanály; s výjimkou nyní musí být oba kanály uloženy a načteny současně.</span><span class="sxs-lookup"><span data-stu-id="15e4b-128">When working with separate data preparation pipelines and models, the same process as single pipelines applies; except now both pipelines need to be saved and loaded simultaneously.</span></span>

<span data-ttu-id="15e4b-129">Vzhledem k tomu, samostatná příprava dat a model školení potrubí:</span><span class="sxs-lookup"><span data-stu-id="15e4b-129">Given separate data preparation and model training pipelines:</span></span>

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

### <a name="save-data-preparation-pipeline-and-trained-model"></a><span data-ttu-id="15e4b-130">Uložení kanálu pro přípravu dat a trénovaného modelu</span><span class="sxs-lookup"><span data-stu-id="15e4b-130">Save data preparation pipeline and trained model</span></span>

<span data-ttu-id="15e4b-131">Chcete-li uložit kanál pro přípravu dat i trénovaný model, použijte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="15e4b-131">To save both the data preparation pipeline and trained model, use the following commands:</span></span>

```csharp
// Save Data Prep transformer
mlContext.Model.Save(dataPrepTransformer, data.Schema, "data_preparation_pipeline.zip");

// Save Trained Model
mlContext.Model.Save(trainedModel, transformedData.Schema, "model.zip");
```

### <a name="load-data-preparation-pipeline-and-trained-model"></a><span data-ttu-id="15e4b-132">Načtení kanálu pro přípravu dat a trénovaného modelu</span><span class="sxs-lookup"><span data-stu-id="15e4b-132">Load data preparation pipeline and trained model</span></span>

<span data-ttu-id="15e4b-133">V samostatném procesu nebo aplikaci načtěte kanál přípravy dat a trénovaný model současně následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="15e4b-133">In a separate process or application, load the data preparation pipeline and trained model simultaneously as follows:</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define data preparation and trained model schemas
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline and trained model
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip",out dataPrepPipelineSchema);
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```
