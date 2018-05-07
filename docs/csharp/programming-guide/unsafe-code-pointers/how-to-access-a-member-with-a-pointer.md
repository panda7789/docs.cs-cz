---
title: 'Postupy: Přístup ke členu pomocí ukazatele (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], member access
ms.assetid: 1e998498-8c85-4a78-8ce2-4d8c20f08342
ms.openlocfilehash: 20f0dd18bb5ca132d05335953958d8f747b6abc4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Výrazy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Typy](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed – příkaz](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
