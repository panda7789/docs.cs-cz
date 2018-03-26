---
title: 'Postupy: Přírůstek a úbytek ukazatelů (Průvodce programováním v C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
caps.latest.revision: ''
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2c8efc6d0844d867ad6eebccf3bb22c03e6d5020
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2018
---
# <a name="how-to-increment-and-decrement-pointers-c-programming-guide"></a>Postupy: Přírůstek a úbytek ukazatelů (Průvodce programováním v C#)
Přírůstek a snížení operátory, `++` a `--`, chcete-li změnit umístění ukazatele podle [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) pro ukazatel typu ukazatele – typ *. Přírůstek a snížení výrazy mít tento tvar:  
  
```  
++p;  
p++;  
--p;  
p--;  
```  
  
 Operátory přírůstku a snížení lze použít na ukazatele libovolného typu, s výjimkou typu `void*`.  
  
 Účinek použití operátor přírůstku na ukazatel typu `pointer-type` je přidání [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) na adresu, která je součástí proměnné ukazatele.  
  
 Účinek použití operátor snížení na ukazatel typu `pointer-type` je odečtena `sizeof` (`pointer-type`) z adresy, která je součástí proměnné ukazatele.  
  
 Žádné výjimky jsou generovány, pokud došlo k přetečení domény ukazatele a výsledek závisí na implementaci.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu jste jednotlivé kroky pole pomocí ukazatele a narůstajících o velikosti `int`. Pro každý krok zobrazit adresu a je obsah pole elementu.  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]  
  
 **Hodnota: 0 @ adresa: 12860272**  
**Hodnota: 1 @ adresa: 12860276**  
**Hodnota: 2 @ adresa: 12860280**  
**Hodnota: 3 @ adresa: 12860284**  
**Hodnota: 4 @ adresa: 12860288**   
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
