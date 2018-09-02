---
title: '&amp;= – Operátor (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
ms.openlocfilehash: f3a6fe20ca89a90b5a64118d73fb39e9a364d1e9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406732"
---
# <a name="amp-operator-c-reference"></a>&amp;= – Operátor (referenční dokumentace jazyka C#)
Operátor přiřazení AND.  
  
## <a name="remarks"></a>Poznámky  
 Pomocí výrazu `&=` operátor přiřazení, jako například  
  
```csharp  
x &= y  
```  
  
 je ekvivalentem  
  
```csharp  
x = x & y  
```  
  
 s tím rozdílem, že `x` se jenom vyhodnotí jednou. [& – Operátor](../../../csharp/language-reference/operators/and-operator.md) provádí bitové logické AND operace na celočíselných operandech a logický operátor AND `bool` operandy.  
  
 `&=` Operátor nelze přetížit přímo, ale uživatelské typy mohou přetížit binárního souboru [& – operátor](../../../csharp/language-reference/operators/and-operator.md) (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/CSharp/and-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
