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
# <a name="repeated-fields-for-lists-and-arrays"></a><span data-ttu-id="34bf8-103">Opakující se pole pro seznamy a pole</span><span class="sxs-lookup"><span data-stu-id="34bf8-103">Repeated fields for lists and arrays</span></span>

<span data-ttu-id="34bf8-104">Seznamy zadáte ve vyrovnávací paměti protokolu (Protobuf) pomocí klíčového `repeated` slova prefix.</span><span class="sxs-lookup"><span data-stu-id="34bf8-104">You specify lists in Protocol Buffer (Protobuf) by using the `repeated` prefix keyword.</span></span> <span data-ttu-id="34bf8-105">Následující příklad ukazuje, jak vytvořit seznam:</span><span class="sxs-lookup"><span data-stu-id="34bf8-105">The following example shows how to create a list:</span></span>

```protobuf
message Person {
    // Other fields elided
    repeated string aliases = 8;
}
```

<span data-ttu-id="34bf8-106">Ve generovaném kódu `repeated` jsou pole `Google.Protobuf.Collections.RepeatedField<T>` reprezentována obecným typem, nikoli předdefinovanými typy kolekcí .NET.</span><span class="sxs-lookup"><span data-stu-id="34bf8-106">In the generated code, `repeated` fields are represented by the `Google.Protobuf.Collections.RepeatedField<T>` generic type rather than any of the built-in .NET collection types.</span></span>

<span data-ttu-id="34bf8-107">Typ `RepeatedField<T>` obsahuje kód potřebný k serializaci a rekonstrukci seznamu do binárního formátu drátu.</span><span class="sxs-lookup"><span data-stu-id="34bf8-107">The `RepeatedField<T>` type includes the code required to serialize and deserialize the list to the binary wire format.</span></span> <span data-ttu-id="34bf8-108">Implementuje všechna standardní rozhraní kolekce .NET, například <xref:System.Collections.Generic.IList%601> a <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="34bf8-108">It implements all the standard .NET collection interfaces, such as <xref:System.Collections.Generic.IList%601> and <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="34bf8-109">Takže můžete použít linq dotazy nebo převést na pole nebo seznam snadno.</span><span class="sxs-lookup"><span data-stu-id="34bf8-109">So you can use LINQ queries or convert it to an array or a list easily.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="34bf8-110">[Předchozí](protobuf-nested-types.md)
>[další](protobuf-reserved.md)</span><span class="sxs-lookup"><span data-stu-id="34bf8-110">[Previous](protobuf-nested-types.md)
[Next](protobuf-reserved.md)</span></span>
