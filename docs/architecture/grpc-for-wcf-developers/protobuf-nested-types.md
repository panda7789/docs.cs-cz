---
title: Protobuf vnořené typy – gRPC pro vývojáře WCF
description: Přečtěte si o vnořených typech zpráv v Protobuf a gRPC a o tom C#, jak se generují v.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: ec9fc522619230c1201bfef1e8128f7356936212
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846308"
---
# <a name="protobuf-nested-types"></a><span data-ttu-id="65bec-103">Vnořené typy protobuf</span><span class="sxs-lookup"><span data-stu-id="65bec-103">Protobuf nested types</span></span>

<span data-ttu-id="65bec-104">Stejně jako C# umožňuje deklarovat třídy uvnitř jiných tříd, Protobuf umožňuje vnořovat definice zpráv v rámci jiných zpráv.</span><span class="sxs-lookup"><span data-stu-id="65bec-104">Just like C# allows you to declare classes inside other classes, Protobuf allows you to nest message definitions within other messages.</span></span> <span data-ttu-id="65bec-105">Následující příklad ukazuje, jak vytvořit vnořené typy zpráv:</span><span class="sxs-lookup"><span data-stu-id="65bec-105">The following example shows how to create nested message types:</span></span>

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

<span data-ttu-id="65bec-106">V generovaném C# kódu se typ`Inner`deklaruje ve vnořené statické`Types`třídě v rámci třídy`HelloRequest`:</span><span class="sxs-lookup"><span data-stu-id="65bec-106">In the generated C# code, the `Inner` type will be declared in a nested static `Types` class within the `HelloRequest` class:</span></span>

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
><span data-ttu-id="65bec-107">[Předchozí](protobuf-data-types.md)
>[Další](protobuf-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="65bec-107">[Previous](protobuf-data-types.md)
[Next](protobuf-repeated.md)</span></span>
