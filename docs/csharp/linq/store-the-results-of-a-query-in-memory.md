---
title: Store výsledky dotazu v paměti
description: Jak ukládat výsledky.
ms.date: 11/30/2016
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 52d502a841c428bd90a26c803ba577e76c17197c
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404298"
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

[LINQ (Language Integrated Query)](index.md)