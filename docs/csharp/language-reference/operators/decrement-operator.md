---
title: -- – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- --_CSharpKeyword
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4eb68143103d44defeac7191e7c4ce7d1ee90e9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="---operator-c-reference"></a>-- – operátor (Referenční dokumentace jazyka C#)
Operátor snížení (`--`) snižuje jeho operand o 1. Operátor snížení může vyskytovat před nebo po jeho operand: `--variable` a `variable--`. První formulář je operace snížení předpony. Výsledkem operace je hodnota operand "po" byla odečte. Druhý formulář je operátory snížení operace. Výsledkem operace je hodnota operand "před" jeho odečte.  
  
## <a name="remarks"></a>Poznámky  
 Operátory snížení obsahuje předdefinované číselné a výčtové typy.  
  
 Uživatelem definované typy může přetížit `--` – operátor (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)). Operace u celočíselných typů jsou obecně povoleny na výčtu.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#8](../../../csharp/language-reference/operators/codesnippet/CSharp/decrement-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
