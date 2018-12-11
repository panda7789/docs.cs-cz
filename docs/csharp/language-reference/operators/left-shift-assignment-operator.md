---
title: '&lt;&lt;= – Operátor - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: f49c6360d6fee3f6d612aee51446545f25cd7d18
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239170"
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
