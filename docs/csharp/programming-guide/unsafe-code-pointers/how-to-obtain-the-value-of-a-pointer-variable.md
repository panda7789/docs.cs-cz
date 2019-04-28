---
title: 'Postupy: získávání hodnoty proměnné ukazatele - C# Průvodce programováním pro službu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
ms.openlocfilehash: 288d8cb2d286f55cc9a162614d45ef7b298f79f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61677981"
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a>Postupy: získávání hodnoty proměnné ukazatele (C# Programming Guide)

Použijte operátor dereference ukazatele k získání proměnnou na umístění, na které odkazuje ukazatel. Výraz používá následující formulář, kde `p` je typ ukazatele:  

```csharp
*p;  
```

Unární operátor dereference nelze použít ve výrazu typu jiného než typu ukazatel. Navíc na nelze použít [void](../../../csharp/language-reference/keywords/void.md) ukazatele.  

Při použití operátoru dereference na [null](../../../csharp/language-reference/keywords/null.md) ukazatelem, výsledek závisí na implementaci.  

## <a name="example"></a>Příklad

V následujícím příkladu se proměnná typu `char` lze přistupovat pomocí ukazatele na různé typy. Všimněte si, že adresa `theChar` spuštění, se liší, protože fyzická adresa přidělené na proměnnou můžete změnit.  

 [!code-csharp[csProgGuidePointers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#5)]  

 [!code-csharp[csProgGuidePointers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#6)]  
  
**Hodnota theChar = Z**  
**Adresa theChar = 12F718**  
**Hodnota pChar = Z**  
**Hodnota pinta = 90**  

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Výrazy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [Typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed – příkaz](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
