---
title: Trénování a vyhodnocení modelu
description: Naučte se sestavovat modely strojového učení, shromažďovat metriky a měřit výkon pomocí ML.NET. Model strojového učení identifikuje vzory v rámci školicích dat a umožňuje tak předpovědi pomocí nových dat.
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 0e0f43225b9bf243c31b3095817bdcbdb3123012
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976763"
---
# <a name="train-and-evaluate-a-model"></a><span data-ttu-id="46922-104">Trénování a vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="46922-104">Train and evaluate a model</span></span>

<span data-ttu-id="46922-105">Naučte se sestavovat modely strojového učení, shromažďovat metriky a měřit výkon pomocí ML.NET.</span><span class="sxs-lookup"><span data-stu-id="46922-105">Learn how to build machine learning models, collect metrics, and measure performance with ML.NET.</span></span> <span data-ttu-id="46922-106">I když tato ukázka nasazuje regresní model, koncepce se použijí v rámci většiny ostatních algoritmů.</span><span class="sxs-lookup"><span data-stu-id="46922-106">Although this sample trains a regression model, the concepts are applicable throughout a majority of the other algorithms.</span></span>

## <a name="split-data-for-training-and-testing"></a><span data-ttu-id="46922-107">Rozdělit data pro školení a testování</span><span class="sxs-lookup"><span data-stu-id="46922-107">Split data for training and testing</span></span>

<span data-ttu-id="46922-108">Cílem modelu strojového učení je identifikovat vzory v rámci školicích dat.</span><span class="sxs-lookup"><span data-stu-id="46922-108">The goal of a machine learning model is to identify patterns within training data.</span></span> <span data-ttu-id="46922-109">Tyto vzory slouží k vytváření předpovědi pomocí nových dat.</span><span class="sxs-lookup"><span data-stu-id="46922-109">These patterns are used to make predictions using new data.</span></span>

<span data-ttu-id="46922-110">Data je možné modelovat podle třídy, jako je `HousingData`.</span><span class="sxs-lookup"><span data-stu-id="46922-110">The data can be modeled by a class like `HousingData`.</span></span>

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

