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
# <a name="protobuf-nested-types"></a>Vnořené typy protobuf

Stejně jako C# umožňuje deklarovat třídy uvnitř jiných tříd, Protobuf umožňuje vnořovat definice zpráv v rámci jiných zpráv. Následující příklad ukazuje, jak vytvořit vnořené typy zpráv:

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
