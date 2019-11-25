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
# <a name="save-and-load-trained-models"></a><span data-ttu-id="fb600-103">Ukládání a načítání vycvičených modelů</span><span class="sxs-lookup"><span data-stu-id="fb600-103">Save and load trained models</span></span>

<span data-ttu-id="fb600-104">Naučte se, jak ukládat a načítat do vaší aplikace školený modely.</span><span class="sxs-lookup"><span data-stu-id="fb600-104">Learn how to save and load trained models in your application.</span></span>

<span data-ttu-id="fb600-105">V průběhu procesu sestavování modelu je model umístěn v paměti a je přístupný v rámci životního cyklu aplikace.</span><span class="sxs-lookup"><span data-stu-id="fb600-105">Throughout the model building process, a model lives in memory and is accessible throughout the application's lifecycle.</span></span> <span data-ttu-id="fb600-106">Pokud se ale aplikace zastaví, pokud se model neuloží místně nebo vzdáleně, už není přístupný.</span><span class="sxs-lookup"><span data-stu-id="fb600-106">However, once the application stops running, if the model is not saved somewhere locally or remotely, it's no longer accessible.</span></span> <span data-ttu-id="fb600-107">Modely jsou obvykle používány v určitém bodě po školení v jiných aplikacích, a to buď pro odvození nebo opětovné školení.</span><span class="sxs-lookup"><span data-stu-id="fb600-107">Typically models are used at some point after training in other applications either for inference or re-training.</span></span> <span data-ttu-id="fb600-108">Proto je důležité model Uložit.</span><span class="sxs-lookup"><span data-stu-id="fb600-108">Therefore, it's important to store the model.</span></span> <span data-ttu-id="fb600-109">Pomocí kroků popsaných v následujících částech tohoto dokumentu uložte a načtěte modely při použití kanálů pro přípravu a školicí kanály pro přípravu dat, jako je tomu níže.</span><span class="sxs-lookup"><span data-stu-id="fb600-109">Save and load models using the steps described in subsequent sections of this document when using data preparation and model training pipelines like the one detailed below.</span></span> <span data-ttu-id="fb600-110">I když tato ukázka používá model lineární regrese, stejný postup se vztahuje i na jiné algoritmy ML.NET.</span><span class="sxs-lookup"><span data-stu-id="fb600-110">Although this sample uses a linear regression model, the same process applies to other ML.NET algorithms.</span></span>

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

<span data-ttu-id="fb600-111">Vzhledem k tomu, že většina modelů a kanálů přípravy dat dědí ze stejné sady tříd, signatury metody Save a Load pro tyto komponenty jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="fb600-111">Because most models and data preparation pipelines inherit from the same set of classes, the save and load method signatures for these components is the same.</span></span> <span data-ttu-id="fb600-112">V závislosti na vašem případu použití můžete kombinovat kanál přípravy dat a model do jediného [`EstimatorChain`](xref:Microsoft.ML.Data.TransformerChain%601) , který by představoval výstup jednoho [`ITransformer`](xref:Microsoft.ML.ITransformer) nebo oddělit je tak, aby pro každý vytvořil samostatný [`ITransformer`](xref:Microsoft.ML.ITransformer) .</span><span class="sxs-lookup"><span data-stu-id="fb600-112">Depending on your use case, you can either combine the data preparation pipeline and model into a single [`EstimatorChain`](xref:Microsoft.ML.Data.TransformerChain%601) which would output a single [`ITransformer`](xref:Microsoft.ML.ITransformer) or separate them thus creating a separate [`ITransformer`](xref:Microsoft.ML.ITransformer) for each.</span></span>

## <a name="save-a-model-locally"></a><span data-ttu-id="fb600-113">Místní uložení modelu</span><span class="sxs-lookup"><span data-stu-id="fb600-113">Save a model locally</span></span>

<span data-ttu-id="fb600-114">Při ukládání modelu potřebujete dvě věci:</span><span class="sxs-lookup"><span data-stu-id="fb600-114">When saving a model you need two things:</span></span>

1. <span data-ttu-id="fb600-115">[`ITransformer`](xref:Microsoft.ML.ITransformer) modelu.</span><span class="sxs-lookup"><span data-stu-id="fb600-115">The [`ITransformer`](xref:Microsoft.ML.ITransformer) of the model.</span></span>
2. <span data-ttu-id="fb600-116">[`DataViewSchema`](xref:Microsoft.ML.DataViewSchema) očekávaného vstupu [`ITransformer`](xref:Microsoft.ML.ITransformer).</span><span class="sxs-lookup"><span data-stu-id="fb600-116">The [`DataViewSchema`](xref:Microsoft.ML.DataViewSchema) of the [`ITransformer`](xref:Microsoft.ML.ITransformer)'s expected input.</span></span>

<span data-ttu-id="fb600-117">Po školení modelu použijte metodu [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) k uložení proučeného modelu do souboru s názvem `model.zip` pomocí `DataViewSchema` vstupních dat.</span><span class="sxs-lookup"><span data-stu-id="fb600-117">After training the model, use the [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) method to save the trained model to a file called `model.zip` using the `DataViewSchema` of the input data.</span></span>

```csharp
// Save Trained Model
mlContext.Model.Save(trainedModel, data.Schema, "model.zip");
```

## <a name="load-a-model-stored-locally"></a><span data-ttu-id="fb600-118">Načtení modelu místně uloženého</span><span class="sxs-lookup"><span data-stu-id="fb600-118">Load a model stored locally</span></span>

