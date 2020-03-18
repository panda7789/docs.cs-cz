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
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality"></a>Výpočet metrik pro vyhodnocení kvality modelu strojového učení

> [!NOTE]
> Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiál může být může být může změnit. Další informace naleznete na [stránce ML.NET.](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet)

Tento návod a související ukázka jsou aktuálně pomocí **ML.NET verze 0.10**. Další informace naleznete v poznámkách k verzi na [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

Jak hodnotíte kvalitu po tréninku modelu? Každý úkol strojového učení zveřejňuje metriky pro hodnocení kvality.

K vyhodnocení modelu můžete použít odpovídající kontext úkolu, jako v následujícím příkladu:

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```
