---
title: Opakující se pole pro seznamy a pole – gRPC pro vývojáře WCF
description: Seznamte se s tím, jak jsou kolekce zpracovávány pomocí Protobuf a jak souvisejí s kolekcemi .NET.
ms.date: 09/09/2019
ms.openlocfilehash: 17c579bc98ba62ea74b9452bdb28efd96fc51406
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967370"
---
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="23309-103">Opakující se pole pro seznamy a pole</span><span class="sxs-lookup"><span data-stu-id="23309-103">Repeated fields for lists and arrays</span></span>

<span data-ttu-id="23309-104">Seznamy jsou určené v Protobuf pomocí klíčového slova `repeated` předpony.</span><span class="sxs-lookup"><span data-stu-id="23309-104">Lists are specified in Protobuf using the `repeated` prefix keyword.</span></span> <span data-ttu-id="23309-105">Následující příklad ukazuje, jak vytvořit seznam:</span><span class="sxs-lookup"><span data-stu-id="23309-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="23309-106">Ve vygenerovaném kódu `repeated` pole jsou reprezentovány pomocí obecného typu `Google.Protobuf.Collections.RepeatedField<T>` namísto jakýchkoli vestavěných typů kolekce .NET.</span><span class="sxs-lookup"><span data-stu-id="23309-106">In the generated code, `repeated` fields are represented by the `Google.Protobuf.Collections.RepeatedField<T>` generic type rather than any of the built-in .NET collection types.</span></span> <span data-ttu-id="23309-107">Typ `RepeatedField<T>` obsahuje kód potřebný k serializaci a deserializaci seznamu do binárního formátu.</span><span class="sxs-lookup"><span data-stu-id="23309-107">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span> <span data-ttu-id="23309-108">Implementuje všechna rozhraní .NET Collection Standard, například <xref:System.Collections.Generic.IList%601> a <xref:System.Collections.Generic.IEnumerable%601>, takže můžete použít dotazy LINQ nebo je snadno převést na pole nebo seznam.</span><span class="sxs-lookup"><span data-stu-id="23309-108">It implements all the standard .NET collection interfaces such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>, so you can use LINQ queries or convert it to an array or a list easily.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="23309-109">[Předchozí](protobuf-nested-types.md)
>[Další](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="23309-109">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
