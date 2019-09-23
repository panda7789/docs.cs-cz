---
title: Protobuf vnořené typy – gRPC pro vývojáře WCF
description: Přečtěte si o vnořených typech zpráv v Protobuf a gRPC a o tom C#, jak se generují v.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 39bc52b37cc9e57cfe0ed5a5118c348de5f014d8
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184188"
---
# <a name="protobuf-nested-types"></a><span data-ttu-id="3de31-103">Vnořené typy Protobuf</span><span class="sxs-lookup"><span data-stu-id="3de31-103">Protobuf nested types</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="3de31-104">Stejně jako C# umožňuje deklarovat třídy uvnitř jiných tříd, Protobuf umožňuje vnořovat definice zpráv v rámci jiných zpráv.</span><span class="sxs-lookup"><span data-stu-id="3de31-104">Just like C# allows you to declare classes inside other classes, Protobuf allows you to nest message definitions within other messages.</span></span> <span data-ttu-id="3de31-105">Následující příklad ukazuje, jak vytvořit vnořené typy zpráv:</span><span class="sxs-lookup"><span data-stu-id="3de31-105">The following example shows how to create nested message types:</span></span>

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

<span data-ttu-id="3de31-106">Ve vygenerovaném C# kódu `Inner` bude typ deklarován ve vnořené `HelloRequest` statické `Types` třídě v rámci třídy:</span><span class="sxs-lookup"><span data-stu-id="3de31-106">In the generated C# code, the `Inner` type will be declared in a nested static `Types` class within the `HelloRequest` class:</span></span>

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
><span data-ttu-id="3de31-107">[Předchozí](protobuf-data-types.md)
>[Další](protobuf-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="3de31-107">[Previous](protobuf-data-types.md)
[Next](protobuf-repeated.md)</span></span>
