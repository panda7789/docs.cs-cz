---
title: '|= – operátor (Referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
ms.openlocfilehash: 18246d013275c8d6c8ad7e05409387457afc3442
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
---
# <a name="-operator-c-reference"></a>|= – operátor (Referenční dokumentace jazyka C#)
Operátor přiřazení OR.  
  
## <a name="remarks"></a>Poznámky  
 K pomocí výrazu `|=` operátor přiřazení, jako například  
  
```csharp  
x |= y  
```  
  
 je ekvivalentem  
  
```csharp  
x = x | y  
```  
  
 Kromě toho, že `x` je Vyhodnocená jenom jednou. [ &#124; Operátor](../../../csharp/language-reference/operators/or-operator.md) bitové logický provoz nebo na integrální operandy a logické nebo provádí bool operandy.  
  
 `|=` Operátor nemohou být přetíženy přímo, ale může přetížit uživatelem definované typy [ &#124; operátor](../../../csharp/language-reference/operators/or-operator.md) (viz [operátor](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#10](../../../csharp/language-reference/operators/codesnippet/CSharp/or-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
