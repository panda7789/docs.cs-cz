---
title: from clause (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- from_CSharpKeyword
- from
helpviewer_keywords:
- from clause [C#]
- from keyword [C#]
ms.assetid: 1aefd18c-1314-47f8-99ec-9bcefb09e699
ms.openlocfilehash: e8bb7782fc60a3af20d5926e609a5edea68fd1a3
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027977"
---
# <a name="from-clause-c-reference"></a>from clause (Referenční dokumentace jazyka C#)

Výraz dotazu musí začínat `from` klauzule. Kromě toho může výrazu dotazu obsahovat dílčí dotazy, které také začínat `from` klauzule. `from` Klauzuli určuje následující:

- Zdroj dat, na kterém se spustí dotazu nebo poddotazu.

- Místní *proměnnou rozsahu* představující každý prvek v pořadí zdroje.

Proměnná rozsahu a zdroji dat jsou silného typu. Zdroj dat, kterou se odkazuje v `from` klauzule musí mít typ <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, nebo odvozený typ jako <xref:System.Linq.IQueryable%601>.

V následujícím příkladu `numbers` je zdroj dat a `num` je proměnnou rozsahu. Všimněte si, že obě proměnné jsou silného typu i prostřednictvím [var](var.md) – klíčové slovo se používá.

[!code-csharp[cscsrefQueryKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#1)]

## <a name="the-range-variable"></a>Proměnná rozsahu

Kompilátor odvodí typ proměnné rozsahu při zdroje dat implementuje <xref:System.Collections.Generic.IEnumerable%601>. Například pokud má zdroj typu `IEnumerable<Customer>`, pak je potřeba odvodit proměnnou rozsahu `Customer`. Jenom jednou, který je nutné zadat typ explicitně je při zdroj je není obecný `IEnumerable` zadejte například <xref:System.Collections.ArrayList>. Další informace najdete v tématu [postup: dotazu na ArrayList pomocí LINQ](../../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).

V předchozím příkladu `num` je odvodit být typu `int`. Vzhledem k tomu, že proměnná rozsahu je silného typu, můžete v něm volat metody nebo ho použít jiné operace. Například místo psaní `select num`, můžete napsat `select num.ToString()` způsobí výraz dotazu pro vrácení pořadí řetězců místo celých čísel. Nebo můžete napsat `select n + 10` způsobí výraz, který se vrátí pořadí 14, 11, 13, 12, 10. Další informace najdete v tématu [klauzuli select](select-clause.md).

Proměnná rozsahu je třeba proměnné iterace ve [foreach](foreach-in.md) příkaz s výjimkou jeden velmi důležitý rozdíl: proměnnou rozsahu nikdy ve skutečnosti ukládá data ze zdroje. Ho, kterou právě syntaktické pohodlí, která umožňuje dotaz pro popište, co se stane, když je proveden dotaz. Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](../../programming-guide/concepts/linq/introduction-to-linq-queries.md).

## <a name="compound-from-clauses"></a>Složené klauzulí from

V některých případech každý prvek v pořadí zdroj může sám sebe být buď pořadí nebo obsahovat. Váš zdroj dat může být například `IEnumerable<Student>` kde každý objekt student v pořadí obsahuje seznam výsledků testu. Pro přístup k seznamu vnitřní v každém `Student` elementu, můžete použít složené `from` klauzule. Způsob je jako pomocí vnořené [foreach](foreach-in.md) příkazy. Můžete přidat [kde](partial-method.md) nebo [orderby](orderby-clause.md) klauzule buď `from` klauzule filtrování výsledků. Následující příklad ukazuje posloupnost `Student` objekty, z nichž každý obsahuje vnitřní `List` celých čísel představující testování skóre. Chcete-li získat přístup k seznamu vnitřní, použijte složené `from` klauzule. Můžete vložit klauzule mezi těmito dvěma `from` klauzule v případě potřeby.

[!code-csharp[cscsrefQueryKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#2)]

## <a name="using-multiple-from-clauses-to-perform-joins"></a>Použití více klauzulí from k provedení spojení

Složené `from` klauzule slouží k přístupu vnitřní kolekcí v jeden zdroj dat. Ale dotazu může také obsahovat více `from` věty, které generovat další dotazy z nezávislé datové zdroje. Tento postup umožňuje provádět určité operace spojení, které nejsou možné pomocí [klauzuli join](join-clause.md).

Následující příklad ukazuje, jak dva `from` klauzule můžete použít k dokončení křížové spojení dvou datových zdrojů.

[!code-csharp[cscsrefQueryKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#3)]

Další informace o připojení k operace, které používají více `from` klauzule, najdete v části [provést levá vnější spojení](../../linq/perform-left-outer-joins.md).

## <a name="see-also"></a>Viz také:

[Klíčová slova dotazu (LINQ)](query-keywords.md)  
[LINQ (Language Integrated Query)](../../linq/index.md)  