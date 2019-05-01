---
title: Vypočítat metriky k vyhodnocení, machine learning model kvality - ML.NET
description: Zjistěte, jak vypočítat metriky k vyhodnocení a ověření strojového učení modelu kvality pomocí ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: ad71f7da6981ac370e60725f88d3c70b1d5c5237
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019201"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality---mlnet"></a>Vypočítat metriky k vyhodnocení, machine learning model kvality - ML.NET

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