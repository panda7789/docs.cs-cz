---
title: "&amp;= – Operátor (referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bea90651faaafe7b754ce1cf16bddbab997d5f5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-c-reference"></a>&amp;= – Operátor (referenční dokumentace jazyka C#)
Operátor přiřazení a.  
  
## <a name="remarks"></a>Poznámky  
 K pomocí výrazu `&=` operátor přiřazení, jako například  
  
```  
x &= y  
```  
  
 je ekvivalentem  
  
```  
x = x & y  
```  
  
 Kromě toho, že `x` je Vyhodnocená jenom jednou. [& Operátor](../../../csharp/language-reference/operators/and-operator.md) bitové logické a operace na integrální operandy a logické a provádí `bool` operandy.  
  
 `&=` Operátor nemohou být přetíženy přímo, ale uživatelem definované typy může přetížit binárního souboru [& operátor](../../../csharp/language-reference/operators/and-operator.md) (viz [operátor](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/CSharp/and-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
