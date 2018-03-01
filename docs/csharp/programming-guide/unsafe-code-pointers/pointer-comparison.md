---
title: "Porovnání ukazatelů (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0b45b9152272244b9a0c9d0fa3787973f8f8182a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="pointer-comparison-c-programming-guide"></a>Porovnání ukazatelů (Průvodce programováním v C#)
Můžete použít následující operátory k porovnání ukazatelů libovolného typu:  
  
 **==   !=   \<   >   \<=   >=**  
  
 Relační operátory porovnávání adresy dva operandy jako v případě, že jsou bez znaménka celých čísel.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuidePointers#16](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#17](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_2.cs)]  
  
## <a name="sample-output"></a>Vzorový výstup  
 `True`  
  
 `False`  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Výrazy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)  
 [Manipulace s ukazateli](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
 [Typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Typy](../../../csharp/language-reference/keywords/types.md)  
 [nezabezpečený](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed – příkaz](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
