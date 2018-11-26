---
title: Vypočítat metriky k vyhodnocení, machine learning model kvality - ML.NET
description: Zjistěte, jak vypočítat metriky k vyhodnocení a ověření strojového učení modelu kvality pomocí ML.NET
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: 6fd4dfab6104b4398918e42ed70584b04169a8c1
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297674"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality---mlnet"></a><span data-ttu-id="414a5-103">Vypočítat metriky k vyhodnocení, machine learning model kvality - ML.NET</span><span class="sxs-lookup"><span data-stu-id="414a5-103">Calculate metrics to evaluate machine learning model quality - ML.NET</span></span>

<span data-ttu-id="414a5-104">Jak při hodnocení kvality po trénování modelu?</span><span class="sxs-lookup"><span data-stu-id="414a5-104">How do you evaluate quality after you train the model?</span></span> <span data-ttu-id="414a5-105">Každý úkol machine learning poskytuje metriky pro hodnocení kvality.</span><span class="sxs-lookup"><span data-stu-id="414a5-105">Each machine learning task exposes metrics for quality evaluation.</span></span>

<span data-ttu-id="414a5-106">Odpovídající "kontextu" úlohy můžete použít k vyhodnocení modelu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="414a5-106">You can use the corresponding 'context' of the task to evaluate the model, as in the following example:</span></span>

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```