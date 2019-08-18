---
title: 'Postupy: Identifikace typu s možnou C# hodnotou null – Průvodce programováním'
ms.custom: seodec18
description: Naučte se určit, jestli typ je typ s možnou hodnotou null nebo instance je typu s možnou hodnotou null.
ms.date: 09/24/2018
helpviewer_keywords:
- nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: 43a35874b8c9f52c4b98a93e1217994980e1b223
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567376"
---
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a>Postupy: Identifikace typu s možnouC# hodnotou null (Průvodce programováním)

Následující příklad ukazuje, jak určit, zda <xref:System.Type?displayProperty=nameWithType> instance představuje uzavřený obecný typ s možnou hodnotou null, to znamená <xref:System.Nullable%601?displayProperty=nameWithType> typ s parametrem `T`zadaného typu:

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

Jak ukazuje příklad, použijte operátor [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) k vytvoření <xref:System.Type?displayProperty=nameWithType> objektu.  
  
Pokud chcete zjistit, zda je instance typu s možnou hodnotou null, nepoužívejte <xref:System.Object.GetType%2A?displayProperty=nameWithType> metodu k <xref:System.Type> získání instance, která má být testována pomocí předchozího kódu. Při volání <xref:System.Object.GetType%2A?displayProperty=nameWithType> metody na instanci typu s možnou hodnotou null je instance zabalena do [](using-nullable-types.md#boxing-and-unboxing) <xref:System.Object>. Jako zabalení instance typu s možnou hodnotou null, která není null, je ekvivalentem zabalení hodnoty nadřazeného typu, <xref:System.Object.GetType%2A> <xref:System.Type> vrátí objekt, který představuje nadřízený typ typu s možnou hodnotou null:

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

Nepoužívejte operátor [is](../../language-reference/keywords/is.md) k určení, zda je instance typu s možnou hodnotou null. Jak ukazuje následující příklad, nelze odlišit typy instancí typu s možnou hodnotou null a jeho nadřízený typ pomocí `is` operátoru:

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

K určení, jestli je instance typu s možnou hodnotou null, můžete použít kód prezentovaný v následujícím příkladu:

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]
  
## <a name="see-also"></a>Viz také:

- [Typy s možnou hodnotou null](index.md)
- [Použití typů s možnou hodnotou null](using-nullable-types.md)
- <xref:System.Nullable.GetUnderlyingType%2A>
