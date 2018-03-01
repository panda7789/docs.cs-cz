---
title: "++ – operátor (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6deb2f772fefc93020e7eaaed6be35e48b11df7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
