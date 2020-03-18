---
title: Trénování modelu strojového učení pomocí křížového ověřování
description: Naučte se používat křížové ověřování k vytváření robustnějších modelů strojového učení v ML.NET. Křížové ověřování je technika trénování a vyhodnocení modelu, která rozděluje data do několika oddílů a trénuje více algoritmů na těchto oddílech.
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to,title-hack-0625
ms.openlocfilehash: 87eae789478752423f3e682d4db6cead0391aa6e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73976927"
---
# <a name="train-a-machine-learning-model-using-cross-validation"></a>Trénování modelu strojového učení pomocí křížového ověřování

Naučte se používat křížové ověřování k trénování robustnějších modelů strojového učení v ML.NET.

Křížové ověřování je technika trénování a vyhodnocení modelu, která rozděluje data do několika oddílů a trénuje více algoritmů na těchto oddílech. Tato technika zlepšuje robustnost modelu tím, že podrží data z tréninkového procesu. Kromě zlepšení výkonu na neviditelné pozorování, v prostředí s omezenými daty může být účinným nástrojem pro trénování modelů s menší datovou sadou.

## <a name="the-data-and-data-model"></a>Datový a datový model

Uvedená data ze souboru, který má následující formát:

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
620.00, 148330.32, 140913.81, 136686.39, 146105.37
550.00, 557033.46, 529181.78, 513306.33, 548677.95
1127.00, 479320.99, 455354.94, 441694.30, 472131.18
1120.00, 47504.98, 45129.73, 43775.84, 46792.41
```

Data mohou být modelována `HousingData` podle třídy, jako je, a načtena do . [`IDataView`](xref:Microsoft.ML.IDataView)

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

Před zpracováním dat před jejich použitím k vytvoření modelu strojového učení. V této ukázce jsou sloupce `Size` a `HistoricalPrices` sloučeny do jednoho vektoru `Features` prvku, který je výstupem do nového sloupce nazývaného [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) pomocí metody. Kromě získávání dat do formátu očekávaného ML.NET algoritmy, zřetězení sloupců optimalizuje následné operace v kanálu použitím operace jednou pro zřetězený sloupec namísto každého ze samostatných sloupců.

Jakmile jsou sloupce sloučeny do [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) jednoho vektoru, je `Size` `HistoricalPrices` použita na `Features` sloupec získat a ve stejném rozsahu mezi 0-1.

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

## <a name="train-model-with-cross-validation"></a>Model vlaku s křížovou validací

Jakmile jsou data předem zpracována, je čas trénovat model. Nejprve vyberte algoritmus, který je nejvíce v souladu s úlohou strojového učení, která má být provedena. Vzhledem k tomu, že předpovídaná hodnota je číselně souvislá hodnota, úkol je regrese. Jedním z regresních algoritmů implementovaných [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) ML.NET je algoritmus. Chcete-li trénovat model s [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) křížovým ověřením, použijte metodu.

> [!NOTE]
> Přestože tato ukázka používá lineární regresní model, CrossValidate se vztahuje na všechny ostatní úlohy strojového učení v ML.NET s výjimkou detekce anomálií.

```csharp
// Define StochasticDualCoordinateAscent algorithm estimator
IEstimator<ITransformer> sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Apply 5-fold cross validation
var cvResults = mlContext.Regression.CrossValidate(transformedData, sdcaEstimator, numberOfFolds: 5);
```

[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*)provádí následující operace:

1. Rozdělí data do počtu oddílů rovnající se hodnotě zadané v parametru. `numberOfFolds` Výsledkem každého oddílu [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) je objekt.
1. Model je trénovaný na každém z oddílů pomocí zadaný odhad algoritmu strojového učení na trénovací datové sady.
1. Výkon každého modelu je vyhodnocen pomocí metody na [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) testovací datové sadě.
1. Model spolu s jeho metriky jsou vráceny pro každý z modelů.

Výsledek uložený `cvResults` v je [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) kolekce objektů. Tento objekt zahrnuje trénovaný model, stejně [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) jako [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics) metriky, které jsou přístupné z a vlastnosti v uvedeném pořadí. V této `Model` ukázce [`ITransformer`](xref:Microsoft.ML.ITransformer) je `Metrics` vlastnost typu [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics)a vlastnost je typu .

## <a name="evaluate-the-model"></a>Vyhodnocení modelu

Metriky pro různé trénované modely `Metrics` lze přistupovat prostřednictvím vlastnosti jednotlivého [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) objektu. V tomto případě [r-kvadrát metrika](https://en.wikipedia.org/wiki/Coefficient_of_determination) je `rSquared`přístupná a uloženy v proměnné .

```csharp
IEnumerable<double> rSquared =
    cvResults
        .Select(fold => fold.Metrics.RSquared);
```

Pokud zkontrolujete obsah `rSquared` proměnné, výstup by měl být pět hodnot v rozsahu od 0-1, kde blíže k 1 znamená nejlepší. Pomocí metrik, jako je R-Squared, vyberte modely od nejlepšího po nejhorší. Potom vyberte nejvyšší model, chcete-li předpovědět nebo provést další operace s.

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
