---
title: '&lt;&lt;= – Operátor (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: c689aeccdf3ad6cc6c672cc101a4f0aa92f19791
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517201"
---
# <a name="ltlt-operator-c-reference"></a>&lt;&lt;= – Operátor (referenční dokumentace jazyka C#)
Operátor přiřazení posunutí doleva.  
  
## <a name="remarks"></a>Poznámky  
 Výraz ve tvaru  
  
```csharp  
x <<= y  
```  
  
 je vyhodnocen jako  
  
```csharp  
x = x << y  
```  
  
 s tím rozdílem, že `x` se jenom vyhodnotí jednou. [<< Operátor](../../../csharp/language-reference/operators/left-shift-operator.md) posune `x` doleva o počet bitů určený `y`.  
  
 `<<=` Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [<< operátor](../../../csharp/language-reference/operators/left-shift-operator.md) (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#12](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
