---
title: Vypočítat metriky k vyhodnocení, machine learning model kvality - ML.NET
description: Zjistěte, jak vypočítat metriky k vyhodnocení a ověření strojového učení modelu kvality pomocí ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: ad71f7da6981ac370e60725f88d3c70b1d5c5237
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679213"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality---mlnet"></a><span data-ttu-id="4eb99-103">Vypočítat metriky k vyhodnocení, machine learning model kvality - ML.NET</span><span class="sxs-lookup"><span data-stu-id="4eb99-103">Calculate metrics to evaluate machine learning model quality - ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="4eb99-104">Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit.</span><span class="sxs-lookup"><span data-stu-id="4eb99-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="4eb99-105">Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="4eb99-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="4eb99-106">Aktuálně používáte této ukázky s postupy a související **ML.NET verze 0.10**.</span><span class="sxs-lookup"><span data-stu-id="4eb99-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="4eb99-107">Další informace najdete v tématu poznámky k verzi v [úložiště GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="4eb99-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="4eb99-108">Jak při hodnocení kvality po trénování modelu?</span><span class="sxs-lookup"><span data-stu-id="4eb99-108">How do you evaluate quality after you train the model?</span></span> <span data-ttu-id="4eb99-109">Každý úkol machine learning poskytuje metriky pro hodnocení kvality.</span><span class="sxs-lookup"><span data-stu-id="4eb99-109">Each machine learning task exposes metrics for quality evaluation.</span></span>

<span data-ttu-id="4eb99-110">Odpovídající "kontextu" úlohy můžete použít k vyhodnocení modelu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="4eb99-110">You can use the corresponding 'context' of the task to evaluate the model, as in the following example:</span></span>

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```