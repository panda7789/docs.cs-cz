---
title: true – – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- true operator [C#]
ms.assetid: acaba817-5da5-4364-b3b2-2e5c75ec1839
ms.openlocfilehash: 54b8d764dc673598474d6adbbee82e0223a16b93
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45609926"
---
# <a name="true-operator-c-reference"></a>true – – operátor (Referenční dokumentace jazyka C#)
Vrátí [bool](../../../csharp/language-reference/keywords/bool.md) hodnotu `true` k označení, že operand má hodnotu true a vrátí `false` jinak.  
  
 Před C# 2.0 `true` a `false` operátory byly použity k vytvoření typy s možnou hodnotou Null hodnotu definovanou uživatelem, které byly kompatibilní s typy, jako `SqlBool`. Však jazyk teď poskytuje integrovanou podporu pro typy s možnou hodnotou Null, a kdykoli je to možné, abyste používali tyto místo přetížení `true` a `false` operátory. Další informace najdete v tématu [typy připouštějící hodnotu Null](../../../csharp/programming-guide/nullable-types/index.md).  
  
 S s povolenou hodnotou Null, logické hodnoty výrazu `a != b` , nemusí být nutně roven `!(a == b)` protože jedna nebo obě hodnoty může mít hodnotu null. Je potřeba obě přetížení `true` a `false` operátory samostatně pro zajištění správné identifikace hodnot null ve výrazu. Následující příklad ukazuje, jak přetížení a použít `true` a `false` operátory.  
  
 [!code-csharp[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/true-operator_1.cs)]  
  
 Typ, který přetížení `true` a `false` operátory lze používat pro řídicí výraz v [Pokud](../../../csharp/language-reference/keywords/if-else.md), [proveďte](../../../csharp/language-reference/keywords/do.md), [při](../../../csharp/language-reference/keywords/while.md), a [ pro](../../../csharp/language-reference/keywords/for.md) příkazy a [podmíněné výrazy](../../../csharp/language-reference/operators/conditional-operator.md).  
  
 Pokud typ definuje operátor `true`, musíte také definovat operátor [false](../../../csharp/language-reference/keywords/false.md).  
  
 Typ nejde přetížit přímo podmíněné logické operátory ([ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) a [ &#124; &#124; ](../../../csharp/language-reference/operators/conditional-or-operator.md)), ale stejného účinku lze dosáhnout přetížení standardní logické operátory a operátory `true` a `false`.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)  
- [false](../../../csharp/language-reference/keywords/false.md)
