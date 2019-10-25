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

V generovaném C# kódu se typ`Inner`deklaruje ve vnořené statické`Types`třídě v rámci třídy`HelloRequest`:

```csharp
var inner = new Outer.Types.Inner { Text = "Hello" };
```

>[!div class="step-by-step"]
>[Předchozí](protobuf-data-types.md)
>[Další](protobuf-repeated.md)
