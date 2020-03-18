---
title: Opakované trénování modelu
description: Přečtěte si, jak přeškolit model v ML.NET
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 735782a4a0877a917b6e1885f009aa49d834170f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73976967"
---
# <a name="re-train-a-model"></a><span data-ttu-id="9e1c2-103">Opakované trénování modelu</span><span class="sxs-lookup"><span data-stu-id="9e1c2-103">Re-train a model</span></span>

<span data-ttu-id="9e1c2-104">Přečtěte si, jak přeškolit model strojového učení v ML.NET.</span><span class="sxs-lookup"><span data-stu-id="9e1c2-104">Learn how to retrain a machine learning model in ML.NET.</span></span>

<span data-ttu-id="9e1c2-105">Svět a data kolem něj se mění konstantním tempem.</span><span class="sxs-lookup"><span data-stu-id="9e1c2-105">The world and the data around it change at a constant pace.</span></span> <span data-ttu-id="9e1c2-106">Jako takové modely je třeba změnit a aktualizovat také.</span><span class="sxs-lookup"><span data-stu-id="9e1c2-106">As such, models need to change and update as well.</span></span> <span data-ttu-id="9e1c2-107">ML.NET poskytuje funkce pro re-training modely pomocí naučené parametry modelu jako výchozí bod neustále stavět na předchozí zkušenosti, spíše než od začátku pokaždé.</span><span class="sxs-lookup"><span data-stu-id="9e1c2-107">ML.NET provides functionality for re-training models using learned model parameters as a starting point to continually build on previous experience rather than starting from scratch every time.</span></span>

<span data-ttu-id="9e1c2-108">Následující algoritmy jsou re-trainable v ML.NET:</span><span class="sxs-lookup"><span data-stu-id="9e1c2-108">The following algorithms are re-trainable in ML.NET:</span></span>

- [<span data-ttu-id="9e1c2-109">AveragedPerceptronTrainer</span><span class="sxs-lookup"><span data-stu-id="9e1c2-109">AveragedPerceptronTrainer</span></span>](xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer)
- [<span data-ttu-id="9e1c2-110">FieldAwareFactorizationMachineTrainer</span><span class="sxs-lookup"><span data-stu-id="9e1c2-110">FieldAwareFactorizationMachineTrainer</span></span>](xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer)
- [<span data-ttu-id="9e1c2-111">LbfgsLogisticRegressionBinaryTrainer</span><span class="sxs-lookup"><span data-stu-id="9e1c2-111">LbfgsLogisticRegressionBinaryTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer)
- [<span data-ttu-id="9e1c2-112">LbfgsMaximumEntropyMulticlassTrainer</span><span class="sxs-lookup"><span data-stu-id="9e1c2-112">LbfgsMaximumEntropyMulticlassTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer)
- [<span data-ttu-id="9e1c2-113">LbfgsPoissonRegressionTrainer</span><span class="sxs-lookup"><span data-stu-id="9e1c2-113">LbfgsPoissonRegressionTrainer</span></span>](xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer)
- [<span data-ttu-id="9e1c2-114">LineárníSvmTrainer</span><span class="sxs-lookup"><span data-stu-id="9e1c2-114">LinearSvmTrainer</span></span>](xref:Microsoft.ML.Trainers.LinearSvmTrainer)
- [<span data-ttu-id="9e1c2-115">OnlineGradientDescentTrainer</span><span class="sxs-lookup"><span data-stu-id="9e1c2-115">OnlineGradientDescentTrainer</span></span>](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer)
- [<span data-ttu-id="9e1c2-116">SgdCalibratedTrainer</span><span class="sxs-lookup"><span data-stu-id="9e1c2-116">SgdCalibratedTrainer</span></span>](xref:Microsoft.ML.Trainers.SgdCalibratedTrainer)
- [<span data-ttu-id="9e1c2-117">SgdNonCalibratedTrainer</span><span class="sxs-lookup"><span data-stu-id="9e1c2-117">SgdNonCalibratedTrainer</span></span>](xref:Microsoft.ML.Trainers.SgdNonCalibratedTrainer)
- [<span data-ttu-id="9e1c2-118">SymbolickýSgdLogisticRegressionBinaryTrainer</span><span class="sxs-lookup"><span data-stu-id="9e1c2-118">SymbolicSgdLogisticRegressionBinaryTrainer</span></span>](xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer)

