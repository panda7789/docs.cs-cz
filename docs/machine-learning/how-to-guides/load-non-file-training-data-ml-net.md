---
title: Trénování modelu strojového učení s daty, která není v textovém souboru - ML.NET
description: Objevte, jak používat ML.NET načíst nesouborové trénovacích dat pro strojové učení, model školení v rámci kanálu předpovědi.
ms.date: 03/18/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 32de37e45b9e19669ea06d74c7f252ec885fe004
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2019
ms.locfileid: "58186088"
---
# <a name="train-a-machine-learning-model-with-data-thats-not-in-a-text-file---mlnet"></a><span data-ttu-id="75e8f-103">Trénování modelu strojového učení s daty, která není v textovém souboru - ML.NET</span><span class="sxs-lookup"><span data-stu-id="75e8f-103">Train a machine learning model with data that's not in a text file - ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="75e8f-104">Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit.</span><span class="sxs-lookup"><span data-stu-id="75e8f-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="75e8f-105">Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="75e8f-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="75e8f-106">Aktuálně používáte této ukázky s postupy a související **ML.NET verze 0,11**.</span><span class="sxs-lookup"><span data-stu-id="75e8f-106">This how-to and related sample are currently using **ML.NET version 0.11**.</span></span> <span data-ttu-id="75e8f-107">Další informace najdete v tématu poznámky k verzi v [úložiště GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="75e8f-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="75e8f-108">V případě použití běžně předvedenou ML.NET je použití `TextLoader` číst trénovací data ze souboru.</span><span class="sxs-lookup"><span data-stu-id="75e8f-108">The commonly demonstrated use case for ML.NET is use the `TextLoader` to read the training data from a file.</span></span>
<span data-ttu-id="75e8f-109">Ale v scénáře v reálném čase školení data mohou být jinde, jako například:</span><span class="sxs-lookup"><span data-stu-id="75e8f-109">However, in real-time training scenarios the data can be elsewhere, such as:</span></span>

* <span data-ttu-id="75e8f-110">v tabulkách SQL</span><span class="sxs-lookup"><span data-stu-id="75e8f-110">in SQL tables</span></span>
* <span data-ttu-id="75e8f-111">JSON/XML</span><span class="sxs-lookup"><span data-stu-id="75e8f-111">JSON/XML</span></span>
* <span data-ttu-id="75e8f-112">extrahovaná ze souborů protokolů</span><span class="sxs-lookup"><span data-stu-id="75e8f-112">extracted from log files</span></span>
* <span data-ttu-id="75e8f-113">vygenerované v reálném čase</span><span class="sxs-lookup"><span data-stu-id="75e8f-113">generated on the fly</span></span>

<span data-ttu-id="75e8f-114">Použití [pochopení schématu](https://github.com/dotnet/machinelearning/tree/master/docs/code/SchemaComprehension.md) zpřístupnit stávající C# `IEnumerable` do ML.NET jako `DataView`.</span><span class="sxs-lookup"><span data-stu-id="75e8f-114">Use [schema comprehension](https://github.com/dotnet/machinelearning/tree/master/docs/code/SchemaComprehension.md) to bring an existing C# `IEnumerable` into ML.NET as a `DataView`.</span></span>

<span data-ttu-id="75e8f-115">V tomto příkladu budete vytvářet odběratele změn prediktivního modelu a extrahování následující funkce z produkčního prostředí systému:</span><span class="sxs-lookup"><span data-stu-id="75e8f-115">For this example, you'll build the customer churn prediction model, and extract the following features from your production system:</span></span>

* <span data-ttu-id="75e8f-116">ID zákazníka (Ignorovat modelem)</span><span class="sxs-lookup"><span data-stu-id="75e8f-116">Customer ID (ignored by the model)</span></span>
* <span data-ttu-id="75e8f-117">Určuje, zda má zákazník Měněná (cíl "štítek")</span><span class="sxs-lookup"><span data-stu-id="75e8f-117">Whether the customer has churned (the target 'label')</span></span>
* <span data-ttu-id="75e8f-118">Demografické kategorie (jeden řetězec, například "mladé dospělá osoba" atd.)</span><span class="sxs-lookup"><span data-stu-id="75e8f-118">The 'demographic category' (one string, like 'young adult' etc.)</span></span>
* <span data-ttu-id="75e8f-119">Počet návštěv z posledních 5 dní.</span><span class="sxs-lookup"><span data-stu-id="75e8f-119">The number of visits from the last 5 days.</span></span>

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

<span data-ttu-id="75e8f-120">Načtení těchto dat do `DataView` a trénování modelu, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="75e8f-120">Load this data into the `DataView` and train the model, using the following code:</span></span>

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
var trainData = mlContext.Data.LoadFromEnumerable(churnData);

// Build the learning pipeline.
// In our case, we will one-hot encode the demographic category, and concatenate that with the number of visits.
// We apply our FastTree binary classifier to predict the 'HasChurned' label.

var pipeline = mlContext.Transforms.Categorical.OneHotEncoding("DemographicCategory")
    .Append(mlContext.Transforms.Concatenate("Features", "DemographicCategory", "LastVisits"))
    .Append(mlContext.BinaryClassification.Trainers.FastTree("HasChurned", "Features", numTrees: 20));

var model = pipeline.Fit(trainData);
```
