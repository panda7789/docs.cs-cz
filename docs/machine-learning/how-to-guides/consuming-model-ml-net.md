---
title: Zprovoznění trénovaný model strojového učení v aplikacích – ML.NET
description: Objevte, jak využívají model trénovaného a vyhodnocené strojového učení v aplikacích pomocí ML.NET
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: ff3f0a8856382d020129693bcf722f572fd87606
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131570"
---
# <a name="operationalize-a-trained-machine-learning-model-in-apps---mlnet"></a>Zprovoznění trénovaný model strojového učení v aplikacích – ML.NET

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
