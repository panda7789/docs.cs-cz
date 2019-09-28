---
title: 'Postupy: Identifikace typu hodnoty s možnou hodnotou C# null – Průvodce programováním'
ms.custom: seodec18
description: Naučte se, jak určit, jestli typ je typ hodnoty s možnou hodnotou null nebo instance je typu s možnou hodnotou null.
ms.date: 09/26/2019
helpviewer_keywords:
- nullable value types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: 15b1ffedf57648955ee5a004514841a5d140292b
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392604"
---
# <a name="how-to-identify-a-nullable-value-type-c-programming-guide"></a>Postupy: určení typu hodnoty s možnou hodnotouC# null (Průvodce programováním)

Následující příklad ukazuje, jak určit, zda instance <xref:System.Type?displayProperty=nameWithType> představuje uzavřený obecný typ hodnoty s možnou hodnotou null, tj. typ <xref:System.Nullable%601?displayProperty=nameWithType> s určeným parametrem typu `T`:

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

Jak ukazuje příklad, použijte operátor [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) k vytvoření objektu <xref:System.Type?displayProperty=nameWithType>.

Chcete-li určit, zda je instance typu hodnoty s možnou hodnotou null, nepoužívejte metodu <xref:System.Object.GetType%2A?displayProperty=nameWithType> pro získání instance <xref:System.Type> pro otestování pomocí předchozího kódu. Když zavoláte metodu <xref:System.Object.GetType%2A?displayProperty=nameWithType> u instance typu hodnoty s možnou hodnotou null, je instance [zabalená](using-nullable-types.md#boxing-and-unboxing) na <xref:System.Object>. Jako zabalení instance typu s možnou hodnotou null, která není null, je ekvivalentem zabalení hodnoty nadřízeného typu, <xref:System.Object.GetType%2A> vrátí objekt <xref:System.Type>, který představuje nadřízený typ hodnoty s možnou hodnotou null:

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

Nepoužívejte operátor [is](../../language-reference/keywords/is.md) k určení, zda je instance typu hodnot s možnou hodnotou null. Jak ukazuje následující příklad, nelze odlišit typy instancí typu hodnoty s možnou hodnotou null a jeho nadřízený typ pomocí operátoru `is`:

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

K určení, zda je instance typu s možnou hodnotou null, lze použít kód prezentovaný v následujícím příkladu:

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]

## <a name="see-also"></a>Viz také:

- [Typy hodnot s možnou hodnotou null](index.md)
- [Použití typů hodnot s možnou hodnotou null](using-nullable-types.md)
- <xref:System.Nullable.GetUnderlyingType%2A>
