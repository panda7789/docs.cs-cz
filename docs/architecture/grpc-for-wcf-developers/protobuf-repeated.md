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
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="a0d7d-103">Opakující se pole pro seznamy a pole</span><span class="sxs-lookup"><span data-stu-id="a0d7d-103">Repeated fields for lists and arrays</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="a0d7d-104">Seznamy jsou určené v Protobuf pomocí `repeated` klíčového slova prefix.</span><span class="sxs-lookup"><span data-stu-id="a0d7d-104">Lists are specified in Protobuf using the `repeated` prefix keyword.</span></span> <span data-ttu-id="a0d7d-105">Následující příklad ukazuje, jak vytvořit seznam:</span><span class="sxs-lookup"><span data-stu-id="a0d7d-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="a0d7d-106">Ve vygenerovaném kódu `repeated` jsou pole reprezentována `Google.Protobuf.Collections.RepeatedField<T>` obecným typem namísto jakýchkoli vestavěných typů kolekce .NET.</span><span class="sxs-lookup"><span data-stu-id="a0d7d-106">In the generated code, `repeated` fields are represented by the `Google.Protobuf.Collections.RepeatedField<T>` generic type rather than any of the built-in .NET collection types.</span></span> <span data-ttu-id="a0d7d-107">`RepeatedField<T>` Typ zahrnuje kód potřebný k serializaci a deserializaci seznamu do binárního formátu.</span><span class="sxs-lookup"><span data-stu-id="a0d7d-107">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span> <span data-ttu-id="a0d7d-108">Implementuje všechna standardní rozhraní .NET Collection, jako jsou <xref:System.Collections.Generic.IList%601> a <xref:System.Collections.Generic.IEnumerable%601>, takže můžete snadno použít dotazy LINQ nebo je převést na pole nebo seznam.</span><span class="sxs-lookup"><span data-stu-id="a0d7d-108">It implements all the standard .NET collection interfaces such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>, so you can use LINQ queries or convert it to an array or a list easily.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a0d7d-109">[Předchozí](protobuf-nested-types.md)
>[Další](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="a0d7d-109">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
