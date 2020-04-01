---
title: Trénování a vyhodnocení modelu
description: Zjistěte, jak vytvářet modely strojového učení, shromažďovat metriky a měřit výkon s ML.NET. Model strojového učení identifikuje vzory v rámci trénovacích dat, aby se předpovědi pomocí nových dat.
ms.date: 03/31/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 51499f2c0ece615a99740bd9b27f99d4b5ed1d01
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523857"
---
# <a name="train-and-evaluate-a-model"></a><span data-ttu-id="01671-104">Trénování a vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="01671-104">Train and evaluate a model</span></span>

<span data-ttu-id="01671-105">Zjistěte, jak vytvářet modely strojového učení, shromažďovat metriky a měřit výkon s ML.NET.</span><span class="sxs-lookup"><span data-stu-id="01671-105">Learn how to build machine learning models, collect metrics, and measure performance with ML.NET.</span></span> <span data-ttu-id="01671-106">I když tato ukázka trénuje regresní model, koncepty jsou použitelné ve většině ostatních algoritmů.</span><span class="sxs-lookup"><span data-stu-id="01671-106">Although this sample trains a regression model, the concepts are applicable throughout a majority of the other algorithms.</span></span>

## <a name="split-data-for-training-and-testing"></a><span data-ttu-id="01671-107">Rozdělení dat pro školení a testování</span><span class="sxs-lookup"><span data-stu-id="01671-107">Split data for training and testing</span></span>

<span data-ttu-id="01671-108">Cílem modelu strojového učení je identifikovat vzory v rámci trénovacích dat.</span><span class="sxs-lookup"><span data-stu-id="01671-108">The goal of a machine learning model is to identify patterns within training data.</span></span> <span data-ttu-id="01671-109">Tyto vzory se používají k předpovědi pomocí nových dat.</span><span class="sxs-lookup"><span data-stu-id="01671-109">These patterns are used to make predictions using new data.</span></span>

<span data-ttu-id="01671-110">Data mohou být modelována `HousingData`podle třídy, jako je .</span><span class="sxs-lookup"><span data-stu-id="01671-110">The data can be modeled by a class like `HousingData`.</span></span>

```csharp
public class HousingData
{
    [LoadColumn(0)]
    public float Size { get; set; }

    [LoadColumn(1, 3)]
    [VectorType(3)]
    public float[] HistoricalPrices { get; set; }

    [LoadColumn(4)]
    [ColumnName("Label")]
    public float CurrentPrice { get; set; }
}
```

