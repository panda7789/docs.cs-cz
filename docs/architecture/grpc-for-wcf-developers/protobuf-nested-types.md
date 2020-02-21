---
title: Protobuf vnořené typy – gRPC pro vývojáře WCF
description: Přečtěte si o vnořených typech zpráv v Protobuf a gRPC a o tom C#, jak se generují v.
ms.date: 09/09/2019
ms.openlocfilehash: 7b9a331336ebe1ca7bc75fdd164b7b88ae4f9db2
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542843"
---
# <a name="protobuf-nested-types"></a><span data-ttu-id="f3bb0-103">Vnořené typy protobuf</span><span class="sxs-lookup"><span data-stu-id="f3bb0-103">Protobuf nested types</span></span>

<span data-ttu-id="f3bb0-104">Stejně jako C# umožňuje deklarovat třídy uvnitř jiných tříd, vyrovnávací paměť protokolu (Protobuf) umožňuje vnořovat definice zpráv v rámci jiných zpráv.</span><span class="sxs-lookup"><span data-stu-id="f3bb0-104">Just as C# allows you to declare classes inside other classes, Protocol Buffer (Protobuf) allows you to nest message definitions within other messages.</span></span> <span data-ttu-id="f3bb0-105">Následující příklad ukazuje, jak vytvořit vnořené typy zpráv:</span><span class="sxs-lookup"><span data-stu-id="f3bb0-105">The following example shows how to create nested message types:</span></span>

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

<span data-ttu-id="f3bb0-106">V generovaném C# kódu se typ `Inner` deklaruje ve vnořené statické `Types` třídě v rámci třídy `HelloRequest`:</span><span class="sxs-lookup"><span data-stu-id="f3bb0-106">In the generated C# code, the `Inner` type will be declared in a nested static `Types` class within the `HelloRequest` class:</span></span>

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
><span data-ttu-id="f3bb0-107">[Předchozí](protobuf-data-types.md)
>[Další](protobuf-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="f3bb0-107">[Previous](protobuf-data-types.md)
[Next](protobuf-repeated.md)</span></span>
