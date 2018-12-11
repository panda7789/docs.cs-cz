---
title: 'Postupy: získávání adresy proměnné - C# Průvodce programováním pro službu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
ms.openlocfilehash: 3e2eac468643b755c6db2d6055427baa7ce2b7a7
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241772"
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
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Výrazy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [Typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [Typy](../../../csharp/language-reference/keywords/types.md)  
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
- [fixed – příkaz](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