<span data-ttu-id="01671-111">Vzhledem k následujícím údajům, které jsou načteny do . [`IDataView`](xref:Microsoft.ML.IDataView)</span><span class="sxs-lookup"><span data-stu-id="01671-111">Given the following data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

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
    },
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
```

<span data-ttu-id="01671-112">Pomocí [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) metody rozdělte data do vlakových a testovacích sad.</span><span class="sxs-lookup"><span data-stu-id="01671-112">Use the [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the data into train and test sets.</span></span> <span data-ttu-id="01671-113">Výsledkem [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) bude objekt, který [`IDataView`](xref:Microsoft.ML.IDataView) obsahuje dva členy, jeden pro vlakové sady a druhý pro testovací sadu.</span><span class="sxs-lookup"><span data-stu-id="01671-113">The result will be a [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) object which contains two [`IDataView`](xref:Microsoft.ML.IDataView) members, one for the train set and the other for the test set.</span></span> <span data-ttu-id="01671-114">Procento rozdělení dat je `testFraction` určeno parametrem.</span><span class="sxs-lookup"><span data-stu-id="01671-114">The data split percentage is determined by the `testFraction` parameter.</span></span> <span data-ttu-id="01671-115">Níže uvedený úryvek podrží 20 procent původních dat pro testovací sadu.</span><span class="sxs-lookup"><span data-stu-id="01671-115">The snippet below is holding out 20 percent of the original data for the test set.</span></span>

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a><span data-ttu-id="01671-116">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="01671-116">Prepare the data</span></span>

<span data-ttu-id="01671-117">Data musí být předem zpracovány před trénování modelu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="01671-117">The data needs to be pre-processed before training a machine learning model.</span></span> <span data-ttu-id="01671-118">Více informací o přípravě dat naleznete na článku s [návody k přípravě dat](prepare-data-ml-net.md) a na [`transforms page`](../resources/transforms.md).</span><span class="sxs-lookup"><span data-stu-id="01671-118">More information on data preparation can be found on the [data prep how-to article](prepare-data-ml-net.md) as well as the [`transforms page`](../resources/transforms.md).</span></span>

<span data-ttu-id="01671-119">ML.NET algoritmy mají omezení pro typy vstupních sloupců.</span><span class="sxs-lookup"><span data-stu-id="01671-119">ML.NET algorithms have constraints on input column types.</span></span> <span data-ttu-id="01671-120">Kromě toho výchozí hodnoty se používají pro vstupní a výstupní názvy sloupců, pokud nejsou zadány žádné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="01671-120">Additionally, default values are used for input and output column names when no values are specified.</span></span>

### <a name="working-with-expected-column-types"></a><span data-ttu-id="01671-121">Práce s očekávanými typy sloupců</span><span class="sxs-lookup"><span data-stu-id="01671-121">Working with expected column types</span></span>

<span data-ttu-id="01671-122">Algoritmy strojového učení v ML.NET očekávat plovoucí vektor známé velikosti jako vstup.</span><span class="sxs-lookup"><span data-stu-id="01671-122">The machine learning algorithms in ML.NET expect a float vector of known size as input.</span></span> <span data-ttu-id="01671-123">Použijte [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) atribut na datový model, pokud jsou všechna data již v číselném formátu a jsou určena ke zpracování společně (tj. obrazové body).</span><span class="sxs-lookup"><span data-stu-id="01671-123">Apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to your data model when all of the data is already in numerical format and is intended to be processed together (i.e. image pixels).</span></span>

<span data-ttu-id="01671-124">Pokud data nejsou všechna číselná a chcete použít různé transformace dat na každý [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) sloupec jednotlivě, použijte metodu po zpracování všech sloupců a zkombinujte všechny jednotlivé sloupce do jednoho vektoru prvku, který je výstupem do nového sloupce.</span><span class="sxs-lookup"><span data-stu-id="01671-124">If data is not all numerical and you want to apply different data transformations on each of the columns individually, use the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) method after all of the columns have been processed to combine all of the individual columns into a single feature vector that is output to a new column.</span></span>

<span data-ttu-id="01671-125">Následující úryvek kombinuje `Size` sloupce `HistoricalPrices` a do jednoho vektoru prvku, který `Features`je výstupem do nového sloupce s názvem .</span><span class="sxs-lookup"><span data-stu-id="01671-125">The following snippet combines the `Size` and `HistoricalPrices` columns into a single feature vector that is output to a new column called `Features`.</span></span> <span data-ttu-id="01671-126">Vzhledem k tomu, že [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) je rozdíl `Features` v měřítkách, se použije na sloupec normalizovat data.</span><span class="sxs-lookup"><span data-stu-id="01671-126">Because there is a difference in scales, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) is applied to the `Features` column to normalize the data.</span></span>

```csharp
// Define Data Prep Estimator
// 1. Concatenate Size and Historical into a single feature vector output to a new column called Features
// 2. Normalize Features vector
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", "Size", "HistoricalPrices")
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// Create data prep transformer
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(trainData);

