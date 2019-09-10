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
