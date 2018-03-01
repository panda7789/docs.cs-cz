---
title: "&gt;&gt;= – Operátor (referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6bd0a61860c35a485d61585a90ba297f75d8cf1a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="gtgt-operator-c-reference"></a>&gt;&gt;= – Operátor (referenční dokumentace jazyka C#)
Operátor přiřazení posunutí doprava.  
  
## <a name="remarks"></a>Poznámky  
 Výraz, který formuláře  
  
```  
x >>= y  
```  
  
 vyhodnotí jako  
  
```  
x = x >> y  
```  
  
 Kromě toho, že `x` je Vyhodnocená jenom jednou. [>> Operátor](../../../csharp/language-reference/operators/right-shift-operator.md) posune `x` doprava o částku určeného `y`.  
  
 >> = Operátor nemohou být přetíženy přímo, ale může přetížit uživatelem definované typy [>> operátor](../../../csharp/language-reference/operators/right-shift-operator.md) (viz [operátor](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