// Apply transforms to training data
IDataView transformedTrainingData = dataPrepTransformer.Transform(trainData);
```

### <a name="working-with-default-column-names"></a><span data-ttu-id="01671-127">Práce s výchozími názvy sloupců</span><span class="sxs-lookup"><span data-stu-id="01671-127">Working with default column names</span></span>

<span data-ttu-id="01671-128">ML.NET algoritmy používají výchozí názvy sloupců, pokud nejsou zadány žádné.</span><span class="sxs-lookup"><span data-stu-id="01671-128">ML.NET algorithms use default column names when none are specified.</span></span> <span data-ttu-id="01671-129">Všechny školitelů `featureColumnName` mají parametr volaný pro vstupy algoritmu a v případě `labelColumnName`potřeby mají také parametr pro očekávanou hodnotu s názvem .</span><span class="sxs-lookup"><span data-stu-id="01671-129">All trainers have a parameter called `featureColumnName` for the inputs of the algorithm and when applicable they also have a parameter for the expected value called `labelColumnName`.</span></span> <span data-ttu-id="01671-130">Ve výchozím nastavení `Features` `Label` jsou tyto hodnoty a resp.</span><span class="sxs-lookup"><span data-stu-id="01671-130">By default those values are `Features` and `Label` respectively.</span></span>

<span data-ttu-id="01671-131">Pomocí [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) metody během předběžného zpracování k vytvoření `Features`nového sloupce s názvem , není nutné zadat název sloupce funkce v parametrech `IDataView`algoritmu, protože již existuje v předem zpracovaném .</span><span class="sxs-lookup"><span data-stu-id="01671-131">By using the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) method during pre-processing to create a new column called `Features`, there is no need to specify the feature column name in the parameters of the algorithm since it already exists in the pre-processed `IDataView`.</span></span> <span data-ttu-id="01671-132">Sloupec popisek `CurrentPrice`je , [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) ale vzhledem k tomu, že `CurrentPrice` atribut `Label` se používá v datovém modelu, ML.NET přejmenuje sloupec, na který odebere potřebu poskytnout `labelColumnName` parametr pro odhad algoritmu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="01671-132">The label column is `CurrentPrice`, but since the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute is used in the data model, ML.NET renames the `CurrentPrice` column to `Label` which removes the need to provide the `labelColumnName` parameter to the machine learning algorithm estimator.</span></span>

<span data-ttu-id="01671-133">Pokud nechcete používat výchozí názvy sloupců, předejte názvy sloupců prvku a popisku jako parametry při definování odhadu algoritmu strojového učení, jak ukazuje následující úryvek:</span><span class="sxs-lookup"><span data-stu-id="01671-133">If you don't want to use the default column names, pass in the names of the feature and label columns as parameters when defining the machine learning algorithm estimator as demonstrated by the subsequent snippet:</span></span>

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="caching-data"></a><span data-ttu-id="01671-134">Ukládání dat do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="01671-134">Caching data</span></span>

<span data-ttu-id="01671-135">Ve výchozím nastavení jsou data při zpracování líně načtena nebo streamována, což znamená, že školitelé mohou načíst data z disku a iterát ovat je vícekrát během tréninku.</span><span class="sxs-lookup"><span data-stu-id="01671-135">By default, when data is processed, it is lazily loaded or streamed which means that trainers may load the data from disk and iterate over it multiple times during training.</span></span> <span data-ttu-id="01671-136">Ukládání do mezipaměti se proto doporučuje pro datové sady, které se vejdou do paměti, aby se snížil počet načítání dat z disku.</span><span class="sxs-lookup"><span data-stu-id="01671-136">Therefore, caching is recommended for datasets that fit into memory to reduce the number of times data is loaded from disk.</span></span> <span data-ttu-id="01671-137">Ukládání do mezipaměti se [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) provádí [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A)jako součást pomocí .</span><span class="sxs-lookup"><span data-stu-id="01671-137">Caching is done as part of an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) by using [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A).</span></span>

<span data-ttu-id="01671-138">Doporučuje se používat [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A) před všemi trenéry v potrubí.</span><span class="sxs-lookup"><span data-stu-id="01671-138">It's recommended to use [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A) before any trainers in the pipeline.</span></span>

<span data-ttu-id="01671-139">Pomocí následujícího [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A) , [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) přidání před trenér ukládá výsledky předchozích odhadů pro pozdější použití trenérem.</span><span class="sxs-lookup"><span data-stu-id="01671-139">Using the following [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601), adding [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A) before the [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) trainer caches the results of the previous estimators for later use by the trainer.</span></span>

```csharp
// 1. Concatenate Size and Historical into a single feature vector output to a new column called Features
// 2. Normalize Features vector
// 3. Cache prepared data
// 4. Use Sdca trainer to train the model
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", "Size", "HistoricalPrices")
        .Append(mlContext.Transforms.NormalizeMinMax("Features"))
        .AppendCacheCheckpoint(mlContext);
        .Append(mlContext.Regression.Trainers.Sdca());
```

## <a name="train-the-machine-learning-model"></a><span data-ttu-id="01671-140">Trénování modelu strojového učení</span><span class="sxs-lookup"><span data-stu-id="01671-140">Train the machine learning model</span></span>

<span data-ttu-id="01671-141">Jakmile jsou data předem zpracována, [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase%602.Fit%2A) použijte metodu k trénování modelu strojového učení s regresním algoritmem. [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer)</span><span class="sxs-lookup"><span data-stu-id="01671-141">Once the data is pre-processed, use the [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase%602.Fit%2A) method to train the machine learning model with the [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) regression algorithm.</span></span>

```csharp
// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a><span data-ttu-id="01671-142">Extrahovat parametry modelu</span><span class="sxs-lookup"><span data-stu-id="01671-142">Extract model parameters</span></span>

<span data-ttu-id="01671-143">Po vyškolení modelu extrahujte získané [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) poznatky pro kontrolu nebo rekvalifikaci.</span><span class="sxs-lookup"><span data-stu-id="01671-143">After the model has been trained, extract the learned [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) for inspection or retraining.</span></span> <span data-ttu-id="01671-144">Poskytují [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) zkreslení a naučené koeficienty nebo hmotnosti trénovaného modelu.</span><span class="sxs-lookup"><span data-stu-id="01671-144">The [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) provide the bias and learned coefficients or weights of the trained model.</span></span>

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> <span data-ttu-id="01671-145">Ostatní modely mají parametry, které jsou specifické pro jejich úkoly.</span><span class="sxs-lookup"><span data-stu-id="01671-145">Other models have parameters that are specific to their tasks.</span></span> <span data-ttu-id="01671-146">[Například K-Means algoritmus](xref:Microsoft.ML.Trainers.KMeansTrainer) vloží data do clusteru [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) na základě centroids a obsahuje vlastnost, která ukládá tyto naučené centroids.</span><span class="sxs-lookup"><span data-stu-id="01671-146">For example, the [K-Means algorithm](xref:Microsoft.ML.Trainers.KMeansTrainer) puts data into cluster based on centroids and the [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) contains a property that stores these learned centroids.</span></span> <span data-ttu-id="01671-147">Další informace najdete v `ModelParameters` [ `Microsoft.ML.Trainers` dokumentaci k rozhraní API](xref:Microsoft.ML.Trainers) a vyhledejte třídy, které obsahují v jejich názvu.</span><span class="sxs-lookup"><span data-stu-id="01671-147">To learn more, visit the [`Microsoft.ML.Trainers` API Documentation](xref:Microsoft.ML.Trainers) and look for classes that contain `ModelParameters` in their name.</span></span>

