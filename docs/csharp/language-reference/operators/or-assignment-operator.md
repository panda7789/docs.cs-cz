---
title: '|= – operátor (Referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
ms.openlocfilehash: fe56005ce94656b5e8a075cddfb91dc0da096cf7
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44707189"
---
# <a name="-operator-c-reference"></a>|= – operátor (Referenční dokumentace jazyka C#)
Operátor přiřazení OR.  
  
## <a name="remarks"></a>Poznámky  
 Pomocí výrazu `|=` operátor přiřazení, jako například  
  
```csharp  
x |= y  
```  
  
 je ekvivalentem  
  
```csharp  
x = x | y  
```  
  
 s tím rozdílem, že `x` se jenom vyhodnotí jednou. [ &#124; Operátor](../../../csharp/language-reference/operators/or-operator.md) provádí bitové logické OR operace na celočíselných operandech a logický operátor OR na operandech typu bool.  
  
 `|=` Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [ &#124; operátor](../../../csharp/language-reference/operators/or-operator.md) (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#10](../../../csharp/language-reference/operators/codesnippet/CSharp/or-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
