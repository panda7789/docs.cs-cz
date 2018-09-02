---
title: '?: – operátor (Referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 150149453a67d8e5319461266865cb25be180347
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43421501"
---
# <a name="-operator-c-reference"></a>?: – operátor (Referenční dokumentace jazyka C#)
Podmíněný operátor (`?:`), obvykle označovaný jako Ternární podmiňovací operátor vrátí jednu ze dvou hodnot v závislosti na hodnotě logického výrazu. Následuje syntaxe pro podmiňovací operátor.  
  
```  
condition ? first_expression : second_expression;  
```  
  
## <a name="remarks"></a>Poznámky  
 `condition` Se musí vyhodnotit na `true` nebo `false`. Pokud `condition` je `true`, `first_expression` jsou vyhodnoceny a výsledek. Pokud `condition` je `false`, `second_expression` jsou vyhodnoceny a výsledek. Je vyhodnocen pouze jeden ze dvou výrazů.  
  
 Typ parametru `first_expression` a `second_expression` musí být stejné, nebo musí existovat implicitní převod z jednoho typu na druhý.  
  
 Můžete vyjádřit výpočty, které by jinak vyžadovaly `if-else` konstrukce více stručně a výstižně pomocí podmíněného operátoru. Například následující kód používá nejprve `if` příkaz a poté podmiňovací operátor pro klasifikaci celého čísla jako kladné nebo záporné.  
  
```csharp
int input = Convert.ToInt32(Console.ReadLine());  
string classify;  
  
// if-else construction.  
if (input > 0)  
    classify = "positive";  
else  
    classify = "negative";  
  
// ?: conditional operator.  
classify = (input > 0) ? "positive" : "negative";  
```  
  
 Podmiňovací operátor je asociativní zprava. Výraz `a ? b : c ? d : e` se vyhodnotí jako `a ? b : (c ? d : e)`, nikoli jako `(a ? b : c) ? d : e`.  
  
 Podmiňovací operátor nelze přetížit.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#41](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)  
- [if-else](../../../csharp/language-reference/keywords/if-else.md)  
- [Operátory ?. a ?[]](../../../csharp/language-reference/operators/null-conditional-operators.md)  
- [?? – operátor](../../../csharp/language-reference/operators/null-coalescing-operator.md)
