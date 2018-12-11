---
title: '&gt;&gt; Operator - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: fc3d683f212c71620049ec6adee3d20bd5c1437c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239992"
---
# <a name="gtgt-operator-c-reference"></a>&gt;&gt; – Operátor (referenční dokumentace jazyka C#)
Operátor posunutí doprava (`>>`) posune jeho prvního operandu vpravo o počet bitů určený svým druhým operandem.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je první operand [int](../../../csharp/language-reference/keywords/int.md) nebo [uint](../../../csharp/language-reference/keywords/uint.md) (množství 32-bit), počet posunů je dán pět bity nižšího řádu druhého operandu (Druhý operand & 0x1f).  
  
 Pokud je první operand [dlouhé](../../../csharp/language-reference/keywords/long.md) nebo [ulong](../../../csharp/language-reference/keywords/ulong.md) (množství 64-bit), počet posunů je dán šest bity nižšího řádu druhého operandu (Druhý operand & 0x3f).  
  
 Pokud je první operand [int](../../../csharp/language-reference/keywords/int.md) nebo [dlouhé](../../../csharp/language-reference/keywords/long.md), pravého posunutí je aritmetické posun (horní prázdnou bity jsou nastaveny na bit znaménka). Pokud je první operand je typu [uint](../../../csharp/language-reference/keywords/uint.md) nebo [ulong](../../../csharp/language-reference/keywords/ulong.md), pravého posunutí je logický posun (bity nejvyšším jsou vyplněny nulami).  
  
 Lze přetěžovat uživatelsky definované typy `>>` operátor; typ první operand musí být uživatelem definovaný typ, a musí být typu druhého operandu [int](../../../csharp/language-reference/keywords/int.md). Další informace najdete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md). Při je binární operátor přetížen, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#26](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
