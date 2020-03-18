---
title: Převody ukazatelů – programovací příručka jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 517166331d2bcf73132269ce2adcf68d5f60b4fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76745360"
---
# <a name="pointer-conversions-c-programming-guide"></a>Převody ukazatele (Průvodce programováním v C#)
V následující tabulce jsou uvedeny předdefinované implicitní převody ukazatelů. Implicitní převody může dojít v mnoha situacích, včetně metody vyvolání a přiřazení příkazy.  
  
## <a name="implicit-pointer-conversions"></a>Implicitní převody ukazatelů  
  
|From|Akce|  
|----------|--------|  
|Libovolný typ ukazatele|void*|  
|null|Libovolný typ ukazatele|  
  
 Explicitní převod ukazatele se používá k provádění převodů, pro které neexistuje žádný implicitní převod, pomocí výrazu přetypování. Následující tabulka ukazuje tyto převody.  
  
## <a name="explicit-pointer-conversions"></a>Explicitní převody ukazatelů  
  
|From|Akce|  
|----------|--------|  
|Libovolný typ ukazatele|Jakýkoli jiný typ ukazatele|  
|sbyte, byte, short, ushort, int, uint, long nebo ulong|Libovolný typ ukazatele|  
|Libovolný typ ukazatele|sbyte, byte, short, ushort, int, uint, long nebo ulong|  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je `int` ukazatel na převést `byte`na ukazatel na . Všimněte si, že ukazatel odkazuje na nejnižší adresovaný bajt proměnné. Když postupně zvětšujete výsledek až `int` do velikosti (4 bajty), můžete zobrazit zbývající bajty proměnné.  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Typy ukazatelů](pointer-types.md)
- [Referenční typy](../../language-reference/keywords/reference-types.md)
- [Typy hodnot](../../language-reference/builtin-types/value-types.md)
- [unsafe](../../language-reference/keywords/unsafe.md)
- [fixed – příkaz](../../language-reference/keywords/fixed-statement.md)
- [stackalloc](../../language-reference/operators/stackalloc.md)
