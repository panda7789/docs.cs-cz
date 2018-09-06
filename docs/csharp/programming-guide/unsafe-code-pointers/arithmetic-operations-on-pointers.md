---
title: Aritmetické operace na ukazatelích (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
ms.openlocfilehash: 3694699466f7a200eecd5eef85f60fa19f9584a8
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43862300"
---
# <a name="arithmetic-operations-on-pointers-c-programming-guide"></a>Aritmetické operace na ukazatelích (Průvodce programováním v C#)
Toto téma popisuje použití aritmetické operátory `+` a **-** manipulace s ukazateli.  
  
> [!NOTE]
>  Nelze provést všechny aritmetické operace u ukazatelů typu void.  
  
## <a name="adding-and-subtracting-numeric-values-to-or-from-pointers"></a>Přičítání a odečítání číselné hodnoty do nebo z ukazatele  
 Můžete přidat hodnotu `n` typu [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [dlouhé](../../../csharp/language-reference/keywords/long.md), nebo [ulong](../../../csharp/language-reference/keywords/ulong.md) na ukazatel, `p`, libovolného typu s výjimkou `void*`. Výsledek `p+n` je ukazatel výsledkem přidání `n * sizeof(p) to the address of p`. Obdobně `p-n` je ukazatel výsledkem odečtením `n * sizeof(p)` z adresy `p`.  
  
## <a name="subtracting-pointers"></a>Odečtení ukazatele  
 Můžete rovněž odečíst ukazateli stejného typu. Výsledek je vždy typu `long`. Například pokud `p1` a `p2` jsou ukazatele typ `pointer-type*`, pak výraz `p1-p2` výsledkem:  
  
 `((long)p1 - (long)p2)/sizeof(pointer_type)`  
  
 Při přetečení aritmetické operace domény ukazatele a výsledek závisí na implementaci, nejsou generovány žádné výjimky.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuidePointers#14](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#15](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_2.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Nebezpečný kód a ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
- [Výrazy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)  
- [Manipulace s ukazateli](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
- [Typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [Typy](../../../csharp/language-reference/keywords/types.md)  
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
- [fixed – příkaz](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
