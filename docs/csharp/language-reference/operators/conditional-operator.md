---
title: "?: – operátor (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bbd434e02ece4843bab4ffded6877f81f622950c
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/02/2018
---
# <a name="-operator-c-reference"></a>?: – operátor (Referenční dokumentace jazyka C#)
Podmíněný operátor (`?:`), často označovaný jako Ternární podmíněný operátor vrátí jeden ze dvou hodnot v závislosti na hodnotě výrazu logické hodnoty. Následuje syntaxe pro podmiňovací operátor.  
  
```  
condition ? first_expression : second_expression;  
```  
  
## <a name="remarks"></a>Poznámky  
 `condition` Se musí vyhodnotit `true` nebo `false`. Pokud `condition` je `true`, `first_expression` je vyhodnocena a že bude výsledek. Pokud `condition` je `false`, `second_expression` je vyhodnocena a že bude výsledek. Je vyhodnocen pouze jeden ze dvou výrazů.  
  
 Buď typ `first_expression` a `second_expression` musí být stejné, nebo implicitní převod musí existovat z jednoho typu na druhý.  
  
 Můžete express výpočty, které mohou vyžadovat jinak `if-else` vytváření více výstižně pomocí podmíněný operátor. Například následující kód používá nejprve `if` příkaz a poté podmíněný operátor klasifikovat jako kladné nebo záporné celé číslo.  
  
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
  
 Podmiňovací operátor je asociativní zprava. Výraz `a ? b : c ? d : e` je vyhodnoceno jako `a ? b : (c ? d : e)`, ne jako `(a ? b : c) ? d : e`.  
  
 Podmiňovací operátor nelze přetížit.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#41](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)  
 [if-else](../../../csharp/language-reference/keywords/if-else.md)  
 [?. a? Operátory](../../../csharp/language-reference/operators/null-conditional-operators.md)  
 [?? – operátor](../../../csharp/language-reference/operators/null-conditional-operator.md)
