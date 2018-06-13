---
title: '&gt;&gt; Operátor (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: 061a69250ef5524fa6b5f7bb4b9527057dd86e05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33285886"
---
# <a name="gtgt-operator-c-reference"></a>&gt;&gt; Operátor (referenční dokumentace jazyka C#)
Operátor posunutí doprava (`>>`) posune jeho první operand právo podle počtu bitů určeného její druhý operand.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je první operand [int](../../../csharp/language-reference/keywords/int.md) nebo [Celé_číslo](../../../csharp/language-reference/keywords/uint.md) (32bitová verze množství), počet posunutí je dáno nejnižší pět bitů Druhý operand (Druhý operand & 0x1f).  
  
 Pokud je první operand [dlouho](../../../csharp/language-reference/keywords/long.md) nebo [ulong](../../../csharp/language-reference/keywords/ulong.md) (množství 64-bit), počet posunutí je dáno na nejnižší šesti bits Druhý operand (Druhý operand & 0x3f).  
  
 Pokud je první operand [int](../../../csharp/language-reference/keywords/int.md) nebo [dlouho](../../../csharp/language-reference/keywords/long.md), aritmetické posunutí je posunutí doprava (horní prázdný bity jsou nastaveny na bit přihlašování). Pokud je první operand typu [Celé_číslo](../../../csharp/language-reference/keywords/uint.md) nebo [ulong](../../../csharp/language-reference/keywords/ulong.md), je logické shift posunutí doprava (horní bity jsou vyplněna nula).  
  
 Uživatelem definované typy může přetížit `>>` operátor; typ první operand musí být uživatelem definovaný typ, a musí být typ Druhý operand [int](../../../csharp/language-reference/keywords/int.md). Další informace najdete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md). Při binární operátor je přetížena, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#26](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
