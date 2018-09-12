---
title: -&gt; – Operátor (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: fb95e508ce1339868723bcc3178851e8c1355c1f
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44700580"
---
# <a name="-gt-operator-c-reference"></a>-&gt; – Operátor (referenční dokumentace jazyka C#)
`->` Operátor kombinuje ukazatel přesměrování a člen přístup.  
  
## <a name="remarks"></a>Poznámky  
 Výraz formuláře  
  
```csharp  
x->y  
```  
  
 (kde `x` je ukazatel typu `T*` a `y` je členem skupiny `T`) je ekvivalentní,  
  
```csharp  
(*x).y  
```  
  
 `->` Operátor lze použít pouze v kódu, který je označen jako [nebezpečné](../../../csharp/language-reference/keywords/unsafe.md).  
  
 `->` Operátor nelze přetížit.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#15](../../../csharp/language-reference/operators/codesnippet/CSharp/dereference-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
