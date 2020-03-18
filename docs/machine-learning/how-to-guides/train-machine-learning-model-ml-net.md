---
title: Trénování a vyhodnocení modelu
description: Zjistěte, jak vytvářet modely strojového učení, shromažďovat metriky a měřit výkon s ML.NET. Model strojového učení identifikuje vzory v rámci trénovacích dat, aby se předpovědi pomocí nových dat.
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 0e0f43225b9bf243c31b3095817bdcbdb3123012
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73976763"
---
# <a name="train-and-evaluate-a-model"></a><span data-ttu-id="18ad3-104">Trénování a vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="18ad3-104">Train and evaluate a model</span></span>

<span data-ttu-id="18ad3-105">Zjistěte, jak vytvářet modely strojového učení, shromažďovat metriky a měřit výkon s ML.NET.</span><span class="sxs-lookup"><span data-stu-id="18ad3-105">Learn how to build machine learning models, collect metrics, and measure performance with ML.NET.</span></span> <span data-ttu-id="18ad3-106">I když tato ukázka trénuje regresní model, koncepty jsou použitelné ve většině ostatních algoritmů.</span><span class="sxs-lookup"><span data-stu-id="18ad3-106">Although this sample trains a regression model, the concepts are applicable throughout a majority of the other algorithms.</span></span>

## <a name="split-data-for-training-and-testing"></a><span data-ttu-id="18ad3-107">Rozdělení dat pro školení a testování</span><span class="sxs-lookup"><span data-stu-id="18ad3-107">Split data for training and testing</span></span>

<span data-ttu-id="18ad3-108">Cílem modelu strojového učení je identifikovat vzory v rámci trénovacích dat.</span><span class="sxs-lookup"><span data-stu-id="18ad3-108">The goal of a machine learning model is to identify patterns within training data.</span></span> <span data-ttu-id="18ad3-109">Tyto vzory se používají k předpovědi pomocí nových dat.</span><span class="sxs-lookup"><span data-stu-id="18ad3-109">These patterns are used to make predictions using new data.</span></span>

<span data-ttu-id="18ad3-110">Data mohou být modelována `HousingData`podle třídy, jako je .</span><span class="sxs-lookup"><span data-stu-id="18ad3-110">The data can be modeled by a class like `HousingData`.</span></span>

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

<span data-ttu-id="18ad3-111">Vzhledem k následujícím údajům, které jsou načteny do . [`IDataView`](xref:Microsoft.ML.IDataView)</span><span class="sxs-lookup"><span data-stu-id="18ad3-111">Given the following data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

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

<span data-ttu-id="18ad3-112">Pomocí [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) metody rozdělte data do vlakových a testovacích sad.</span><span class="sxs-lookup"><span data-stu-id="18ad3-112">Use the [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) method to split the data into train and test sets.</span></span> <span data-ttu-id="18ad3-113">Výsledkem [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) bude objekt, který [`IDataView`](xref:Microsoft.ML.IDataView) obsahuje dva členy, jeden pro vlakové sady a druhý pro testovací sadu.</span><span class="sxs-lookup"><span data-stu-id="18ad3-113">The result will be a [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) object which contains two [`IDataView`](xref:Microsoft.ML.IDataView) members, one for the train set and the other for the test set.</span></span> <span data-ttu-id="18ad3-114">Procento rozdělení dat je `testFraction` určeno parametrem.</span><span class="sxs-lookup"><span data-stu-id="18ad3-114">The data split percentage is determined by the `testFraction` parameter.</span></span> <span data-ttu-id="18ad3-115">Níže uvedený úryvek podrží 20 procent původních dat pro testovací sadu.</span><span class="sxs-lookup"><span data-stu-id="18ad3-115">The snippet below is holding out 20 percent of the original data for the test set.</span></span>

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a><span data-ttu-id="18ad3-116">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="18ad3-116">Prepare the data</span></span>

