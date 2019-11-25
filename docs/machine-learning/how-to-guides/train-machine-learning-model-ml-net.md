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
# <a name="train-and-evaluate-a-model"></a>Trénování a vyhodnocení modelu

Naučte se sestavovat modely strojového učení, shromažďovat metriky a měřit výkon pomocí ML.NET. I když tato ukázka nasazuje regresní model, koncepce se použijí v rámci většiny ostatních algoritmů.

## <a name="split-data-for-training-and-testing"></a>Rozdělit data pro školení a testování

Cílem modelu strojového učení je identifikovat vzory v rámci školicích dat. Tyto vzory slouží k vytváření předpovědi pomocí nových dat.

Data je možné modelovat podle třídy, jako je `HousingData`.

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

S ohledem na následující data, která jsou načtena do [`IDataView`](xref:Microsoft.ML.IDataView).

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

Použijte metodu [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) pro rozdělení dat do vlakových a testovacích sad. Výsledkem bude [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) objekt, který obsahuje dva členy [`IDataView`](xref:Microsoft.ML.IDataView) , jeden pro sadu vlaků a druhý pro sadu testů. Procentuální hodnota rozdělení dat je určena parametrem `testFraction`. Níže uvedený fragment kódu vydrží 20% původních dat pro sadu testů.

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a>Příprava dat

Data musí být před školením modelu Machine Learning předem zpracovaná. Další informace o přípravě dat najdete v [článku o postupu pro přípravu dat](prepare-data-ml-net.md) a na [`transforms page`](../resources/transforms.md).

ML.NET algoritmy mají omezení na vstupních typech sloupců. Kromě toho se pro vstupní a výstupní názvy sloupců použijí výchozí hodnoty, pokud nejsou zadány žádné hodnoty.

### <a name="working-with-expected-column-types"></a>Práce s očekávanými typy sloupců

Algoritmy strojového učení v ML.NET očekávají jako vstup plovoucí vektor známé velikosti. Použijte atribut [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) pro datový model, pokud jsou všechna data již v číselném formátu a mají být zpracována společně (tj. obrazové body).

Pokud data nejsou všechna číselná a chcete u každého sloupce použít různé transformace dat, použijte metodu [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) po zpracování všech sloupců pro zkombinování všech jednotlivých sloupců do jediného vektoru funkce, který je výstupem do nového sloupce.

Následující fragment kódu kombinuje `Size` a `HistoricalPrices` sloupce do jednoho vektoru funkce, který je výstupem do nového sloupce s názvem `Features`. Vzhledem k tomu, že existuje rozdíl v měřítku,`NormalizeMinMax`pro `Features` sloupce použít k normalizaci dat [](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) .

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

### <a name="working-with-default-column-names"></a>Práce s názvy výchozích sloupců

Algoritmy ML.NET používají výchozí názvy sloupců, pokud nejsou zadané žádné. Všechny školitele mají parametr s názvem `featureColumnName` pro vstupy algoritmu a pokud je to možné, mají také parametr pro očekávanou hodnotu s názvem `labelColumnName`. Ve výchozím nastavení jsou tyto hodnoty `Features` a `Label` v uvedeném pořadí.

Pomocí metody [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) během předběžného zpracování pro vytvoření nového sloupce s názvem `Features`není nutné zadávat název sloupce funkce v parametrech algoritmu, protože již existuje v předem zpracovaném `IDataView`. Sloupec popisku je `CurrentPrice`, ale vzhledem k tomu, že se v datovém modelu používá atribut [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) , ml.NET přejmenuje sloupec `CurrentPrice` na `Label`, který eliminuje nutnost zadat parametr `labelColumnName` pro Estimator algoritmus Machine Learning.

Pokud nechcete používat výchozí názvy sloupců, předejte při definování Estimator algoritmu pro strojové učení, které ukazuje následující fragment kódu, názvy sloupců funkce a popisku jako parametry:

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="train-the-machine-learning-model"></a>Výuka modelu Machine Learning

Jakmile jsou data předem zpracovaná, použijte metodu [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) k výuce modelu Machine learning pomocí [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) regresního algoritmu.

```csharp
// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a>Extrahovat parametry modelu

Po výuce modelu vyextrahujte získanou [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) pro kontrolu nebo opětovné školení. [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) poskytuje posun a zjištěné koeficienty nebo váhy vyškolených modelů.

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> Další modely mají parametry, které jsou specifické pro jejich úkoly. Například [algoritmus k znamená](xref:Microsoft.ML.Trainers.KMeansTrainer) , že data do clusteru jsou založena na centroids a [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) obsahuje vlastnost, která je uložena se zjištěnými centroids. Další informace najdete v dokumentaci k [rozhraní API`Microsoft.ML.Trainers`](xref:Microsoft.ML.Trainers) a hledejte třídy, které v názvu obsahují `ModelParameters`.

## <a name="evaluate-model-quality"></a>Vyhodnocení kvality modelu

Chcete-li si vybrat nejlepší model provádění, je nezbytné vyhodnotit jeho výkon na testovacích datech. Použijte metodu [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) k měření různých metrik pro vyškolený model.

> [!NOTE]
> Metoda `Evaluate` vytváří různé metriky v závislosti na tom, který úkol strojového učení byl proveden. Další podrobnosti najdete v [dokumentaci k rozhraní API`Microsoft.ML.Data`](xref:Microsoft.ML.Data) a hledejte třídy, které v názvu obsahují `Metrics`.

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

V předchozím příkladu kódu:

1. Testovací sada dat je předem zpracovaná pomocí transformací přípravných dat, které byly dříve definovány.
2. K předpovědií testovacích dat se používá školicí model strojového učení.
3. V metodě `Evaluate` jsou hodnoty ve sloupci `CurrentPrice` testovacích dat porovnány se sloupcem `Score` nově výstupního předpovědi pro výpočet metriky pro regresní model, přičemž jedna z nich je v `rSquared` proměnné uložena pomocí R-čtverce.

> [!NOTE]
> V tomto malém příkladu je R-kvadrát číslo, které není v rozsahu 0-1, protože je omezená velikost dat. Ve scénáři reálného světa byste měli očekávat zobrazení hodnoty mezi 0 a 1.
