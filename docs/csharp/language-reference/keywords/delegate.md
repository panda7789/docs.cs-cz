---
title: "delegate (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- delegate_CSharpKeyword
- delegate
- CS0123
helpviewer_keywords:
- delegate keyword [C#]
- function pointers [C#]
ms.assetid: 0bb8cb6d-2f87-47c7-9d1f-d65c1cd01e9f
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 179e89cea0e683b72e57536d4e4d86b019493aed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="delegate-c-reference"></a>delegate (Referenční dokumentace jazyka C#)
Deklarace typu delegáta je podobná podpis metody. Má návratovou hodnotu a libovolný počet parametrů libovolného typu:  
  
```  
public delegate void TestDelegate(string message);  
public delegate int TestDelegate(MyType m, long num);  
```  
  
 A `delegate` je odkaz na typ, který slouží k zapouzdření pojmenovaná nebo anonymní metody. Delegáti jsou podobná ukazatelů na funkce v jazyce C++; Delegáti jsou však bezpečnost typů a zabezpečení. Aplikace delegáti, naleznete v [delegáti](../../../csharp/programming-guide/delegates/index.md) a [obecní delegáti](../../../csharp/programming-guide/generics/generic-delegates.md).  
  
## <a name="remarks"></a>Poznámky  
 Delegáti slouží jako základ pro [události](../../../csharp/programming-guide/events/index.md).  
  
 Delegát se dá vytvořit instance tím, že přidružíte buď pomocí metody s názvem nebo anonymní. Další informace najdete v tématu [s názvem metody](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) a [anonymní metody](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).  
  
 Delegát musí být vytvořena s metoda nebo lambda výraz, který má kompatibilní návratový typ a vstupní parametry. Další informace o stupeň odchylky, který je povolen v podpis metody naleznete v tématu [odchylky v delegátech](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md). Pro použití s anonymní metody jsou delegát a kód, který se má přidružit ho deklarovat společně. Obou směrech konkretizujete Delegáti jsou popsané v této části.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csrefKeywordsTypes#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/delegate_1.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Odkazové typy](../../../csharp/language-reference/keywords/reference-types.md)  
 [Delegáti](../../../csharp/programming-guide/delegates/index.md)  
 [Události](../../../csharp/programming-guide/events/index.md)  
 [Delegáti s pojmenované vs. Anonymní metody](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
 [Anonymní metody](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
