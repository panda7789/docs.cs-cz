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
# <a name="train-and-evaluate-a-model"></a>Trénování a vyhodnocení modelu

Zjistěte, jak vytvářet modely strojového učení, shromažďovat metriky a měřit výkon s ML.NET. I když tato ukázka trénuje regresní model, koncepty jsou použitelné ve většině ostatních algoritmů.

## <a name="split-data-for-training-and-testing"></a>Rozdělení dat pro školení a testování

Cílem modelu strojového učení je identifikovat vzory v rámci trénovacích dat. Tyto vzory se používají k předpovědi pomocí nových dat.

Data mohou být modelována `HousingData`podle třídy, jako je .

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

Vzhledem k následujícím údajům, které jsou načteny do . [`IDataView`](xref:Microsoft.ML.IDataView)

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

Pomocí [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) metody rozdělte data do vlakových a testovacích sad. Výsledkem [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) bude objekt, který [`IDataView`](xref:Microsoft.ML.IDataView) obsahuje dva členy, jeden pro vlakové sady a druhý pro testovací sadu. Procento rozdělení dat je `testFraction` určeno parametrem. Níže uvedený úryvek podrží 20 procent původních dat pro testovací sadu.

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a>Příprava dat

Data musí být předem zpracovány před trénování modelu strojového učení. Více informací o přípravě dat naleznete na článku s [návody k přípravě dat](prepare-data-ml-net.md) a na [`transforms page`](../resources/transforms.md).

ML.NET algoritmy mají omezení pro typy vstupních sloupců. Kromě toho výchozí hodnoty se používají pro vstupní a výstupní názvy sloupců, pokud nejsou zadány žádné hodnoty.

### <a name="working-with-expected-column-types"></a>Práce s očekávanými typy sloupců

Algoritmy strojového učení v ML.NET očekávat plovoucí vektor známé velikosti jako vstup. Použijte [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) atribut na datový model, pokud jsou všechna data již v číselném formátu a jsou určena ke zpracování společně (tj. obrazové body).

Pokud data nejsou všechna číselná a chcete použít různé transformace dat na každý [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) sloupec jednotlivě, použijte metodu po zpracování všech sloupců a zkombinujte všechny jednotlivé sloupce do jednoho vektoru prvku, který je výstupem do nového sloupce.

Následující úryvek kombinuje `Size` sloupce `HistoricalPrices` a do jednoho vektoru prvku, který `Features`je výstupem do nového sloupce s názvem . Vzhledem k tomu, že [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) je rozdíl `Features` v měřítkách, se použije na sloupec normalizovat data.

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

### <a name="working-with-default-column-names"></a>Práce s výchozími názvy sloupců

ML.NET algoritmy používají výchozí názvy sloupců, pokud nejsou zadány žádné. Všechny školitelů `featureColumnName` mají parametr volaný pro vstupy algoritmu a v případě `labelColumnName`potřeby mají také parametr pro očekávanou hodnotu s názvem . Ve výchozím nastavení `Features` `Label` jsou tyto hodnoty a resp.

Pomocí [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) metody během předběžného zpracování k vytvoření `Features`nového sloupce s názvem , není nutné zadat název sloupce funkce v parametrech `IDataView`algoritmu, protože již existuje v předem zpracovaném . Sloupec popisek `CurrentPrice`je , [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) ale vzhledem k tomu, že `CurrentPrice` atribut `Label` se používá v datovém modelu, ML.NET přejmenuje sloupec, na který odebere potřebu poskytnout `labelColumnName` parametr pro odhad algoritmu strojového učení.

Pokud nechcete používat výchozí názvy sloupců, předejte názvy sloupců prvku a popisku jako parametry při definování odhadu algoritmu strojového učení, jak ukazuje následující úryvek:

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="train-the-machine-learning-model"></a>Trénování modelu strojového učení

Jakmile jsou data předem zpracována, [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) použijte metodu k trénování modelu strojového učení s regresním algoritmem. [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer)

```csharp
// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a>Extrahovat parametry modelu

Po vyškolení modelu vyhovuťte získané [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) poznatky pro inspekci nebo přeškolení. Poskytují [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) zkreslení a naučené koeficienty nebo hmotnosti trénovaného modelu.

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> Ostatní modely mají parametry, které jsou specifické pro jejich úkoly. [Například K-Means algoritmus](xref:Microsoft.ML.Trainers.KMeansTrainer) vloží data do clusteru [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) na základě centroids a obsahuje vlastnost, která ukládá tyto naučené centroids. Další informace najdete v `ModelParameters` [ `Microsoft.ML.Trainers` dokumentaci k rozhraní API](xref:Microsoft.ML.Trainers) a vyhledejte třídy, které obsahují v jejich názvu.

## <a name="evaluate-model-quality"></a>Vyhodnocení kvality modelu

Chcete-li pomoci vybrat nejvýkonnější model, je nezbytné vyhodnotit jeho výkon na testovací data. Pomocí [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) metody, k měření různých metrik pro trénovaný model.

> [!NOTE]
> Metoda `Evaluate` vytváří různé metriky v závislosti na tom, který úkol strojového učení byl proveden. Další podrobnosti naleznete v `Metrics` [ `Microsoft.ML.Data` dokumentaci k rozhraní API](xref:Microsoft.ML.Data) a vyhledejte třídy, které obsahují v jejich názvu.

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

V předchozí ukázce kódu:

1. Sada testovacích dat je předem zpracována pomocí dříve definovaných transformací přípravy dat.
2. Trénovaný model strojového učení se používá k předpovědi na testovací data.
3. V `Evaluate` metodě jsou hodnoty `CurrentPrice` ve sloupci sady testovacích `Score` dat porovnány se sloupcem nově výstupních předpovědí pro výpočet metrik pro regresní model, z nichž jedna, R-Squared je uložena v `rSquared` proměnné.

> [!NOTE]
> V tomto malém příkladu R-Squared je číslo není v rozsahu 0-1 z důvodu omezené velikosti dat. V reálném scénáři byste měli očekávat hodnotu mezi 0 a 1.
