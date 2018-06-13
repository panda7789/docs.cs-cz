---
title: 'Postupy: Získávání hodnoty proměnné ukazatele (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
ms.openlocfilehash: c53026149837681235c6d1001707a25b9c8b40b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322949"
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a>Postupy: Získávání hodnoty proměnné ukazatele (Průvodce programováním v C#)
Deferenční operátor ukazatel pomocí můžete získat proměnnou v umístění, na kterou ukazatel odkazuje. Výraz má následující podobu, kde `p` je ukazatel typu:  
  
```  
*p;  
```  
  
 Deferenční operátor unární nelze použít na výrazy, které jiného typu než je ukazatel typu. Navíc nelze použít, aby [void](../../../csharp/language-reference/keywords/void.md) ukazatel.  
  
 Když použijete deferenční operátor k [null](../../../csharp/language-reference/keywords/null.md) ukazatele, výsledek závisí na implementaci.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu, proměnné typu `char` přistupuje pomocí ukazatele různých typů. Všimněte si, že adresa `theChar` se liší z spustit na spustit, protože fyzické adresy přidělené do proměnné, můžete změnit.  
  
 [!code-csharp[csProgGuidePointers#5](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#6](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_2.cs)]  
  
 **Hodnota theChar = Z**  
**Adresa theChar = 12F718**  
**Hodnota pChar = Z**   
**Hodnota pinta = 90**    
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Výrazy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Typy](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed – příkaz](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
