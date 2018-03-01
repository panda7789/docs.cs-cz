---
title: "unchecked (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c05e7cb742d8e8f5a7804656a5ec13548d0498b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="unchecked-c-reference"></a>unchecked (Referenční dokumentace jazyka C#)
`unchecked` – Klíčové slovo je použít k potlačení kontrola Přetečení aritmetické operace integrální type a převody.  
  
 V kontextu není zaškrtnuto není v případě výraz vytvoří hodnotu, která je mimo rozsah typu cílové příznakem přetečení. Například protože výpočet v následujícím příkladu se provádí v `unchecked` bloku nebo výraz, skutečnost, že je výsledek příliš velký pro celé číslo se ignoruje, a `int1` přiřazena hodnota-2,147,483,639.  
  
 [!code-csharp[csrefKeywordsChecked#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_1.cs)]  
  
 Pokud `unchecked` prostředí je odebrán, dojde k chybě kompilace. Přetečení lze zjistit v době kompilace, protože všechny podmínky výrazu jsou konstanty.  
  
 Výrazy, které obsahují podmínky nekonstantní jsou ve výchozím nastavení zaškrtnuté políčko v době kompilace a čas spuštění. V tématu [zaškrtnutí](../../../csharp/language-reference/keywords/checked.md) informace o povolení prostředí zaškrtnuté.  
  
 Vzhledem k tomu, že kontrola pro přetečení trvá určitou dobu, použijte nezaškrtnuté kódu v situacích, kdy se nehrozí nebezpečí přetečení může zlepšit výkon. Ale pokud přetečení je možné, by měl použít prostředí zaškrtnuté.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje způsob použití `unchecked` – klíčové slovo.  
  
 [!code-csharp[csrefKeywordsChecked#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_2.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Zaškrtnuto a nezaškrtnuto](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
 [zaškrtnutí](../../../csharp/language-reference/keywords/checked.md)
