---
title: '%= – operátor (Referenční dokumentace jazyka C#)'
ms.date: 04/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: aadcb5ef969ff408cc1e738fc0f5b67152fdc78b
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171964"
---
# <a name="-operator-c-reference"></a>%= – operátor (Referenční dokumentace jazyka C#)
Operátor přiřazení zbytku.  
  
## <a name="remarks"></a>Poznámky  
 K pomocí výrazu `%=` operátor přiřazení, jako například  
  
```csharp  
x %= y  
```  
  
 je ekvivalentem  
  
```csharp  
x = x % y  
```  
  
 Kromě toho, že `x` je Vyhodnocená jenom jednou. [% – Operátor](../../../csharp/language-reference/operators/remainder-operator.md) je předdefinovaná pro číselné typy vypočítat zbytek po dělení.  
  
 `%=` Operátor nemohou být přetíženy přímo, ale může přetížit uživatelem definované typy [% – operátor](../../../csharp/language-reference/operators/remainder-operator.md) (viz [– operátor (referenční dokumentace jazyka C#)](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
