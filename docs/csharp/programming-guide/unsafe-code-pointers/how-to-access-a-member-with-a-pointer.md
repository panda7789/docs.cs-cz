---
title: "Postupy: Přístup ke členu pomocí ukazatele (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointers [C#], member access
ms.assetid: 1e998498-8c85-4a78-8ce2-4d8c20f08342
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 622d9910b09c9197b7f4ccd5e54e2675fbbbbccb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-a-member-with-a-pointer-c-programming-guide"></a>Postupy: Přístup ke členu pomocí ukazatele (Průvodce programováním v C#)
Pro přístup ke členu struktura, který je deklarován v kontextu unsafe, můžete použít operátor přístupu členů, jak je znázorněno v následujícím příkladu, ve kterém `p` je ukazatel na [struktura](../../../csharp/language-reference/keywords/struct.md) obsahující členem `x`.  
  
```  
CoOrds* p = &home;  
p -> x = 25; //member access operator ->  
```  
  
## <a name="example"></a>Příklad  
 V tomto příkladu [struktura](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, který obsahuje dvě souřadnice `x` a `y` je deklarována a vytvořena. Pomocí operátor přístupu členů `->` a ukazatel na instanci `home`, `x` a `y` přiřazené hodnoty.  
  
> [!NOTE]
>  Všimněte si, že výraz `p->x` je ekvivalentní výrazu `(*p).x`, a získáte stejný výsledek pomocí některé z dvou výrazů.  
  
 [!code-csharp[csProgGuidePointers#9](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#10](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_2.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Výrazy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Typy](../../../csharp/language-reference/keywords/types.md)  
 [nezabezpečený](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed – příkaz](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
