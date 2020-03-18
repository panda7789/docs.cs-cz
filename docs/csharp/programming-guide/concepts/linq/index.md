---
title: Dotaz integrovaný jazykem (LINQ) (C#)
ms.date: 02/02/2017
ms.assetid: 19dd1782-905b-4a9d-a3e9-618453037fa2
ms.openlocfilehash: 07a9d68c042d524ee9faba8122b406a81e816378
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73418244"
---
# <a name="language-integrated-query-linq"></a>LINQ (Language Integrated Query)

Jazykintegrovaný dotaz (LINQ) je název pro sadu technologií založených na integraci dotazovacích funkcí přímo do jazyka C#. Dotazy na data jsou tradičně vyjádřeny jako jednoduché řetězce bez kontroly typu v době kompilace nebo podpory technologie IntelliSense. Kromě toho se musíte naučit jiný dotazovací jazyk pro každý typ zdroje dat: databáze SQL, dokumenty XML, různé webové služby a tak dále. S LINQ dotaz je prvotřídní jazyk konstrukce, stejně jako třídy, metody, události. Můžete psát dotazy proti silně zadaným kolekcíobjektů pomocí klíčových slov jazyka a známé operátory. Řada technologií LINQ poskytuje konzistentní prostředí dotazů pro objekty (LINQ na objekty), relační databáze (LINQ to SQL) a XML (LINQ na XML).

Pro vývojáře, který píše dotazy, nejviditelnější "jazykově integrované" část LINQ je výraz dotazu. Výrazy dotazu jsou zapsány v syntaxi deklarativního *dotazu*. Pomocí syntaxe dotazu můžete provádět operace filtrování, řazení a seskupování na zdrojích dat s minimem kódu. Stejné vzory výrazů základnídotaz použít k dotazování a transformaci dat v databázích SQL, Datových sadách ADO .NET, dokumentech XML a datových proudech a kolekcích .NET.

Můžete psát dotazy LINQ v jazyce C# pro sql server databáze, dokumenty XML, <xref:System.Collections.IEnumerable> ADO.NET <xref:System.Collections.Generic.IEnumerable%601> datové sady a všechny kolekce objektů, které podporuje nebo obecné rozhraní. Podpora LINQ je také poskytována třetími stranami pro mnoho webových služeb a dalších implementací databází.

Následující příklad ukazuje celou operaci dotazu. Kompletní operace zahrnuje vytvoření zdroje dat, definování výrazu dotazu a `foreach` spuštění dotazu v příkazu.

[!code-csharp[csProgGuideLINQ#11](~/samples/snippets/csharp/concepts/linq/index_1.cs)]

Následující obrázek z sady Visual Studio znázorňuje částečně vyplněný dotaz LINQ na databázi serveru SQL Server v jazyce C# i jazyce Visual Basic s úplnou kontrolou typu a podporou technologie IntelliSense:

![Diagram, který zobrazuje dotaz LINQ s Intellisense.](./media/introduction-to-linq/linq-query-intellisense.png)

## <a name="query-expression-overview"></a>Přehled výrazu dotazu

- Výrazy dotazu lze použít k dotazování a transformaci dat z libovolného zdroje dat s podporou LINQ. Například jeden dotaz může načíst data z databáze SQL a vytvořit datový proud XML jako výstup.
- Výrazy dotazu jsou snadno zvládnout, protože používají mnoho známých konstrukce jazyka C#.
- Proměnné ve výrazu dotazu jsou všechny silného typu, i když v mnoha případech není nutné zadat typ explicitně, protože kompilátor můžete odvodit. Další informace naleznete [v tématu Typ relací v operacích dotazu LINQ](type-relationships-in-linq-query-operations.md).
- Dotaz není proveden, dokud iterate přes proměnnou dotazu, `foreach` například v příkazu. Další informace naleznete [v tématu Úvod do linq dotazy](introduction-to-linq-queries.md).
- V době kompilace jsou výrazy dotazu převedeny na volání metody Operátor standardnídotaz podle pravidel stanovených ve specifikaci C#. Jakýkoli dotaz, který lze vyjádřit pomocí syntaxe dotazu, lze také vyjádřit pomocí syntaxe metody. Ve většině případů je však syntaxe dotazu čitelnější a stručnější. Další informace naleznete v [tématu C# specifikace jazyka](~/_csharplang/spec/expressions.md#query-expressions) a [standardní operátory dotazu přehled](standard-query-operators-overview.md).
- Při psaní dotazů LINQ doporučujeme použít syntaxi dotazu, kdykoli je to možné, a syntaxi metody, kdykoli je to nutné. Neexistuje žádný sémantický nebo výkon rozdíl mezi dvěma různými formami. Výrazy dotazu jsou často čitelnější než ekvivalentní výrazy napsané v syntaxi metody.
- Některé operace dotazu, například <xref:System.Linq.Enumerable.Count%2A> nebo <xref:System.Linq.Enumerable.Max%2A>, nemají žádnou rovnocennou klauzuli výrazu dotazu a proto musí být vyjádřeny jako volání metody. Syntaxe metody lze kombinovat se syntaxí dotazu různými způsoby. Další informace naleznete [v tématu Syntaxe a syntaxe metody dotazu v linq](query-syntax-and-method-syntax-in-linq.md).
- Výrazy dotazu lze kompilovat do stromů výrazů nebo delegátů v závislosti na typu, na který je dotaz použit. <xref:System.Collections.Generic.IEnumerable%601>dotazy jsou kompilovány delegátům. <xref:System.Linq.IQueryable>a <xref:System.Linq.IQueryable%601> dotazy jsou kompilovány do stromů výrazů. Další informace naleznete v [tématu Expression trees](../../../expression-trees.md).

## <a name="next-steps"></a>Další kroky

Chcete-li se dozvědět více podrobností o LINQ, začněte tím, že se seznámíte s některými základními pojmy v [základech výrazu dotazu](../../../linq/query-expression-basics.md)a pak si přečtěte dokumentaci k technologii LINQ, o kterou máte zájem:

- Dokumenty XML: [LINQ to XML](linq-to-xml-overview.md)  
- ADO.NET entity: [LINQ pro entity](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md)
- Kolekce.NET, soubory, řetězce a tak dále: [LINQ na objekty](linq-to-objects.md)

Chcete-li získat hlubší pochopení LINQ obecně, naleznete v tématu [LINQ v C#](../../../linq/linq-in-csharp.md).

Chcete-li začít pracovat s LINQ v C#, naleznete v kurzu [Práce s LINQ](../../../tutorials/working-with-linq.md).
