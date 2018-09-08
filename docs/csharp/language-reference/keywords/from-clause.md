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
ms.openlocfilehash: c8c124f44df292b8323560cce541cca2765e2790
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44186406"
---
# <a name="from-clause-c-reference"></a>from clause (Referenční dokumentace jazyka C#)

Výraz dotazu musí začínat `from` klauzuli. Kromě toho výraz dotazu může obsahovat dílčí dotazy, které také začínají `from` klauzuli. `from` Klauzule určuje následující:

- Zdroj dat, na kterém se spustí dotazu nebo poddotazu.

- Místní *proměnnou rozsahu* , který představuje každý prvek ve zdrojové sekvenci.

Proměnná rozsahu a zdroji dat jsou silného typu. Zdroj dat odkazuje `from` klauzule musí mít typ <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, nebo odvozeného typu, jako <xref:System.Linq.IQueryable%601>.

V následujícím příkladu `numbers` je zdrojem dat a `num` je proměnná rozsahu. Všimněte si, že obě proměnné jsou silného typu i když [var](var.md) – klíčové slovo se používá.

[!code-csharp[cscsrefQueryKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#1)]

## <a name="the-range-variable"></a>Proměnná rozsahu

Kompilátor odvodí typ proměnné rozsahu, když zdroj dat implementuje <xref:System.Collections.Generic.IEnumerable%601>. Například, pokud zdroji má typ `IEnumerable<Customer>`, pak proměnná rozsahu je odvozena jako `Customer`. Který je nutné zadat typ je explicitně při zdroji se pouze neobecnou `IEnumerable` jako <xref:System.Collections.ArrayList>. Další informace najdete v tématu [postupy: vytvoření dotazu na ArrayList pomocí LINQ](../../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).

V předchozím příkladu `num` odvodit typ `int`. Vzhledem k tomu, že proměnná rozsahu je silně typováno, můžete volat metody nebo použít v jiné operace. Například místo zápisu `select num`, můžete napsat `select num.ToString()` způsobit výrazu dotazu k vrácení sekvence řetězců místo celých čísel. Nebo můžete napsat `select n + 10` způsobit výraz k vrácení sekvence 14, 11, 13, 12, 10. Další informace najdete v tématu [klauzule select](select-clause.md).

Proměnná rozsahu je jako proměnná iterace v [foreach](foreach-in.md) příkaz s výjimkou jednoho velmi důležitý rozdíl: Proměnná rozsahu nikdy ve skutečnosti ukládá data ze zdroje. To, kterou právě syntaktické pohodlí, které umožňuje dotaz tak, aby popište, co dojde při spuštění dotazu. Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](../../programming-guide/concepts/linq/introduction-to-linq-queries.md).

## <a name="compound-from-clauses"></a>Složené z klauzule

V některých případech může každý prvek ve zdrojové sekvenci může sám buď jako sekvence nebo obsahovat sekvence. Zdroj dat může být například `IEnumerable<Student>` kde každý student v pořadí obsahuje seznam skóre v testech. Pro přístup k seznamu vnitřní v každé `Student` element, můžete použít složené `from` klauzule. Jako postup se používá jako použití vnořených [foreach](foreach-in.md) příkazy. Můžete přidat [kde](partial-method.md) nebo [orderby](orderby-clause.md) klauzule buď `from` klauzule můžete filtrovat výsledky. Následující příklad ukazuje posloupnost `Student` objektů, z nichž každý obsahuje vnitřní `List` celých čísel představujících testu skóre. Pro přístup k seznamu vnitřní, použijte složeného `from` klauzuli. Můžete vložit klauzule mezi těmito dvěma `from` klauzule v případě potřeby.

[!code-csharp[cscsrefQueryKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#2)]

## <a name="using-multiple-from-clauses-to-perform-joins"></a>Použití více z klauzule k provádění spojení

Složeného `from` klauzule slouží k přístupu k vnitřních kolekcí do jednoho datového zdroje. Ale dotazu může také obsahovat více `from` klauzule, které generují doplňkové dotazů ze zdroje dat nezávislé. Tato technika umožňuje provádět určité operace spojení, které nejsou možné pomocí [klauzule join](join-clause.md).

Následující příklad ukazuje, jak dva `from` klauzule můžete použít k vytvoření kompletní křížové spojení dvou datových zdrojů.

[!code-csharp[cscsrefQueryKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#3)]

Další informace o operace spojení, které používají více `from` klauzule, naleznete v tématu [provést levá vnější spojení](../../linq/perform-left-outer-joins.md).

## <a name="see-also"></a>Viz také:

- [Klíčová slova dotazu (LINQ)](query-keywords.md)  
- [LINQ (Language Integrated Query)](../../linq/index.md)  
