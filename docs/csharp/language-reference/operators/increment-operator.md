---
title: ++ – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
ms.openlocfilehash: 0fe1150ca7267d02feeab33168eab7f79734c2a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a>++ – operátor (Referenční dokumentace jazyka C#)
Operátor přírůstku (`++`) jeho operand zvýší o 1. Operátor přírůstku může vyskytovat před nebo po jeho operand: `++variable` a `variable++`.  
  
## <a name="remarks"></a>Poznámky  
 První formulář je předpona přírůstek operace. Výsledkem operace je hodnota operand po byla zvýšena.  
  
 Druhý formulář je operace operátory přírůstku. Výsledkem operace je hodnota operand předtím, než byla zvýšena.  
  
 Operátory přírůstku obsahuje předdefinované číselné a výčtové typy. Uživatelem definované typy může přetížit `++` operátor. Operace u celočíselných typů jsou obecně povoleny na výčtu.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