<span data-ttu-id="18ad3-117">Data musí být předem zpracovány před trénování modelu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="18ad3-117">The data needs to be pre-processed before training a machine learning model.</span></span> <span data-ttu-id="18ad3-118">Více informací o přípravě dat naleznete na článku s [návody k přípravě dat](prepare-data-ml-net.md) a na [`transforms page`](../resources/transforms.md).</span><span class="sxs-lookup"><span data-stu-id="18ad3-118">More information on data preparation can be found on the [data prep how-to article](prepare-data-ml-net.md) as well as the [`transforms page`](../resources/transforms.md).</span></span>

<span data-ttu-id="18ad3-119">ML.NET algoritmy mají omezení pro typy vstupních sloupců.</span><span class="sxs-lookup"><span data-stu-id="18ad3-119">ML.NET algorithms have constraints on input column types.</span></span> <span data-ttu-id="18ad3-120">Kromě toho výchozí hodnoty se používají pro vstupní a výstupní názvy sloupců, pokud nejsou zadány žádné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="18ad3-120">Additionally, default values are used for input and output column names when no values are specified.</span></span>

### <a name="working-with-expected-column-types"></a><span data-ttu-id="18ad3-121">Práce s očekávanými typy sloupců</span><span class="sxs-lookup"><span data-stu-id="18ad3-121">Working with expected column types</span></span>

<span data-ttu-id="18ad3-122">Algoritmy strojového učení v ML.NET očekávat plovoucí vektor známé velikosti jako vstup.</span><span class="sxs-lookup"><span data-stu-id="18ad3-122">The machine learning algorithms in ML.NET expect a float vector of known size as input.</span></span> <span data-ttu-id="18ad3-123">Použijte [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) atribut na datový model, pokud jsou všechna data již v číselném formátu a jsou určena ke zpracování společně (tj. obrazové body).</span><span class="sxs-lookup"><span data-stu-id="18ad3-123">Apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to your data model when all of the data is already in numerical format and is intended to be processed together (i.e. image pixels).</span></span>

<span data-ttu-id="18ad3-124">Pokud data nejsou všechna číselná a chcete použít různé transformace dat na každý [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) sloupec jednotlivě, použijte metodu po zpracování všech sloupců a zkombinujte všechny jednotlivé sloupce do jednoho vektoru prvku, který je výstupem do nového sloupce.</span><span class="sxs-lookup"><span data-stu-id="18ad3-124">If data is not all numerical and you want to apply different data transformations on each of the columns individually, use the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method after all of the columns have been processed to combine all of the individual columns into a single feature vector that is output to a new column.</span></span>

<span data-ttu-id="18ad3-125">Následující úryvek kombinuje `Size` sloupce `HistoricalPrices` a do jednoho vektoru prvku, který `Features`je výstupem do nového sloupce s názvem .</span><span class="sxs-lookup"><span data-stu-id="18ad3-125">The following snippet combines the `Size` and `HistoricalPrices` columns into a single feature vector that is output to a new column called `Features`.</span></span> <span data-ttu-id="18ad3-126">Vzhledem k tomu, že [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) je rozdíl `Features` v měřítkách, se použije na sloupec normalizovat data.</span><span class="sxs-lookup"><span data-stu-id="18ad3-126">Because there is a difference in scales, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) is applied to the `Features` column to normalize the data.</span></span>

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

### <a name="working-with-default-column-names"></a><span data-ttu-id="18ad3-127">Práce s výchozími názvy sloupců</span><span class="sxs-lookup"><span data-stu-id="18ad3-127">Working with default column names</span></span>

<span data-ttu-id="18ad3-128">ML.NET algoritmy používají výchozí názvy sloupců, pokud nejsou zadány žádné.</span><span class="sxs-lookup"><span data-stu-id="18ad3-128">ML.NET algorithms use default column names when none are specified.</span></span> <span data-ttu-id="18ad3-129">Všechny školitelů `featureColumnName` mají parametr volaný pro vstupy algoritmu a v případě `labelColumnName`potřeby mají také parametr pro očekávanou hodnotu s názvem .</span><span class="sxs-lookup"><span data-stu-id="18ad3-129">All trainers have a parameter called `featureColumnName` for the inputs of the algorithm and when applicable they also have a parameter for the expected value called `labelColumnName`.</span></span> <span data-ttu-id="18ad3-130">Ve výchozím nastavení `Features` `Label` jsou tyto hodnoty a resp.</span><span class="sxs-lookup"><span data-stu-id="18ad3-130">By default those values are `Features` and `Label` respectively.</span></span>

