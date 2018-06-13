---
title: '&lt;&lt;= – Operátor (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: e5f3886670baa34b0360501ee15280b93fac36bc
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171790"
---
# <a name="ltlt-operator-c-reference"></a>&lt;&lt;= – Operátor (referenční dokumentace jazyka C#)
Operátor přiřazení posunutí doleva.  
  
## <a name="remarks"></a>Poznámky  
 Výraz, který formuláře  
  
```csharp  
x <<= y  
```  
  
 vyhodnotí jako  
  
```csharp  
x = x << y  
```  
  
 Kromě toho, že `x` je Vyhodnocená jenom jednou. [<< Operátor](../../../csharp/language-reference/operators/left-shift-operator.md) posune `x` zbývajících podle počtu bitů určeného `y`.  
  
 `<<=` Operátor nemohou být přetíženy přímo, ale může přetížit uživatelem definované typy [<< operátor](../../../csharp/language-reference/operators/left-shift-operator.md) (viz [operátor](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#12](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
