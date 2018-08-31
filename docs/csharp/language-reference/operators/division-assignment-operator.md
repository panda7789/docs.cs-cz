---
title: /= – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
ms.openlocfilehash: 8fff048cc441181aa3f0e3c0c638d501aaf9de3f
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2018
ms.locfileid: "43330929"
---
# <a name="-operator-c-reference"></a>/= – operátor (Referenční dokumentace jazyka C#)
Operátor přiřazení dělení.  
  
## <a name="remarks"></a>Poznámky  
 Pomocí výrazu `/=` operátor přiřazení, jako například  
  
```csharp  
x /= y  
```  
  
 je ekvivalentem  
  
```csharp  
x = x / y  
```  
  
 s tím rozdílem, že `x` se jenom vyhodnotí jednou. [/ – Operátor](../../../csharp/language-reference/operators/division-operator.md) je předdefinovaný pro číselné typy provádět dělení.  
  
 `/=` Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [/ – operátor](../../../csharp/language-reference/operators/division-operator.md) (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)). Na všechny složené operátory přiřazení implicitně přetížení binární operátor přetížení ekvivalentní složeného přiřazení.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
