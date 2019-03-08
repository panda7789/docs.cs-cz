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
# <a name="inspect-intermediate-data-values-during-mlnet-pipeline-processing"></a><span data-ttu-id="f878a-103">Zkontrolovat hodnoty dočasných dat během zpracování kanálu ML.NET</span><span class="sxs-lookup"><span data-stu-id="f878a-103">Inspect intermediate data values during ML.NET pipeline processing</span></span>

> [!NOTE]
> <span data-ttu-id="f878a-104">Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit.</span><span class="sxs-lookup"><span data-stu-id="f878a-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="f878a-105">Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="f878a-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="f878a-106">Aktuálně používáte této ukázky s postupy a související **ML.NET verze 0.10**.</span><span class="sxs-lookup"><span data-stu-id="f878a-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="f878a-107">Další informace najdete v tématu poznámky k verzi v [úložiště GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="f878a-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="f878a-108">Během testu můžete sledovat a ověřte výsledky zpracování dat v časovém okamžiku.</span><span class="sxs-lookup"><span data-stu-id="f878a-108">During the experiment, you may want to observe and validate the data processing results at a given point.</span></span> <span data-ttu-id="f878a-109">To není snadné, protože operace ML.NET jsou opožděná, vytváření objektů, které jsou "příslibů" dat.</span><span class="sxs-lookup"><span data-stu-id="f878a-109">This isn't easy since ML.NET operations are lazy, constructing objects that are 'promises' of data.</span></span>

<span data-ttu-id="f878a-110">`GetColumn<T>` – Metoda rozšíření umožňuje kontrolovat zprostředkující data.</span><span class="sxs-lookup"><span data-stu-id="f878a-110">The `GetColumn<T>` extension method lets you inspect the intermediate data.</span></span> <span data-ttu-id="f878a-111">Vrátí obsah jako jeden datový sloupec `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="f878a-111">It returns the contents of one data column as an `IEnumerable`.</span></span>

<span data-ttu-id="f878a-112">Následující příklad ukazuje způsob použití `GetColumn<T>` – metoda rozšíření:</span><span class="sxs-lookup"><span data-stu-id="f878a-112">The following example shows how to use the `GetColumn<T>` extension method:</span></span>

<span data-ttu-id="f878a-113">[Příklad souboru](https://github.com/dotnet/machinelearning/tree/master/test/data/adult.tiny.with-schema.txt):</span><span class="sxs-lookup"><span data-stu-id="f878a-113">[Example file](https://github.com/dotnet/machinelearning/tree/master/test/data/adult.tiny.with-schema.txt):</span></span>
```
Label   Workclass   education   marital-status
0   Private 11th    Never-married
0   Private HS-grad Married-civ-spouse
1   Local-gov   Assoc-acdm  Married-civ-spouse
1   Private Some-college    Married-civ-spouse

```

<span data-ttu-id="f878a-114">Naše třída je definována takto:</span><span class="sxs-lookup"><span data-stu-id="f878a-114">Our class is defined as follows:</span></span>

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