<span data-ttu-id="46922-111">S ohledem na následující data, která jsou načtena do [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="46922-111">Given the following data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

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

<span data-ttu-id="46922-112">Použijte metodu [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) pro rozdělení dat do vlakových a testovacích sad.</span><span class="sxs-lookup"><span data-stu-id="46922-112">Use the [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) method to split the data into train and test sets.</span></span> <span data-ttu-id="46922-113">Výsledkem bude [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) objekt, který obsahuje dva členy [`IDataView`](xref:Microsoft.ML.IDataView) , jeden pro sadu vlaků a druhý pro sadu testů.</span><span class="sxs-lookup"><span data-stu-id="46922-113">The result will be a [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) object which contains two [`IDataView`](xref:Microsoft.ML.IDataView) members, one for the train set and the other for the test set.</span></span> <span data-ttu-id="46922-114">Procentuální hodnota rozdělení dat je určena parametrem `testFraction`.</span><span class="sxs-lookup"><span data-stu-id="46922-114">The data split percentage is determined by the `testFraction` parameter.</span></span> <span data-ttu-id="46922-115">Níže uvedený fragment kódu vydrží 20% původních dat pro sadu testů.</span><span class="sxs-lookup"><span data-stu-id="46922-115">The snippet below is holding out 20 percent of the original data for the test set.</span></span>

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a><span data-ttu-id="46922-116">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="46922-116">Prepare the data</span></span>

<span data-ttu-id="46922-117">Data musí být před školením modelu Machine Learning předem zpracovaná.</span><span class="sxs-lookup"><span data-stu-id="46922-117">The data needs to be pre-processed before training a machine learning model.</span></span> <span data-ttu-id="46922-118">Další informace o přípravě dat najdete v [článku o postupu pro přípravu dat](prepare-data-ml-net.md) a na [`transforms page`](../resources/transforms.md).</span><span class="sxs-lookup"><span data-stu-id="46922-118">More information on data preparation can be found on the [data prep how-to article](prepare-data-ml-net.md) as well as the [`transforms page`](../resources/transforms.md).</span></span>

<span data-ttu-id="46922-119">ML.NET algoritmy mají omezení na vstupních typech sloupců.</span><span class="sxs-lookup"><span data-stu-id="46922-119">ML.NET algorithms have constraints on input column types.</span></span> <span data-ttu-id="46922-120">Kromě toho se pro vstupní a výstupní názvy sloupců použijí výchozí hodnoty, pokud nejsou zadány žádné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="46922-120">Additionally, default values are used for input and output column names when no values are specified.</span></span>

### <a name="working-with-expected-column-types"></a><span data-ttu-id="46922-121">Práce s očekávanými typy sloupců</span><span class="sxs-lookup"><span data-stu-id="46922-121">Working with expected column types</span></span>

<span data-ttu-id="46922-122">Algoritmy strojového učení v ML.NET očekávají jako vstup plovoucí vektor známé velikosti.</span><span class="sxs-lookup"><span data-stu-id="46922-122">The machine learning algorithms in ML.NET expect a float vector of known size as input.</span></span> <span data-ttu-id="46922-123">Použijte atribut [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) pro datový model, pokud jsou všechna data již v číselném formátu a mají být zpracována společně (tj. obrazové body).</span><span class="sxs-lookup"><span data-stu-id="46922-123">Apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to your data model when all of the data is already in numerical format and is intended to be processed together (i.e. image pixels).</span></span>

<span data-ttu-id="46922-124">Pokud data nejsou všechna číselná a chcete u každého sloupce použít různé transformace dat, použijte metodu [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) po zpracování všech sloupců pro zkombinování všech jednotlivých sloupců do jediného vektoru funkce, který je výstupem do nového sloupce.</span><span class="sxs-lookup"><span data-stu-id="46922-124">If data is not all numerical and you want to apply different data transformations on each of the columns individually, use the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method after all of the columns have been processed to combine all of the individual columns into a single feature vector that is output to a new column.</span></span>

<span data-ttu-id="46922-125">Následující fragment kódu kombinuje `Size` a `HistoricalPrices` sloupce do jednoho vektoru funkce, který je výstupem do nového sloupce s názvem `Features`.</span><span class="sxs-lookup"><span data-stu-id="46922-125">The following snippet combines the `Size` and `HistoricalPrices` columns into a single feature vector that is output to a new column called `Features`.</span></span> <span data-ttu-id="46922-126">Vzhledem k tomu, že existuje rozdíl v měřítku,`NormalizeMinMax`pro `Features` sloupce použít k normalizaci dat [](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) .</span><span class="sxs-lookup"><span data-stu-id="46922-126">Because there is a difference in scales, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) is applied to the `Features` column to normalize the data.</span></span>

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

### <a name="working-with-default-column-names"></a><span data-ttu-id="46922-127">Práce s názvy výchozích sloupců</span><span class="sxs-lookup"><span data-stu-id="46922-127">Working with default column names</span></span>

<span data-ttu-id="46922-128">Algoritmy ML.NET používají výchozí názvy sloupců, pokud nejsou zadané žádné.</span><span class="sxs-lookup"><span data-stu-id="46922-128">ML.NET algorithms use default column names when none are specified.</span></span> <span data-ttu-id="46922-129">Všechny školitele mají parametr s názvem `featureColumnName` pro vstupy algoritmu a pokud je to možné, mají také parametr pro očekávanou hodnotu s názvem `labelColumnName`.</span><span class="sxs-lookup"><span data-stu-id="46922-129">All trainers have a parameter called `featureColumnName` for the inputs of the algorithm and when applicable they also have a parameter for the expected value called `labelColumnName`.</span></span> <span data-ttu-id="46922-130">Ve výchozím nastavení jsou tyto hodnoty `Features` a `Label` v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="46922-130">By default those values are `Features` and `Label` respectively.</span></span>

