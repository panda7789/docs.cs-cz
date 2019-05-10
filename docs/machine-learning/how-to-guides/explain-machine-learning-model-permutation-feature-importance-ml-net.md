---
title: Vysvětlují modelu predikce na základě důležitosti funkce permutaci
description: Pochopení důležitosti funkce modelů s důležitostí permutaci funkce v ML.NET
ms.date: 05/02/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: 2f444508990a902a1c61b72b1be2263d8d93ba70
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65066187"
---
# <a name="explain-model-predictions-using-permutation-feature-importance"></a>Vysvětlují modelu predikce na základě důležitosti funkce permutaci

Zjistěte, jak popisují ML.NET strojového učení předpovědí modelu podle principy, které funkce příspěvek muset predikce na základě důležitosti funkce permutací (PFI).

Modely strojového učení se často představit jako černé skříňky, které se daly přijímat vstupy a generovat výstup. Zprostředkující kroky nebo interakcí mezi funkcí, které ovlivňují výstupu jsou zřídka pochopitelné. Machine learning zavedeném do více aspektů každodenního života jako je například zdravotní péče, je naprosto pochopit, proč strojového učení rozhodnutí, která využívá model dělá. Například pokud Diagnostika vyrábí celá modelu strojového učení, odborníci v oblasti zdravotní péče potřebovat způsob, jak prozkoumat faktory, které byly přidány do toho, že Diagnostika. Poskytuje správné diagnostiku dokonce vytvářet velký rozdíl na, jestli pacienta má rychlé obnovení, nebo ne. Čím vyšší stupeň explainability v modelu, větší jistotou pracovníky tudíž přijmout nebo odmítnout rozhodnutí modelem.

Různých technik vytváření slouží k vysvětlení modelů, z nichž jeden je PFI. PFI je technika, použít k vysvětlení klasifikačních a regresních modelů, které se [společnosti Breiman *doménových struktur Random* papíru](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf)(viz část 10). Na vysoké úrovni je způsob, jakým funguje tak, že náhodně přesouvání dat jednu funkci současně pro celou datovou sadu a výpočtu, kolik metrika výkonu zájmu snižuje. Čím větší změny, důležitější, je tato funkce. 

Kromě toho zvýrazněním nejdůležitější funkce tvůrci modelu soustředit se na pomocí některé podsady lépe vystihuje funkcí, které může potenciálně snížit šum a čas školení.

## <a name="load-the-data"></a>Načtení dat

Funkce v datové sadě, se používají pro tuto ukázku se ve sloupcích 1 – 12. Cílem je možnost předvídat `Price`. 

| Sloupec | Funkce | Popis 
| --- | --- | --- |
| 1 | CrimeRate | Za hlavu crime
| 2 | ResidentialZones | Domácí zón ve městě
| 3 | CommercialZones | Domácí bez zón ve městě
| 4 | NearWater | Blízkosti textu vody
| 5 | ToxicWasteLevels | Toxicity úrovně (PPM)
| 6 | AverageRoomNumber | Průměrný počet místnosti interně
| 7 | HomeAge | Stáří Domovská stránka
| 8 | BusinessCenterDistance | Vzdálenost do nejbližší oblasti podnikání
| 9 | HighwayAccess | Blízkosti dálnice
| 10 | TaxRate | Sazba daně vlastnost
| 11 | StudentTeacherRatio | Poměr studentů pro učitele
| 12 | PercentPopulationBelowPoverty | Procento naplnění žijete pod chudoby
| 13 | Cena | Cena Domovská stránka

Ukázkové datové sady, která je zobrazena níže:

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

Data v této ukázce můžete modelovány pomocí třídy jako `HousingPriceData`:

