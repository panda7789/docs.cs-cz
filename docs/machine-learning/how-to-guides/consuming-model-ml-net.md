---
title: Zprovoznění trénovaný model strojového učení v aplikacích – ML.NET
description: Objevte, jak využívají model trénovaného a vyhodnocené strojového učení v aplikacích pomocí ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: be6906c939b82d00067babaeebe809dae3de413a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650424"
---
# <a name="operationalize-a-trained-machine-learning-model-in-apps---mlnet"></a>Zprovoznění trénovaný model strojového učení v aplikacích – ML.NET

> [!NOTE]
> Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit. Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Aktuálně používáte této ukázky s postupy a související **ML.NET verze 0.10**. Další informace najdete v tématu poznámky k verzi v [úložišti dotnet/machinelearning githubu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)

Pokud model metriky vypadat dobře na vás, je čas na zprovoznění modelu. `model` Trvalý a znovu používané v různých prostředích, použití stejných kroků, které "se" během cvičení mohou být spotřebovány objektů, které jste vytvořili.

Pokud chcete uložit do souboru modelu a jej znovu načíst (potenciálně v jiném kontextu), použijte následující příklad:

```csharp
using (var stream = File.Create(modelPath))
{
    // Saving and loading happens to 'dynamic' models.
    mlContext.Model.Save(model, stream);
}

// Potentially, the lines below can be in a different process altogether.

// When you load the model, it's a transformer.
ITransformer loadedModel;
using (var stream = File.OpenRead(modelPath))
    loadedModel = mlContext.Model.Load(stream);
```
