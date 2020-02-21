---
title: Opakující se pole pro seznamy a pole – gRPC pro vývojáře WCF
description: Pochopte, jak Protobuf zpracovává kolekce a jak souvisí s kolekcemi .NET.
ms.date: 09/09/2019
ms.openlocfilehash: 16f2b5a54b032f32c8fcb9d572d5284fe589cb01
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542956"
---
# <a name="repeated-fields-for-lists-and-arrays"></a>Opakující se pole pro seznamy a pole

V části vyrovnávací paměť protokolu (Protobuf) určíte seznamy pomocí klíčového slova prefix `repeated`. Následující příklad ukazuje, jak vytvořit seznam:

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

Ve vygenerovaném kódu `repeated` pole jsou reprezentovány pomocí obecného typu `Google.Protobuf.Collections.RepeatedField<T>` namísto jakýchkoli vestavěných typů kolekce .NET. 

Typ `RepeatedField<T>` obsahuje kód potřebný k serializaci a deserializaci seznamu do binárního formátu. Implementuje všechna standardní rozhraní .NET Collection, například <xref:System.Collections.Generic.IList%601> a <xref:System.Collections.Generic.IEnumerable%601>. Takže můžete snadno použít dotazy LINQ nebo je převést na pole nebo seznam.

>[!div class="step-by-step"]
>[Předchozí](protobuf-nested-types.md)
>[Další](protobuf-reserved.md)
