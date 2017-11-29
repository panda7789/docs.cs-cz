---
title: "Postupy: Získávání hodnoty proměnné ukazatele (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8065c10bec737789f13dcbafe147b50eedb9da36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Výrazy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Typy](../../../csharp/language-reference/keywords/types.md)  
 [nezabezpečený](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed – příkaz](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