## <a name="evaluate-model-quality"></a><span data-ttu-id="01671-148">Vyhodnocení kvality modelu</span><span class="sxs-lookup"><span data-stu-id="01671-148">Evaluate model quality</span></span>

<span data-ttu-id="01671-149">Chcete-li pomoci vybrat nejvýkonnější model, je nezbytné vyhodnotit jeho výkon na testovací data.</span><span class="sxs-lookup"><span data-stu-id="01671-149">To help choose the best performing model, it is essential to evaluate its performance on test data.</span></span> <span data-ttu-id="01671-150">Pomocí [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) metody, k měření různých metrik pro trénovaný model.</span><span class="sxs-lookup"><span data-stu-id="01671-150">Use the [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) method, to measure various metrics for the trained model.</span></span>

> [!NOTE]
> <span data-ttu-id="01671-151">Metoda `Evaluate` vytváří různé metriky v závislosti na tom, který úkol strojového učení byl proveden.</span><span class="sxs-lookup"><span data-stu-id="01671-151">The `Evaluate` method produces different metrics depending on which machine learning task was performed.</span></span> <span data-ttu-id="01671-152">Další podrobnosti naleznete v `Metrics` [ `Microsoft.ML.Data` dokumentaci k rozhraní API](xref:Microsoft.ML.Data) a vyhledejte třídy, které obsahují v jejich názvu.</span><span class="sxs-lookup"><span data-stu-id="01671-152">For more details, visit the [`Microsoft.ML.Data` API Documentation](xref:Microsoft.ML.Data) and look for classes that contain `Metrics` in their name.</span></span>

```csharp
// Measure trained model performance
// Apply data prep transformer to test data
IDataView transformedTestData = dataPrepTransformer.Transform(testData);

// Use trained model to make inferences on test data
IDataView testDataPredictions = trainedModel.Transform(transformedTestData);

// Extract model metrics and get RSquared
RegressionMetrics trainedModelMetrics = mlContext.Regression.Evaluate(testDataPredictions);
double rSquared = trainedModelMetrics.RSquared;
```

<span data-ttu-id="01671-153">V předchozí ukázce kódu:</span><span class="sxs-lookup"><span data-stu-id="01671-153">In the previous code sample:</span></span>

1. <span data-ttu-id="01671-154">Sada testovacích dat je předem zpracována pomocí dříve definovaných transformací přípravy dat.</span><span class="sxs-lookup"><span data-stu-id="01671-154">Test data set is pre-processed using the data preparation transforms previously defined.</span></span>
2. <span data-ttu-id="01671-155">Trénovaný model strojového učení se používá k předpovědi na testovací data.</span><span class="sxs-lookup"><span data-stu-id="01671-155">The trained machine learning model is used to make predictions on the test data.</span></span>
3. <span data-ttu-id="01671-156">V `Evaluate` metodě jsou hodnoty `CurrentPrice` ve sloupci sady testovacích `Score` dat porovnány se sloupcem nově výstupních předpovědí pro výpočet metrik pro regresní model, z nichž jedna, R-Squared je uložena v `rSquared` proměnné.</span><span class="sxs-lookup"><span data-stu-id="01671-156">In the `Evaluate` method, the values in the `CurrentPrice` column of the test data set are compared against the `Score` column of the newly output predictions to calculate the metrics for the regression model, one of which, R-Squared is stored in the `rSquared` variable.</span></span>

> [!NOTE]
> <span data-ttu-id="01671-157">V tomto malém příkladu R-Squared je číslo není v rozsahu 0-1 z důvodu omezené velikosti dat.</span><span class="sxs-lookup"><span data-stu-id="01671-157">In this small example, the R-Squared is a number not in the range of 0-1 because of the limited size of the data.</span></span> <span data-ttu-id="01671-158">V reálném scénáři byste měli očekávat hodnotu mezi 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="01671-158">In a real-world scenario, you should expect to see a value between 0 and 1.</span></span>
