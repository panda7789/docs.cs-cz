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
# <a name="operationalize-a-trained-machine-learning-model-in-apps---mlnet"></a><span data-ttu-id="51209-103">Zprovoznění trénovaný model strojového učení v aplikacích – ML.NET</span><span class="sxs-lookup"><span data-stu-id="51209-103">Operationalize a trained machine learning model in apps - ML.NET</span></span>

<span data-ttu-id="51209-104">Pokud model metriky vypadat dobře na vás, je čas na zprovoznění modelu.</span><span class="sxs-lookup"><span data-stu-id="51209-104">When the model metrics look good to you, it's time to 'operationalize' the model.</span></span> <span data-ttu-id="51209-105">`model` Trvalý a znovu používané v různých prostředích, použití stejných kroků, které "se" během cvičení mohou být spotřebovány objektů, které jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="51209-105">The `model` object you built can be consumed, persisted, and reused in different environments, applying the same steps that it 'learned' during training.</span></span>

<span data-ttu-id="51209-106">Pokud chcete uložit do souboru modelu a jej znovu načíst (potenciálně v jiném kontextu), použijte následující příklad:</span><span class="sxs-lookup"><span data-stu-id="51209-106">To save the model to a file, and reload it (potentially in a different context), use the following example:</span></span>

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
