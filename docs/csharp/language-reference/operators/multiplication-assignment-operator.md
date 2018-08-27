---
title: '*= – operátor (Referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: e47bc5c681c94ac3fc5c345c56b3814350ffa5ec
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932347"
---
# <a name="-operator-c-reference"></a>*= – operátor (Referenční dokumentace jazyka C#)
Operátor přiřazení binárního násobení.  
  
## <a name="remarks"></a>Poznámky  
 Pomocí výrazu `*=` operátor přiřazení, jako například  
  
```csharp  
x *= y  
```  
  
 je ekvivalentem  
  
```csharp  
x = x * y  
```  
  
 s tím rozdílem, že `x` se jenom vyhodnotí jednou. [* – Operátor](../../../csharp/language-reference/operators/multiplication-operator.md) předdefinovaných číselných typů k provedení násobení.  
  
 `*=` Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [* – operátor](../../../csharp/language-reference/operators/multiplication-operator.md) (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
