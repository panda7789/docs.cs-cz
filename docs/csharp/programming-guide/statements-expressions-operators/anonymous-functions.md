---
title: Anonymní funkce (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymus functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: 51a3c2e8399fdaae19ebe33f0d9ecc4bfd598799
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="anonymous-functions-c-programming-guide"></a>Anonymní funkce (Průvodce programováním v C#)
Anonymní funkce je "vložené" příkaz nebo výraz, který lze použít bez ohledu na očekáván je typ delegáta. Můžete ji k inicializaci pojmenované delegáta nebo předat místo typu s názvem delegáta jako parametr metody.  
  
 Existují dva druhy anonymní funkce, které jsou jednotlivě popsané v následujících tématech:  
  
-   [Lambda – výrazy](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
-   [Anonymní metody](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
    > [!NOTE]
    >  Lambda – výrazy mohou být vázány stromů výrazů a delegáti.  
  
## <a name="the-evolution-of-delegates-in-c"></a>Vývoj Delegáti v jazyce C#  
 V C# 1.0 jste vytvořili instanci delegáta pomocí explicitní inicializaci pomocí metody, která byla definována někde v kódu. C# 2.0 zaveden koncept anonymní metody jako způsob, jak zapisuje nepojmenované vložené příkaz bloky, které mohou být provedeny v vyvolání delegáta. Lambda – výrazy, které jsou v principu podobná anonymní metody ale výrazovou a stručným se zavedl C# 3.0. Tyto dvě funkce se souhrnně označují jako *anonymní funkce*. Obecně platí, aplikace, jejichž cílem verze 3.5 nebo novější z [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] by použití výrazů lambda.  
  
 Následující příklad ukazuje vývoj delegáta vytvoření z jazyka C# 1.0 pro C# 3.0:  
  
 [!code-csharp[csProgGuideLINQ#65](../../../csharp/programming-guide/arrays/codesnippet/CSharp/anonymous-functions_1.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Příkazy, výrazy a operátory](../../../csharp/programming-guide/statements-expressions-operators/index.md)  
 [Výrazy lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [Delegáti](../../../csharp/programming-guide/delegates/index.md)  
 [Stromy výrazů](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)
