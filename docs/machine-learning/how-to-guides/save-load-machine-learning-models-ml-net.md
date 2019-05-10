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
# <a name="save-and-load-trained-models"></a><span data-ttu-id="04599-103">Uložení a načtení trénované modely</span><span class="sxs-lookup"><span data-stu-id="04599-103">Save and load trained models</span></span>

<span data-ttu-id="04599-104">Zjistěte, jak uložit a načíst trénované modely ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="04599-104">Learn how to save and load trained models in your application.</span></span> 

<span data-ttu-id="04599-105">V průběhu procesu vytváření modelu model je umístěn v paměti a je dostupný v průběhu životního cyklu aplikace.</span><span class="sxs-lookup"><span data-stu-id="04599-105">Throughout the model building process, a model lives in memory and is accessible throughout the application's lifecycle.</span></span> <span data-ttu-id="04599-106">Po aplikaci se zastaví, pokud model není uložen někde místně nebo vzdáleně, je však již nebude dostupná.</span><span class="sxs-lookup"><span data-stu-id="04599-106">However, once the application stops running, if the model is not saved somewhere locally or remotely, it's no longer accessible.</span></span> <span data-ttu-id="04599-107">Modely se obvykle používají v určitém okamžiku po školení v jiných aplikacích, ať už pro odvození nebo znovu školení.</span><span class="sxs-lookup"><span data-stu-id="04599-107">Typically models are used at some point after training in other applications either for inference or re-training.</span></span> <span data-ttu-id="04599-108">Proto je důležité k ukládání modelu.</span><span class="sxs-lookup"><span data-stu-id="04599-108">Therefore, it's important to store the model.</span></span> <span data-ttu-id="04599-109">Uložení a načtení modelů pomocí kroků popsaných v dalších částech tohoto dokumentu, při použití přípravy dat a modelu trénovacích kanálů stejný, jako je podrobně popsaný níže.</span><span class="sxs-lookup"><span data-stu-id="04599-109">Save and load models using the steps described in subsequent sections of this document when using data preparation and model training pipelines like the one detailed below.</span></span> <span data-ttu-id="04599-110">I když tato ukázka používá model lineární regrese, stejný postup se vztahuje na jiné ML.NET algoritmy.</span><span class="sxs-lookup"><span data-stu-id="04599-110">Although this sample uses a linear regression model, the same process applies to other ML.NET algorithms.</span></span>

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

<span data-ttu-id="04599-111">Protože většina modely a data přípravy kanály dědit z stejná sada tříd, uložit a načíst podpisy metod pro tyto součásti je stejný.</span><span class="sxs-lookup"><span data-stu-id="04599-111">Because most models and data preparation pipelines inherit from the same set of classes, the save and load method signatures for these components is the same.</span></span> <span data-ttu-id="04599-112">V závislosti na vašemu případu použití, můžete buď kombinovat kanálu přípravy dat a modelu do jednoho [ `EstimatorChain` ](xref:Microsoft.ML.Data.TransformerChain%601) který by výstup jedné [ `ITransformer` ](xref:Microsoft.ML.ITransformer) nebo jim tak vytváření oddělení samostatné [ `ITransformer` ](xref:Microsoft.ML.ITransformer) pro každý.</span><span class="sxs-lookup"><span data-stu-id="04599-112">Depending on your use case, you can either combine the data preparation pipeline and model into a single [`EstimatorChain`](xref:Microsoft.ML.Data.TransformerChain%601) which would output a single [`ITransformer`](xref:Microsoft.ML.ITransformer) or separate them thus creating a separate [`ITransformer`](xref:Microsoft.ML.ITransformer) for each.</span></span> 

## <a name="save-a-model-locally"></a><span data-ttu-id="04599-113">Uložit model místně</span><span class="sxs-lookup"><span data-stu-id="04599-113">Save a model locally</span></span>

<span data-ttu-id="04599-114">Při ukládání modelu budete potřebovat dvě věci:</span><span class="sxs-lookup"><span data-stu-id="04599-114">When saving a model you need two things:</span></span>

1. <span data-ttu-id="04599-115">[ `ITransformer` ](xref:Microsoft.ML.ITransformer) Modelu.</span><span class="sxs-lookup"><span data-stu-id="04599-115">The [`ITransformer`](xref:Microsoft.ML.ITransformer) of the model.</span></span>
2. <span data-ttu-id="04599-116">[ `DataViewSchema` ](xref:Microsoft.ML.DataViewSchema) z [ `ITransformer` ](xref:Microsoft.ML.ITransformer)očekávaný vstup.</span><span class="sxs-lookup"><span data-stu-id="04599-116">The [`DataViewSchema`](xref:Microsoft.ML.DataViewSchema) of the [`ITransformer`](xref:Microsoft.ML.ITransformer)'s expected input.</span></span>

<span data-ttu-id="04599-117">Po trénování modelu, použijte [ `Save` ](xref:Microsoft.ML.ModelOperationsCatalog.Save*) volá metodu pro uložení naučeného modelu do souboru `model.zip` pomocí `DataViewSchema` vstupní data.</span><span class="sxs-lookup"><span data-stu-id="04599-117">After training the model, use the [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) method to save the trained model to a file called `model.zip` using the `DataViewSchema` of the input data.</span></span> 

```csharp
// Save Trained Model
mlContext.Model.Save(trainedModel, data.Schema, "model.zip");
```

