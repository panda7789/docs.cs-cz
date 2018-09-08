---
title: 'Postupy: Získávání hodnoty proměnné ukazatele (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
ms.openlocfilehash: 66f341e193a0f018adb76a40617f85266519e602
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44138263"
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a>Postupy: Získávání hodnoty proměnné ukazatele (Průvodce programováním v C#)
Použijte operátor dereference ukazatele k získání proměnnou na umístění, na které odkazuje ukazatel. Výraz používá následující formulář, kde `p` je typ ukazatele:  
  
```  
*p;  
```  
  
 Unární operátor dereference nelze použít ve výrazu typu jiného než typu ukazatel. Navíc na nelze použít [void](../../../csharp/language-reference/keywords/void.md) ukazatele.  
  
 Při použití operátoru dereference na [null](../../../csharp/language-reference/keywords/null.md) ukazatelem, výsledek závisí na implementaci.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se proměnná typu `char` lze přistupovat pomocí ukazatele na různé typy. Všimněte si, že adresa `theChar` spuštění, se liší, protože fyzická adresa přidělené na proměnnou můžete změnit.  
  
 [!code-csharp[csProgGuidePointers#5](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#6](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_2.cs)]  
  
**Hodnota theChar = Z**
**adresu theChar = 12F718**
**hodnotu pChar = Z**
**hodnotu pinta = 90**

## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Výrazy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [Typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [Typy](../../../csharp/language-reference/keywords/types.md)  
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
- [fixed – příkaz](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