<span data-ttu-id="46922-131">Pomocí metody [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) během předběžného zpracování pro vytvoření nového sloupce s názvem `Features`není nutné zadávat název sloupce funkce v parametrech algoritmu, protože již existuje v předem zpracovaném `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="46922-131">By using the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method during pre-processing to create a new column called `Features`, there is no need to specify the feature column name in the parameters of the algorithm since it already exists in the pre-processed `IDataView`.</span></span> <span data-ttu-id="46922-132">Sloupec popisku je `CurrentPrice`, ale vzhledem k tomu, že se v datovém modelu používá atribut [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) , ml.NET přejmenuje sloupec `CurrentPrice` na `Label`, který eliminuje nutnost zadat parametr `labelColumnName` pro Estimator algoritmus Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="46922-132">The label column is `CurrentPrice`, but since the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute is used in the data model, ML.NET renames the `CurrentPrice` column to `Label` which removes the need to provide the `labelColumnName` parameter to the machine learning algorithm estimator.</span></span>

<span data-ttu-id="46922-133">Pokud nechcete používat výchozí názvy sloupců, předejte při definování Estimator algoritmu pro strojové učení, které ukazuje následující fragment kódu, názvy sloupců funkce a popisku jako parametry:</span><span class="sxs-lookup"><span data-stu-id="46922-133">If you don't want to use the default column names, pass in the names of the feature and label columns as parameters when defining the machine learning algorithm estimator as demonstrated by the subsequent snippet:</span></span>

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="train-the-machine-learning-model"></a><span data-ttu-id="46922-134">Výuka modelu Machine Learning</span><span class="sxs-lookup"><span data-stu-id="46922-134">Train the machine learning model</span></span>

<span data-ttu-id="46922-135">Jakmile jsou data předem zpracovaná, použijte metodu [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) k výuce modelu Machine learning pomocí [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) regresního algoritmu.</span><span class="sxs-lookup"><span data-stu-id="46922-135">Once the data is pre-processed, use the [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) method to train the machine learning model with the [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) regression algorithm.</span></span>

```csharp
// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a><span data-ttu-id="46922-136">Extrahovat parametry modelu</span><span class="sxs-lookup"><span data-stu-id="46922-136">Extract model parameters</span></span>

