---
title: Natrénování a vyhodnocení modelu
description: Zjistěte, jak natrénování a vyhodnocení modelů strojového učení v ML.NET
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 2abb17aad6091cd6a5f0b6f82835011d01b40153
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063627"
---
# <a name="train-and-evaluate-a-model"></a><span data-ttu-id="f09dc-103">Natrénování a vyhodnocení modelu</span><span class="sxs-lookup"><span data-stu-id="f09dc-103">Train and evaluate a model</span></span>

<span data-ttu-id="f09dc-104">Zjistěte, jak vytvářet modely strojového učení, extrahovat zjištěná parametry a měření výkonu s ML.NET.</span><span class="sxs-lookup"><span data-stu-id="f09dc-104">Learn how to build machine learning models, extract learned parameters and measure performance with ML.NET.</span></span> <span data-ttu-id="f09dc-105">I když tato ukázka trénovat regresní model, koncepty platí v celé většinou ostatní algoritmy.</span><span class="sxs-lookup"><span data-stu-id="f09dc-105">Although this sample trains a regression model, the concepts are applicable throughout a majority of the other algorithms.</span></span>

## <a name="split-data-for-training-and-testing"></a><span data-ttu-id="f09dc-106">Rozdělení dat pro trénování a testování</span><span class="sxs-lookup"><span data-stu-id="f09dc-106">Split data for training and testing</span></span>

<span data-ttu-id="f09dc-107">Cílem model strojového učení je pro identifikaci vzorů v rámci trénovací data.</span><span class="sxs-lookup"><span data-stu-id="f09dc-107">The goal of a machine learning model is to identify patterns within training data.</span></span> <span data-ttu-id="f09dc-108">Tyto vzory se používají k vytvářet predikce na nová data.</span><span class="sxs-lookup"><span data-stu-id="f09dc-108">These patterns are used to make predictions using new data.</span></span>

<span data-ttu-id="f09dc-109">Zadaný datový model následující:</span><span class="sxs-lookup"><span data-stu-id="f09dc-109">Given the following data model:</span></span>

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

