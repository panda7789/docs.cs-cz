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
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="d3ca0-103">Opakující se pole pro seznamy a pole</span><span class="sxs-lookup"><span data-stu-id="d3ca0-103">Repeated fields for lists and arrays</span></span>

<span data-ttu-id="d3ca0-104">V části vyrovnávací paměť protokolu (Protobuf) určíte seznamy pomocí klíčového slova prefix `repeated`.</span><span class="sxs-lookup"><span data-stu-id="d3ca0-104">You specify lists in Protocol Buffer (Protobuf) by using the `repeated` prefix keyword.</span></span> <span data-ttu-id="d3ca0-105">Následující příklad ukazuje, jak vytvořit seznam:</span><span class="sxs-lookup"><span data-stu-id="d3ca0-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="d3ca0-106">Ve vygenerovaném kódu `repeated` pole jsou reprezentovány pomocí obecného typu `Google.Protobuf.Collections.RepeatedField<T>` namísto jakýchkoli vestavěných typů kolekce .NET.</span><span class="sxs-lookup"><span data-stu-id="d3ca0-106">In the generated code, `repeated` fields are represented by the `Google.Protobuf.Collections.RepeatedField<T>` generic type rather than any of the built-in .NET collection types.</span></span> 

<span data-ttu-id="d3ca0-107">Typ `RepeatedField<T>` obsahuje kód potřebný k serializaci a deserializaci seznamu do binárního formátu.</span><span class="sxs-lookup"><span data-stu-id="d3ca0-107">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span> <span data-ttu-id="d3ca0-108">Implementuje všechna standardní rozhraní .NET Collection, například <xref:System.Collections.Generic.IList%601> a <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="d3ca0-108">It implements all the standard .NET collection interfaces, such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="d3ca0-109">Takže můžete snadno použít dotazy LINQ nebo je převést na pole nebo seznam.</span><span class="sxs-lookup"><span data-stu-id="d3ca0-109">So you can use LINQ queries or convert it to an array or a list easily.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d3ca0-110">[Předchozí](protobuf-nested-types.md)
>[Další](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="d3ca0-110">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
