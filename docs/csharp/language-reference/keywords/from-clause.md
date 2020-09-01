---
description: from – klauzule – reference jazyka C#
title: from – klauzule – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- from_CSharpKeyword
- from
helpviewer_keywords:
- from clause [C#]
- from keyword [C#]
ms.assetid: 1aefd18c-1314-47f8-99ec-9bcefb09e699
ms.openlocfilehash: 474b22f5a9d8f12c8a4365159817f878761b563c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89140786"
---
# <a name="from-clause-c-reference"></a>from clause (Referenční dokumentace jazyka C#)

Výraz dotazu musí začínat `from` klauzulí. Kromě toho výraz dotazu může obsahovat dílčí dotazy, které také začínají `from` klauzulí. `from`Klauzule určuje následující:

- Zdroj dat, na kterém se spustí dotaz nebo dílčí dotaz

- Místní *Proměnná rozsahu* , která představuje každý prvek ve zdrojové sekvenci.

Jak proměnná rozsahu, tak zdroj dat jsou silného typu. Zdroj dat, na který je odkazováno v `from` klauzuli, musí mít typ <xref:System.Collections.IEnumerable> , <xref:System.Collections.Generic.IEnumerable%601> nebo odvozený typ, jako je například <xref:System.Linq.IQueryable%601> .

V následujícím příkladu `numbers` je zdroj dat a `num` je proměnná rozsahu. Všimněte si, že obě proměnné jsou silného typu, i když je použito klíčové slovo [var](var.md) .

[!code-csharp[cscsrefQueryKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#1)]

## <a name="the-range-variable"></a>Proměnná rozsahu

Kompilátor odvodí typ proměnné rozsahu při implementaci zdroje dat <xref:System.Collections.Generic.IEnumerable%601> . Například pokud má zdroj typ `IEnumerable<Customer>` , je proměnná rozsahu odvozena `Customer` . Jediným okamžikem, kdy je nutné explicitně zadat typ, je, že zdroj je neobecný `IEnumerable` typ, například <xref:System.Collections.ArrayList> . Další informace najdete v tématu [Postup dotazování objektu ArrayList pomocí LINQ](../../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).

V předchozím příkladu `num` je odvozen jako typ `int` . Vzhledem k tomu, že je proměnná rozsahu silného typu, můžete na ni zavolat metody nebo je použít v jiných operacích. Například namísto psaní `select num` můžete napsat, `select num.ToString()` abyste způsobili, že výraz dotazu vrátí sekvenci řetězců místo celých čísel. Nebo můžete napsat, `select num + 10` aby výraz vrátil sekvenci 14, 11, 13, 12, 10. Další informace najdete v tématu [klauzule SELECT](select-clause.md).

Proměnná rozsahu je jako iterační proměnná v příkazu [foreach](foreach-in.md) s výjimkou jednoho velmi důležitého rozdílu: proměnná rozsahu nikdy neukládá data ze zdroje. Jedná se pouze o syntaktické pohodlí, které umožňuje dotazu popsat, co se vyskytne při spuštění dotazu. Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](../../programming-guide/concepts/linq/introduction-to-linq-queries.md).

## <a name="compound-from-clauses"></a>Složené klauzule FROM

V některých případech může být každý prvek ve zdrojové sekvenci sám sebou buď sekvence, nebo obsahovat sekvenci. Zdroj dat může být například, `IEnumerable<Student>` kde každý objekt studenta v sekvenci obsahuje seznam hodnocení testů. Chcete-li získat přístup k vnitřnímu seznamu v rámci jednotlivých `Student` prvků, můžete použít složené `from` klauzule. Technika je jako použití vnořených příkazů [foreach](foreach-in.md) . Můžete přidat klauzule [WHERE](partial-method.md) nebo [OrderBy](orderby-clause.md) do obou `from` klauzulí pro filtrování výsledků. Následující příklad ukazuje sekvenci `Student` objektů, z nichž každý obsahuje vnitřní `List` celočíselnou hodnotu reprezentující hodnocení testů. Pro přístup k vnitřnímu seznamu použijte složenou `from` klauzuli. V případě potřeby můžete do obou klauzulí vkládat klauzule `from` .

[!code-csharp[cscsrefQueryKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#2)]

## <a name="using-multiple-from-clauses-to-perform-joins"></a>Použití více klauzulí FROM pro provedení spojení

Složená `from` klauzule se používá pro přístup k vnitřním kolekcím v jednom zdroji dat. Dotaz však může obsahovat také více `from` klauzulí, které generují doplňkové dotazy z nezávislých zdrojů dat. Tato technika vám umožní provádět určité typy operací spojení, které nejsou možné pomocí [klauzule JOIN](join-clause.md).

Následující příklad ukazuje, jak `from` lze pomocí dvou klauzulí vytvořit úplné vzájemné spojení dvou zdrojů dat.

[!code-csharp[cscsrefQueryKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#3)]

Další informace o operacích spojení, které používají více `from` klauzulí, najdete v tématu věnovaném [vykonání levého vnějšího spojení](../../linq/perform-left-outer-joins.md).

## <a name="see-also"></a>Viz také

- [Klíčová slova dotazu (LINQ)](query-keywords.md)
- [LINQ (Language Integrated Query)](../../linq/index.md)
