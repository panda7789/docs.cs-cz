---
title: Interpretovat ML.NET modely s důležitostí permutačních vlastností
description: Seznamte se s významem funkcí modelů s významem funkce permutace v ML.NET
ms.date: 01/30/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: c1163a41cd2feb0e8785ae9d4c6a71dfbedf3f12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77092613"
---
# <a name="interpret-model-predictions-using-permutation-feature-importance"></a>Interpretovat předpovědi modelu pomocí důležitosti funkce permutace

Pomocí důležitosti funkce permutace (PFI) se dozvíte, jak interpretovat ML.NET předpovědi modelu strojového učení. PFI poskytuje relativní příspěvek každé funkce k predikci.

Modely strojového učení jsou často považovány za černé skříňky, které berou vstupy a generují výstup. Mezilehlé kroky nebo interakce mezi funkcemi, které ovlivňují výstup, jsou zřídka pochopeny. Vzhledem k tomu, že strojové učení je zavedeno do dalších aspektů každodenního života, jako je zdravotní péče, je nanejvýš důležité pochopit, proč model strojového učení činí rozhodnutí, která činí. Pokud jsou například diagnózy prováděny modelem strojového učení, potřebují zdravotničtí pracovníci způsob, jak se podívat na faktory, které byly provedeny při vytváření této diagnózy. Poskytnutí správné diagnózy by mohlo mít velký vliv na to, zda má pacient rychlé zotavení nebo ne. Proto čím vyšší je úroveň vysvětlitelnosti v modelu, tím větší důvěra zdravotnických pracovníků musí přijmout nebo odmítnout rozhodnutí učiněná modelem.

Různé techniky se používají k vysvětlení modelů, z nichž jeden je PFI. PFI je technika používaná k vysvětlení klasifikačních a regresních modelů, která je [inspirována Breimanovým *papírem Random Forests* ](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) (viz oddíl 10). Na vysoké úrovni, způsob, jakým to funguje, je náhodným mícháním dat po jedné funkci pro celou datovou sadu a výpočtem, o kolik se snižuje metrika výkonu zájmu. Čím větší je změna, tím důležitější je tato funkce.

Kromě toho zvýrazněním nejdůležitějších funkcí se tvůrci modelů mohou zaměřit na použití podmnožiny smysluplnějších funkcí, které mohou potenciálně snížit hluk a dobu školení.

## <a name="load-the-data"></a>Načtení dat

Funkce v datové sadě používané pro tuto ukázku jsou ve sloupcích 1-12. Cílem je předpovědět `Price`.

| Sloupec | Funkce | Popis
| --- | --- | --- |
| 1 | Míra kriminality | Míra kriminality na obyvatele
| 2 | Obytné zóny | Obytné zóny ve městě
| 3 | Komerční zóny | Nebytové zóny ve městě
| 4 | V blízkostiVoda | Blízkost vodního útvaru
| 5 | Toxické odpadyÚrovně | Úrovně toxicity (PPM)
| 6 | AverageRoomNumber | Průměrný počet pokojů v domě
| 7 | Domácí věk | Věk domova
| 8 | Vzdálenost businesscentra | Vzdálenost do nejbližší obchodní čtvrti
| 9 | HighwayAccess | Blízkost dálnic
| 10 | Daňová sazba | Sazba daně z nemovitých věcí
| 11 | StudentUčitelRatio | Poměr studentů k učitelům
| 12 | PercentPopulationBelowChudoba | Procento obyvatel žijících pod hranicí chudoby
| 13 | Price | Cena domu

Ukázka datové sady je uvedena níže:

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

Data v této ukázce mohou `HousingPriceData` být modelována podle třídy jako a načtena do . [`IDataView`](xref:Microsoft.ML.IDataView)

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

Níže uvedený příklad kódu ilustruje proces školení lineárníregresní model předpovědět ceny domů.

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

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a>Vysvětlete model s důležitostí permutačních vlastností (PFI)

V ML.NET [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) použijte metodu pro příslušný úkol.

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance =
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

Výsledkem použití [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) na trénovací [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) datové sady je objekty. [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics)poskytuje souhrnné statistiky, jako je střední [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) a směrodatná odchylka `permutationCount` pro více pozorování rovnající se počtu permutací určených parametrem.

Důležitost nebo v tomto případě absolutní průměrný pokles metriky R-kvadrát vypočítaný lze [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) pak seřadit z nejdůležitějšího na nejméně důležitý.

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

Tisk hodnot pro každou z `featureImportanceMetrics` funkcí v in by generovat výstup podobný níže. Mějte na paměti, že byste měli očekávat, že se zobrazí různé výsledky, protože tyto hodnoty se liší v závislosti na datech, která jsou uvedena.

| Funkce | Změnit na R-Squared |
|:--|:--:|
HighwayAccess       |   -0.042731
StudentUčitelRatio |   -0.012730
Vzdálenost businesscentra| -0.010491
Daňová sazba             |   -0.008545
AverageRoomNumber   |   -0.003949
Míra kriminality           |   -0.003665
Komerční zóny     |   0.002749
Domácí věk             |   -0.002426
Obytné zóny    |   -0.002319
V blízkostiVoda           |   0.000203
PercentPopulationLivingPodchudoba|    0.000031
Toxické odpadyÚrovně    |   -0.000019

Podíváme-li se na pět nejdůležitějších prvků pro tuto datovou sadu, cena domu předpovídaná tímto modelem je ovlivněna jeho blízkostí k dálnicím, poměrem studentů škol v této oblasti, blízkostí k hlavním pracovním centrům, sazbou daně z nemovitosti a průměrný počet pokojů v domácnosti.
