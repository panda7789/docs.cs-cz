---
title: Výuka modelu strojového učení pomocí vzájemného ověřování
description: Naučte se používat vzájemné ověřování k vytváření robustnějších modelů strojového učení v ML.NET. Křížové ověřování je technikou pro vyhodnocení školení a modelů, které rozdělí data do několika oddílů a navlakuje více algoritmů na těchto oddílech.
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to,title-hack-0625
ms.openlocfilehash: 87eae789478752423f3e682d4db6cead0391aa6e
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976927"
---
# <a name="train-a-machine-learning-model-using-cross-validation"></a>Výuka modelu strojového učení pomocí vzájemného ověřování

Naučte se používat vzájemné ověřování k výuce robustnějších modelů strojového učení v ML.NET.

Křížové ověřování je technikou pro vyhodnocení školení a modelů, které rozdělí data do několika oddílů a navlakuje více algoritmů na těchto oddílech. Tento postup zvyšuje odolnost modelu tím, že podrží data z procesu školení. Kromě zlepšení výkonu u nezpracovaných pozorování v prostředích s omezenými daty může být účinný nástroj pro školení modelů s menší datovou sadou.

## <a name="the-data-and-data-model"></a>Data a datový model

Zadaná data ze souboru, který má následující formát:

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
620.00, 148330.32, 140913.81, 136686.39, 146105.37
550.00, 557033.46, 529181.78, 513306.33, 548677.95
1127.00, 479320.99, 455354.94, 441694.30, 472131.18
1120.00, 47504.98, 45129.73, 43775.84, 46792.41
```

Data lze modelovat podle třídy, jako je `HousingData` a načtena do [`IDataView`](xref:Microsoft.ML.IDataView).

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

## <a name="prepare-the-data"></a>Příprava dat

Předem zpracujte data před jejich použitím k sestavení modelu Machine Learning. V této ukázce jsou sloupce `Size` a `HistoricalPrices` sloučeny do jediného vektoru funkce, který je výstupem do nového sloupce s názvem `Features` pomocí metody [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) . Kromě získání dat do formátu očekávaného algoritmy ML.NET optimalizuje sloupce následné operace v kanálu, a to použitím operace jednou pro zřetězený sloupec místo každého samostatného sloupce.

Až se sloupce sloučí do jednoho vektoru, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) se u sloupce `Features` použije k získání `Size` a `HistoricalPrices` ve stejném rozsahu mezi 0-1.

```csharp
// Define data prep estimator
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", new string[] { "Size", "HistoricalPrices" })
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// Create data prep transformer
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(data);

// Transform data
IDataView transformedData = dataPrepTransformer.Transform(data);
```

## <a name="train-model-with-cross-validation"></a>Výuka modelu pomocí vzájemného ověřování

Jakmile jsou data předem zpracovaná, je čas je vyškolit. Nejdřív vyberte algoritmus, který nejlépe odpovídá úloze strojového učení, která se má provést. Vzhledem k tomu, že předpokládaná hodnota je numericky souvislá hodnota, je úkol regresní. Jedním z regresních algoritmů implementovaných službou ML.NET je [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) algoritmus. Pro výuku modelu pomocí křížového ověřování použijte metodu [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) .

> [!NOTE]
> I když tato ukázka používá model lineární regrese, CrossValidate se vztahuje na všechny ostatní úlohy strojového učení v ML.NET s výjimkou detekce anomálií.

```csharp
// Define StochasticDualCoordinateAscent algorithm estimator
IEstimator<ITransformer> sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Apply 5-fold cross validation
var cvResults = mlContext.Regression.CrossValidate(transformedData, sdcaEstimator, numberOfFolds: 5);
```

[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) provádí následující operace:

1. Rozdělí data do několika oddílů, které se rovnají hodnotě zadané v parametru `numberOfFolds`. Výsledkem každého oddílu je [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) objekt.
1. Model se vystavuje na každém oddílu pomocí zadaného algoritmu strojového učení Estimator v sadě školicích dat.
1. Výkon každého modelu se vyhodnocuje pomocí metody [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) v sadě testovacích dat.
1. Model spolu s jeho metrikami se vrátí pro každý model.

Výsledek uložený v `cvResults` je kolekce objektů [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) . Tento objekt obsahuje trained model a také metriky, které jsou přístupné ve formě [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) a [`Metrics`ch](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics) vlastností v uvedeném pořadí. V této ukázce je vlastnost `Model` typu [`ITransformer`](xref:Microsoft.ML.ITransformer) a vlastnost `Metrics` je typu [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics).

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

K metrikám různých vyškolených modelů lze přistupovat prostřednictvím vlastnosti `Metrics` jednotlivého objektu [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) . V tomto případě je k dispozici [metrika R-kvadrát](https://en.wikipedia.org/wiki/Coefficient_of_determination) , která je uložena v proměnné `rSquared`.

```csharp
IEnumerable<double> rSquared =
    cvResults
        .Select(fold => fold.Metrics.RSquared);
```

Pokud provedete kontrolu obsahu `rSquared` proměnné, výstup by měl mít pět hodnot od 0-1, kde blíže k 1 znamená nejlepší. Pomocí metrik, jako je R-kvadrát, vyberte modely od nejvyšších po nejhorší výkon. Pak vyberte horní model, který bude předpovědi, nebo proveďte další operace s.

```csharp
// Select all models
ITransformer[] models =
    cvResults
        .OrderByDescending(fold => fold.Metrics.RSquared)
        .Select(fold => fold.Model)
        .ToArray();

// Get Top Model
ITransformer topModel = models[0];
```
