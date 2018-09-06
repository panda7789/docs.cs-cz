---
title: ^= – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
ms.openlocfilehash: d6546f23ffb6dee792339a7e3863bf58ae668d58
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43857229"
---
# <a name="-operator-c-reference"></a>^= – operátor (Referenční dokumentace jazyka C#)
Operátor přiřazení exkluzivní disjunkce OR.  
  
## <a name="remarks"></a>Poznámky  
 Výraz ve tvaru  
  
```csharp  
x ^= y  
```  
  
 je vyhodnocen jako  
  
```csharp  
x = x ^ y  
```  
  
 s tím rozdílem, že `x` se jenom vyhodnotí jednou. [^ – Operátor](../../../csharp/language-reference/operators/xor-operator.md) provádí bitový exkluzivní operátor OR operaci na celočíselných operandech a logické exkluzivní disjunkce OR na [bool](../../../csharp/language-reference/keywords/bool.md) operandy.  
  
 ^ = – Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [^ – operátor](../../../csharp/language-reference/operators/xor-operator.md) (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
