---
title: "*= – operátor (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dc2201f78e1e05bd0ccdea04522896c00294bdd6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>*= – operátor (Referenční dokumentace jazyka C#)
Operátor přiřazení binárního násobení.  
  
## <a name="remarks"></a>Poznámky  
 K pomocí výrazu `*=` operátor přiřazení, jako například  
  
```  
x *= y  
```  
  
 je ekvivalentem  
  
```  
x = x * y  
```  
  
 Kromě toho, že `x` je Vyhodnocená jenom jednou. [* Operátor](../../../csharp/language-reference/operators/multiplication-operator.md) je předdefinovaná pro číselné typy provést násobení.  
  
 `*=` Operátor nemohou být přetíženy přímo, ale může přetížit uživatelem definované typy [* operátor](../../../csharp/language-reference/operators/multiplication-operator.md) (viz [operátor](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
