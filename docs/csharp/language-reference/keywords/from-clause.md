---
title: from klauzule - C# Reference
ms.date: 07/20/2015
f1_keywords:
- from_CSharpKeyword
- from
helpviewer_keywords:
- from clause [C#]
- from keyword [C#]
ms.assetid: 1aefd18c-1314-47f8-99ec-9bcefb09e699
ms.openlocfilehash: 388b9c0245b112d619fc173f6019b3f7dbf59940
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715293"
---
# <a name="from-clause-c-reference"></a>from clause (Referenční dokumentace jazyka C#)

Výraz dotazu `from` musí začínat klauzulí. Výraz dotazu může navíc obsahovat dílčí dotazy, které `from` také začínají klauzulí. Doložka `from` specifikuje následující:

- Zdroj dat, na kterém bude spuštěn dotaz nebo dílčí dotaz.

- Místní *proměnná rozsahu,* která představuje každý prvek ve zdrojové sekvenci.

Proměnná rozsahu i zdroj dat jsou silně zadány. Zdroj dat odkazovaný `from` v klauzuli musí <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601>mít typ , nebo <xref:System.Linq.IQueryable%601>odvozený typ, například .

V následujícím příkladu `numbers` je zdroj `num` dat a je proměnná rozsahu. Všimněte si, že obě proměnné jsou silně zadali i v případě, [že](var.md) var klíčové slovo se používá.

[!code-csharp[cscsrefQueryKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#1)]

## <a name="the-range-variable"></a>Proměnná rozsahu

Kompilátor odvodí typ proměnné rozsahu při implementaci <xref:System.Collections.Generic.IEnumerable%601>zdroje dat . Například pokud zdroj má typ `IEnumerable<Customer>`, pak je odvozen a `Customer`proměnná rozsahu . Typ je nutné zadat pouze tehdy, je-li zdrojem neobecný `IEnumerable` typ, například <xref:System.Collections.ArrayList>. Další informace naleznete v [tématu Jak zadat dotaz na polelist s LINQ](../../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).

V předchozím `num` příkladu se odvodí jako typ `int`. Vzhledem k tomu, že proměnná rozsahu je silně zadána, můžete volat metody na něm nebo ji použít v jiných operacích. Například místo zápisu `select num`můžete `select num.ToString()` zapisovat, abyste způsobili, že výraz dotazu vrátí posloupnost řetězců namísto celá čísla. Nebo můžete `select num + 10` napsat způsobit výraz vrátit sekvence 14, 11, 13, 12, 10. Další informace naleznete v [tématu select clause](select-clause.md).

Proměnná rozsahu je jako iterace proměnné [foreach](foreach-in.md) prohlášení s výjimkou jednoho velmi důležitý rozdíl: rozsah proměnné nikdy ve skutečnosti ukládá data ze zdroje. Je to jen syntaktické pohodlí, které umožňuje dotazu popsat, co se stane při spuštění dotazu. Další informace naleznete [v tématu Úvod do LINQ dotazy (C#)](../../programming-guide/concepts/linq/introduction-to-linq-queries.md).

## <a name="compound-from-clauses"></a>Směs z klauzulí

V některých případech každý prvek ve zdrojové sekvenci může být sám buď sekvence nebo obsahují sekvenci. Zdrojem dat může být `IEnumerable<Student>` například místo, kde každý objekt studenta v sekvenci obsahuje seznam výsledků testů. Chcete-li získat přístup `Student` k vnitřnímu `from` seznamu v rámci každého prvku, můžete použít složené klauzule. Technika je jako použití vnořené [foreach](foreach-in.md) příkazy. Můžete přidat [where](partial-method.md) nebo [orderby](orderby-clause.md) `from` klauzule do jedné klauzule filtrovat výsledky. Následující příklad ukazuje posloupnost `Student` objektů, z `List` nichž každý obsahuje vnitřní celá čísla představující výsledky testu. Chcete-li získat přístup k `from` vnitřnímu seznamu, použijte složenou klauzuli. V případě potřeby můžete `from` vložit klauzule mezi dvě klauzule.

[!code-csharp[cscsrefQueryKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#2)]

## <a name="using-multiple-from-clauses-to-perform-joins"></a>Použití více z klauzulí k provedení spojení

Složená `from` klauzule se používá pro přístup k vnitřní kolekce v jednom zdroji dat. Dotaz však může také `from` obsahovat více klauzulí, které generují doplňkové dotazy z nezávislých zdrojů dat. Tato technika umožňuje provádět určité typy operací spojení, které nejsou možné pomocí [klauzule join](join-clause.md).

Následující příklad ukazuje, `from` jak lze použít dvě klauzule k vytvoření úplného křížového spojení dvou zdrojů dat.

[!code-csharp[cscsrefQueryKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#3)]

Další informace o operacích `from` spojení, které používají více klauzulí, naleznete v [tématu Provedení levého vnějšího spojení](../../linq/perform-left-outer-joins.md).

## <a name="see-also"></a>Viz také

- [Klíčová slova dotazu (LINQ)](query-keywords.md)
- [LINQ (Language Integrated Query)](../../linq/index.md)
