---
title: Trénování a vyhodnocení modelu
description: Zjistěte, jak vytvářet modely strojového učení, extrahovat zjištěná parametry a měření výkonu s ML.NET. I když tato ukázka trénovat regresní model, koncepty platí v celé většinou ostatní algoritmy.
ms.date: 06/11/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0612
ms.openlocfilehash: b7799d19f5ad51ce509cc6872d9053cad1158552
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025590"
---
# <a name="train-and-evaluate-a-model"></a>Trénování a vyhodnocení modelu

Zjistěte, jak vytvářet modely strojového učení, extrahovat zjištěná parametry a měření výkonu s ML.NET. I když tato ukázka trénovat regresní model, koncepty platí v celé většinou ostatní algoritmy.

## <a name="split-data-for-training-and-testing"></a>Rozdělení dat pro trénování a testování

Cílem model strojového učení je pro identifikaci vzorů v rámci trénovací data. Tyto vzory se používají k vytvářet predikce na nová data.

Zadaný datový model následující:

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

Načtení dat do [ `IDataView` ](xref:Microsoft.ML.IDataView):

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

Použití [ `TrainTestSplit` ](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) metodu pro rozdělení dat na trénování a testování sad. Výsledkem bude [ `TrainTestData` ](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) objekt, který obsahuje dva [ `IDataView` ](xref:Microsoft.ML.IDataView) členy, jeden pro sadu trénování a druhý pro testovací sadu. Data rozdělit procento závisí `testFraction` parametru. Následující fragment drží si 20 procent společností z žebříčku původní data pro sadu testů.

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a>Příprava dat

Data musí být předem zpracovaných před trénování modelu strojového učení. Další informace o přípravě dat můžete najít na [článek pro přípravu dat](prepare-data-ml-net.md) také [ `transforms page` ](../resources/transforms.md).

Algoritmy ML.NET mají omezení týkající se sloupci vstupní typy. Navíc jsou použity výchozí hodnoty pro názvy sloupců vstupních a výstupních, když nejsou určeny žádné hodnoty.

### <a name="working-with-expected-column-types"></a>Práce s typy očekávaných sloupců

Algoritmy strojového učení v ML.NET očekávat float vektor známou velikost jako vstup. Použít [ `VectorType` ](xref:Microsoft.ML.Data.VectorTypeAttribute) atribut datový model, při všech dat je již v číselném formátu a má být zpracovány současně (tj. pixely obrázku). 

Pokud data nejsou všechny číselné a chcete k použití různých datových transformací na všech sloupcích jednotlivě, použijte [ `Concatenate` ](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) metoda po všech sloupců byly zpracovány ke sloučení všech jednotlivých sloupců vektor jednu funkci, která je výstup do nového sloupce. 

Následující fragment kódu kombinuje `Size` a `HistoricalPrices` názvem sloupce do jednoho funkce vektor, který je výstup do nového sloupce `Features`. Vzhledem k tomu, že existuje rozdíl v škálování, [ `NormalizeMinMax` ](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) platí pro `Features` k normalizaci dat sloupce.

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

### <a name="working-with-default-column-names"></a>Práce s výchozí názvy sloupců

ML.NET algoritmy používat výchozí názvy sloupců, pokud jsou zadána žádná. Všechny školitelé mít parametr s názvem `featureColumnName` vstupů algoritmu a použít parametr pro očekávané hodnoty mají také volat `labelColumnName`. Ve výchozím nastavení jsou tyto hodnoty `Features` a `Label` v uvedeném pořadí. 

S použitím [ `Concatenate` ](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) volána metoda během předběžného zpracování k vytvoření nového sloupce `Features`, není nutné zadat název sloupce funkce v parametrech algoritmus, protože již existuje v Předběžně zpracovat `IDataView`. Popisek sloupce je `CurrentPrice`, ale od té doby [ `ColumnName` ](xref:Microsoft.ML.Data.ColumnNameAttribute) atribut se používá v datovém modelu, ML.NET přejmenuje `CurrentPrice` sloupec, který se `Label` což eliminuje nutnost poskytnout `labelColumnName` parametr se strojovým učením estimator algoritmus. 

Pokud už nechcete používat výchozí názvy sloupců, předejte názvy sloupců funkce a popisek jako parametry při definování strojového učení algoritmu odhad, jak je uvedeno v následující fragment kódu:

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="train-the-machine-learning-model"></a>Trénování modelu strojového učení

Jakmile jsou data předem zpracovaných, použijte [ `Fit` ](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) metodu pro trénování modelu strojového učení s [ `StochasticDualCoordinateAscent` ](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) regresní algoritmus.

```csharp
// Define StochasticDualCoodrinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a>Extrahovat parametry modelu

Jakmile model se trénuje, extrahovat zjištěná [ `ModelParameters` ](xref:Microsoft.ML.Trainers.ModelParametersBase%601) pro kontrolu nebo znovu školení. [ `LinearRegressionModelParameters` ](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) Posunu omezení a zjištěná nebo váhy trénovaného modelu. 

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> Další modely mají parametry, které jsou specifické pro jejich úkoly. Například [algoritmus K-Means](xref:Microsoft.ML.Trainers.KMeansTrainer) zařadí data do clusteru podle centroids a [ `KMeansModelParameters` ](xref:Microsoft.ML.Trainers.KMeansModelParameters) obsahuje vlastnost, která ukládá tyto zkušenosti centroids. Další informace najdete [ `Microsoft.ML.Trainers` dokumentace k rozhraní API](xref:Microsoft.ML.Trainers) a hledejte tříd, které obsahují `ModelParameters` v názvu. 

## <a name="evaluate-model-quality"></a>Vyhodnocení kvalita modelu

Pomoc při výběru nejvýkonnějšího modelu, je nutné vyhodnotit její výkon na testovací data. Použití [ `Evaluate` ](xref:Microsoft.ML.RegressionCatalog.Evaluate*) metoda měření různé metriky pro trénovaného modelu.

> [!NOTE]
> `Evaluate` Metoda vytvoří různých metrik v závislosti na počítač, který byl learning úloha byla provedena. Další informace najdete [ `Microsoft.ML.Data` dokumentace k rozhraní API](xref:Microsoft.ML.Data) a hledejte tříd, které obsahují `Metrics` v názvu. 

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
1. Sada testovacích dat. předem zpracována pomocí transformace přípravy dat definovaný dříve. 
2. Model trénovaného machine learning slouží k vytvoření predikcí testovací data.
3. V `Evaluate` metody, hodnoty `CurrentPrice` sloupce datové sady testů se porovná s `Score` nově výstupní sloupec modelu předpovědi pro výpočet metrik pro regresi, jedním z nich, spolehlivosti R je uložen v `rSquared` proměnné.

> [!NOTE]
> V tomto příkladu malé spolehlivosti R je číslo není v rozsahu 0-1 z důvodu omezené množství dat. Reálný scénář měli byste očekávat zobrazit hodnotu mezi 0 a 1.
