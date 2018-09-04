---
title: Vrácení dotazu z metody
description: Postup vrácení dotazu.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: 1c5fa534f3f39f8201d93b986e687d85bb303736
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510784"
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a>Postupy: Vrácení dotazu z metody (Průvodce programováním v C#)
Tento příklad ukazuje, jak jako návratovou hodnotu a vrácení dotazu z metody `out` parametru.  
  
 Dotaz objekty jsou složení, což znamená, že jste vrácení dotazu z metody. Objekty, které zastupují dotaz neukládejte výsledný kolekce, ale spíše kroky pro vytvoření výsledku v případě potřeby. Výhodou vrací objekty dotazu z metody je, že můžou být další skládá nebo upravit. Proto všechny návratové hodnoty nebo `out` parametru metody, která vrací dotaz musí mít také tohoto typu. Pokud bude metoda realizována dotaz do konkrétní <xref:System.Collections.Generic.List%601> nebo <xref:System.Array> typ, považuje se vracejí výsledky dotazu namísto samotný dotaz. Proměnné dotazu, který je vrácen z metody lze stále skládá nebo upravit.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu první metoda vrací dotaz jako návratovou hodnotu a druhá metoda vrací dotaz jako `out` parametru. Všimněte si, že v obou případech se dotaz, který je vrácen, nejsou výsledky dotazu.  
  
 [!code-csharp[csProgGuideLINQ#80](~/samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a>Viz také

- [LINQ (Language Integrated Query)](index.md)
