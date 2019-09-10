---
title: Vypočítat metriky pro vyhodnocení kvality modelu Machine Learning
description: Naučte se počítat metriky k vyhodnocení a ověření kvality modelu Machine Learning pomocí ML.NET.
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 529003913b166c966e131b006800f944096605b7
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855560"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality"></a><span data-ttu-id="acc75-103">Vypočítat metriky pro vyhodnocení kvality modelu Machine Learning</span><span class="sxs-lookup"><span data-stu-id="acc75-103">Calculate metrics to evaluate machine learning model quality</span></span> 

> [!NOTE]
> <span data-ttu-id="acc75-104">Toto téma odkazuje na ML.NET, který je aktuálně ve verzi Preview, a materiál může být změněn.</span><span class="sxs-lookup"><span data-stu-id="acc75-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="acc75-105">Další informace najdete na stránce [ml.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) .</span><span class="sxs-lookup"><span data-stu-id="acc75-105">For more information, visit the [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) page.</span></span>

<span data-ttu-id="acc75-106">Tato ukázka s postupy a souvisejícími ukázkami aktuálně používá **ml.NET verze 0,10**.</span><span class="sxs-lookup"><span data-stu-id="acc75-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="acc75-107">Další informace najdete v poznámkách k verzi v [úložišti GitHub/Machinelearning GitHub](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="acc75-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="acc75-108">Jak vyhodnocujete kvalitu po vytvoření modelu?</span><span class="sxs-lookup"><span data-stu-id="acc75-108">How do you evaluate quality after you train the model?</span></span> <span data-ttu-id="acc75-109">Každý úkol strojového učení zpřístupňuje metriky pro vyhodnocení kvality.</span><span class="sxs-lookup"><span data-stu-id="acc75-109">Each machine learning task exposes metrics for quality evaluation.</span></span>

<span data-ttu-id="acc75-110">K vyhodnocení modelu můžete použít odpovídající kontext úlohy, jak je uvedeno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="acc75-110">You can use the corresponding 'context' of the task to evaluate the model, as in the following example:</span></span>

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```
