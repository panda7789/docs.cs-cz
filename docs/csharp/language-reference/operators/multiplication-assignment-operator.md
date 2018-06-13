---
title: '*= – operátor (Referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 6bbf2142ca7e9e05010a29920da52e1439f6e882
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171547"
---
# <a name="-operator-c-reference"></a>*= – operátor (Referenční dokumentace jazyka C#)
Operátor přiřazení binárního násobení.  
  
## <a name="remarks"></a>Poznámky  
 K pomocí výrazu `*=` operátor přiřazení, jako například  
  
```csharp  
x *= y  
```  
  
 je ekvivalentem  
  
```csharp  
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
