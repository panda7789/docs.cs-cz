---
title: 'Postupy: získávání adresy proměnné - C# Průvodce programováním pro službu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
ms.openlocfilehash: cba33803c31ccc144479ad3e7b073ea7057495d5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54490555"
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a>Postupy: získávání adresy proměnné (C# Programming Guide)

Pro získání adresy jednočlenný výraz, který je vyhodnocen pevná proměnná, použití operátoru address-of `&`:  
  
```csharp  
int number;  
int* p = &number; //address-of operator &  
```  
  
 Operátor address-of může používat jedině pro proměnnou. Pokud je proměnná přesunutelný proměnné, můžete použít [oprava příkazu](../../../csharp/language-reference/keywords/fixed-statement.md) dočasně vyřešit proměnnou před získáním adresy.  
  
 Je vaší povinností ujistit, že je proměnná inicializována. Kompilátor nebude vydat chybovou zprávu, pokud proměnná není inicializovaná.  
  
 Nelze získat adresu konstanta nebo hodnota.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu ukazatel na `int`, `p`, je deklarována a přiřazenou adresu proměnnou celého čísla `number`. Proměnná `number` je inicializována v důsledku přiřazení `*p`. Pokud jste zakomentovali tohoto příkazu přiřazení, inicializace proměnné `number` Odebereme, ale není vyvolána žádná chyba kompilace.  

> [!NOTE]
> Kompilaci tohoto příkladu s [ `-unsafe` ](../../language-reference/compiler-options/unsafe-compiler-option.md) – možnost kompilátoru.
  
 [!code-csharp[address-of-a-variable](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#8)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Výrazy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [Typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed – příkaz](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
