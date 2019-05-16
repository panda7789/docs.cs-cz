---
title: Vypočítat metriky k vyhodnocení, machine learning model kvality
description: Zjistěte, jak vypočítat metriky k vyhodnocení a ověření strojového učení modelu kvality pomocí ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 2c7749205b862a42f42b857972057c441ab84364
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641096"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality"></a>Vypočítat metriky k vyhodnocení, machine learning model kvality 

> [!NOTE]
> Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit. Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Aktuálně používáte této ukázky s postupy a související **ML.NET verze 0.10**. Další informace najdete v tématu poznámky k verzi v [úložiště GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

Jak při hodnocení kvality po trénování modelu? Každý úkol machine learning poskytuje metriky pro hodnocení kvality.

Odpovídající "kontextu" úlohy můžete použít k vyhodnocení modelu, jako v následujícím příkladu:

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```
