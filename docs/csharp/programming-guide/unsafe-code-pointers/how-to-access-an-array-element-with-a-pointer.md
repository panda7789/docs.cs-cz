---
title: 'Postupy: Přístup k elementu pole pomocí ukazatele (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], array access
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
ms.openlocfilehash: 92eb7a79c0e7522d1474537aeefbfdb083a11dc2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332036"
---
# <a name="how-to-access-an-array-element-with-a-pointer-c-programming-guide"></a>Postupy: Přístup k elementu pole pomocí ukazatele (Průvodce programováním v C#)
V kontextu unsafe mohly přistupovat k elementu v paměti pomocí přístupu k elementu ukazatele, jak je znázorněno v následujícím příkladu:  
  
```  
 char* charPointer = stackalloc char[123];  
for (int i = 65; i < 123; i++)  
{  
    charPointer[i] = (char)i; //access array elements  
}  
```  
  
 Výraz v hranatých závorkách musí být implicitně převést na `int`, `uint`, `long`, nebo `ulong`. Operaci p [e] je ekvivalentní *(p+e). Jako C a C++, přístup k elementu ukazatel nekontroluje out-of-bounds chyby.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu 123 umístění v paměti přidělovány do pole znaků, `charPointer`. Pole se používá k zobrazení písmena malá a velká písmena vede ke dvěma [pro](../../../csharp/language-reference/keywords/for.md) smyčky.  
  
 Všimněte si, že výraz `charPointer[i]` je ekvivalentní výrazu `*(charPointer + i)`, a získáte stejný výsledek pomocí některé z dvou výrazů.  
  
 [!code-csharp[csProgGuidePointers#11](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#12](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_2.cs)]  
  
 **Velká písmena:**  
**ABCDEFGHIJKLMNOPQRSTUVWXYZ**  
**Malá písmena:**  
**ABCDEFGHIJKLMNOPQRSTUVWXYZ**   
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Výrazy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Typy](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed – příkaz](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
