---
title: Opakující se pole pro seznamy a pole – gRPC pro vývojáře WCF
description: Seznamte se s tím, jak jsou kolekce zpracovávány pomocí Protobuf a jak souvisejí s kolekcemi .NET.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 740af8af39af9bf31be17ad831f481176e30d81f
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846319"
---
# <a name="repeated-fields-for-lists-and-arrays"></a>Opakující se pole pro seznamy a pole

Seznamy jsou určené v Protobuf pomocí klíčového slova `repeated` předpony. Následující příklad ukazuje, jak vytvořit seznam:

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

Ve vygenerovaném kódu `repeated` pole jsou reprezentovány pomocí obecného typu `Google.Protobuf.Collections.RepeatedField<T>` namísto jakýchkoli vestavěných typů kolekce .NET. Typ `RepeatedField<T>` obsahuje kód potřebný k serializaci a deserializaci seznamu do binárního formátu. Implementuje všechna rozhraní .NET Collection Standard, například <xref:System.Collections.Generic.IList%601> a <xref:System.Collections.Generic.IEnumerable%601>, takže můžete použít dotazy LINQ nebo je snadno převést na pole nebo seznam.

>[!div class="step-by-step"]
>[Předchozí](protobuf-nested-types.md)
>[Další](protobuf-reserved.md)
