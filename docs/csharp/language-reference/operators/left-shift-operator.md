---
title: '&lt;&lt; – Operátor (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
ms.openlocfilehash: 036acd6159bcf5ca1677ee6383c9db357625cd67
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44127755"
---
# <a name="ltlt-operator-c-reference"></a>&lt;&lt; – Operátor (referenční dokumentace jazyka C#)
Operátor posunutí doleva (`<<`) staffhubu jeho prvního operandu vlevo o počet bitů určený svým druhým operandem. Musí být typu druhého operandu [int](../../../csharp/language-reference/keywords/int.md) nebo typ, který má předdefinované implicitní převod čísla na `int`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je první operand [int](../../../csharp/language-reference/keywords/int.md) nebo [uint](../../../csharp/language-reference/keywords/uint.md) (množství 32-bit), počet posunů je dán pět bity nižšího řádu druhého operandu. To znamená, že počet skutečné posunutí je 0 až 31 bitů.  
  
 Pokud je první operand [dlouhé](../../../csharp/language-reference/keywords/long.md) nebo [ulong](../../../csharp/language-reference/keywords/ulong.md) (množství 64-bit), počet posunů je dán šest bity nižšího řádu druhého operandu. To znamená že počet skutečné posunutí je 0 až 63 bitů.  
  
 Všechny nejvyšším bity, které jsou v rozsahu typu prvního operandu po přesun se zahodí a prázdný bity nižšího řádu jsou vyplněny nulami. Operace posunutí nikdy nezpůsobí přetečení.  
  
 Lze přetěžovat uživatelsky definované typy `<<` – operátor (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)); typ první operand musí být uživatelem definovaný typ, a musí být typu druhého operandu `int`. Při je binární operátor přetížen, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#14](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-operator_1.cs)]  
  
## <a name="comments"></a>Komentáře  
 Všimněte si, že `i<<1` a `i<<33` poskytují stejný výsledek, protože 1 a 33 mají stejné pět bity nižšího řádu.  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
