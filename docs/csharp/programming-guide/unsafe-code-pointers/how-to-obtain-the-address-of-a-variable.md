---
title: "Postupy: Získávání adresy proměnné (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d0969f7e62864c682660f08cd4198aa4032e0e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a>Postupy: Získávání adresy proměnné (Průvodce programováním v C#)
Získat adresu unární výraz, který vyhodnocuje pevné proměnné, použijte operátor adresy:  
  
```  
int number;  
int* p = &number; //address-of operator &  
```  
  
 Operátor adresy lze použít pouze k proměnné. Pokud je proměnná přenosné proměnné, můžete použít [příkazu pevnou](../../../csharp/language-reference/keywords/fixed-statement.md) dočasně opravit před získávání adresy proměnné.  
  
 Je vaší povinností ujistit, že je inicializováno proměnnou. Kompilátor nevydá chybovou zprávu, pokud není inicializována proměnnou.  
  
 Nelze získat adresu konstanta nebo hodnota.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu ukazatel na `int`, `p`je deklarovaný a přiřazena adresa proměnná typu integer, `number`. Proměnná `number` je inicializován v důsledku přiřazení * p. Pokud provedete tento příkaz přiřazení komentář, inicializace proměnné `number` bude odebrána, ale žádné dojde k chybě kompilace. Všimněte si použití [přístup ke členu](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md) operátor `->` můžete získat a zobrazit adresu uložené v ukazatele.  
  
 [!code-csharp[csProgGuidePointers#7](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#8](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_2.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Výrazy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Typy](../../../csharp/language-reference/keywords/types.md)  
 [nezabezpečený](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed – příkaz](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