<span data-ttu-id="fb600-119">Místně uložené modely lze použít v jiných procesech nebo aplikacích, jako jsou `ASP.NET Core` a `Serverless Web Applications`.</span><span class="sxs-lookup"><span data-stu-id="fb600-119">Models stored locally can be used in other processes or applications like `ASP.NET Core` and `Serverless Web Applications`.</span></span> <span data-ttu-id="fb600-120">Další informace najdete v článcích [použití ml.NET ve webovém rozhraní API](./serve-model-web-api-ml-net.md) a [nasazení ml.NET webových aplikací bez serveru](./serve-model-serverless-azure-functions-ml-net.md) .</span><span class="sxs-lookup"><span data-stu-id="fb600-120">See [Use ML.NET in Web API](./serve-model-web-api-ml-net.md) and [Deploy ML.NET Serverless Web App](./serve-model-serverless-azure-functions-ml-net.md) how-to articles to learn more.</span></span>

<span data-ttu-id="fb600-121">V samostatné aplikaci nebo procesu použijte metodu [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) společně s cestou k souboru, abyste získali vyškolený model do aplikace.</span><span class="sxs-lookup"><span data-stu-id="fb600-121">In a separate application or process, use the [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) method along with the file path to get the trained model into your application.</span></span>

```csharp
//Define DataViewSchema for data preparation pipeline and trained model
DataViewSchema modelSchema;

// Load trained model
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```

## <a name="load-a-model-stored-remotely"></a><span data-ttu-id="fb600-122">Načtení modelu uloženého vzdáleně</span><span class="sxs-lookup"><span data-stu-id="fb600-122">Load a model stored remotely</span></span>

<span data-ttu-id="fb600-123">Chcete-li načíst přípravné kanály a modely uložené ve vzdáleném umístění do vaší aplikace, použijte místo cesty k souboru v metodě [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) [`Stream`](xref:System.IO.Stream) .</span><span class="sxs-lookup"><span data-stu-id="fb600-123">To load data preparation pipelines and models stored in a remote location into your application, use a [`Stream`](xref:System.IO.Stream) instead of a file path in the [`Load`](xref:Microsoft.ML.ModelOperationsCatalog.Load*) method.</span></span>

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

## <a name="working-with-separate-data-preparation-and-model-pipelines"></a><span data-ttu-id="fb600-124">Práce s oddělenými kanály pro přípravu a modelování dat</span><span class="sxs-lookup"><span data-stu-id="fb600-124">Working with separate data preparation and model pipelines</span></span>

> [!NOTE]
> <span data-ttu-id="fb600-125">Práce s oddělenými kanály pro přípravu dat a výuku modelu je volitelná.</span><span class="sxs-lookup"><span data-stu-id="fb600-125">Working with separate data preparation and model training pipelines is optional.</span></span> <span data-ttu-id="fb600-126">Oddělení kanálů usnadňuje kontrolu zjištěných parametrů modelu.</span><span class="sxs-lookup"><span data-stu-id="fb600-126">Separation of pipelines makes it easier to inspect the learned model parameters.</span></span> <span data-ttu-id="fb600-127">V případě předpovědi je snazší Uložit a načíst jeden kanál, který obsahuje operace školení pro přípravu a modelování dat.</span><span class="sxs-lookup"><span data-stu-id="fb600-127">For predictions, it's easier to save and load a single pipeline that includes the data preparation and model training operations.</span></span>

<span data-ttu-id="fb600-128">Při práci se samostatnými kanály pro přípravu dat a modely se používá stejný postup jako u jednoho kanálu. s výjimkou toho je potřeba současně ukládat a načítat oba kanály.</span><span class="sxs-lookup"><span data-stu-id="fb600-128">When working with separate data preparation pipelines and models, the same process as single pipelines applies; except now both pipelines need to be saved and loaded simultaneously.</span></span>

<span data-ttu-id="fb600-129">Předané samostatné kanály pro přípravu a přípravu dat:</span><span class="sxs-lookup"><span data-stu-id="fb600-129">Given separate data preparation and model training pipelines:</span></span>

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

### <a name="save-data-preparation-pipeline-and-trained-model"></a><span data-ttu-id="fb600-130">Uložení kanálu přípravy dat a trained model</span><span class="sxs-lookup"><span data-stu-id="fb600-130">Save data preparation pipeline and trained model</span></span>

<span data-ttu-id="fb600-131">Pokud chcete uložit jak kanál pro přípravu dat, tak i školený model, použijte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="fb600-131">To save both the data preparation pipeline and trained model, use the following commands:</span></span>

```csharp
// Save Data Prep transformer
mlContext.Model.Save(dataPrepTransformer, data.Schema, "data_preparation_pipeline.zip");

// Save Trained Model
mlContext.Model.Save(trainedModel, transformedData.Schema, "model.zip");
```

### <a name="load-data-preparation-pipeline-and-trained-model"></a><span data-ttu-id="fb600-132">Načtení kanálu přípravy dat a trained model</span><span class="sxs-lookup"><span data-stu-id="fb600-132">Load data preparation pipeline and trained model</span></span>

<span data-ttu-id="fb600-133">V samostatném procesu nebo aplikaci načtěte následující kanál pro přípravu dat a školený model současně:</span><span class="sxs-lookup"><span data-stu-id="fb600-133">In a separate process or application, load the data preparation pipeline and trained model simultaneously as follows:</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

// Define data preparation and trained model schemas
DataViewSchema dataPrepPipelineSchema, modelSchema;

// Load data preparation pipeline and trained model
ITransformer dataPrepPipeline = mlContext.Model.Load("data_preparation_pipeline.zip",out dataPrepPipelineSchema);
ITransformer trainedModel = mlContext.Model.Load("model.zip", out modelSchema);
```
