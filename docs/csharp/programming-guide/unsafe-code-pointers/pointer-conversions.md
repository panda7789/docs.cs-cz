---
title: Převody ukazatelů – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 517166331d2bcf73132269ce2adcf68d5f60b4fe
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745360"
---
# <a name="pointer-conversions-c-programming-guide"></a>Převody ukazatele (Průvodce programováním v C#)
V následující tabulce jsou uvedeny předdefinované implicitní převody ukazatele. Implicitní převody mohou nastat v mnoha situacích, včetně vyvolání metody a příkazů přiřazení.  
  
## <a name="implicit-pointer-conversions"></a>Implicitní převody ukazatelů  
  
|Od|Pro|  
|----------|--------|  
|Libovolný typ ukazatele|šekem|  
|null|Libovolný typ ukazatele|  
  
 Pro provedení převodů, pro které neexistuje implicitní převod, je použit explicitní převod ukazatele pomocí výrazu přetypování. Tyto převody jsou uvedené v následující tabulce.  
  
## <a name="explicit-pointer-conversions"></a>Explicitní převody ukazatelů  
  
|Od|Pro|  
|----------|--------|  
|Libovolný typ ukazatele|Jakýkoli jiný typ ukazatele|  
|SByte, Byte, Short, UShort, int, uint, Long nebo ulong|Libovolný typ ukazatele|  
|Libovolný typ ukazatele|SByte, Byte, Short, UShort, int, uint, Long nebo ulong|  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je ukazatel na `int` převeden na ukazatel na `byte`. Všimněte si, že ukazatel ukazuje na nejnižší adresovaný bajt proměnné. Po úspěšném zvýšení výsledku až do velikosti `int` (4 bajty) můžete zobrazit zbývající bajty proměnné.  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Typy ukazatelů](pointer-types.md)
- [Typy odkazů](../../language-reference/keywords/reference-types.md)
- [Typy hodnot](../../language-reference/builtin-types/value-types.md)
- [unsafe](../../language-reference/keywords/unsafe.md)
- [fixed – příkaz](../../language-reference/keywords/fixed-statement.md)
- [stackalloc](../../language-reference/operators/stackalloc.md)
