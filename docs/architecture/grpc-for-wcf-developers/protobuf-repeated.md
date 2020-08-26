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
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="842f9-103">Opakující se pole pro seznamy a pole</span><span class="sxs-lookup"><span data-stu-id="842f9-103">Repeated fields for lists and arrays</span></span>

<span data-ttu-id="842f9-104">V části vyrovnávací paměť protokolu (Protobuf) určíte seznamy pomocí `repeated` klíčového slova prefix.</span><span class="sxs-lookup"><span data-stu-id="842f9-104">You specify lists in Protocol Buffer (Protobuf) by using the `repeated` prefix keyword.</span></span> <span data-ttu-id="842f9-105">Následující příklad ukazuje, jak vytvořit seznam:</span><span class="sxs-lookup"><span data-stu-id="842f9-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="842f9-106">Ve vygenerovaném kódu `repeated` jsou pole reprezentovány vlastnostmi typu jen pro čtení a [`Google.Protobuf.Collections.RepeatedField<T>`][repeated-field] nikoli bez vestavěných typů kolekce .NET.</span><span class="sxs-lookup"><span data-stu-id="842f9-106">In the generated code, `repeated` fields are represented by read-only properties of the [`Google.Protobuf.Collections.RepeatedField<T>`][repeated-field] type rather than any of the built-in .NET collection types.</span></span> <span data-ttu-id="842f9-107">Tento typ implementuje všechna standardní rozhraní .NET Collection, například <xref:System.Collections.Generic.IList%601> a <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="842f9-107">This type implements all the standard .NET collection interfaces, such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="842f9-108">Takže můžete snadno použít dotazy LINQ nebo je převést na pole nebo seznam.</span><span class="sxs-lookup"><span data-stu-id="842f9-108">So you can use LINQ queries or convert it to an array or a list easily.</span></span>

<span data-ttu-id="842f9-109">`RepeatedField<T>`Typ zahrnuje kód potřebný k serializaci a deserializaci seznamu do binárního formátu.</span><span class="sxs-lookup"><span data-stu-id="842f9-109">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span>

[repeated-field]: https://developers.google.cn/protocol-buffers/docs/reference/csharp/class/google/protobuf/collections/repeated-field-t-

>[!div class="step-by-step"]
><span data-ttu-id="842f9-110">[Předchozí](protobuf-nested-types.md) 
> [Další](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="842f9-110">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
