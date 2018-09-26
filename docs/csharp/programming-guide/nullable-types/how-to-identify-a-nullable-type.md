---
title: 'Postupy: identifikace typu s možnou hodnotou Null (C# Programming Guide)'
description: Zjistěte, jak určit, zda typ je typ připouštějící hodnotu null nebo je instance typu s možnou hodnotou Null
ms.date: 09/24/2018
helpviewer_keywords:
- nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: f9957568d3c68f60cc9286718be9f5a496f876e6
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47089984"
---
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a>Postupy: identifikace typu s možnou hodnotou Null (C# Programming Guide)

Následující příklad ukazuje, jak určit, jestli <xref:System.Type?displayProperty=nameWithType> instance představuje uzavřený obecný typ s možnou hodnotou Null, to znamená, <xref:System.Nullable%601?displayProperty=nameWithType> typ pomocí zadaného typu parametru `T`:

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

Jak ukazuje příklad, je použít [typeof](../../language-reference/keywords/typeof.md) operátoru pro vytvoření <xref:System.Type?displayProperty=nameWithType> objektu.  
  
Pokud chcete zjistit, jestli je instance typu s možnou hodnotou Null, nepoužívejte <xref:System.Object.GetType%2A?displayProperty=nameWithType> metodu k získání <xref:System.Type> instance má být testována s předchozím kódu. Při volání <xref:System.Object.GetType%2A?displayProperty=nameWithType> metodu na instanci typu s možnou hodnotou Null, je instance [boxed](using-nullable-types.md#boxing-and-unboxing) k <xref:System.Object>. Je ekvivalentní k zabalení hodnota základního typu boxing nenulovou instanci typu s možnou hodnotou Null <xref:System.Object.GetType%2A> vrátí <xref:System.Type> objekt, který představuje základní typ typu s možnou hodnotou NULL:

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

Nepoužívejte [je](../../language-reference/keywords/is.md) operátor zjistit, zda instanci typu s možnou hodnotou Null. Jak ukazuje následující příklad, nelze rozlišit typy instancí typu s možnou hodnotou Null a jeho nadřízeného typu s použitím `is` operátor:

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

Kód uvedený v následujícím příkladu můžete použít k určení, zda je instance typu s možnou hodnotou NULL:

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]
  
## <a name="see-also"></a>Viz také:

- [Typy s možnou hodnotou Null](index.md)  
- [Použití typů s povolenou hodnotou Null](using-nullable-types.md)  
- <xref:System.Nullable.GetUnderlyingType%2A>  
