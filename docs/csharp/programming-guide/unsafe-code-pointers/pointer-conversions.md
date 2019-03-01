---
title: Převody ukazatele - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 91be48aa2ca64b152af3dc3f33c713bf4adac0c7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968384"
---
# <a name="pointer-conversions-c-programming-guide"></a>Převody ukazatele (Průvodce programováním v C#)
V následující tabulce jsou předdefinované ukazatel implicitní převody. Implicitní převod může dojít v mnoha situacích, včetně příkazů metody vyvolání a přiřazení.  
  
## <a name="implicit-pointer-conversions"></a>Implicitní ukazatel převody  
  
|From|Chcete-li|  
|----------|--------|  
|Libovolný typ ukazatele|typ void *|  
|null|Libovolný typ ukazatele|  
  
 Převod ukazatele explicitní slouží k provádění převodů, pro které neexistuje žádný implicitní převod, pomocí výrazu přetypování. V následující tabulce jsou uvedeny tyto převody.  
  
## <a name="explicit-pointer-conversions"></a>Převody ukazatele explicitní  
  
|From|Chcete-li|  
|----------|--------|  
|Libovolný typ ukazatele|Jiný typ ukazatele|  
|SByte, byte, short, ushort, int, uint, long nebo ulong|Libovolný typ ukazatele|  
|Libovolný typ ukazatele|SByte, byte, short, ushort, int, uint, long nebo ulong|  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu, ukazatel na `int` je převeden na ukazatel na `byte`. Všimněte si, že ukazatel odkazuje na nejnižší adresovaný bajtů proměnné. Když postupně zvyšovat výsledek, až do velikosti `int` (4 bajtů), můžete zobrazit zbývající bajty proměnné.  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Výrazy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [Typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed – příkaz](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
