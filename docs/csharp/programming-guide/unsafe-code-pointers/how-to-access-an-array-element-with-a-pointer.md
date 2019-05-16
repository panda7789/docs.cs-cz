---
title: 'Postupy: přístup k elementu pole pomocí ukazatele - C# Průvodce programováním pro službu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], array access
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
ms.openlocfilehash: b1538068f3ba37a7637e7dc3913e9511d4380daf
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635191"
---
# <a name="how-to-access-an-array-element-with-a-pointer-c-programming-guide"></a>Postupy: přístup k elementu pole pomocí ukazatele (C# Programming Guide)

V nezabezpečeném kontextu můžete přístup k prvku v paměti pomocí přístup k prvkům ukazatele, jak je znázorněno v následujícím příkladu:

```csharp
char* charPointer = stackalloc char[123];
for (int i = 65; i < 123; i++)
{
    charPointer[i] = (char)i; //access array elements
}
```

Výraz v hranatých závorkách musí být implicitně převeditelný na `int`, `uint`, `long`, nebo `ulong`. Operace `p[e]` je ekvivalentní `*(p+e)`. Podobně jako C a C++, přístup k prvkům ukazatel nekontroluje celočíselných chyby.

## <a name="example"></a>Příklad

V tomto příkladu jsou 123 umístění v paměti přidělené na pole znaků `charPointer`. Pole se používá k zobrazení písmena malá a velká písmena ve dvou [pro](../../../csharp/language-reference/keywords/for.md) smyčky.

Všimněte si, že výraz `charPointer[i]` je ekvivalentní výraz `*(charPointer + i)`, a získáte stejný výsledek jedním ze dvou výrazů.

 [!code-csharp[csProgGuidePointers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#11)]

 [!code-csharp[csProgGuidePointers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#12)]

**Velká písmena:**  
**ABCDEFGHIJKLMNOPQRSTUVWXYZ**  
**Malá písmena:**  
**abcdefghijklmnopqrstuvwxyz**  

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Typy](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed – příkaz](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
