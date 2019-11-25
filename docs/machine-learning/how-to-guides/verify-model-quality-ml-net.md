---
title: Vypočítat metriky pro vyhodnocení kvality modelu Machine Learning
description: Naučte se počítat metriky k vyhodnocení a ověření kvality modelu Machine Learning pomocí ML.NET.
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: d6409307cd283ae67d7546c4dc6e19e6089a0766
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975845"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality"></a><span data-ttu-id="df8a6-103">Vypočítat metriky pro vyhodnocení kvality modelu Machine Learning</span><span class="sxs-lookup"><span data-stu-id="df8a6-103">Calculate metrics to evaluate machine learning model quality</span></span>

> [!NOTE]
> <span data-ttu-id="df8a6-104">Toto téma odkazuje na ML.NET, který je aktuálně ve verzi Preview, a materiál může být změněn.</span><span class="sxs-lookup"><span data-stu-id="df8a6-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="df8a6-105">Další informace najdete na stránce [ml.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) .</span><span class="sxs-lookup"><span data-stu-id="df8a6-105">For more information, visit the [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) page.</span></span>

<span data-ttu-id="df8a6-106">Tato ukázka s postupy a souvisejícími ukázkami aktuálně používá **ml.NET verze 0,10**.</span><span class="sxs-lookup"><span data-stu-id="df8a6-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="df8a6-107">Další informace najdete v poznámkách k verzi v [úložišti GitHub/Machinelearning GitHub](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="df8a6-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="df8a6-108">Jak vyhodnocujete kvalitu po vytvoření modelu?</span><span class="sxs-lookup"><span data-stu-id="df8a6-108">How do you evaluate quality after you train the model?</span></span> <span data-ttu-id="df8a6-109">Každý úkol strojového učení zpřístupňuje metriky pro vyhodnocení kvality.</span><span class="sxs-lookup"><span data-stu-id="df8a6-109">Each machine learning task exposes metrics for quality evaluation.</span></span>

<span data-ttu-id="df8a6-110">K vyhodnocení modelu můžete použít odpovídající kontext úlohy, jak je uvedeno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="df8a6-110">You can use the corresponding 'context' of the task to evaluate the model, as in the following example:</span></span>

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```
