---
title: Zkontrolovat hodnoty dočasných dat během zpracování kanálu ML.NET
description: Zjistěte, jak zkontrolovat hodnoty skutečné dočasných dat během ML.NET strojového učení zpracování kanálu
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 3d20f153be7b502fb5a542a942245546412efde2
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57678641"
---
# <a name="inspect-intermediate-data-values-during-mlnet-pipeline-processing"></a>Zkontrolovat hodnoty dočasných dat během zpracování kanálu ML.NET

> [!NOTE]
> Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit. Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Aktuálně používáte této ukázky s postupy a související **ML.NET verze 0.10**. Další informace najdete v tématu poznámky k verzi v [úložiště GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

Během testu můžete sledovat a ověřte výsledky zpracování dat v časovém okamžiku. To není snadné, protože operace ML.NET jsou opožděná, vytváření objektů, které jsou "příslibů" dat.

`GetColumn<T>` – Metoda rozšíření umožňuje kontrolovat zprostředkující data. Vrátí obsah jako jeden datový sloupec `IEnumerable`.

Následující příklad ukazuje způsob použití `GetColumn<T>` – metoda rozšíření:

[Příklad souboru](https://github.com/dotnet/machinelearning/tree/master/test/data/adult.tiny.with-schema.txt):
```
Label   Workclass   education   marital-status
0   Private 11th    Never-married
0   Private HS-grad Married-civ-spouse
1   Local-gov   Assoc-acdm  Married-civ-spouse
1   Private Some-college    Married-civ-spouse

```

Naše třída je definována takto:

```csharp
public class InspectedRow
{
    [LoadColumn(0)]
    public bool IsOver50K { get; set; }
    [LoadColumn(1)]
    public string WorkClass { get; set; }
    [LoadColumn(2)]
    public string Education { get; set; }
    [LoadColumn(3)]
    public string MaritalStatus { get; set; }
}
```

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Read the data into a data view.
var data = mlContext.Data.ReadFromTextFile<InspectedRow>(dataPath, hasHeader: true);

// Start creating our processing pipeline. For now, let's just concatenate all the text columns
// together into one.
var pipeline = mlContext.Transforms.Concatenate("AllFeatures", "WorkClass", "Education", "MaritalStatus");

// Fit our data pipeline and transform data with it.
var transformedData = pipeline.Fit(data).Transform(data);

// Extract the 'AllFeatures' column.
// This will give the entire dataset: make sure to only take several row
// in case the dataset is huge. The is similar to the static API, except
// you have to specify the column name and type.
var featureColumns =
    transformedData
        .GetColumn<string[]>(mlContext, "AllFeatures")
        .Take(20)
        .ToArray();
```