## <a name="load-a-model-stored-locally"></a><span data-ttu-id="04599-118">Načtení modelu ukládají místně</span><span class="sxs-lookup"><span data-stu-id="04599-118">Load a model stored locally</span></span>

<span data-ttu-id="04599-119">Modely se ukládají místně se dá použít v jiných procesů nebo aplikace, jako je `ASP.NET Core` a `Serverless Web Applications`.</span><span class="sxs-lookup"><span data-stu-id="04599-119">Models stored locally can be used in other processes or applications like `ASP.NET Core` and `Serverless Web Applications`.</span></span> <span data-ttu-id="04599-120">Zobrazit [ML.NET použití v rozhraní Web API](./serve-model-web-api-ml-net.md) a [nasazení ML.NET bez serveru webové aplikace](./serve-model-serverless-azure-functions-ml-net.md) články s postupy pro další informace.</span><span class="sxs-lookup"><span data-stu-id="04599-120">See [Use ML.NET in Web API](./serve-model-web-api-ml-net.md) and [Deploy ML.NET Serverless Web App](./serve-model-serverless-azure-functions-ml-net.md) how-to articles to learn more.</span></span> 

<span data-ttu-id="04599-121">V samostatné aplikace nebo proces, použijte [ `Load` ](xref:Microsoft.ML.ModelOperationsCatalog.Load*) metoda spolu se cesta k souboru zobrazíte trénovaného modelu do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="04599-121">In a separate application or process, use the [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) method along with the file path to get the trained model into your application.</span></span>

```csharp
//Define DataViewSchema for data preparation pipeline and trained model
DataViewSchema modelSchema;

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```

## <a name="load-a-model-stored-remotely"></a><span data-ttu-id="04599-122">Načtení modelu vzdáleně uložen</span><span class="sxs-lookup"><span data-stu-id="04599-122">Load a model stored remotely</span></span>

<span data-ttu-id="04599-123">Chcete-li načíst kanálů přípravy dat a modely, které jsou uložené ve vzdáleném umístění do vaší aplikace, použijte [ `Stream` ](xref:System.IO.Stream) namísto cesty souboru v [ `Load` ](xref:Microsoft.ML.ModelOperationsCatalog.Load*) – metoda.</span><span class="sxs-lookup"><span data-stu-id="04599-123">To load data preparation pipelines and models stored in a remote location into your application, use a [`Stream`](xref:System.IO.Stream) instead of a file path in the [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) method.</span></span>

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

## <a name="working-with-separate-data-preparation-and-model-pipelines"></a><span data-ttu-id="04599-124">Práce s kanály modelu a samostatná data pro přípravu</span><span class="sxs-lookup"><span data-stu-id="04599-124">Working with separate data preparation and model pipelines</span></span>

> [!NOTE]
> <span data-ttu-id="04599-125">Práce s kanály trénování modelu a samostatná data pro přípravu je volitelné.</span><span class="sxs-lookup"><span data-stu-id="04599-125">Working with separate data preparation and model training pipelines is optional.</span></span> <span data-ttu-id="04599-126">Oddělení kanály usnadňuje Zkontrolujte parametry zjištěná modelu.</span><span class="sxs-lookup"><span data-stu-id="04599-126">Separation of pipelines makes it easier to inspect the learned model parameters.</span></span> <span data-ttu-id="04599-127">Pro predikcí je jednodušší pro uložení a načtení jeden kanál, který zahrnuje přípravy dat a operace trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="04599-127">For predictions, it's easier to save and load a single pipeline that includes the data preparation and model training operations.</span></span>

<span data-ttu-id="04599-128">Při práci s kanály samostatná data pro přípravu a modely, stejně jako jeden kanály platí; s výjimkou nyní obou kanálů je potřeba uložit a načíst současně.</span><span class="sxs-lookup"><span data-stu-id="04599-128">When working with separate data preparation pipelines and models, the same process as single pipelines applies; except now both pipelines need to be saved and loaded simultaneously.</span></span>

<span data-ttu-id="04599-129">Daný samostatná data pro přípravu a model trénovacích kanálů:</span><span class="sxs-lookup"><span data-stu-id="04599-129">Given separate data preparation and model training pipelines:</span></span>

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

### <a name="save-data-preparation-pipeline-and-trained-model"></a><span data-ttu-id="04599-130">Uložení kanálu přípravy dat a trénovaného modelu</span><span class="sxs-lookup"><span data-stu-id="04599-130">Save data preparation pipeline and trained model</span></span>

<span data-ttu-id="04599-131">Uložení kanálu přípravy dat i trénovaného modelu, použijte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="04599-131">To save both the data preparation pipeline and trained model, use the following commands:</span></span>

```csharp
// Save Data Prep transformer
mlContext.Model.Save(dataPrepTransformer, data.Schema, "data_preparation_pipeline.zip");

// Save Trained Model
mlContext.Model.Save(trainedModel, transformedData.Schema, "model.zip");
```

### <a name="load-data-preparation-pipeline-and-trained-model"></a><span data-ttu-id="04599-132">Načíst kanálu přípravy dat a trénovaného modelu</span><span class="sxs-lookup"><span data-stu-id="04599-132">Load data preparation pipeline and trained model</span></span> 

<span data-ttu-id="04599-133">V samostatném procesu nebo v aplikaci načtěte kanálu přípravy dat a trénovaného modelu současně následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="04599-133">In a separate process or application, load the data preparation pipeline and trained model simultaneously as follows:</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define data preparation and trained model schemas
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline and trained model
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip",out dataPrepPipelineSchema);
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```
