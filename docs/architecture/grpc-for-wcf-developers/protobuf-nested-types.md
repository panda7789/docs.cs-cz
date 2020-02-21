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
# <a name="protobuf-nested-types"></a>Vnořené typy protobuf

Stejně jako C# umožňuje deklarovat třídy uvnitř jiných tříd, vyrovnávací paměť protokolu (Protobuf) umožňuje vnořovat definice zpráv v rámci jiných zpráv. Následující příklad ukazuje, jak vytvořit vnořené typy zpráv:

```protobuf
message Outer {
    message Inner {
        string text = 1;
    }
    Inner inner = 1;
}
```

V generovaném C# kódu se typ `Inner` deklaruje ve vnořené statické `Types` třídě v rámci třídy `HelloRequest`:

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
>[Předchozí](protobuf-data-types.md)
>[Další](protobuf-repeated.md)
