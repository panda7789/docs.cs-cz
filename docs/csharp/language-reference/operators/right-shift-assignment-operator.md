---
title: '&gt;&gt;= – Operátor (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: ccc3f688d985b9e35404550f0c53a7acf8095dd5
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
---
# <a name="gtgt-operator-c-reference"></a>&gt;&gt;= – Operátor (referenční dokumentace jazyka C#)
Operátor přiřazení posunutí doprava.  
  
## <a name="remarks"></a>Poznámky  
 Výraz, který formuláře  
  
```csharp  
x >>= y  
```  
  
 vyhodnotí jako  
  
```csharp  
x = x >> y  
```  
  
 Kromě toho, že `x` je Vyhodnocená jenom jednou. [>> Operátor](../../../csharp/language-reference/operators/right-shift-operator.md) posune `x` doprava o částku určeného `y`.  
  
 >> = Operátor nemohou být přetíženy přímo, ale může přetížit uživatelem definované typy [>> operátor](../../../csharp/language-reference/operators/right-shift-operator.md) (viz [operátor](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
