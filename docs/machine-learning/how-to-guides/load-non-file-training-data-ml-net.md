---
title: Trénování modelu strojového učení s daty, která není v textovém souboru - ML.NET
description: Objevte, jak používat ML.NET načíst nesouborové trénovacích dat pro strojové učení, model školení v rámci kanálu předpovědi.
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 27b327a63cb55b7fce0f4ff7facd3ee7c4a1c85c
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57678611"
---
# <a name="train-a-machine-learning-model-with-data-thats-not-in-a-text-file---mlnet"></a>Trénování modelu strojového učení s daty, která není v textovém souboru - ML.NET

> [!NOTE]
> Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit. Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Aktuálně používáte této ukázky s postupy a související **ML.NET verze 0.10**. Další informace najdete v tématu poznámky k verzi v [úložiště GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

V případě použití běžně předvedenou ML.NET je použití `TextLoader` číst trénovací data ze souboru.
Ale v scénáře v reálném čase školení data mohou být jinde, jako například:

* v tabulkách SQL
* extrahovaná ze souborů protokolů
* vygenerované v reálném čase

Použití [pochopení schématu](https://github.com/dotnet/machinelearning/tree/master/docs/code/SchemaComprehension.md) zpřístupnit stávající C# `IEnumerable` do ML.NET jako `DataView`.

V tomto příkladu budete vytvářet odběratele změn prediktivního modelu a extrahování následující funkce z produkčního prostředí systému:

* ID zákazníka (Ignorovat modelem)
* Určuje, zda má zákazník Měněná (cíl "štítek")
* Demografické kategorie (jeden řetězec, například "mladé dospělá osoba" atd.)
* Počet návštěv z posledních 5 dní.

```csharp
private class CustomerChurnInfo
{
    public string CustomerID { get; set; }
    public bool HasChurned { get; set; }
    public string DemographicCategory { get; set; }
    // Visits during last 5 days, latest to newest.
    [VectorType(5)]
    public float[] LastVisits { get; set; }
}
```

Načtení těchto dat do `DataView` a trénování modelu, pomocí následujícího kódu:

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging,
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Step one: read the data as an IDataView.
// Let's assume that 'GetChurnData()' fetches and returns the training data from somewhere.
IEnumerable<CustomerChurnInfo> churnData = GetChurnInfo();

// Turn the data into the ML.NET data view.
// We can use CreateDataView or CreateStreamingDataView, depending on whether 'churnData' is an IList,
// or merely an IEnumerable.
var trainData = mlContext.Data.ReadFromEnumerable(churnData);

// Build the learning pipeline.
// In our case, we will one-hot encode the demographic category, and concatenate that with the number of visits.
// We apply our FastTree binary classifier to predict the 'HasChurned' label.

var pipeline = mlContext.Transforms.Categorical.OneHotEncoding("DemographicCategory")
    .Append(mlContext.Transforms.Concatenate("Features", "DemographicCategory", "LastVisits"))
    .Append(mlContext.BinaryClassification.Trainers.FastTree("HasChurned", "Features", numTrees: 20));

var model = pipeline.Fit(trainData);
```
