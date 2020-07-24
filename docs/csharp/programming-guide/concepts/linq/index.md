---
title: LINQ (Language-Integrated Query) (C#)
description: Přečtěte si o dotazech integrovaných v jazyce (LINQ) a Projděte si příklad úplné operace dotazu.
ms.date: 02/02/2017
ms.assetid: 19dd1782-905b-4a9d-a3e9-618453037fa2
ms.openlocfilehash: 6c8844c387177ce858b63a52b1f5c7246b570beb
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103424"
---
# <a name="language-integrated-query-linq"></a>LINQ (Language Integrated Query)

LINQ (Language-Integrated Query) je název sady technologií založených na integraci možností dotazů přímo do jazyka C#. Tradičně se dotazy na data vyjadřují jako jednoduché řetězce bez kontroly typu v době kompilace nebo v podpoře technologie IntelliSense. Kromě toho se musíte naučit jiný dotazovací jazyk pro každý typ zdroje dat: databáze SQL, dokumenty XML, různé webové služby a tak dále. Pomocí LINQ je dotazem konstrukce jazyka první třídy, stejně jako třídy, metody a události. Zapisujete dotazy na kolekce objektů se silnými typy pomocí klíčových slov jazyka a známých operátorů. Rodina technologie LINQ nabízí konzistentní možnosti dotazování pro objekty (LINQ to Objects), relační databáze (LINQ to SQL) a XML (LINQ to XML).

Pro vývojáře, který zapisuje dotazy, je nejpravděpodobnější "jazykově integrovaná" část LINQ výraz dotazu. Výrazy dotazů jsou zapsány v deklarativní *syntaxi dotazu*. Pomocí syntaxe dotazů můžete provádět filtrování, řazení a seskupování operací na zdrojích dat s minimálním kódem. Použijete stejné základní vzorce výrazů dotazů pro dotazování a transformaci dat v databázích SQL, ADO.NET datových sadách, dokumentech XML a datových proudech a kolekcích .NET.

Dotazy LINQ můžete psát v jazyce C# pro SQL Server databází, dokumentů XML, datových sad ADO.NET a libovolné kolekci objektů, které podporují <xref:System.Collections.IEnumerable> nebo obecné <xref:System.Collections.Generic.IEnumerable%601> rozhraní. Podporu LINQ poskytují i třetí strany pro mnoho webových služeb a dalších implementací databáze.

Následující příklad ukazuje operaci dokončení dotazu. Operace Complete zahrnuje vytvoření zdroje dat, definování výrazu dotazu a spuštění dotazu v `foreach` příkazu.

[!code-csharp[csProgGuideLINQ#11](~/samples/snippets/csharp/concepts/linq/index_1.cs)]

Následující obrázek ze sady Visual Studio ukazuje částečně dokončený dotaz LINQ na databázi SQL Server v jazyce C# i Visual Basic s úplnou kontrolou typu a podporou technologie IntelliSense:

![Diagram, který zobrazuje dotaz LINQ pomocí technologie IntelliSense.](./media/introduction-to-linq/linq-query-intellisense.png)

## <a name="query-expression-overview"></a>Přehled výrazu dotazu

- Výrazy dotazů lze použít k dotazování a transformaci dat z libovolného zdroje dat s podporou jazyka LINQ. Jeden dotaz může například načíst data z databáze SQL a vytvořit datový proud XML jako výstup.
- Výrazy dotazů jsou snadno hlavní, protože využívají mnoho známých konstrukcí jazyka C#.
- Proměnné ve výrazu dotazu jsou všechny silně typované, i když v mnoha případech nemusíte explicitně zadat typ, protože ho kompilátor může odvodit. Další informace najdete v tématu [vztahy typů v operacích dotazu LINQ](type-relationships-in-linq-query-operations.md).
- Dotaz není proveden, dokud neprovedete iteraci nad proměnnou dotazu, například v `foreach` příkazu. Další informace najdete v tématu [Úvod do dotazů LINQ](introduction-to-linq-queries.md).
- V době kompilace jsou výrazy dotazu převedeny na standardní volání metody operátoru dotazu podle pravidel stanovených ve specifikaci jazyka C#. Jakýkoli dotaz, který lze vyjádřit pomocí syntaxe dotazu, lze také vyjádřit pomocí syntaxe metody. Ve většině případů je ale syntaxe dotazů čitelnější a Stručná. Další informace najdete v tématu Přehled [jazyka C#](~/_csharplang/spec/expressions.md#query-expressions) a [standardní operátory dotazu](standard-query-operators-overview.md).
- Jako pravidlo při psaní dotazů LINQ doporučujeme použít syntaxi dotazu, kdykoli je to možné, a syntaxi metody kdykoli je to nezbytné. Mezi dvěma různými formuláři není žádný sémantický nebo výkonový rozdíl. Výrazy dotazů jsou často čitelnější než ekvivalentní výrazy napsané v syntaxi metody.
- Některé operace dotazu, například <xref:System.Linq.Enumerable.Count%2A> nebo <xref:System.Linq.Enumerable.Max%2A> , nemají žádnou ekvivalentní klauzuli výrazu dotazu a musí být proto vyjádřeny jako volání metody. Syntaxi metody lze kombinovat se syntaxí dotazu různými způsoby. Další informace naleznete v tématu [syntaxe dotazu a syntaxe metody v jazyce LINQ](query-syntax-and-method-syntax-in-linq.md).
- Výrazy dotazů lze zkompilovat do stromů výrazů nebo delegátů v závislosti na typu, na který je dotaz použit. <xref:System.Collections.Generic.IEnumerable%601>dotazy jsou kompilovány pro delegáty. <xref:System.Linq.IQueryable>a <xref:System.Linq.IQueryable%601> dotazy jsou kompilovány do stromů výrazů. Další informace najdete v tématu [stromy výrazů](../../../expression-trees.md).

## <a name="next-steps"></a>Další kroky

Pokud chcete získat další informace o LINQ, začněte tím, že se seznámíte s některými základními koncepty v [základech dotazů na dotazy](../../../linq/query-expression-basics.md)a pak si přečtěte dokumentaci pro technologii LINQ, ve které máte zájem:

- Dokumenty XML: [LINQ to XML](linq-to-xml-overview.md)  
- ADO.NET Entity Framework: [LINQ to](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md) Entities
- Kolekce .NET, soubory, řetězce a tak dále: [LINQ to Objects](linq-to-objects.md)

Chcete-li získat hlubší porozumění LINQ obecně, přečtěte si téma [LINQ v jazyce C#](../../../linq/linq-in-csharp.md).

Chcete-li začít pracovat s LINQ v jazyce C#, přečtěte si kurz [práce s LINQ](../../../tutorials/working-with-linq.md).
