---
title: -&gt; Operátor (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: 09d67b8386da371f7d98a8171f60298b316091ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-gt-operator-c-reference"></a>-&gt; Operátor (referenční dokumentace jazyka C#)
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
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
