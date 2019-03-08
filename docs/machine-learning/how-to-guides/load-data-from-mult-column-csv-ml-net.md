---
title: Načtení dat pomocí mnoho sloupců ze souboru CSV pro machine learning zpracování – ML.NET
description: Zjistěte, jak načíst data data s mnoha sloupci ze souboru CSV pro použití v modelu strojového učení, vytváření, trénování a vyhodnocování s ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: e33fdf1d71b02545e3ea284cc317f5d244c3fc13
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675950"
---
# <a name="load-data-with-many-columns-from-a-csv-file-for-machine-learning-processing---mlnet"></a><span data-ttu-id="f2fc9-103">Načtení dat pomocí mnoho sloupců ze souboru CSV pro machine learning zpracování – ML.NET</span><span class="sxs-lookup"><span data-stu-id="f2fc9-103">Load data with many columns from a CSV file for machine learning processing - ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="f2fc9-104">Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit.</span><span class="sxs-lookup"><span data-stu-id="f2fc9-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="f2fc9-105">Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="f2fc9-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="f2fc9-106">Aktuálně používáte této ukázky s postupy a související **ML.NET verze 0.10**.</span><span class="sxs-lookup"><span data-stu-id="f2fc9-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="f2fc9-107">Další informace najdete v tématu poznámky k verzi v [úložiště GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="f2fc9-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="f2fc9-108">`TextLoader` slouží k načtení dat z textových souborů.</span><span class="sxs-lookup"><span data-stu-id="f2fc9-108">`TextLoader` is used to load data from text files.</span></span> <span data-ttu-id="f2fc9-109">Je třeba zadat sloupců dat, jejich typy a jejich umístění v textovém souboru.</span><span class="sxs-lookup"><span data-stu-id="f2fc9-109">You need to specify the data columns, their types, and their location in the text file.</span></span>

<span data-ttu-id="f2fc9-110">Pokud vstupní soubor obsahuje mnoho sloupců stejného typu a vždy použít současně, přečtěte si je jako *vektoru sloupec*.</span><span class="sxs-lookup"><span data-stu-id="f2fc9-110">When the input file contains many columns of the same type and always used together, read them as a *vector column*.</span></span> <span data-ttu-id="f2fc9-111">Tato strategie výsledků ve schématu vyčištění dat a zabraňuje náklady zbytečně výkon, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f2fc9-111">This strategy results in a clean data schema and avoids unnecessary performance costs, as shown in the following example:</span></span>

<span data-ttu-id="f2fc9-112">[Příklad souboru](https://github.com/dotnet/machinelearning/tree/master/test/data/generated_regression_dataset.csv):</span><span class="sxs-lookup"><span data-stu-id="f2fc9-112">[Example file](https://github.com/dotnet/machinelearning/tree/master/test/data/generated_regression_dataset.csv):</span></span>

```console
-2.75;0.77;-0.61;0.14;1.39;0.38;-0.53;-0.50;-2.13;-0.39;0.46;140.66
-0.61;-0.37;-0.12;0.55;-1.00;0.84;-0.02;1.30;-0.24;-0.50;-2.12;148.12
-0.85;-0.91;1.81;0.02;-0.78;-1.41;-1.09;-0.65;0.90;-0.37;-0.22;402.20
0.28;1.05;-0.24;0.30;-0.99;0.19;0.32;-0.95;-1.19;-0.63;0.75;443.51
```

<span data-ttu-id="f2fc9-113">Čtení tohoto souboru pomocí `TextLoader`:</span><span class="sxs-lookup"><span data-stu-id="f2fc9-113">Reading this file using `TextLoader`:</span></span>

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Create the reader: define the data columns and where to find them in the text file.
var reader = mlContext.Data.CreateTextLoader(
    columns: new TextLoader.Column[]
    {
    // We read the first 10 values as a single float vector.
        new TextLoader.Column("FeatureVector",DataKind.R4,0,9),
        // Separately, read the target variable.
        new TextLoader.Column("Target",DataKind.R4,10)
    },
    // Default separator is tab, but we need a semicolon.
    separatorChar: ';',
    hasHeader: true
);

// Now read the file (remember though, readers are lazy, so the actual reading will happen when the data is accessed).
var data = reader.Read(dataPath);
```    