```csharp
class HousingPriceData
{
    [LoadColumn(0)]
    public float CrimeRate { get; set; }

    [LoadColumn(1)]
    public float ResidentialZones { get; set; }

    [LoadColumn(2)]
    public float CommercialZones { get; set; }

    [LoadColumn(3)]
    public float NearWater { get; set; }

    [LoadColumn(4)]
    public float ToxicWasteLevels { get; set; }

    [LoadColumn(5)]
    public float AverageRoomNumber { get; set; }

    [LoadColumn(6)]
    public float HomeAge { get; set; }

    [LoadColumn(7)]
    public float BusinessCenterDistance { get; set; }

    [LoadColumn(8)]
    public float HighwayAccess { get; set; }

    [LoadColumn(9)]
    public float TaxRate { get; set; }

    [LoadColumn(10)]
    public float StudentTeacherRatio { get; set; }

    [LoadColumn(11)]
    public float PercentPopulationBelowPoverty { get; set; }

    [LoadColumn(12)]
    [ColumnName("Label")]
    public float Price { get; set; }
}
```

Načtení dat do [ `IDataView` ](xref:Microsoft.ML.IDataView).

## <a name="train-the-model"></a>Trénování modelu

Následující vzorový kód ukazuje procesu trénování modelu lineární regrese k předvídání cen organizace.

```csharp
// 1. Get the column name of input features.
string[] featureColumnNames = 
    data.Schema
        .Select(column => column.Name)
        .Where(columnName => columnName != "Label").ToArray();

// 2. Define estimator with data pre-processing steps
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", featureColumnNames)
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// 3. Create transformer using the data pre-processing estimator
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(data);

// 4. Pre-process the training data
IDataView preprocessedTrainData = dataPrepTransformer.Transform(data);

// 5. Define Stochastic Dual Coordinate Ascent machine learning estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// 6. Train machine learning model
var sdcaModel = sdcaEstimator.Fit(preprocessedTrainData);
```

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a>Vysvětlují modelu s permutaci funkce význam (PFI)

Používá ML.NET [ `PermutationFeatureImportance` ](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) metodu pro příslušné úlohy.

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance = 
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

Výsledek použití [ `PermutationFeatureImportance` ](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) na trénovací datové sady je [ `ImmutableArray` ](xref:System.Collections.Immutable.ImmutableArray) z [ `RegressionMetricsStatistics` ](xref:Microsoft.ML.Data.RegressionMetricsStatistics) objekty. [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) poskytuje souhrnné statistiky, jako je průměr a směrodatné odchylky pro více pozorování [ `RegressionMetrics` ](xref:Microsoft.ML.Data.RegressionMetrics) rovna počtu permutací určené `permutationCount` parametru.

Význam, nebo v tomto případě absolutní průměrná snížení spolehlivosti R metrika vypočte tak, že [ `PermutationFeatureImportance` ](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) lze pak provést řazení z vašich nejdůležitějších a nejméně důležitá.  

```csharp
// Order features by importance
var featureImportanceMetrics =
    permutationFeatureImportance
        .Select((metric, index) => new { index, metric.RSquared })
        .OrderByDescending(myFeatures => Math.Abs(myFeatures.RSquared.Mean));

Console.WriteLine("Feature\tPFI");

foreach (var feature in featureImportanceMetrics)
{
    Console.WriteLine($"{featureColumnNames[feature.index],-20}|\t{feature.RSquared.Mean:F6}");
}
```

Tisk hodnoty pro každé z těchto funkcí v `featureImportanceMetrics` vygenerují výstup podobný tomu níže. Mějte na paměti, která by se měl zobrazit odlišné výsledky vzhledem k tomu, že tyto hodnoty se liší podle data, která jsou uvedeny.  

| Funkce | Změnit na spolehlivosti R |
|:--|:--:|
HighwayAccess       |   -0.042731
StudentTeacherRatio |   -0.012730
BusinessCenterDistance| -0.010491
TaxRate             |   -0.008545
AverageRoomNumber   |   -0.003949
CrimeRate           |   -0.003665
CommercialZones     |   0.002749
HomeAge             |   -0.002426
ResidentialZones    |   -0.002319
NearWater           |   0.000203
PercentPopulationLivingBelowPoverty|    0.000031
ToxicWasteLevels    |   -0.000019

A podívejte se na pět nejdůležitější funkce pro tuto datovou sadu, cena house předpovídané pomocí tohoto modelu je ovlivněno umístění v blízkosti dálnice, studenty, vyučující poměr školy v oblasti, blízkosti hlavní zaměstnání centra, sazba daně vlastnost a Průměrný počet místnosti na domovské stránce.