---
title: Ukládání výsledků dotazu do paměti
description: Jak ukládat výsledky.
ms.date: 11/30/2016
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 66a7a95c74db4062e76c54d4339ccb7343f44067
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "65633566"
---
# <a name="store-the-results-of-a-query-in-memory"></a>Ukládání výsledků dotazu do paměti

Dotaz je v podstatě sada pokynů, jak načíst a uspořádat data. Dotazy jsou prováděny líně, protože každá následující položka ve výsledku je požadována. Při použití `foreach` k iterace výsledků položky jsou vráceny jako přístup. Chcete-li vyhodnotit dotaz a uložit `foreach` jeho výsledky bez spuštění smyčky, stačí zavolat jednu z následujících metod na proměnné dotazu:

- <xref:System.Linq.Enumerable.ToList%2A>

- <xref:System.Linq.Enumerable.ToArray%2A>

- <xref:System.Linq.Enumerable.ToDictionary%2A>

- <xref:System.Linq.Enumerable.ToLookup%2A>

 Doporučujeme při ukládání výsledků dotazu přiřadit vrácený objekt kolekce nové proměnné, jak je znázorněno v následujícím příkladu:

## <a name="example"></a>Příklad

[!code-csharp[csProgGuideLINQ#25](~/samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]

## <a name="see-also"></a>Viz také

- [LINQ (Language Integrated Query)](index.md)
