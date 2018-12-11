---
title: '* = – Operátor - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: f8604cdadeda14a5761bc923bd966186fd258a6d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245347"
---
# <a name="-operator-c-reference"></a>*= – operátor (Referenční dokumentace jazyka C#)
Operátor přiřazení binárního násobení.  
  
## <a name="remarks"></a>Poznámky  
 Pomocí výrazu `*=` operátor přiřazení, jako například  
  
```csharp  
x *= y  
```  
  
 je ekvivalentem  
  
```csharp  
x = x * y  
```  
  
 s tím rozdílem, že `x` se jenom vyhodnotí jednou. [* – Operátor](../../../csharp/language-reference/operators/multiplication-operator.md) předdefinovaných číselných typů k provedení násobení.  
  
 `*=` Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [* – operátor](../../../csharp/language-reference/operators/multiplication-operator.md) (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
