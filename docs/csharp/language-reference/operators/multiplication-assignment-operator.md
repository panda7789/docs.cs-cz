---
title: '*= – operátor (Referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 465cf37d38a989d5c1bf6f0d0242c295e55684f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a>*= – operátor (Referenční dokumentace jazyka C#)
Operátor přiřazení binárního násobení.  
  
## <a name="remarks"></a>Poznámky  
 K pomocí výrazu `*=` operátor přiřazení, jako například  
  
```  
x *= y  
```  
  
 je ekvivalentem  
  
```  
x = x * y  
```  
  
 Kromě toho, že `x` je Vyhodnocená jenom jednou. [* Operátor](../../../csharp/language-reference/operators/multiplication-operator.md) je předdefinovaná pro číselné typy provést násobení.  
  
 `*=` Operátor nemohou být přetíženy přímo, ale může přetížit uživatelem definované typy [* operátor](../../../csharp/language-reference/operators/multiplication-operator.md) (viz [operátor](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
