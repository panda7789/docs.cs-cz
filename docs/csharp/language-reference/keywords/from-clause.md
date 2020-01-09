---
title: klauzule FROM – C# odkaz
ms.date: 07/20/2015
f1_keywords:
- from_CSharpKeyword
- from
helpviewer_keywords:
- from clause [C#]
- from keyword [C#]
ms.assetid: 1aefd18c-1314-47f8-99ec-9bcefb09e699
ms.openlocfilehash: 388b9c0245b112d619fc173f6019b3f7dbf59940
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715293"
---
# <a name="from-clause-c-reference"></a>from clause (Referenční dokumentace jazyka C#)

Výraz dotazu musí začínat klauzulí `from`. Kromě toho výraz dotazu může obsahovat dílčí dotazy, které také začínají klauzulí `from`. Klauzule `from` určuje následující:

- Zdroj dat, na kterém se spustí dotaz nebo dílčí dotaz

- Místní *Proměnná rozsahu* , která představuje každý prvek ve zdrojové sekvenci.

Jak proměnná rozsahu, tak zdroj dat jsou silného typu. Zdroj dat, na který odkazuje klauzule `from`, musí mít typ <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>nebo odvozený typ, jako je například <xref:System.Linq.IQueryable%601>.

V následujícím příkladu je `numbers` zdrojem dat a `num` je proměnná rozsahu. Všimněte si, že obě proměnné jsou silného typu, i když je použito klíčové slovo [var](var.md) .

[!code-csharp[cscsrefQueryKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#1)]

## <a name="the-range-variable"></a>Proměnná rozsahu

Kompilátor odvodí typ proměnné rozsahu, když zdroj dat implementuje <xref:System.Collections.Generic.IEnumerable%601>. Pokud má zdroj například typ `IEnumerable<Customer>`, je proměnná rozsahu odvozena pro `Customer`. Jediným okamžikem, kdy je nutné explicitně zadat typ, je, že zdroj je neobecný `IEnumerable` typ, jako je například <xref:System.Collections.ArrayList>. Další informace najdete v tématu [Postup dotazování objektu ArrayList pomocí LINQ](../../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).

V předchozím příkladu je `num` odvozený jako `int`typu. Vzhledem k tomu, že je proměnná rozsahu silného typu, můžete na ni zavolat metody nebo je použít v jiných operacích. Například namísto psaní `select num`můžete napsat `select num.ToString()`, která způsobí, že výraz dotazu vrátí sekvenci řetězců místo celých čísel. Můžete také napsat `select num + 10` a způsobit tak, že výraz vrátí sekvenci 14, 11, 13, 12, 10. Další informace najdete v tématu [klauzule SELECT](select-clause.md).

Proměnná rozsahu je jako iterační proměnná v příkazu [foreach](foreach-in.md) s výjimkou jednoho velmi důležitého rozdílu: proměnná rozsahu nikdy neukládá data ze zdroje. Jedná se pouze o syntaktické pohodlí, které umožňuje dotazu popsat, co se vyskytne při spuštění dotazu. Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](../../programming-guide/concepts/linq/introduction-to-linq-queries.md).

## <a name="compound-from-clauses"></a>Složené klauzule FROM

V některých případech může být každý prvek ve zdrojové sekvenci sám sebou buď sekvence, nebo obsahovat sekvenci. Zdroj dat může být například `IEnumerable<Student>`, kde každý objekt studenta v sekvenci obsahuje seznam hodnocení testů. Chcete-li získat přístup k vnitřnímu seznamu v rámci každého prvku `Student`, můžete použít složené klauzule `from`. Technika je jako použití vnořených příkazů [foreach](foreach-in.md) . Klauzule [WHERE](partial-method.md) nebo [OrderBy](orderby-clause.md) můžete přidat do klauzule `from` pro filtrování výsledků. Následující příklad ukazuje sekvenci `Student` objektů, z nichž každý obsahuje vnitřní `List` celých čísel, která představují hodnocení testů. Chcete-li získat přístup k vnitřnímu seznamu, použijte složenou klauzuli `from`. V případě potřeby můžete do obou klauzulí `from` vkládat klauzule.

[!code-csharp[cscsrefQueryKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#2)]

## <a name="using-multiple-from-clauses-to-perform-joins"></a>Použití více klauzulí FROM pro provedení spojení

Klauzule složeného `from` se používá pro přístup k vnitřním kolekcím v jednom zdroji dat. Dotaz však může obsahovat také více klauzulí `from`, které generují doplňkové dotazy z nezávislých zdrojů dat. Tato technika vám umožní provádět určité typy operací spojení, které nejsou možné pomocí [klauzule JOIN](join-clause.md).

Následující příklad ukazuje, jak lze pomocí dvou klauzulí `from` vytvořit úplné vzájemné spojení dvou zdrojů dat.

[!code-csharp[cscsrefQueryKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#3)]

Další informace o operacích JOIN, které používají více klauzulí `from`, najdete v tématu [provedení levých vnějších spojení](../../linq/perform-left-outer-joins.md).

## <a name="see-also"></a>Viz také:

- [Klíčová slova dotazu (LINQ)](query-keywords.md)
- [ (LINQ)](../../linq/index.md)
