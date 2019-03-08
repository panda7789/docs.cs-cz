---
title: Zprovoznění trénovaný model strojového učení v aplikacích – ML.NET
description: Objevte, jak využívají model trénovaného a vyhodnocené strojového učení v aplikacích pomocí ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: be6906c939b82d00067babaeebe809dae3de413a
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675131"
---
# <a name="operationalize-a-trained-machine-learning-model-in-apps---mlnet"></a><span data-ttu-id="cdbd9-103">Zprovoznění trénovaný model strojového učení v aplikacích – ML.NET</span><span class="sxs-lookup"><span data-stu-id="cdbd9-103">Operationalize a trained machine learning model in apps - ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="cdbd9-104">Toto téma odkazuje na ML.NET, která je aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit.</span><span class="sxs-lookup"><span data-stu-id="cdbd9-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="cdbd9-105">Další informace najdete v článku [Úvod ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="cdbd9-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="cdbd9-106">Aktuálně používáte této ukázky s postupy a související **ML.NET verze 0.10**.</span><span class="sxs-lookup"><span data-stu-id="cdbd9-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="cdbd9-107">Další informace najdete v tématu poznámky k verzi v [úložišti dotnet/machinelearning githubu](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)</span><span class="sxs-lookup"><span data-stu-id="cdbd9-107">For more information, see the release notes at the [dotnet/machinelearning github repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)</span></span>

<span data-ttu-id="cdbd9-108">Pokud model metriky vypadat dobře na vás, je čas na zprovoznění modelu.</span><span class="sxs-lookup"><span data-stu-id="cdbd9-108">When the model metrics look good to you, it's time to 'operationalize' the model.</span></span> <span data-ttu-id="cdbd9-109">`model` Trvalý a znovu používané v různých prostředích, použití stejných kroků, které "se" během cvičení mohou být spotřebovány objektů, které jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="cdbd9-109">The `model` object you built can be consumed, persisted, and reused in different environments, applying the same steps that it 'learned' during training.</span></span>

<span data-ttu-id="cdbd9-110">Pokud chcete uložit do souboru modelu a jej znovu načíst (potenciálně v jiném kontextu), použijte následující příklad:</span><span class="sxs-lookup"><span data-stu-id="cdbd9-110">To save the model to a file, and reload it (potentially in a different context), use the following example:</span></span>

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
