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
# <a name="protobuf-nested-types"></a>Vnořené typy Protobuf

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Stejně jako C# umožňuje deklarovat třídy uvnitř jiných tříd, Protobuf umožňuje vnořovat definice zpráv v rámci jiných zpráv. Následující příklad ukazuje, jak vytvořit vnořené typy zpráv:

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

Ve vygenerovaném C# kódu `Inner` bude typ deklarován ve vnořené `HelloRequest` statické `Types` třídě v rámci třídy:

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
>[Předchozí](protobuf-data-types.md)
>[Další](protobuf-repeated.md)
