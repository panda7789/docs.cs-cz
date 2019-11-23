---
title: Protobuf vnořené typy – gRPC pro vývojáře WCF
description: Přečtěte si o vnořených typech zpráv v Protobuf a gRPC a o tom C#, jak se generují v.
ms.date: 09/09/2019
ms.openlocfilehash: bbc7ed41516d29f867bbc9da5b258f6a3c9ff261
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967386"
---
# <a name="protobuf-nested-types"></a><span data-ttu-id="51ca2-103">Vnořené typy protobuf</span><span class="sxs-lookup"><span data-stu-id="51ca2-103">Protobuf nested types</span></span>

<span data-ttu-id="51ca2-104">Stejně jako C# umožňuje deklarovat třídy uvnitř jiných tříd, Protobuf umožňuje vnořovat definice zpráv v rámci jiných zpráv.</span><span class="sxs-lookup"><span data-stu-id="51ca2-104">Just like C# allows you to declare classes inside other classes, Protobuf allows you to nest message definitions within other messages.</span></span> <span data-ttu-id="51ca2-105">Následující příklad ukazuje, jak vytvořit vnořené typy zpráv:</span><span class="sxs-lookup"><span data-stu-id="51ca2-105">The following example shows how to create nested message types:</span></span>

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

<span data-ttu-id="51ca2-106">V generovaném C# kódu se typ `Inner` deklaruje ve vnořené statické `Types` třídě v rámci třídy `HelloRequest`:</span><span class="sxs-lookup"><span data-stu-id="51ca2-106">In the generated C# code, the `Inner` type will be declared in a nested static `Types` class within the `HelloRequest` class:</span></span>

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
><span data-ttu-id="51ca2-107">[Předchozí](protobuf-data-types.md)
>[Další](protobuf-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="51ca2-107">[Previous](protobuf-data-types.md)
[Next](protobuf-repeated.md)</span></span>
