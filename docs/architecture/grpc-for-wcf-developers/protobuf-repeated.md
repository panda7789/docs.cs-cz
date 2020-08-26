---
title: Opakující se pole pro seznamy a pole – gRPC pro vývojáře WCF
description: Pochopte, jak Protobuf zpracovává kolekce a jak souvisí s kolekcemi .NET.
ms.date: 09/09/2019
ms.openlocfilehash: 7320c76ddc58bcf5cd81150923e8cb635e510047
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867500"
---
# <a name="repeated-fields-for-lists-and-arrays"></a>Opakující se pole pro seznamy a pole

V části vyrovnávací paměť protokolu (Protobuf) určíte seznamy pomocí `repeated` klíčového slova prefix. Následující příklad ukazuje, jak vytvořit seznam:

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

Ve vygenerovaném kódu `repeated` jsou pole reprezentovány vlastnostmi typu jen pro čtení a [`Google.Protobuf.Collections.RepeatedField<T>`][repeated-field] nikoli bez vestavěných typů kolekce .NET. Tento typ implementuje všechna standardní rozhraní .NET Collection, například <xref:System.Collections.Generic.IList%601> a <xref:System.Collections.Generic.IEnumerable%601> . Takže můžete snadno použít dotazy LINQ nebo je převést na pole nebo seznam.

`RepeatedField<T>`Typ zahrnuje kód potřebný k serializaci a deserializaci seznamu do binárního formátu.

[repeated-field]: https://developers.google.cn/protocol-buffers/docs/reference/csharp/class/google/protobuf/collections/repeated-field-t-

>[!div class="step-by-step"]
>[Předchozí](protobuf-nested-types.md) 
> [Další](protobuf-reserved.md)
