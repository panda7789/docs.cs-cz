---
title: Převody ukazatele (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: e0c3a409d76468a6e214a96e8bb326a9d906fe18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322689"
---
# <a name="pointer-conversions-c-programming-guide"></a>Převody ukazatele (Průvodce programováním v C#)
V následující tabulce jsou uvedeny převody předdefinované implicitní ukazatele. Implicitní převody může dojít v mnoha situacích, včetně metoda vyvolání a přiřazení příkazy.  
  
## <a name="implicit-pointer-conversions"></a>Převody implicitní ukazatele  
  
|From|Chcete-li|  
|----------|--------|  
|Žádný typ ukazatele|void *|  
|null|Žádný typ ukazatele|  
  
 Ukazatel explicitní převod se používá k provádění převody, pro které není žádný implicitní převod pomocí výraz přetypování. V následující tabulce jsou tyto převody.  
  
## <a name="explicit-pointer-conversions"></a>Převody explicitní ukazatele  
  
|From|Chcete-li|  
|----------|--------|  
|Žádný typ ukazatele|Jiný typ ukazatele|  
|SByte –, bajtů, krátké, ushort, int, uint, long nebo ulong|Žádný typ ukazatele|  
|Žádný typ ukazatele|SByte –, bajtů, krátké, ushort, int, uint, long nebo ulong|  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu, ukazatel na `int` jsou převedeny na ukazatel na `byte`. Všimněte si, že ukazatele odkazuje na nejnižší adresovaný bajtů proměnné. Když postupně zvýší výsledek, až velikost `int` (4 bajtů), můžete zobrazit zbývající bajty proměnné.  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#4](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-conversions_2.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Výrazy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Typy](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed – příkaz](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