<span data-ttu-id="f09dc-110">Načtení dat do [ `IDataView` ](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="f09dc-110">Load the data into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="f09dc-111">Použití [ `TrainTestSplit` ](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) metodu pro rozdělení dat na trénování a testování sad.</span><span class="sxs-lookup"><span data-stu-id="f09dc-111">Use the [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) method to split the data into train and test sets.</span></span> <span data-ttu-id="f09dc-112">Výsledkem bude [ `TrainTestData` ](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) objekt, který obsahuje dva [ `IDataView` ](xref:Microsoft.ML.IDataView) členy, jeden pro sadu trénování a druhý pro testovací sadu.</span><span class="sxs-lookup"><span data-stu-id="f09dc-112">The result will be a [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) object which contains two [`IDataView`](xref:Microsoft.ML.IDataView) members, one for the train set and the other for the test set.</span></span> <span data-ttu-id="f09dc-113">Data rozdělit procento závisí `testFraction` parametru.</span><span class="sxs-lookup"><span data-stu-id="f09dc-113">The data split percentage is determined by the `testFraction` parameter.</span></span> <span data-ttu-id="f09dc-114">Následující fragment drží si 20 procent společností z žebříčku původní data pro sadu testů.</span><span class="sxs-lookup"><span data-stu-id="f09dc-114">The snippet below is holding out 20 percent of the original data for the test set.</span></span>

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a><span data-ttu-id="f09dc-115">Příprava dat</span><span class="sxs-lookup"><span data-stu-id="f09dc-115">Prepare the data</span></span>

<span data-ttu-id="f09dc-116">Data musí být předem zpracovaných před trénování modelu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="f09dc-116">The data needs to be pre-processed before training a machine learning model.</span></span> <span data-ttu-id="f09dc-117">Další informace o přípravě dat můžete najít na [článek pro přípravu dat](prepare-data-ml-net.md) také [ `transforms page` ](../resources/transforms.md).</span><span class="sxs-lookup"><span data-stu-id="f09dc-117">More information on data preparation can be found on the [data prep how-to article](prepare-data-ml-net.md) as well as the [`transforms page`](../resources/transforms.md).</span></span>

<span data-ttu-id="f09dc-118">Algoritmy ML.NET mají omezení týkající se sloupci vstupní typy.</span><span class="sxs-lookup"><span data-stu-id="f09dc-118">ML.NET algorithms have constraints on input column types.</span></span> <span data-ttu-id="f09dc-119">Navíc jsou použity výchozí hodnoty pro názvy sloupců vstupních a výstupních, když nejsou určeny žádné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f09dc-119">Additionally, default values are used for input and output column names when no values are specified.</span></span>

### <a name="working-with-expected-column-types"></a><span data-ttu-id="f09dc-120">Práce s typy očekávaných sloupců</span><span class="sxs-lookup"><span data-stu-id="f09dc-120">Working with expected column types</span></span>

<span data-ttu-id="f09dc-121">Algoritmy strojového učení v ML.NET očekávat float vektor známou velikost jako vstup.</span><span class="sxs-lookup"><span data-stu-id="f09dc-121">The machine learning algorithms in ML.NET expect a float vector of known size as input.</span></span> <span data-ttu-id="f09dc-122">Použít [ `VectorType` ](xref:Microsoft.ML.Data.VectorTypeAttribute) atribut datový model, při všech dat je již v číselném formátu a má být zpracovány současně (tj. pixely obrázku).</span><span class="sxs-lookup"><span data-stu-id="f09dc-122">Apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to your data model when all of the data is already in numerical format and is intended to be processed together (i.e. image pixels).</span></span> 

<span data-ttu-id="f09dc-123">Pokud data nejsou všechny číselné a chcete k použití různých datových transformací na všech sloupcích jednotlivě, použijte [ `Concatenate` ](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) metoda po všech sloupců byly zpracovány ke sloučení všech jednotlivých sloupců vektor jednu funkci, která je výstup do nového sloupce.</span><span class="sxs-lookup"><span data-stu-id="f09dc-123">If data is not all numerical and you want to apply different data transformations on each of the columns individually, use the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method after all of the columns have been processed to combine all of the individual columns into a single feature vector that is output to a new column.</span></span> 

<span data-ttu-id="f09dc-124">Následující fragment kódu kombinuje `Size` a `HistoricalPrices` názvem sloupce do jednoho funkce vektor, který je výstup do nového sloupce `Features`.</span><span class="sxs-lookup"><span data-stu-id="f09dc-124">The following snippet combines the `Size` and `HistoricalPrices` columns into a single feature vector that is output to a new column called `Features`.</span></span> <span data-ttu-id="f09dc-125">Vzhledem k tomu, že existuje rozdíl v škálování, [ `NormalizeMinMax` ](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) platí pro `Features` k normalizaci dat sloupce.</span><span class="sxs-lookup"><span data-stu-id="f09dc-125">Because there is a difference in scales, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) is applied to the `Features` column to normalize the data.</span></span>

```csharp
// Define Data Prep Estimator
// 1. Concatenate Size and Historical into a single feature vector output to a new column called Features
// 2. Normalize Features vector
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", "Size", "HistoricalPrices")
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// Create data prep transformer
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(trainData);

// Apply tranforms to training data
IDataView transformedTrainingData = dataPrepTransformer.Transform(trainData);
```

### <a name="working-with-default-column-names"></a><span data-ttu-id="f09dc-126">Práce s výchozí názvy sloupců</span><span class="sxs-lookup"><span data-stu-id="f09dc-126">Working with default column names</span></span>

<span data-ttu-id="f09dc-127">ML.NET algoritmy používat výchozí názvy sloupců, pokud jsou zadána žádná.</span><span class="sxs-lookup"><span data-stu-id="f09dc-127">ML.NET algorithms use default column names when none are specified.</span></span> <span data-ttu-id="f09dc-128">Všechny školitelé mít parametr s názvem `featureColumnName` vstupů algoritmu a použít parametr pro očekávané hodnoty mají také volat `labelColumnName`.</span><span class="sxs-lookup"><span data-stu-id="f09dc-128">All trainers have a parameter called `featureColumnName` for the inputs of the algorithm and when applicable they also have a parameter for the expected value called `labelColumnName`.</span></span> <span data-ttu-id="f09dc-129">Ve výchozím nastavení jsou tyto hodnoty `Features` a `Label` v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="f09dc-129">By default those values are `Features` and `Label` respectively.</span></span> 

