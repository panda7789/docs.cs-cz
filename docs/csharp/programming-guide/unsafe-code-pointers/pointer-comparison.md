---
title: Porovnání ukazatelů (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
ms.openlocfilehash: af264cd1572faafe25ee170b35cbeb48ed0fb2aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337701"
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
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Výrazy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)  
 [Manipulace s ukazateli](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
 [Typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Typy](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed – příkaz](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
