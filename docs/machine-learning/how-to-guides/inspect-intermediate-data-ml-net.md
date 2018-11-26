---
title: Zkontrolovat hodnoty dočasných dat během zpracování kanálu ML.NET
description: Zjistěte, jak zkontrolovat hodnoty skutečné dočasných dat během ML.NET strojového učení zpracování kanálu
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: cd229c120f7599c9a304a84a1669947e613fc917
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297680"
---
# <a name="inspect-intermediate-data-values-during-mlnet-pipeline-processing"></a><span data-ttu-id="9631f-103">Zkontrolovat hodnoty dočasných dat během zpracování kanálu ML.NET</span><span class="sxs-lookup"><span data-stu-id="9631f-103">Inspect intermediate data values during ML.NET pipeline processing</span></span>

<span data-ttu-id="9631f-104">Během testu můžete sledovat a ověřte výsledky zpracování dat v časovém okamžiku.</span><span class="sxs-lookup"><span data-stu-id="9631f-104">During the experiment, you may want to observe and validate the data processing results at a given point.</span></span> <span data-ttu-id="9631f-105">To není snadné, protože operace ML.NET jsou opožděná, vytváření objektů, které jsou "příslibů" dat.</span><span class="sxs-lookup"><span data-stu-id="9631f-105">This isn't easy since ML.NET operations are lazy, constructing objects that are 'promises' of data.</span></span>

<span data-ttu-id="9631f-106">`GetColumn<T>` – Metoda rozšíření umožňuje kontrolovat zprostředkující data.</span><span class="sxs-lookup"><span data-stu-id="9631f-106">The `GetColumn<T>` extension method lets you inspect the intermediate data.</span></span> <span data-ttu-id="9631f-107">Vrátí obsah jako jeden datový sloupec `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="9631f-107">It returns the contents of one data column as an `IEnumerable`.</span></span>

<span data-ttu-id="9631f-108">Následující příklad ukazuje způsob použití `GetColumn<T>` – metoda rozšíření:</span><span class="sxs-lookup"><span data-stu-id="9631f-108">The following example shows how to use the `GetColumn<T>` extension method:</span></span>

<span data-ttu-id="9631f-109">[Příklad souboru](https://github.com/dotnet/machinelearning/tree/master/test/data/adult.tiny.with-schema.txt):</span><span class="sxs-lookup"><span data-stu-id="9631f-109">[Example file](https://github.com/dotnet/machinelearning/tree/master/test/data/adult.tiny.with-schema.txt):</span></span>
```
Label   Workclass   education   marital-status
0   Private 11th    Never-married
0   Private HS-grad Married-civ-spouse
1   Local-gov   Assoc-acdm  Married-civ-spouse
1   Private Some-college    Married-civ-spouse

```

<span data-ttu-id="9631f-110">Naše třída je definována takto:</span><span class="sxs-lookup"><span data-stu-id="9631f-110">Our class is defined as follows:</span></span>

```csharp
private class InspectedRow
{
    public bool IsOver50K;
    public string Workclass;
    public string Education;
    public string MaritalStatus;
    public string[] AllFeatures;
}
```

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Create the reader: define the data columns and where to find them in the text file.
var reader = mlContext.Data.TextReader(new TextLoader.Arguments
{
    Column = new[] {
        // A boolean column depicting the 'label'.
        new TextLoader.Column("IsOver50K", DataKind.BL, 0),
        // Three text columns.
        new TextLoader.Column("Workclass", DataKind.TX, 1),
        new TextLoader.Column("Education", DataKind.TX, 2),
        new TextLoader.Column("MaritalStatus", DataKind.TX, 3)
    },
    // First line of the file is a header, not a data row.
    HasHeader = true
});

// Start creating our processing pipeline. For now, let's just concatenate all the text columns
// together into one.
var pipeline = mlContext.Transforms.Concatenate("AllFeatures", "Education", "MaritalStatus");

// Let's verify that the data has been read correctly. 
// First, we read the data file.
var data = reader.Read(dataPath);

// Fit our data pipeline and transform data with it.
var transformedData = pipeline.Fit(data).Transform(data);

// 'transformedData' is a 'promise' of data. Let's actually read it.
var someRows = transformedData
    // Convert to an enumerable of user-defined type. 
    .AsEnumerable<InspectedRow>(mlContext, reuseRowObject: false)
    // Take a couple values as an array.
    .Take(4).ToArray();

// Extract the 'AllFeatures' column.
// This will give the entire dataset: make sure to only take several row
// in case the dataset is huge. The is similar to the static API, except
// you have to specify the column name and type.
var featureColumns = transformedData.GetColumn<string[]>(mlContext, "AllFeatures")
    .Take(20).ToArray();
```