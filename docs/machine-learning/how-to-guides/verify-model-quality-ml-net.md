---
title: Výpočet metrik pro vyhodnocení kvality modelu strojového učení
description: Přečtěte si, jak vypočítat metriky pro vyhodnocení a ověření kvality modelu strojového učení pomocí ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: d6409307cd283ae67d7546c4dc6e19e6089a0766
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73975845"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality"></a><span data-ttu-id="3a333-103">Výpočet metrik pro vyhodnocení kvality modelu strojového učení</span><span class="sxs-lookup"><span data-stu-id="3a333-103">Calculate metrics to evaluate machine learning model quality</span></span>

> [!NOTE]
> <span data-ttu-id="3a333-104">Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiál může být může být může změnit.</span><span class="sxs-lookup"><span data-stu-id="3a333-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="3a333-105">Další informace naleznete na [stránce ML.NET.](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet)</span><span class="sxs-lookup"><span data-stu-id="3a333-105">For more information, visit the [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) page.</span></span>

<span data-ttu-id="3a333-106">Tento návod a související ukázka jsou aktuálně pomocí **ML.NET verze 0.10**.</span><span class="sxs-lookup"><span data-stu-id="3a333-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="3a333-107">Další informace naleznete v poznámkách k verzi na [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="3a333-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="3a333-108">Jak hodnotíte kvalitu po tréninku modelu?</span><span class="sxs-lookup"><span data-stu-id="3a333-108">How do you evaluate quality after you train the model?</span></span> <span data-ttu-id="3a333-109">Každý úkol strojového učení zveřejňuje metriky pro hodnocení kvality.</span><span class="sxs-lookup"><span data-stu-id="3a333-109">Each machine learning task exposes metrics for quality evaluation.</span></span>

<span data-ttu-id="3a333-110">K vyhodnocení modelu můžete použít odpovídající kontext úkolu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="3a333-110">You can use the corresponding 'context' of the task to evaluate the model, as in the following example:</span></span>

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```
