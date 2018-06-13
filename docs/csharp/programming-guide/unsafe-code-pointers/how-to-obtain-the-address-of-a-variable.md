---
title: 'Postupy: Získávání adresy proměnné (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
ms.openlocfilehash: bb52aee3341194697b40b30ec14afced61a200be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340122"
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a>Postupy: Získávání adresy proměnné (Průvodce programováním v C#)
Pokud chcete získat adresu unární výraz, který vyhodnocuje pevné proměnné, použijte operátor adresy `&`:  
  
```csharp  
int number;  
int* p = &number; //address-of operator &  
```  
  
 Operátor adresy lze použít pouze k proměnné. Pokud je proměnná přenosné proměnné, můžete použít [příkazu pevnou](../../../csharp/language-reference/keywords/fixed-statement.md) dočasně opravit před získávání adresy proměnné.  
  
 Je vaší povinností ujistit, že je inicializováno proměnnou. Kompilátor není vydat chybovou zprávu, pokud proměnnou není inicializován.  
  
 Nelze získat adresu konstanta nebo hodnota.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu ukazatel na `int`, `p`je deklarovaný a přiřazena adresa proměnná typu integer, `number`. Proměnná `number` je inicializován v důsledku přiřazení `*p`. Pokud jste komentář tento příkaz přiřazení inicializace proměnné `number` je odebrán, ale žádné dojde k chybě kompilace.  

> [!NOTE]
> Kompilace v tomto příkladu se [ `-unsafe` ](../../language-reference/compiler-options/unsafe-compiler-option.md) – možnost kompilátoru.
  
 [!code-csharp[address-of-a-variable](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#8)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Výrazy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Typy](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed – příkaz](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
