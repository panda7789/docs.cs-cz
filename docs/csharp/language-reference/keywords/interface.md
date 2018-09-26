---
title: interface (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 4adc7ba106e0044ba6aff94ea3180d9c8e3ded7b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47081984"
---
# <a name="interface-c-reference"></a>interface (Referenční dokumentace jazyka C#)

Rozhraní obsahuje pouze podpisy [metody](../../programming-guide/classes-and-structs/methods.md), [vlastnosti](../../programming-guide/classes-and-structs/properties.md), [události](../../programming-guide/events/index.md) nebo [indexery](../../programming-guide/indexers/index.md). Třída nebo struktura, která implementuje rozhraní, musí implementovat členy rozhraní zadané v definici rozhraní. V následujícím příkladu musí třída `ImplementationClass` implementovat metodu s názvem `SampleMethod`, která nemá žádné parametry a vrací `void`.

Další informace a příklady najdete v tématu [rozhraní](../../programming-guide/interfaces/index.md).

## <a name="example"></a>Příklad

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

Rozhraní může být členem oboru názvů nebo třídy a může obsahovat podpisy následujících členů:

- [Metody](../../programming-guide/classes-and-structs/methods.md)

- [Vlastnosti](../../programming-guide/classes-and-structs/using-properties.md)

- [Indexery](../../programming-guide/indexers/using-indexers.md)

- [Události](event.md)

Rozhraní může dědit z jednoho nebo více základních rozhraní.

Jestliže seznam základních typů obsahuje základní třídu a rozhraní, musí se základní třída nacházet v seznamu jako první.

Třída, která implementuje rozhraní, může explicitně implementovat členy rozhraní. Explicitně implementovaný člen není přístupný prostřednictvím instance třídy, ale pouze prostřednictvím instance rozhraní.

Další podrobnosti a příklady kódu implementace explicitního rozhraní naleznete v tématu [explicitní implementaci rozhraní](../../programming-guide/interfaces/explicit-interface-implementation.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje implementaci rozhraní. V tomto příkladu obsahuje rozhraní deklaraci vlastnosti a třída obsahuje implementaci. Jakákoli instance třídy, která implementuje rozhraní `IPoint`, má celočíselné vlastnosti `x` a `y`.

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)  
- [Klíčová slova jazyka C#](index.md)  
- [Odkazové typy](reference-types.md)  
- [Rozhraní](../../programming-guide/interfaces/index.md)  
- [Použití vlastností](../../programming-guide/classes-and-structs/using-properties.md)  
- [Použití indexerů](../../programming-guide/indexers/using-indexers.md)  
- [class](class.md)  
- [struct](struct.md)  
- [Rozhraní](../../programming-guide/interfaces/index.md)
