---
title: Převody ukazatelů – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 81b2110e6a571e174693fd272d1c6b4bf44dbae3
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588218"
---
# <a name="pointer-conversions-c-programming-guide"></a>Převody ukazatele (Průvodce programováním v C#)
V následující tabulce jsou uvedeny předdefinované implicitní převody ukazatele. Implicitní převody mohou nastat v mnoha situacích, včetně vyvolání metody a příkazů přiřazení.  
  
## <a name="implicit-pointer-conversions"></a>Implicitní převody ukazatelů  
  
|From|Chcete-li|  
|----------|--------|  
|Libovolný typ ukazatele|šekem|  
|null|Libovolný typ ukazatele|  
  
 Pro provedení převodů, pro které neexistuje implicitní převod, je použit explicitní převod ukazatele pomocí výrazu přetypování. Tyto převody jsou uvedené v následující tabulce.  
  
## <a name="explicit-pointer-conversions"></a>Explicitní převody ukazatelů  
  
|From|Chcete-li|  
|----------|--------|  
|Libovolný typ ukazatele|Jakýkoli jiný typ ukazatele|  
|SByte, Byte, Short, UShort, int, uint, Long nebo ulong|Libovolný typ ukazatele|  
|Libovolný typ ukazatele|SByte, Byte, Short, UShort, int, uint, Long nebo ulong|  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je ukazatel na `int` převedený na ukazatel na. `byte` Všimněte si, že ukazatel ukazuje na nejnižší adresovaný bajt proměnné. Po úspěšném zvýšení výsledku až do velikosti `int` (4 bajty) můžete zobrazit zbývající bajty proměnné.  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Typy ukazatelů](./pointer-types.md)
- [Typy](../../language-reference/keywords/types.md)
- [unsafe](../../language-reference/keywords/unsafe.md)
- [fixed – příkaz](../../language-reference/keywords/fixed-statement.md)
- [stackalloc](../../language-reference/operators/stackalloc.md)
