---
title: Natrénování a vyhodnocení modelu strojového učení pomocí křížového ověření
description: Zjistěte, jak trénovat a vyhodnocovat u nich model strojového učení pomocí křížového ověření
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: a15dfbfcd563cf9df9c25779a5854a9f556523d1
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65066163"
---
# <a name="train-and-evaluate-a-machine-learning-model-using-cross-validation"></a>Natrénování a vyhodnocení modelu strojového učení pomocí křížového ověření

Zjistěte, jak můžete vytvářet robustnější modely strojového učení v ML.NET křížového ověření. 

Křížové ověření je školení a model hodnocení technika, která rozdělí data do několika oddílů a trénovat více algoritmy v těchto oddílech. Tento postup zlepšuje odolnost modelu tím, že se data z procesu trénování. Kromě vylepšení výkonu na neviditelný pozorování, v prostředí omezené dat může být efektivní nástroj pro trénování modelů s menší datové sady.

## <a name="the-data-and-data-model"></a>Data a datový model

Zadaný data ze souboru, který má následující formát:

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
620.00, 148330.32, 140913.81, 136686.39, 146105.37
550.00, 557033.46, 529181.78, 513306.33, 548677.95
1127.00, 479320.99, 455354.94, 441694.30, 472131.18
1120.00, 47504.98, 45129.73, 43775.84, 46792.41
```

Data můžete modelovány pomocí třídy jako `HousingData`:

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

Načtení dat do do [ `IDataView` ](xref:Microsoft.ML.IDataView).

## <a name="prepare-the-data"></a>Příprava dat

Předběžně zpracovat data před sestavením modelu strojového učení. V této ukázce `Size` a `HistoricalPrices` sloupce jsou sloučeny do jednoho funkce vektor, který je použita pro nový sloupec s názvem `Features` pomocí [ `Concatenate` ](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) metody. Kromě získávání dat do formátu očekávaném ML.NET algoritmy, zřetězení sloupce optimalizuje následné operace v kanálu použitím operace pro zřetězených sloupců místo jednotlivých samostatné sloupce. 

Jakmile sloupce, které jsou sloučeny do jednoho vektoru [ `NormalizeMinMax` ](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) platí pro `Features` sloupce, chcete-li získat `Size` a `HistoricalPrices` ve stejném rozsahu od 0 – 1. 

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

## <a name="train-model-with-cross-validation"></a>Trénování modelu s křížové ověření

Jakmile byl předem zpracovaných dat, je čas pro trénování modelu. Nejdřív vyberte algoritmus, který nejlépe odpovídá strojového učení úloh, která se má provést. Protože předpovězené hodnoty je číselně průběžné hodnota, je úloha regrese. Jeden z algoritmů regrese implementované ML.NET je [ `StochasticDualCoordinateAscentCoordinator` ](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) algoritmus. Pro trénování modelu s použitím křížového ověření [ `CrossValidate` ](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) metody. 

> [!NOTE]
> I když tato ukázka používá model lineární regrese, CrossValidate se vztahuje na všechny ostatní strojového učení úkoly v ML.NET s výjimkou detekce anomálií.

```csharp
// Define StochasticDualCoordinateAscent algorithm estimator
IEstimator<ITransformer> sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Apply 5-fold cross validation
var cvResults = mlContext.Regression.CrossValidate(transformedData, sdcaEstimator, numberOfFolds: 5);
```

[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) provádí následující operace:

1. Rozděluje data do několika oddílů, které se rovná hodnotě zadané v `numberOfFolds` parametru. Výsledek každý oddíl je [ `TrainTestData` ](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) objektu.
1. Model se trénuje na všech oddílů pomocí zadaného strojového učení algoritmu odhaduje na trénovací datové sady.
1. Každý model výkonu je vyhodnocen pomocí [ `Evaluate` ](xref:Microsoft.ML.RegressionCatalog.Evaluate*) metodu na testovací datové sady. 
1. Model spolu s jeho metriky se vrátí pro každou modelů.

Výsledek je uložen v `cvResults` je kolekce [ `CrossValidationResult` ](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult`1) objekty. Tento objekt obsahuje trénovaného modelu, stejně jako metriky, které jsou obě přístupné formuláře [ `Model` ](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult`1.Model) a [ `Metrics` ](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult`1.Metrics) vlastnosti v uvedeném pořadí. V této ukázce `Model` vlastnost je typu [ `ITransformer` ](xref:Microsoft.ML.ITransformer) a `Metrics` vlastnost je typu [ `RegressionMetrics` ](xref:Microsoft.ML.Data.RegressionMetrics). 

## <a name="extract-metrics"></a>Extrahovat metriky

Metriky pro různé trénované modely přístupné prostřednictvím `Metrics` vlastnost jednotlivých [ `CrossValidationResult` ](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) objektu. V takovém případě [spolehlivosti R metrika](https://en.wikipedia.org/wiki/Coefficient_of_determination) se často a ukládají v proměnné `rSquared`. 

```csharp
IEnumerable<double> rSquared = 
    cvResults
        .Select(fold => fold.Metrics.RSquared);
```

Je-li si prohlédnout obsah `rSquared` proměnné, výstup by měl být pět hodnoty v rozsahu od 0-1, kde blíže 1 znamená, že nejlepší.

## <a name="select-the-best-performing-model"></a>Výběr nejvýkonnějšího modelu

Použití metrik, jako je spolehlivosti R, vyberte modelů z nejlepších nejhorší provádění. Vyberte hlavní model k predikci nebo provádět další operace s.

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
