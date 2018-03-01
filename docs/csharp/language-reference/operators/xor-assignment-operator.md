---
title: "^= – operátor (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8d4de06dbfd269dc5e0f2cc5003e8981068220a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>^= – operátor (Referenční dokumentace jazyka C#)
Operátor přiřazení exkluzivní disjunkce OR.  
  
## <a name="remarks"></a>Poznámky  
 Výraz, který formuláře  
  
```  
x ^= y  
```  
  
 vyhodnotí jako  
  
```  
x = x ^ y  
```  
  
 Kromě toho, že `x` je Vyhodnocená jenom jednou. [^ – Operátor](../../../csharp/language-reference/operators/xor-operator.md) provádí bitový exkluzivní disjunkce OR operaci na integrální operandy a logických exkluzivní disjunkce OR na [bool](../../../csharp/language-reference/keywords/bool.md) operandy.  
  
 ^ = – Operátor nemohou být přetíženy přímo, ale může přetížit uživatelem definované typy [^ – operátor](../../../csharp/language-reference/operators/xor-operator.md) (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
