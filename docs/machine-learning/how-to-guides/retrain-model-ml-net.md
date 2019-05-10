---
title: Znovu trénování modelu
description: Zjistěte, jak programovém přeučení modelů v ML.NET
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 552698c02a7846db588822fa68d094dece160ea0
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063549"
---
# <a name="re-train-a-model"></a><span data-ttu-id="c5633-103">Znovu trénování modelu</span><span class="sxs-lookup"><span data-stu-id="c5633-103">Re-train a model</span></span>

<span data-ttu-id="c5633-104">Zjistěte, jak přeučování v ML.NET model strojového učení.</span><span class="sxs-lookup"><span data-stu-id="c5633-104">Learn how to retrain a machine learning model in ML.NET.</span></span>

<span data-ttu-id="c5633-105">Celém světě a data kolem něj změnit konstantní tempem.</span><span class="sxs-lookup"><span data-stu-id="c5633-105">The world and the data around it change at a constant pace.</span></span> <span data-ttu-id="c5633-106">Modely proto nutné změnit a aktualizovat také.</span><span class="sxs-lookup"><span data-stu-id="c5633-106">As such, models need to change and update as well.</span></span> <span data-ttu-id="c5633-107">ML.NET poskytuje funkce pro znovu trénovací modely s využitím zjistili parametry modelu jako výchozí bod k průběžně sestavení na předchozí zkušenosti a nikoli pokaždé, když vytváříte od začátku.</span><span class="sxs-lookup"><span data-stu-id="c5633-107">ML.NET provides functionality for re-training models using learned model parameters as a starting point to continually build on previous experience rather than starting from scratch every time.</span></span>  

<span data-ttu-id="c5633-108">Tyto algoritmy jsou znovu trainable v ML.NET:</span><span class="sxs-lookup"><span data-stu-id="c5633-108">The following algorithms are re-trainable in ML.NET:</span></span>

- [<span data-ttu-id="c5633-109">AveragedPerceptronTrainer</span><span class="sxs-lookup"><span data-stu-id="c5633-109">AveragedPerceptronTrainer</span></span>](xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer)
- [<span data-ttu-id="c5633-110">FieldAwareFactorizationMachineTrainer</span><span class="sxs-lookup"><span data-stu-id="c5633-110">FieldAwareFactorizationMachineTrainer</span></span>](xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer)
- [<span data-ttu-id="c5633-111">LbfgsLogisticRegressionBinaryTrainer</span><span class="sxs-lookup"><span data-stu-id="c5633-111">LbfgsLogisticRegressionBinaryTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer)
- [<span data-ttu-id="c5633-112">LbfgsMaximumEntropyMulticlassTrainer</span><span class="sxs-lookup"><span data-stu-id="c5633-112">LbfgsMaximumEntropyMulticlassTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer)
- [<span data-ttu-id="c5633-113">LbfgsPoissonRegressionTrainer</span><span class="sxs-lookup"><span data-stu-id="c5633-113">LbfgsPoissonRegressionTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer)
- [<span data-ttu-id="c5633-114">LinearSvmTrainer</span><span class="sxs-lookup"><span data-stu-id="c5633-114">LinearSvmTrainer</span></span>](xref:Microsoft.ML.Trainers.LinearSvmTrainer)
- [<span data-ttu-id="c5633-115">OnlineGradientDescentTrainer</span><span class="sxs-lookup"><span data-stu-id="c5633-115">OnlineGradientDescentTrainer</span></span>](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer)
- [<span data-ttu-id="c5633-116">SgdCalibratedTrainer</span><span class="sxs-lookup"><span data-stu-id="c5633-116">SgdCalibratedTrainer</span></span>](xref:Microsoft.ML.Trainers.SgdCalibratedTrainer)
- [<span data-ttu-id="c5633-117">SgdNonCalibratedTrainer</span><span class="sxs-lookup"><span data-stu-id="c5633-117">SgdNonCalibratedTrainer</span></span>](xref:Microsoft.ML.Trainers.SgdNonCalibratedTrainer)
- [<span data-ttu-id="c5633-118">SymbolicSgdLogisticRegressionBinaryTrainer</span><span class="sxs-lookup"><span data-stu-id="c5633-118">SymbolicSgdLogisticRegressionBinaryTrainer</span></span>](xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer)

## <a name="load-pre-trained-model"></a><span data-ttu-id="c5633-119">Načíst předem vytrénovaných model</span><span class="sxs-lookup"><span data-stu-id="c5633-119">Load pre-trained model</span></span>

