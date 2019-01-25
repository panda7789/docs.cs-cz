---
title: 'Postupy: Získávání hodnoty proměnné ukazatele - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
ms.openlocfilehash: 5fbc925b6770bc951a0d7ec856898f62c265462e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577149"
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a>Postupy: Získávání hodnoty proměnné ukazatele (C# Průvodce programováním v)
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

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Výrazy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [Typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed – příkaz](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
