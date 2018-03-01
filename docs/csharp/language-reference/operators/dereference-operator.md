---
title: "-&gt;Operátor (referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4c5918f56257feb29d2624ba29b8cebaaa4f4ebe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-gt-operator-c-reference"></a>-&gt;Operátor (referenční dokumentace jazyka C#)
`->` Operátor kombinuje ukazatel vyhodnocení a člen přístup.  
  
## <a name="remarks"></a>Poznámky  
 Výraz formuláře,  
  
```  
x->y  
```  
  
 (kde `x` je ukazatel typu `T*` a `y` je členem `T`) je ekvivalentní,  
  
```  
(*x).y  
```  
  
 `->` Operátor lze použít pouze v kódu, který je označený jako [unsafe](../../../csharp/language-reference/keywords/unsafe.md).  
  
 `->` Operátor nemohou být přetíženy.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#15](../../../csharp/language-reference/operators/codesnippet/CSharp/dereference-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