## <a name="load-pre-trained-model"></a><span data-ttu-id="9e1c2-119">Načíst předem trénovaný model</span><span class="sxs-lookup"><span data-stu-id="9e1c2-119">Load pre-trained model</span></span>

<span data-ttu-id="9e1c2-120">Nejprve načtěte předem trénovaný model do aplikace.</span><span class="sxs-lookup"><span data-stu-id="9e1c2-120">First, load the pre-trained model into your application.</span></span> <span data-ttu-id="9e1c2-121">Další informace o načítání trénovacích kanálů a modelů najdete v [tématu Uložení a načtení trénovaného modelu](save-load-machine-learning-models-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="9e1c2-121">To learn more about loading training pipelines and models, see [Save and load a trained model](save-load-machine-learning-models-ml-net.md).</span></span>

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

## <a name="extract-pre-trained-model-parameters"></a><span data-ttu-id="9e1c2-122">Extrahovat předem vycvičené parametry modelu</span><span class="sxs-lookup"><span data-stu-id="9e1c2-122">Extract pre-trained model parameters</span></span>

<span data-ttu-id="9e1c2-123">Jakmile je model načten, extrahujte naučené parametry modelu přístupem k vlastnosti [`Model`](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) předem trénovaného modelu.</span><span class="sxs-lookup"><span data-stu-id="9e1c2-123">Once the model is loaded, extract the learned model parameters by accessing the [`Model`](xref:Microsoft.ML.Data.PredictionTransformerBase`1.Model*) property of the pre-trained model.</span></span> <span data-ttu-id="9e1c2-124">Předem trénovaný model byl trénován [`OnlineGradientDescentTrainer`](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) pomocí[`RegressionPredictionTransformer`](xref:Microsoft.ML.Data.RegressionPredictionTransformer%601) lineárního [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters)regresního modelu, který vytváří výstupy .</span><span class="sxs-lookup"><span data-stu-id="9e1c2-124">The pre-trained model was trained using the linear regression model [`OnlineGradientDescentTrainer`](xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer) which creates a[`RegressionPredictionTransformer`](xref:Microsoft.ML.Data.RegressionPredictionTransformer%601) that outputs [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters).</span></span> <span data-ttu-id="9e1c2-125">Tyto lineární regresní modelparametry obsahují naučené zkreslení a váhy nebo koeficienty modelu.</span><span class="sxs-lookup"><span data-stu-id="9e1c2-125">These linear regression model parameters contain the learned bias and weights or coefficients of the model.</span></span> <span data-ttu-id="9e1c2-126">Tyto hodnoty budou použity jako výchozí bod pro nový přetrénovaný model.</span><span class="sxs-lookup"><span data-stu-id="9e1c2-126">These values will be used as a starting point for the new re-trained model.</span></span>

```csharp
// Extract trained model parameters
LinearRegressionModelParameters originalModelParameters =
    ((ISingleFeaturePredictionTransformer<object>)trainedModel).Model as LinearRegressionModelParameters;
```

## <a name="re-train-model"></a><span data-ttu-id="9e1c2-127">Přetáčí model</span><span class="sxs-lookup"><span data-stu-id="9e1c2-127">Re-train model</span></span>

<span data-ttu-id="9e1c2-128">Proces rekvalifikace modelu se nijak neliší od procesu trénování modelu.</span><span class="sxs-lookup"><span data-stu-id="9e1c2-128">The process for retraining a model is no different than that of training a model.</span></span> <span data-ttu-id="9e1c2-129">Jediným rozdílem [`Fit`](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*) je, že metoda kromě dat také bere jako vstup původní naučené parametry modelu a používá je jako výchozí bod v procesu re-training.</span><span class="sxs-lookup"><span data-stu-id="9e1c2-129">The only difference is, the [`Fit`](xref:Microsoft.ML.Trainers.OnlineLinearTrainer`2.Fit*) method in addition to the data also takes as input the original learned model parameters and uses them as a starting point in the re-training process.</span></span>

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

## <a name="compare-model-parameters"></a><span data-ttu-id="9e1c2-130">Porovnání parametrů modelu</span><span class="sxs-lookup"><span data-stu-id="9e1c2-130">Compare model parameters</span></span>

<span data-ttu-id="9e1c2-131">Jak poznáš, že k retréninku skutečně došlo?</span><span class="sxs-lookup"><span data-stu-id="9e1c2-131">How do you know if re-training actually happened?</span></span> <span data-ttu-id="9e1c2-132">Jedním ze způsobů by bylo porovnat, zda re-trained model parametry se liší od těch původního modelu.</span><span class="sxs-lookup"><span data-stu-id="9e1c2-132">One way would be to compare whether the re-trained model's parameters are different than those of the original model.</span></span> <span data-ttu-id="9e1c2-133">Ukázka kódu níže porovná originál s přetrénované model váhy a výstupy je do konzoly.</span><span class="sxs-lookup"><span data-stu-id="9e1c2-133">The code sample below compares the original against the re-trained model weights and outputs them to the console.</span></span>

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

<span data-ttu-id="9e1c2-134">V následující tabulce je uvedeno, jak může výstup vypadat.</span><span class="sxs-lookup"><span data-stu-id="9e1c2-134">The table below shows what the output might look like.</span></span>

|<span data-ttu-id="9e1c2-135">Původní</span><span class="sxs-lookup"><span data-stu-id="9e1c2-135">Original</span></span> | <span data-ttu-id="9e1c2-136">Přeškolená</span><span class="sxs-lookup"><span data-stu-id="9e1c2-136">Retrained</span></span> | <span data-ttu-id="9e1c2-137">Rozdíl</span><span class="sxs-lookup"><span data-stu-id="9e1c2-137">Difference</span></span> |
|---|---|---|
| <span data-ttu-id="9e1c2-138">33039.86</span><span class="sxs-lookup"><span data-stu-id="9e1c2-138">33039.86</span></span> | <span data-ttu-id="9e1c2-139">56293.76</span><span class="sxs-lookup"><span data-stu-id="9e1c2-139">56293.76</span></span> | <span data-ttu-id="9e1c2-140">-23253.9</span><span class="sxs-lookup"><span data-stu-id="9e1c2-140">-23253.9</span></span> |
| <span data-ttu-id="9e1c2-141">29099.14</span><span class="sxs-lookup"><span data-stu-id="9e1c2-141">29099.14</span></span> | <span data-ttu-id="9e1c2-142">49586.03</span><span class="sxs-lookup"><span data-stu-id="9e1c2-142">49586.03</span></span> | <span data-ttu-id="9e1c2-143">-20486.89</span><span class="sxs-lookup"><span data-stu-id="9e1c2-143">-20486.89</span></span> |
| <span data-ttu-id="9e1c2-144">28938.38</span><span class="sxs-lookup"><span data-stu-id="9e1c2-144">28938.38</span></span> | <span data-ttu-id="9e1c2-145">48609.23</span><span class="sxs-lookup"><span data-stu-id="9e1c2-145">48609.23</span></span> | <span data-ttu-id="9e1c2-146">-19670.85</span><span class="sxs-lookup"><span data-stu-id="9e1c2-146">-19670.85</span></span> |
| <span data-ttu-id="9e1c2-147">30484.02</span><span class="sxs-lookup"><span data-stu-id="9e1c2-147">30484.02</span></span> | <span data-ttu-id="9e1c2-148">53745.43</span><span class="sxs-lookup"><span data-stu-id="9e1c2-148">53745.43</span></span> | <span data-ttu-id="9e1c2-149">-23261.41</span><span class="sxs-lookup"><span data-stu-id="9e1c2-149">-23261.41</span></span> |