<span data-ttu-id="18ad3-131">Pomocí [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) metody během předběžného zpracování k vytvoření `Features`nového sloupce s názvem , není nutné zadat název sloupce funkce v parametrech `IDataView`algoritmu, protože již existuje v předem zpracovaném .</span><span class="sxs-lookup"><span data-stu-id="18ad3-131">By using the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method during pre-processing to create a new column called `Features`, there is no need to specify the feature column name in the parameters of the algorithm since it already exists in the pre-processed `IDataView`.</span></span> <span data-ttu-id="18ad3-132">Sloupec popisek `CurrentPrice`je , [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) ale vzhledem k tomu, že `CurrentPrice` atribut `Label` se používá v datovém modelu, ML.NET přejmenuje sloupec, na který odebere potřebu poskytnout `labelColumnName` parametr pro odhad algoritmu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="18ad3-132">The label column is `CurrentPrice`, but since the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute is used in the data model, ML.NET renames the `CurrentPrice` column to `Label` which removes the need to provide the `labelColumnName` parameter to the machine learning algorithm estimator.</span></span>

<span data-ttu-id="18ad3-133">Pokud nechcete používat výchozí názvy sloupců, předejte názvy sloupců prvku a popisku jako parametry při definování odhadu algoritmu strojového učení, jak ukazuje následující úryvek:</span><span class="sxs-lookup"><span data-stu-id="18ad3-133">If you don't want to use the default column names, pass in the names of the feature and label columns as parameters when defining the machine learning algorithm estimator as demonstrated by the subsequent snippet:</span></span>

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="train-the-machine-learning-model"></a><span data-ttu-id="18ad3-134">Trénování modelu strojového učení</span><span class="sxs-lookup"><span data-stu-id="18ad3-134">Train the machine learning model</span></span>

<span data-ttu-id="18ad3-135">Jakmile jsou data předem zpracována, [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) použijte metodu k trénování modelu strojového učení s regresním algoritmem. [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer)</span><span class="sxs-lookup"><span data-stu-id="18ad3-135">Once the data is pre-processed, use the [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) method to train the machine learning model with the [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) regression algorithm.</span></span>

