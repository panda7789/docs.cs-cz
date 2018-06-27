---
title: delegate (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- delegate_CSharpKeyword
- delegate
- CS0123
helpviewer_keywords:
- delegate keyword [C#]
- function pointers [C#]
ms.assetid: 0bb8cb6d-2f87-47c7-9d1f-d65c1cd01e9f
ms.openlocfilehash: ba1cfdcc56b3d2301a07ffa4af793e7002da21bb
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948420"
---
# <a name="delegate-c-reference"></a>delegate (Referenční dokumentace jazyka C#)

Deklarace typu delegáta je podobná podpis metody. Má návratovou hodnotu a libovolný počet parametrů libovolného typu:

```csharp
public delegate void TestDelegate(string message);
public delegate int TestDelegate(MyType m, long num);
```

A `delegate` je odkaz na typ, který slouží k zapouzdření pojmenovaná nebo anonymní metody. Delegáti jsou podobná ukazatelů na funkce v jazyce C++; Delegáti jsou však bezpečnost typů a zabezpečení. Aplikace delegáti, naleznete v [delegáti](../../../csharp/programming-guide/delegates/index.md) a [obecní delegáti](../../../csharp/programming-guide/generics/generic-delegates.md).

## <a name="remarks"></a>Poznámky

Delegáti slouží jako základ pro [události](../../../csharp/programming-guide/events/index.md).

Delegát se dá vytvořit instance tím, že přidružíte buď pomocí metody s názvem nebo anonymní. Další informace najdete v tématu [s názvem metody](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) a [anonymní metody](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).

Delegát musí být vytvořena s metoda nebo lambda výraz, který má kompatibilní návratový typ a vstupní parametry. Další informace o stupeň odchylky, který je povolen v podpis metody naleznete v tématu [odchylky v delegátech](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md). Pro použití s anonymní metody jsou delegát a kód, který se má přidružit ho deklarovat společně. Obou směrech konkretizujete Delegáti jsou popsané v této části.

## <a name="example"></a>Příklad

[!code-csharp[csrefKeywordsTypes#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#8)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
[Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
[Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
[Odkazové typy](../../../csharp/language-reference/keywords/reference-types.md)  
[Delegáti](../../../csharp/programming-guide/delegates/index.md)  
[Události](../../../csharp/programming-guide/events/index.md)  
[Delegáti s pojmenovanými vs. anonymními metodami](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
[Anonymní metody](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
