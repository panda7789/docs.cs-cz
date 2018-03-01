---
title: "&lt;&lt;Operátor (referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 400dbc799c68bb9e1bc00695954115f2eb6af7c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltlt-operator-c-reference"></a>&lt;&lt;Operátor (referenční dokumentace jazyka C#)
Operátor posunutí doleva (`<<`) posuny jeho první operand zbývajících podle počtu bitů určeného její druhý operand. Musí být typ Druhý operand [int](../../../csharp/language-reference/keywords/int.md) nebo typu, který má předdefinované implicitní číselný převod na `int`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je první operand [int](../../../csharp/language-reference/keywords/int.md) nebo [Celé_číslo](../../../csharp/language-reference/keywords/uint.md) (32bitová verze množství), počet posunutí je dáno nejnižší pět bitů Druhý operand. Počet skutečné posunutí je bits 0 až 31.  
  
 Pokud je první operand [dlouho](../../../csharp/language-reference/keywords/long.md) nebo [ulong](../../../csharp/language-reference/keywords/ulong.md) (množství 64-bit), počet posunutí je dáno na nejnižší šesti bits Druhý operand. Počet skutečné posunutí je 0 až 63 bitů.  
  
 Všechny nejvyšších bitů, které jsou v rozsahu typu první operand po k posunu nejsou zahozena a bits prázdný nejnižší jsou vyplněna nula. Posunutí operations nikdy příčina přetečení.  
  
 Uživatelem definované typy může přetížit `<<` – operátor (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)); typ první operand musí být uživatelem definovaný typ, a musí být typ Druhý operand `int`. Při binární operátor je přetížena, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#14](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-operator_1.cs)]  
  
## <a name="comments"></a>Komentáře  
 Všimněte si, že `i<<1` a `i<<33` poskytnout stejný výsledek, protože 1 a 33 mají stejné nejnižší pět bits.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
