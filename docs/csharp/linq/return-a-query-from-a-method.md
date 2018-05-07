---
title: Vrácení dotazu z metody
description: Postup vrácení dotazu.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: 6a1d581c46c7b0b2062859fd60701dd25ea54eea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a>Postupy: Vrácení dotazu z metody (Průvodce programováním v C#)
Tento příklad ukazuje, jak jako návratová hodnota a jako vrácení dotazu z metody `out` parametr.  
  
 Objekty dotazu jsou složení, což znamená, že se můžete vrátit dotazu z metody. Objekty, které představují dotazy neukládejte výsledné kolekce, ale spíš kroky nepřineslo výsledky v případě potřeby. Výhodou vrácení objekty dotazu z metody je, aby mohly být další sestavit a upravit. Proto všechny návratové hodnoty nebo `out` parametru metody, která vrací dotaz musí také mít typu. Pokud bude metodu realizována dotazu do konkrétní <xref:System.Collections.Generic.List%601> nebo <xref:System.Array> typu, považuje vracejí výsledky dotazu místo samotný dotaz. Proměnné dotazu, která je vrácena z metody můžete stále složené nebo upravil.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu, první metoda vrací dotaz jako typ návratové hodnoty, a druhá metoda vrací dotaz jako `out` parametr. Všimněte si, že v obou případech je dotaz, který se vrátí, nebyl výsledky dotazu.  
  
 [!code-csharp[csProgGuideLINQ#80](../../../samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a>Viz také  
 [LINQ – výrazy dotazů](index.md)
