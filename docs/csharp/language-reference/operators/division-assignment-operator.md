---
title: "/= – operátor (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 26096d9b5dfc565c9933f1ed8ffb241dc900d9ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>/= – operátor (Referenční dokumentace jazyka C#)
Operátor přiřazení dělení.  
  
## <a name="remarks"></a>Poznámky  
 K pomocí výrazu `/=` operátor přiřazení, jako například  
  
```  
x /= y  
```  
  
 je ekvivalentem  
  
```  
x = x / y  
```  
  
 Kromě toho, že `x` je Vyhodnocená jenom jednou. [Nebo operátor](../../../csharp/language-reference/operators/division-operator.md) je předdefinovaná pro číselné typy provádět dělení.  
  
 `/=` Operátor nemohou být přetíženy přímo, ale může přetížit uživatelem definované typy [nebo operátor](../../../csharp/language-reference/operators/division-operator.md) (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)). Na všechny složené operátory přiřazení přetížení binární operátor implicitně přetížení ekvivalentní složeného přiřazení.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
