---
title: '&amp;= – Operátor (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
ms.openlocfilehash: a749cf2f73faa80df49699b1e466cde290ed386e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="amp-operator-c-reference"></a>&amp;= – Operátor (referenční dokumentace jazyka C#)
Operátor přiřazení a.  
  
## <a name="remarks"></a>Poznámky  
 K pomocí výrazu `&=` operátor přiřazení, jako například  
  
```  
x &= y  
```  
  
 je ekvivalentem  
  
```  
x = x & y  
```  
  
 Kromě toho, že `x` je Vyhodnocená jenom jednou. [& Operátor](../../../csharp/language-reference/operators/and-operator.md) bitové logické a operace na integrální operandy a logické a provádí `bool` operandy.  
  
 `&=` Operátor nemohou být přetíženy přímo, ale uživatelem definované typy může přetížit binárního souboru [& operátor](../../../csharp/language-reference/operators/and-operator.md) (viz [operátor](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/CSharp/and-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
