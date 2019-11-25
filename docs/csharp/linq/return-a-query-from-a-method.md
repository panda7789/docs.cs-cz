---
title: Vrácení dotazu z metody
description: Jak vrátit dotaz.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: 1df533770f76301432b104d6f8398f1687750cce
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73972512"
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a>Postup vrácení dotazu z metody (C# Průvodce programováním)
Tento příklad ukazuje, jak vrátit dotaz z metody jako návratovou hodnotu a jako parametr `out`.  
  
 Objekty dotazů jsou sestavitelné, což znamená, že můžete vracet dotaz z metody. Objekty, které reprezentují dotazy, neukládají výslednou kolekci, ale v případě potřeby pak kroky k vyprodukování výsledků. Výhodou vrácení objektů dotazů z metod je, že je lze dále sestavit nebo upravit. Proto všechny vrácené hodnoty nebo parametry `out` metody, která vrací dotaz, musí mít také tento typ. Pokud metoda materializuje dotaz do konkrétního <xref:System.Collections.Generic.List%601> nebo <xref:System.Array> typu, považuje se za vracené výsledky dotazu místo dotazu samotného. Proměnnou dotazu, která je vrácena z metody, lze stále sestavit nebo upravit.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu vrátí první metoda dotaz jako návratovou hodnotu a druhá metoda vrátí dotaz jako parametr `out`. Všimněte si, že v obou případech se jedná o dotaz, který je vrácen, nikoli výsledky dotazu.  
  
 [!code-csharp[csProgGuideLINQ#80](~/samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a>Viz také:

- [LINQ (Language Integrated Query)](index.md)