```csharp
// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a><span data-ttu-id="18ad3-136">Extrahovat parametry modelu</span><span class="sxs-lookup"><span data-stu-id="18ad3-136">Extract model parameters</span></span>

<span data-ttu-id="18ad3-137">Po vyškolení modelu vyhovuťte získané [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) poznatky pro inspekci nebo přeškolení.</span><span class="sxs-lookup"><span data-stu-id="18ad3-137">After the model has been trained, extract the learned [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) for inspection or re-training.</span></span> <span data-ttu-id="18ad3-138">Poskytují [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) zkreslení a naučené koeficienty nebo hmotnosti trénovaného modelu.</span><span class="sxs-lookup"><span data-stu-id="18ad3-138">The [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) provide the bias and learned coefficients or weights of the trained model.</span></span>

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> <span data-ttu-id="18ad3-139">Ostatní modely mají parametry, které jsou specifické pro jejich úkoly.</span><span class="sxs-lookup"><span data-stu-id="18ad3-139">Other models have parameters that are specific to their tasks.</span></span> <span data-ttu-id="18ad3-140">[Například K-Means algoritmus](xref:Microsoft.ML.Trainers.KMeansTrainer) vloží data do clusteru [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) na základě centroids a obsahuje vlastnost, která ukládá tyto naučené centroids.</span><span class="sxs-lookup"><span data-stu-id="18ad3-140">For example, the [K-Means algorithm](xref:Microsoft.ML.Trainers.KMeansTrainer) puts data into cluster based on centroids and the [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) contains a property that stores these learned centroids.</span></span> <span data-ttu-id="18ad3-141">Další informace najdete v `ModelParameters` [ `Microsoft.ML.Trainers` dokumentaci k rozhraní API](xref:Microsoft.ML.Trainers) a vyhledejte třídy, které obsahují v jejich názvu.</span><span class="sxs-lookup"><span data-stu-id="18ad3-141">To learn more, visit the [`Microsoft.ML.Trainers` API Documentation](xref:Microsoft.ML.Trainers) and look for classes that contain `ModelParameters` in their name.</span></span>

## <a name="evaluate-model-quality"></a><span data-ttu-id="18ad3-142">Vyhodnocení kvality modelu</span><span class="sxs-lookup"><span data-stu-id="18ad3-142">Evaluate model quality</span></span>

<span data-ttu-id="18ad3-143">Chcete-li pomoci vybrat nejvýkonnější model, je nezbytné vyhodnotit jeho výkon na testovací data.</span><span class="sxs-lookup"><span data-stu-id="18ad3-143">To help choose the best performing model, it is essential to evaluate its performance on test data.</span></span> <span data-ttu-id="18ad3-144">Pomocí [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) metody, k měření různých metrik pro trénovaný model.</span><span class="sxs-lookup"><span data-stu-id="18ad3-144">Use the [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) method, to measure various metrics for the trained model.</span></span>

> [!NOTE]
> <span data-ttu-id="18ad3-145">Metoda `Evaluate` vytváří různé metriky v závislosti na tom, který úkol strojového učení byl proveden.</span><span class="sxs-lookup"><span data-stu-id="18ad3-145">The `Evaluate` method produces different metrics depending on which machine learning task was performed.</span></span> <span data-ttu-id="18ad3-146">Další podrobnosti naleznete v `Metrics` [ `Microsoft.ML.Data` dokumentaci k rozhraní API](xref:Microsoft.ML.Data) a vyhledejte třídy, které obsahují v jejich názvu.</span><span class="sxs-lookup"><span data-stu-id="18ad3-146">For more details, visit the [`Microsoft.ML.Data` API Documentation](xref:Microsoft.ML.Data) and look for classes that contain `Metrics` in their name.</span></span>

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

<span data-ttu-id="18ad3-147">V předchozí ukázce kódu:</span><span class="sxs-lookup"><span data-stu-id="18ad3-147">In the previous code sample:</span></span>

1. <span data-ttu-id="18ad3-148">Sada testovacích dat je předem zpracována pomocí dříve definovaných transformací přípravy dat.</span><span class="sxs-lookup"><span data-stu-id="18ad3-148">Test data set is pre-processed using the data preparation transforms previously defined.</span></span>
2. <span data-ttu-id="18ad3-149">Trénovaný model strojového učení se používá k předpovědi na testovací data.</span><span class="sxs-lookup"><span data-stu-id="18ad3-149">The trained machine learning model is used to make predictions on the test data.</span></span>
3. <span data-ttu-id="18ad3-150">V `Evaluate` metodě jsou hodnoty `CurrentPrice` ve sloupci sady testovacích `Score` dat porovnány se sloupcem nově výstupních předpovědí pro výpočet metrik pro regresní model, z nichž jedna, R-Squared je uložena v `rSquared` proměnné.</span><span class="sxs-lookup"><span data-stu-id="18ad3-150">In the `Evaluate` method, the values in the `CurrentPrice` column of the test data set are compared against the `Score` column of the newly output predictions to calculate the metrics for the regression model, one of which, R-Squared is stored in the `rSquared` variable.</span></span>

> [!NOTE]
> <span data-ttu-id="18ad3-151">V tomto malém příkladu R-Squared je číslo není v rozsahu 0-1 z důvodu omezené velikosti dat.</span><span class="sxs-lookup"><span data-stu-id="18ad3-151">In this small example, the R-Squared is a number not in the range of 0-1 because of the limited size of the data.</span></span> <span data-ttu-id="18ad3-152">V reálném scénáři byste měli očekávat hodnotu mezi 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="18ad3-152">In a real-world scenario, you should expect to see a value between 0 and 1.</span></span>
