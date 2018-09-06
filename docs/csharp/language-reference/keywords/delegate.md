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
ms.openlocfilehash: 7a5f46d137e22da01b2ab6cd3eee57d66c411e8f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44031385"
---
# <a name="delegate-c-reference"></a>delegate (Referenční dokumentace jazyka C#)

Deklarace typu delegáta je podobná signatuře metody. Nemá návratovou hodnotu a libovolný počet parametrů typu:

```csharp
public delegate void TestDelegate(string message);
public delegate int TestDelegate(MyType m, long num);
```

A `delegate` je typem odkazu, který můžete použít k zapouzdření pojmenovaná nebo anonymní metodu. Delegáti jsou podobní ukazatelům na funkci v jazyce C++; Delegáti jsou však typově bezpečné a zabezpečené. Aplikace delegátů viz [delegáti](../../../csharp/programming-guide/delegates/index.md) a [obecných delegátů](../../../csharp/programming-guide/generics/generic-delegates.md).

## <a name="remarks"></a>Poznámky

Delegáti jsou základem [události](../../../csharp/programming-guide/events/index.md).

Delegát může být vytvořena tím, že přidružíte buď pomocí pojmenovaných nebo anonymní metodu. Další informace najdete v tématu [metody s názvem](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) a [anonymní metody](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).

Delegát musí být vytvořena pomocí metody nebo lambda výraz, který je kompatibilní návratový typ a vstupní parametry. Další informace o stupeň odchylky, který je povolen v podpisu metody, naleznete v tématu [odchylky v delegátech](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md). Pro použití s anonymní metody delegáta a kód k ní být přidruženo jsou deklarovány společně. Oba způsoby konkretizujete delegátů jsou popsány v této části.

## <a name="example"></a>Příklad

[!code-csharp[csrefKeywordsTypes#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#8)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
- [Odkazové typy](../../../csharp/language-reference/keywords/reference-types.md)  
- [Delegáti](../../../csharp/programming-guide/delegates/index.md)  
- [Události](../../../csharp/programming-guide/events/index.md)  
- [Delegáti s pojmenovanými vs. anonymními metodami](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
- [Anonymní metody](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
