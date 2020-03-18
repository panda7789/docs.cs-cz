---
title: Opakovaná pole pro seznamy a pole - gRPC pro vývojáře WCF
description: Pochopit, jak Protobuf zpracovává kolekce a jak se vztahují k kolekcím .NET.
ms.date: 09/09/2019
ms.openlocfilehash: 63d99532d14deea7800673dd5a6350dd9362ad54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147968"
---
# <a name="repeated-fields-for-lists-and-arrays"></a>Opakující se pole pro seznamy a pole

Seznamy zadáte ve vyrovnávací paměti protokolu (Protobuf) pomocí klíčového `repeated` slova prefix. Následující příklad ukazuje, jak vytvořit seznam:

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

Ve generovaném kódu `repeated` jsou pole `Google.Protobuf.Collections.RepeatedField<T>` reprezentována obecným typem, nikoli předdefinovanými typy kolekcí .NET.

Typ `RepeatedField<T>` obsahuje kód potřebný k serializaci a rekonstrukci seznamu do binárního formátu drátu. Implementuje všechna standardní rozhraní kolekce .NET, například <xref:System.Collections.Generic.IList%601> a <xref:System.Collections.Generic.IEnumerable%601>. Takže můžete použít linq dotazy nebo převést na pole nebo seznam snadno.

>[!div class="step-by-step"]
>[Předchozí](protobuf-nested-types.md)
>[další](protobuf-reserved.md)
