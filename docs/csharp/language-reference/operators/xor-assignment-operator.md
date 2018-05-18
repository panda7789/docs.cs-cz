---
title: ^= – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
ms.openlocfilehash: b868f2cdbfa8a80f89a12e6194a30154481f0b07
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
---
# <a name="-operator-c-reference"></a>^= – operátor (Referenční dokumentace jazyka C#)
Operátor přiřazení exkluzivní disjunkce OR.  
  
## <a name="remarks"></a>Poznámky  
 Výraz, který formuláře  
  
```csharp  
x ^= y  
```  
  
 vyhodnotí jako  
  
```csharp  
x = x ^ y  
```  
  
 Kromě toho, že `x` je Vyhodnocená jenom jednou. [^ – Operátor](../../../csharp/language-reference/operators/xor-operator.md) provádí bitový exkluzivní disjunkce OR operaci na integrální operandy a logických exkluzivní disjunkce OR na [bool](../../../csharp/language-reference/keywords/bool.md) operandy.  
  
 ^ = – Operátor nemohou být přetíženy přímo, ale může přetížit uživatelem definované typy [^ – operátor](../../../csharp/language-reference/operators/xor-operator.md) (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