<span data-ttu-id="f09dc-130">S použitím [ `Concatenate` ](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) volána metoda během předběžného zpracování k vytvoření nového sloupce `Features`, není nutné zadat název sloupce funkce v parametrech algoritmus, protože již existuje v Předběžně zpracovat `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="f09dc-130">By using the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method during pre-processing to create a new column called `Features`, there is no need to specify the feature column name in the parameters of the algorithm since it already exists in the pre-processed `IDataView`.</span></span> <span data-ttu-id="f09dc-131">Popisek sloupce je `CurrentPrice`, ale od té doby [ `ColumnName` ](xref:Microsoft.ML.Data.ColumnNameAttribute) atribut se používá v datovém modelu, ML.NET přejmenuje `CurrentPrice` sloupec, který se `Label` což eliminuje nutnost poskytnout `labelColumnName` parametr se strojovým učením estimator algoritmus.</span><span class="sxs-lookup"><span data-stu-id="f09dc-131">The label column is `CurrentPrice`, but since the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute is used in the data model, ML.NET renames the `CurrentPrice` column to `Label` which removes the need to provide the `labelColumnName` parameter to the machine learning algorithm estimator.</span></span> 

<span data-ttu-id="f09dc-132">Pokud už nechcete používat výchozí názvy sloupců, předejte názvy sloupců funkce a popisek jako parametry při definování strojového učení algoritmu odhad, jak je uvedeno v následující fragment kódu:</span><span class="sxs-lookup"><span data-stu-id="f09dc-132">If you don't want to use the default column names, pass in the names of the feature and label columns as parameters when defining the machine learning algorithm estimator as demonstrated by the subsequent snippet:</span></span>

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="train-the-machine-learning-model"></a><span data-ttu-id="f09dc-133">Trénování modelu strojového učení</span><span class="sxs-lookup"><span data-stu-id="f09dc-133">Train the machine learning model</span></span>

<span data-ttu-id="f09dc-134">Jakmile jsou data předem zpracovaných, použijte [ `Fit` ](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) metodu pro trénování modelu strojového učení s [ `StochasticDualCoordinateAscent` ](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) regresní algoritmus.</span><span class="sxs-lookup"><span data-stu-id="f09dc-134">Once the data is pre-processed, use the [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) method to train the machine learning model with the [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) regression algorithm.</span></span>

```csharp
// Define StochasticDualCoodrinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a><span data-ttu-id="f09dc-135">Extrahovat parametry modelu</span><span class="sxs-lookup"><span data-stu-id="f09dc-135">Extract model parameters</span></span>

<span data-ttu-id="f09dc-136">Jakmile model se trénuje, extrahovat zjištěná [ `ModelParameters` ](xref:Microsoft.ML.Trainers.ModelParametersBase`1) pro kontrolu nebo znovu školení.</span><span class="sxs-lookup"><span data-stu-id="f09dc-136">After the model has been trained, extract the learned [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase`1) for inspection or re-training.</span></span> <span data-ttu-id="f09dc-137">[ `LinearRegressionModelParameters` ](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) Posunu omezení a zjištěná nebo váhy trénovaného modelu.</span><span class="sxs-lookup"><span data-stu-id="f09dc-137">The [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) provide the bias and learned coefficients or weights of the trained model.</span></span> 

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> <span data-ttu-id="f09dc-138">Další modely mají parametry, které jsou specifické pro jejich úkoly.</span><span class="sxs-lookup"><span data-stu-id="f09dc-138">Other models have parameters that are specific to their tasks.</span></span> <span data-ttu-id="f09dc-139">Například [algoritmus K-Means](xref:Microsoft.ML.Trainers.KMeansTrainer) zařadí data do clusteru podle centroids a [ `KMeansModelParameters` ](xref:Microsoft.ML.Trainers.KMeansModelParameters) obsahuje vlastnost, která ukládá tyto zkušenosti centroids.</span><span class="sxs-lookup"><span data-stu-id="f09dc-139">For example, the [K-Means algorithm](xref:Microsoft.ML.Trainers.KMeansTrainer) puts data into cluster based on centroids and the [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) contains a property that stores these learned centroids.</span></span> <span data-ttu-id="f09dc-140">Další informace najdete [ `Microsoft.ML.Trainers` dokumentace k rozhraní API](xref:Microsoft.ML.Trainers) a hledejte tříd, které obsahují `ModelParameters` v názvu.</span><span class="sxs-lookup"><span data-stu-id="f09dc-140">To learn more, visit the [`Microsoft.ML.Trainers` API Documentation](xref:Microsoft.ML.Trainers) and look for classes that contain `ModelParameters` in their name.</span></span> 

