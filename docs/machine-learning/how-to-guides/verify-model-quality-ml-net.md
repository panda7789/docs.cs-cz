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
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality"></a>Vypočítat metriky pro vyhodnocení kvality modelu Machine Learning

> [!NOTE]
> Toto téma odkazuje na ML.NET, který je aktuálně ve verzi Preview, a materiál může být změněn. Další informace najdete na stránce [ml.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) .

Tato ukázka s postupy a souvisejícími ukázkami aktuálně používá **ml.NET verze 0,10**. Další informace najdete v poznámkách k verzi v [úložišti GitHub/Machinelearning GitHub](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

Jak vyhodnocujete kvalitu po vytvoření modelu? Každý úkol strojového učení zpřístupňuje metriky pro vyhodnocení kvality.

K vyhodnocení modelu můžete použít odpovídající kontext úlohy, jak je uvedeno v následujícím příkladu:

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```
