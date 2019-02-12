---
title: Trénování modelu strojového učení s daty, která není v textovém souboru - ML.NET
description: Objevte, jak používat ML.NET načíst nesouborové trénovacích dat pro strojové učení, model školení v rámci kanálu předpovědi.
ms.date: 02/06/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 4ffbc69629aa9dc6cea5d33c704bc9c57a4a612c
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092017"
---
# <a name="train-a-machine-learning-model-with-data-thats-not-in-a-text-file---mlnet"></a><span data-ttu-id="c15a8-103">Trénování modelu strojového učení s daty, která není v textovém souboru - ML.NET</span><span class="sxs-lookup"><span data-stu-id="c15a8-103">Train a machine learning model with data that's not in a text file - ML.NET</span></span>

<span data-ttu-id="c15a8-104">V případě použití běžně předvedenou ML.NET je použití `TextLoader` číst trénovací data ze souboru.</span><span class="sxs-lookup"><span data-stu-id="c15a8-104">The commonly demonstrated use case for ML.NET is use the `TextLoader` to read the training data from a file.</span></span>
<span data-ttu-id="c15a8-105">Ale v scénáře v reálném čase školení data mohou být jinde, jako například:</span><span class="sxs-lookup"><span data-stu-id="c15a8-105">However, in real-time training scenarios the data can be elsewhere, such as:</span></span>

* <span data-ttu-id="c15a8-106">v tabulkách SQL</span><span class="sxs-lookup"><span data-stu-id="c15a8-106">in SQL tables</span></span>
* <span data-ttu-id="c15a8-107">extrahovaná ze souborů protokolů</span><span class="sxs-lookup"><span data-stu-id="c15a8-107">extracted from log files</span></span>
* <span data-ttu-id="c15a8-108">vygenerované v reálném čase</span><span class="sxs-lookup"><span data-stu-id="c15a8-108">generated on the fly</span></span>

<span data-ttu-id="c15a8-109">Použití [pochopení schématu](https://github.com/dotnet/machinelearning/tree/master/docs/code/SchemaComprehension.md) zpřístupnit stávající C# `IEnumerable` do ML.NET jako `DataView`.</span><span class="sxs-lookup"><span data-stu-id="c15a8-109">Use [schema comprehension](https://github.com/dotnet/machinelearning/tree/master/docs/code/SchemaComprehension.md) to bring an existing C# `IEnumerable` into ML.NET as a `DataView`.</span></span>

<span data-ttu-id="c15a8-110">V tomto příkladu budete vytvářet odběratele změn prediktivního modelu a extrahování následující funkce z produkčního prostředí systému:</span><span class="sxs-lookup"><span data-stu-id="c15a8-110">For this example, you'll build the customer churn prediction model, and extract the following features from your production system:</span></span>

* <span data-ttu-id="c15a8-111">ID zákazníka (Ignorovat modelem)</span><span class="sxs-lookup"><span data-stu-id="c15a8-111">Customer ID (ignored by the model)</span></span>
* <span data-ttu-id="c15a8-112">Určuje, zda má zákazník Měněná (cíl "štítek")</span><span class="sxs-lookup"><span data-stu-id="c15a8-112">Whether the customer has churned (the target 'label')</span></span>
* <span data-ttu-id="c15a8-113">Demografické kategorie (jeden řetězec, například "mladé dospělá osoba" atd.)</span><span class="sxs-lookup"><span data-stu-id="c15a8-113">The 'demographic category' (one string, like 'young adult' etc.)</span></span>
* <span data-ttu-id="c15a8-114">Počet návštěv z posledních 5 dní.</span><span class="sxs-lookup"><span data-stu-id="c15a8-114">The number of visits from the last 5 days.</span></span>

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

<span data-ttu-id="c15a8-115">Načtení těchto dat do `DataView` a trénování modelu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="c15a8-115">Load this data into the `DataView` and train the model, using the following code:</span></span>

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