<span data-ttu-id="c5633-120">Nejdřív načtěte předem natrénovaných modelů do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="c5633-120">First, load the pre-trained model into your application.</span></span> <span data-ttu-id="c5633-121">Další informace o načítání trénovacích kanálů a modely, najdete v článku související [článek](./consuming-model-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="c5633-121">To learn more about loading training pipelines and models, see the related [how-to article](./consuming-model-ml-net.md).</span></span>

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

## <a name="extract-pre-trained-model-parameters"></a><span data-ttu-id="c5633-122">Extrahovat parametry předem vytrénovaných modelu</span><span class="sxs-lookup"><span data-stu-id="c5633-122">Extract pre-trained model parameters</span></span>

<span data-ttu-id="c5633-123">Po načtení modelu extrahovat parametry zjištěná modelu díky přístupu [ `Model` ](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) vlastnost předem natrénovaných modelů.</span><span class="sxs-lookup"><span data-stu-id="c5633-123">Once the model is loaded, extract the learned model parameters by accessing the [`Model`](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) property of the pre-trained model.</span></span> <span data-ttu-id="c5633-124">Předem vytrénovaných model se trénuje pomocí trénování modelu lineární regrese [ `OnlineGradientDescentTrainer` ](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) vytváří[ `RegressionPredictionTransformer` ](xref:Microsoft.ML.Data.RegressionPredictionTransformer`1) , který vypíše [ `LinearRegressionModelParameters` ](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters).</span><span class="sxs-lookup"><span data-stu-id="c5633-124">The pre-trained model was trained using the linear regression model [`OnlineGradientDescentTrainer`](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) which creates a[`RegressionPredictionTransformer`](xref:Microsoft.ML.Data.RegressionPredictionTransformer`1) that outputs [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters).</span></span> <span data-ttu-id="c5633-125">Tyto parametry modelu lineární regrese obsahovat zjištěná posun a váhy nebo koeficienty modelu.</span><span class="sxs-lookup"><span data-stu-id="c5633-125">These linear regression model parameters contain the learned bias and weights or coefficients of the model.</span></span> <span data-ttu-id="c5633-126">Tyto hodnoty se použije jako výchozí bod pro nové znovu trénovaného modelu.</span><span class="sxs-lookup"><span data-stu-id="c5633-126">These values will be used as a starting point for the new re-trained model.</span></span>

```csharp
// Extract trained model parameters
LinearRegressionModelParameters originalModelParameters = 
    ((ISingleFeaturePredictionTransformer<object>)trainedModel).Model as LinearRegressionModelParameters;
```

## <a name="re-train-model"></a><span data-ttu-id="c5633-127">Znovu trénování modelu</span><span class="sxs-lookup"><span data-stu-id="c5633-127">Re-train model</span></span>

<span data-ttu-id="c5633-128">Proces přetrénování modelu se nijak neliší od u trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="c5633-128">The process for retraining a model is no different than that of training a model.</span></span> <span data-ttu-id="c5633-129">Jediným rozdílem je, [ `Fit` ](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*) metoda kromě dat taky přijímá jako vstup původní zjistili parametry modelu a použije je jako počáteční bod v procesu znovu školení.</span><span class="sxs-lookup"><span data-stu-id="c5633-129">The only difference is, the [`Fit`](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*) method in addition to the data also takes as input the original learned model parameters and uses them as a starting point in the re-training process.</span></span>  

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

## <a name="compare-model-parameters"></a><span data-ttu-id="c5633-130">Porovnání parametry modelu</span><span class="sxs-lookup"><span data-stu-id="c5633-130">Compare model parameters</span></span>

<span data-ttu-id="c5633-131">Jak poznáte, pokud znovu školení doopravdy stalo?</span><span class="sxs-lookup"><span data-stu-id="c5633-131">How do you know if re-training actually happened?</span></span> <span data-ttu-id="c5633-132">Jedním ze způsobů je porovnat, zda parametry znovu trénovaného modelu se můžou lišit od těch, které původní model.</span><span class="sxs-lookup"><span data-stu-id="c5633-132">One way would be to compare whether the re-trained model's parameters are different than those of the original model.</span></span> <span data-ttu-id="c5633-133">Následující ukázka kódu porovná původní proti váhy znovu trénovaného modelu a vypíše do konzoly.</span><span class="sxs-lookup"><span data-stu-id="c5633-133">The code sample below compares the original against the re-trained model weights and outputs them to the console.</span></span>

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

<span data-ttu-id="c5633-134">Následující tabulka ukazuje, jak může vypadat výstup.</span><span class="sxs-lookup"><span data-stu-id="c5633-134">The table below shows what the output might look like.</span></span> 

|<span data-ttu-id="c5633-135">Původní</span><span class="sxs-lookup"><span data-stu-id="c5633-135">Original</span></span> | <span data-ttu-id="c5633-136">Retrained</span><span class="sxs-lookup"><span data-stu-id="c5633-136">Retrained</span></span> | <span data-ttu-id="c5633-137">Rozdíl</span><span class="sxs-lookup"><span data-stu-id="c5633-137">Difference</span></span> |
|---|---|---|
| <span data-ttu-id="c5633-138">33039.86</span><span class="sxs-lookup"><span data-stu-id="c5633-138">33039.86</span></span> | <span data-ttu-id="c5633-139">56293.76</span><span class="sxs-lookup"><span data-stu-id="c5633-139">56293.76</span></span> | <span data-ttu-id="c5633-140">-23253.9</span><span class="sxs-lookup"><span data-stu-id="c5633-140">-23253.9</span></span> |
| <span data-ttu-id="c5633-141">29099.14</span><span class="sxs-lookup"><span data-stu-id="c5633-141">29099.14</span></span> | <span data-ttu-id="c5633-142">49586.03</span><span class="sxs-lookup"><span data-stu-id="c5633-142">49586.03</span></span> | <span data-ttu-id="c5633-143">-20486.89</span><span class="sxs-lookup"><span data-stu-id="c5633-143">-20486.89</span></span> |
| <span data-ttu-id="c5633-144">28938.38</span><span class="sxs-lookup"><span data-stu-id="c5633-144">28938.38</span></span> | <span data-ttu-id="c5633-145">48609.23</span><span class="sxs-lookup"><span data-stu-id="c5633-145">48609.23</span></span> | <span data-ttu-id="c5633-146">-19670.85</span><span class="sxs-lookup"><span data-stu-id="c5633-146">-19670.85</span></span> |
| <span data-ttu-id="c5633-147">30484.02</span><span class="sxs-lookup"><span data-stu-id="c5633-147">30484.02</span></span> | <span data-ttu-id="c5633-148">53745.43</span><span class="sxs-lookup"><span data-stu-id="c5633-148">53745.43</span></span> | <span data-ttu-id="c5633-149">-23261.41</span><span class="sxs-lookup"><span data-stu-id="c5633-149">-23261.41</span></span> |