## <a name="evaluate-model-quality"></a><span data-ttu-id="f09dc-141">Vyhodnocení kvalita modelu</span><span class="sxs-lookup"><span data-stu-id="f09dc-141">Evaluate model quality</span></span>

<span data-ttu-id="f09dc-142">Pomoc při výběru nejvýkonnějšího modelu, je nutné vyhodnotit její výkon na testovací data.</span><span class="sxs-lookup"><span data-stu-id="f09dc-142">To help choose the best performing model, it is essential to evaluate its performance on test data.</span></span> <span data-ttu-id="f09dc-143">Použití [ `Evaluate` ](xref:Microsoft.ML.RegressionCatalog.Evaluate*) metoda měření různé metriky pro trénovaného modelu.</span><span class="sxs-lookup"><span data-stu-id="f09dc-143">Use the [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) method, to measure various metrics for the trained model.</span></span>

> [!NOTE]
> <span data-ttu-id="f09dc-144">`Evaluate` Metoda vytvoří různých metrik v závislosti na počítač, který byl learning úloha byla provedena.</span><span class="sxs-lookup"><span data-stu-id="f09dc-144">The `Evaluate` method produces different metrics depending on which machine learning task was was performed.</span></span> <span data-ttu-id="f09dc-145">Další informace najdete [ `Microsoft.ML.Data` dokumentace k rozhraní API](xref:Microsoft.ML.Data) a hledejte tříd, které obsahují `Metrics` v názvu.</span><span class="sxs-lookup"><span data-stu-id="f09dc-145">For more details, visit the [`Microsoft.ML.Data` API Documentation](xref:Microsoft.ML.Data) and look for classes that contain `Metrics` in their name.</span></span> 

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

<span data-ttu-id="f09dc-146">V předchozí ukázce kódu:</span><span class="sxs-lookup"><span data-stu-id="f09dc-146">In the previous code sample:</span></span>  
1. <span data-ttu-id="f09dc-147">Sada testovacích dat. předem zpracována pomocí transformace přípravy dat definovaný dříve.</span><span class="sxs-lookup"><span data-stu-id="f09dc-147">Test data set is pre-processed using the data preparation transforms previously defined.</span></span> 
2. <span data-ttu-id="f09dc-148">Model trénovaného machine learning slouží k vytvoření predikcí testovací data.</span><span class="sxs-lookup"><span data-stu-id="f09dc-148">The trained machine learning model is used to make predictions on the test data.</span></span>
3. <span data-ttu-id="f09dc-149">V `Evaluate` metody, hodnoty `CurrentPrice` sloupce datové sady testů se porovná s `Score` nově výstupní sloupec modelu předpovědi pro výpočet metrik pro regresi, jedním z nich, spolehlivosti R je uložen v `rSquared` proměnné.</span><span class="sxs-lookup"><span data-stu-id="f09dc-149">In the `Evaluate` method, the values in the `CurrentPrice` column of the test data set are compared against the `Score` column of the newly output predictions to calculate the metrics for the regression model, one of which, R-Squared is stored in the `rSquared` variable.</span></span>

> [!NOTE]
> <span data-ttu-id="f09dc-150">V tomto příkladu malé spolehlivosti R je číslo není v rozsahu 0-1 z důvodu omezené množství dat.</span><span class="sxs-lookup"><span data-stu-id="f09dc-150">In this small example, the R-Squared is a number not in the range of 0-1 because of the limited size of the data.</span></span> <span data-ttu-id="f09dc-151">Reálný scénář měli byste očekávat zobrazit hodnotu mezi 0 a 1.</span><span class="sxs-lookup"><span data-stu-id="f09dc-151">In a real-world scenario, you should expect to see a value between 0 and 1.</span></span>
