---
title: Opakující se pole pro seznamy a pole – gRPC pro vývojáře WCF
description: Seznamte se s tím, jak jsou kolekce zpracovávány pomocí Protobuf a jak souvisejí s kolekcemi .NET.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: ad06551bf3eaec795865af227815b78c9601d0db
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184181"
---
# <a name="repeated-fields-for-lists-and-arrays"></a>Opakující se pole pro seznamy a pole

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Seznamy jsou určené v Protobuf pomocí `repeated` klíčového slova prefix. Následující příklad ukazuje, jak vytvořit seznam:

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

Ve vygenerovaném kódu `repeated` jsou pole reprezentována `Google.Protobuf.Collections.RepeatedField<T>` obecným typem namísto jakýchkoli vestavěných typů kolekce .NET. `RepeatedField<T>` Typ zahrnuje kód potřebný k serializaci a deserializaci seznamu do binárního formátu. Implementuje všechna standardní rozhraní .NET Collection, jako jsou <xref:System.Collections.Generic.IList%601> a <xref:System.Collections.Generic.IEnumerable%601>, takže můžete snadno použít dotazy LINQ nebo je převést na pole nebo seznam.

>[!div class="step-by-step"]
>[Předchozí](protobuf-nested-types.md)
>[Další](protobuf-reserved.md)
