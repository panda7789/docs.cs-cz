---
title: Store výsledky dotazu v paměti
description: Jak ukládat výsledky.
ms.date: 11/30/2016
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 98a300b2c11eb037ed4ce34caea2673a4e0f8e6b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525227"
---
# <a name="store-the-results-of-a-query-in-memory"></a>Store výsledky dotazu v paměti

Dotaz je v podstatě sadu pokynů pro načtení a organizujte data. Dotazy jsou laxně, provést, protože je požadována každé následné položky ve výsledku. Při použití `foreach` k iteraci výsledky, položky se vrátí jako přistupovat. K vyhodnocení dotazu a uložit jeho výsledky bez spuštění `foreach` smyčky, stačí zavolat jednu z následujících metod v proměnné dotazu:

- <xref:System.Linq.Enumerable.ToList%2A>

- <xref:System.Linq.Enumerable.ToArray%2A>

- <xref:System.Linq.Enumerable.ToDictionary%2A>

- <xref:System.Linq.Enumerable.ToLookup%2A>

 Doporučujeme vám, že při ukládání výsledků dotazu, přiřadíte objekt vrácený kolekce do nové proměnné jak je znázorněno v následujícím příkladu:

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideLINQ#25](~/samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]

## <a name="see-also"></a>Viz také:

- [LINQ (Language Integrated Query)](index.md)