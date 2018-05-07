---
title: false – – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: f2001d92e99476131d6f03e13f0bc12104f638b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="false-operator-c-reference"></a>false – – operátor (Referenční dokumentace jazyka C#)
Vrátí [bool](../../../csharp/language-reference/keywords/bool.md) hodnotu `true` označuje, že operand `false` a vrátí `false` jinak.  
  
 Před C# 2.0 `true` a `false` operátory jste použili k vytvoření typů s povolenou hodnotou Null hodnotu definovanou uživatelem, které byly kompatibilní s typy, jako `SqlBool`. Ale jazyk teď poskytuje integrovanou podporu pro typy hodnot s povolenou hodnotou Null, a kdykoli je to možné postupujte podle těchto místo přetížení `true` a `false` operátory. Další informace najdete v tématu [typy s možnou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md).  
  
 S s možnou hodnotou Null logické hodnoty, výraz `a != b` není nutně roven `!(a == b)` vzhledem k tomu, že jedna nebo obě hodnoty může mít hodnotu null. Budete muset přetížení i `true` a `false` operátorům samostatně správně zpracování hodnot null ve výrazu. Následující příklad ukazuje, jak přetížení a používat `true` a `false` operátory.  
  
 [!code-csharp[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/false-operator_1.cs)]  
  
 Typ, který přetížení `true` a `false` operátory lze použít pro řízení výrazu v [Pokud](../../../csharp/language-reference/keywords/if-else.md), [provést](../../../csharp/language-reference/keywords/do.md), [při](../../../csharp/language-reference/keywords/while.md), a [ pro](../../../csharp/language-reference/keywords/for.md) příkazy a v [podmíněné výrazy](../../../csharp/language-reference/operators/conditional-operator.md).  
  
 Pokud typ definuje operátor `false`, musí definovat také operátor [true](../../../csharp/language-reference/keywords/true.md).  
  
 Typ nelze přímo přetížení podmíněného logické operátory [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) a [ &#124; &#124; ](../../../csharp/language-reference/operators/conditional-or-operator.md), ale lze dosáhnout ekvivalentní vliv přetížení regulární logické operátory operátory a `true` a `false`.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)  
 [true](../../../csharp/language-reference/keywords/true.md)
