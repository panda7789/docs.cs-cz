---
title: -&gt; Operátor (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: 037229b2081a43077cb4b5d02a8929b06ba9e077
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
---
# <a name="-gt-operator-c-reference"></a>-&gt; Operátor (referenční dokumentace jazyka C#)
`->` Operátor kombinuje ukazatel vyhodnocení a člen přístup.  
  
## <a name="remarks"></a>Poznámky  
 Výraz formuláře,  
  
```csharp  
x->y  
```  
  
 (kde `x` je ukazatel typu `T*` a `y` je členem `T`) je ekvivalentní,  
  
```csharp  
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
