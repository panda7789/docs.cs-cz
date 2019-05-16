---
title: 'Postupy: přírůstek a úbytek ukazatelů – C# Průvodce programováním pro službu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
ms.openlocfilehash: 040437bc8cbab4ba12f243434bdea7798711ce8a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635173"
---
# <a name="how-to-increment-and-decrement-pointers-c-programming-guide"></a>Postupy: přírůstek a úbytek ukazatelů (C# Programming Guide)

Použít přírůstek a snížení operátory `++` a `--`, chcete-li změnit umístění ukazatele podle `sizeof(pointer-type)` ukazatele typu `pointer-type*`. Výrazy Inkrementace a dekrementace následující podobu:  
  
```csharp
++p;  
p++;  
--p;  
p--;  
```  
  
 Operátory přírůstku a snížení lze použít u libovolného typu s výjimkou typu ukazatele `void*`.  
  
 Efekt použití operátoru Inkrementace na ukazatel typu `pointer-type*` je přidání `sizeof(pointer-type)` na adresu, která je obsažena v proměnné ukazatele.  
  
 Efekt použití operátoru dekrementace na ukazatel typu `pointer-type*` se má odečíst `sizeof(pointer-type)` z adresy, které jsou obsaženy v proměnné ukazatele.  
  
 Nejsou generovány žádné výjimky, když došlo k přetečení domény ukazatele a výsledek závisí na implementaci.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu můžete projít pole zvýšením ukazatel velikostí `int`. U každého kroku si prohlédnout adresu a obsah elementu pole.  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#13)]  
  
**Hodnota: 0 @ adresa: 12860272**
**hodnota: 1 @ adresa: 12860276**
**hodnota: 2 @ adresa: 12860280**
**hodnota: 3 @ adresa : 12860284**
**hodnota: 4 @ adresa: 12860288**

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
- [Manipulace s ukazateli](../../../csharp/programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
- [Typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed – příkaz](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
- [sizeof](../../../csharp/language-reference/keywords/sizeof.md)
