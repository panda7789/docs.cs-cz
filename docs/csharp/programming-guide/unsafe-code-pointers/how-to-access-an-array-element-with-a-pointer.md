---
title: "Postupy: Přístup k elementu pole pomocí ukazatele (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointers [C#], array access
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 737c1d7fc0bc0a739de5c0a6cbc5dc09f813133e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Výrazy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Typy](../../../csharp/language-reference/keywords/types.md)  
 [nezabezpečený](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed – příkaz](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