<span data-ttu-id="46922-137">Po výuce modelu vyextrahujte získanou [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) pro kontrolu nebo opětovné školení.</span><span class="sxs-lookup"><span data-stu-id="46922-137">After the model has been trained, extract the learned [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) for inspection or re-training.</span></span> <span data-ttu-id="46922-138">[`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) poskytuje posun a zjištěné koeficienty nebo váhy vyškolených modelů.</span><span class="sxs-lookup"><span data-stu-id="46922-138">The [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) provide the bias and learned coefficients or weights of the trained model.</span></span>

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> <span data-ttu-id="46922-139">Další modely mají parametry, které jsou specifické pro jejich úkoly.</span><span class="sxs-lookup"><span data-stu-id="46922-139">Other models have parameters that are specific to their tasks.</span></span> <span data-ttu-id="46922-140">Například [algoritmus k znamená](xref:Microsoft.ML.Trainers.KMeansTrainer) , že data do clusteru jsou založena na centroids a [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) obsahuje vlastnost, která je uložena se zjištěnými centroids.</span><span class="sxs-lookup"><span data-stu-id="46922-140">For example, the [K-Means algorithm](xref:Microsoft.ML.Trainers.KMeansTrainer) puts data into cluster based on centroids and the [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) contains a property that stores these learned centroids.</span></span> <span data-ttu-id="46922-141">Další informace najdete v dokumentaci k [rozhraní API`Microsoft.ML.Trainers`](xref:Microsoft.ML.Trainers) a hledejte třídy, které v názvu obsahují `ModelParameters`.</span><span class="sxs-lookup"><span data-stu-id="46922-141">To learn more, visit the [`Microsoft.ML.Trainers` API Documentation](xref:Microsoft.ML.Trainers) and look for classes that contain `ModelParameters` in their name.</span></span>

## <a name="evaluate-model-quality"></a><span data-ttu-id="46922-142">Vyhodnocení kvality modelu</span><span class="sxs-lookup"><span data-stu-id="46922-142">Evaluate model quality</span></span>

<span data-ttu-id="46922-143">Chcete-li si vybrat nejlepší model provádění, je nezbytné vyhodnotit jeho výkon na testovacích datech.</span><span class="sxs-lookup"><span data-stu-id="46922-143">To help choose the best performing model, it is essential to evaluate its performance on test data.</span></span> <span data-ttu-id="46922-144">Použijte metodu [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) k měření různých metrik pro vyškolený model.</span><span class="sxs-lookup"><span data-stu-id="46922-144">Use the [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) method, to measure various metrics for the trained model.</span></span>

> [!NOTE]
> <span data-ttu-id="46922-145">Metoda `Evaluate` vytváří různé metriky v závislosti na tom, který úkol strojového učení byl proveden.</span><span class="sxs-lookup"><span data-stu-id="46922-145">The `Evaluate` method produces different metrics depending on which machine learning task was performed.</span></span> <span data-ttu-id="46922-146">Další podrobnosti najdete v [dokumentaci k rozhraní API`Microsoft.ML.Data`](xref:Microsoft.ML.Data) a hledejte třídy, které v názvu obsahují `Metrics`.</span><span class="sxs-lookup"><span data-stu-id="46922-146">For more details, visit the [`Microsoft.ML.Data` API Documentation](xref:Microsoft.ML.Data) and look for classes that contain `Metrics` in their name.</span></span>

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

<span data-ttu-id="46922-147">V předchozím příkladu kódu:</span><span class="sxs-lookup"><span data-stu-id="46922-147">In the previous code sample:</span></span>

1. <span data-ttu-id="46922-148">Testovací sada dat je předem zpracovaná pomocí transformací přípravných dat, které byly dříve definovány.</span><span class="sxs-lookup"><span data-stu-id="46922-148">Test data set is pre-processed using the data preparation transforms previously defined.</span></span>
2. <span data-ttu-id="46922-149">K předpovědií testovacích dat se používá školicí model strojového učení.</span><span class="sxs-lookup"><span data-stu-id="46922-149">The trained machine learning model is used to make predictions on the test data.</span></span>
3. <span data-ttu-id="46922-150">V metodě `Evaluate` jsou hodnoty ve sloupci `CurrentPrice` testovacích dat porovnány se sloupcem `Score` nově výstupního předpovědi pro výpočet metriky pro regresní model, přičemž jedna z nich je v `rSquared` proměnné uložena pomocí R-čtverce.</span><span class="sxs-lookup"><span data-stu-id="46922-150">In the `Evaluate` method, the values in the `CurrentPrice` column of the test data set are compared against the `Score` column of the newly output predictions to calculate the metrics for the regression model, one of which, R-Squared is stored in the `rSquared` variable.</span></span>

> [!NOTE]
> <span data-ttu-id="46922-151">V tomto malém příkladu je R-kvadrát číslo, které není v rozsahu 0-1, protože je omezená velikost dat.</span><span class="sxs-lookup"><span data-stu-id="46922-151">In this small example, the R-Squared is a number not in the range of 0-1 because of the limited size of the data.</span></span> <span data-ttu-id="46922-152">Ve scénáři reálného světa byste měli očekávat zobrazení hodnoty mezi 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="46922-152">In a real-world scenario, you should expect to see a value between 0 and 1.</span></span>
