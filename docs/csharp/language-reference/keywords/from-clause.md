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
ms.openlocfilehash: 21f7cf15de621bf862dedb82e87177900506a728
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218394"
---
# <a name="from-clause-c-reference"></a>from clause (Referenční dokumentace jazyka C#)
Výraz dotazu musí začínat `from` klauzule. Kromě toho může výrazu dotazu obsahovat dílčí dotazy, které také začínat `from` klauzule. `from` Klauzuli určuje následující:  
  
-   Zdroj dat, na kterém se spustí dotazu nebo poddotazu.  
  
-   Místní *proměnnou rozsahu* představující každý prvek v pořadí zdroje.  
  
 Proměnná rozsahu a zdroji dat jsou silného typu. Zdroj dat, kterou se odkazuje v `from` klauzule musí mít typ <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, nebo odvozený typ jako <xref:System.Linq.IQueryable%601>.  
  
 V následujícím příkladu `numbers` je zdroj dat a `num` je proměnnou rozsahu. Všimněte si, že obě proměnné jsou silného typu i prostřednictvím [var](../../../csharp/language-reference/keywords/var.md) – klíčové slovo se používá.  
  
 [!code-csharp[cscsrefQueryKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_1.cs)]  
  
## <a name="the-range-variable"></a>Proměnná rozsahu  
 Kompilátor odvodí typ proměnné rozsahu při zdroje dat implementuje <xref:System.Collections.Generic.IEnumerable%601>. Například pokud má zdroj typu `IEnumerable<Customer>`, pak je potřeba odvodit proměnnou rozsahu `Customer`. Jenom jednou, který je nutné zadat typ explicitně je při zdroj je není obecný `IEnumerable` zadejte například <xref:System.Collections.ArrayList>. Další informace najdete v tématu [postup: dotazu na ArrayList pomocí LINQ](../../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).  
  
 V předchozím příkladu `num` je odvodit být typu `int`. Vzhledem k tomu, že proměnná rozsahu je silného typu, můžete v něm volat metody nebo ho použít jiné operace. Například místo psaní `select num`, můžete napsat `select num.ToString()` způsobí výraz dotazu pro vrácení pořadí řetězců místo celých čísel. Nebo můžete napsat `select n + 10` způsobí výraz, který se vrátí pořadí 14, 11, 13, 12, 10. Další informace najdete v tématu [klauzuli select](../../../csharp/language-reference/keywords/select-clause.md).  
  
 Proměnná rozsahu je třeba proměnné iterace ve [foreach](../../../csharp/language-reference/keywords/foreach-in.md) příkaz s výjimkou jeden velmi důležitý rozdíl: proměnnou rozsahu nikdy ve skutečnosti ukládá data ze zdroje. Ho, kterou právě syntaktické pohodlí, která umožňuje dotaz pro popište, co se stane, když je proveden dotaz. Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
## <a name="compound-from-clauses"></a>Složené klauzulí from  
 V některých případech každý prvek v pořadí zdroj může sám sebe být buď pořadí nebo obsahovat. Váš zdroj dat může být například `IEnumerable<Student>` kde každý objekt student v pořadí obsahuje seznam výsledků testu. Pro přístup k seznamu vnitřní v každém `Student` elementu, můžete použít složené `from` klauzule. Způsob je jako pomocí vnořené [foreach](../../../csharp/language-reference/keywords/foreach-in.md) příkazy. Můžete přidat [kde](../../../csharp/language-reference/keywords/partial-method.md) nebo [orderby](../../../csharp/language-reference/keywords/orderby-clause.md) klauzule buď `from` klauzule filtrování výsledků. Následující příklad ukazuje posloupnost `Student` objekty, z nichž každý obsahuje vnitřní `List` celých čísel představující testování skóre. Chcete-li získat přístup k seznamu vnitřní, použijte složené `from` klauzule. Můžete vložit klauzule mezi těmito dvěma `from` klauzule v případě potřeby.  
  
 [!code-csharp[cscsrefQueryKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_2.cs)]  
  
## <a name="using-multiple-from-clauses-to-perform-joins"></a>Použití více klauzulí from k provedení spojení  
 Složené `from` klauzule slouží k přístupu vnitřní kolekcí v jeden zdroj dat. Ale dotazu může také obsahovat více `from` věty, které generovat další dotazy z nezávislé datové zdroje. Tento postup umožňuje provádět určité operace spojení, které nejsou možné pomocí [klauzuli join](../../../csharp/language-reference/keywords/join-clause.md).  
  
 Následující příklad ukazuje, jak dva `from` klauzule můžete použít k dokončení křížové spojení dvou datových zdrojů.  
  
 [!code-csharp[cscsrefQueryKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_3.cs)]  
  
 Další informace o připojení k operace, které používají více `from` klauzule, najdete v části [postup: provedení operací spojování vlastní](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md).  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova dotazu (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [LINQ – výrazy dotazů](../../../csharp/programming-guide/linq-query-expressions/index.md)
