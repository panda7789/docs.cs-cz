---
title: '%= – operátor (Referenční dokumentace jazyka C#)'
ms.date: 04/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: 009c162b13fab05ba349d0535fe8dfae206502f3
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507934"
---
# <a name="-operator-c-reference"></a>%= – operátor (Referenční dokumentace jazyka C#)
Operátor přiřazení zbytku.  
  
## <a name="remarks"></a>Poznámky  
 Pomocí výrazu `%=` operátor přiřazení, jako například  
  
```csharp  
x %= y  
```  
  
 je ekvivalentem  
  
```csharp  
x = x % y  
```  
  
 s tím rozdílem, že `x` se jenom vyhodnotí jednou. [% – Operátor](../../../csharp/language-reference/operators/remainder-operator.md) předdefinovaných číselných typů k výpočtu zbytek po dělení.  
  
 `%=` Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [% – operátor](../../../csharp/language-reference/operators/remainder-operator.md) (viz [– operátor (referenční dokumentace jazyka C#)](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
