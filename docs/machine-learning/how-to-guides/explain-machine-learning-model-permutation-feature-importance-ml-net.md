---
title: Vysvětlete předpovědi modelů pomocí funkce permutace důležitost
description: Pochopení funkcí důležitosti modelů s funkcí permutace v ML.NET
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: 9617582c79b2278e3a68e7acf84568247b81eca1
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70167658"
---
# <a name="explain-model-predictions-using-permutation-feature-importance"></a>Vysvětlete předpovědi modelů pomocí funkce permutace důležitost

Naučte se vysvětlovat ML.NET Machine Learning model předpovědi tím, že porozumíte funkcím příspěvku předpovědi pomocí funkce permutace důležitost (PFI).

Modely strojového učení se často považovat za černé čtverečky, které přijímají vstupy a generují výstup. Zprostředkující kroky nebo interakce mezi funkcemi, které ovlivňují výstup, se zřídka rozumí. Vzhledem k tomu, že je strojové učení zahrnuté do více aspektů každodenního života, jako je zdravotní péče, je velmi důležité pochopit, proč model strojového učení provádí rozhodnutí. Například pokud jsou diagnostiky provedeny modelem strojového učení, odborníci na zdravotní péči potřebují způsob, jak se podívat na faktory, které se při diagnostikování prováděly. Poskytnutí správné diagnostiky by mohlo způsobit velký rozdíl na tom, jestli má pacient rychlejší obnovení. Čím vyšší je úroveň vyjasnění v modelu, větší spolehlivé odborníky na zdravotní péči musí přijmout nebo odmítnout rozhodnutí učiněná modelem.

K vysvětlení modelů, z nichž jeden je PFI, se používají různé techniky. PFI je technika, která se používá k vysvětlení klasifikací a regresních modelů, které jsou nechte inspirovaty pomocí [ *náhodných doménových struktur* Breiman](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf)(viz oddíl 10). Na nejvyšší úrovni je způsob, jakým funguje, náhodným pohybem dat pro celou datovou sadu a výpočtem množství metriky výkonu, které se v zájmu sníží. Čím větší je tato změna, tím důležitější je funkce. 

Kromě toho zvýrazňováním nejdůležitějších funkcí se mohou tvůrci modelů soustředit na použití podmnožiny smysluplných funkcí, které mohou potenciálně snižovat dobu šumu a školení.

## <a name="load-the-data"></a>Načtení dat

Funkce v datové sadě používané pro tuto ukázku jsou ve sloupcích 1-12. Cílem je předpovědět `Price`. 

| Sloupec | Funkce | Popis 
| --- | --- | --- |
| 1 | CrimeRate | Sazba za trestných činů za hlavu
| 2 | ResidentialZones | Místní zóny ve městě
| 3 | CommercialZones | Jiné než místní zóny ve městě
| 4 | NearWater | Blízkost k tělo vody
| 5 | ToxicWasteLevels | Úrovně toxicity (PPM)
| 6 | AverageRoomNumber | Průměrný počet místností v domu
| 7 | Domovská stránka | Stáří domů
| 8 | BusinessCenterDistance | Vzdálenost k nejbližší obchodní oblasti
| 9 | HighwayAccess | Blízkost k dálnicím
| 10 | TaxRate | Daňová sazba vlastnosti
| 11 | StudentTeacherRatio | Poměr studentů k učitelům
| 12 | PercentPopulationBelowPoverty | Procento populace žijících po chudobě
| 13 | Cena | Cena domovské stránky

Ukázka datové sady je uvedena níže:

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

Data v této ukázce lze modelovat podle třídy, jako `HousingPriceData` je a načtena [`IDataView`](xref:Microsoft.ML.IDataView)do.

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

## <a name="train-the-model"></a>Trénování modelu

Následující ukázka kódu znázorňuje proces školení modelu lineární regrese k předvídání cen za domácnosti.

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

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a>Vysvětlení modelu s funkcí permutace – důležitost (PFI)

V ml.NET použijte [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) metodu pro příslušnou úlohu.

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance = 
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

Výsledkem použití [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) v datové sadě školení [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) je [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) objekt. [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics)poskytuje souhrnnou statistiku, například střední hodnotu a směrodatnou odchylku pro více pozorování [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) rovnající se počtu permutací určených `permutationCount` parametrem.

Důležitost, nebo v tomto případě je absolutní průměrná míra snížení metriky R-čtverce vypočítaná pomocí [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) lze seřadit od nejdůležitějších po nejméně důležité.  

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

Tisk hodnot pro jednotlivé funkce v `featureImportanceMetrics` nástroji by vygeneroval výstup podobný tomuto:. Mějte na paměti, že byste měli očekávat, že byste měli zobrazit různé výsledky, protože tyto hodnoty se liší v závislosti na datech, která jsou uvedena.  

| Funkce | Změnit na R-čtvercový |
|:--|:--:|
HighwayAccess       |   -0,042731
StudentTeacherRatio |   -0,012730
BusinessCenterDistance| -0,010491
TaxRate             |   -0,008545
AverageRoomNumber   |   -0,003949
CrimeRate           |   -0,003665
CommercialZones     |   0,002749
Domovská stránka             |   -0,002426
ResidentialZones    |   -0,002319
NearWater           |   0,000203
PercentPopulationLivingBelowPoverty|    0,000031
ToxicWasteLevels    |   -0,000019

Podíváme se na pět nejdůležitějších funkcí pro tuto datovou sadu. cena na pracovišti, kterou tento model předpovídá, je ovlivněná jeho blízkostí vůči dálnicím, poměru učitelů v oblasti škol v oblasti, blízkost k hlavním pracovním centrům, daňové sazbě vlastností a Průměrný počet místností v domácnosti
