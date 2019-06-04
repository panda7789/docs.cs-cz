---
title: Language-Integrated Query (LINQ) (C#)
ms.date: 02/02/2017
ms.assetid: 19dd1782-905b-4a9d-a3e9-618453037fa2
ms.openlocfilehash: 1f2cbab6295fd9a2c2b3458f520dbf231d9b5413
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484541"
---
# <a name="language-integrated-query-linq"></a>LINQ (Language Integrated Query)

Language Integrated Query (LINQ) je název pro sadu technologií, v závislosti na integraci schopnosti příkazů jazyka přímo do jazyka C#. Tradičně dotazů na data jsou vyjádřené jako jednoduchý řetězce bez kontrolu typu v kompilaci čas nebo podporu technologie IntelliSense. Kromě toho budete muset učit jazyk dotazu pro každý typ zdroje dat: Databáze SQL, dokumenty XML, různé webové služby a tak dále. S dotazy LINQ dotaz, který je typů prvotřídní jazykové konstrukce, stejně jako třídy, metody a události. Psát dotazy proti silně typované kolekce objektů s použitím známých operátory a klíčová slova jazyka.  LINQ řadu technologií poskytuje konzistentní dotazu prostředí pro objekty (LINQ to Objects), relačních databází (LINQ to SQL) a XML (LINQ to XML).  

Pro vývojáře, který zapíše dotazy je většina viditelnou část "language-integrated" LINQ výrazu dotazu. Výrazy dotazů jsou napsané v deklarativní *syntaxe dotazu*. Pomocí syntaxe dotazu, můžete provádět filtrování, řazení a seskupení operací u zdrojů dat s minimálním kódu. Použijte stejné vzorce výrazu základního dotazu pro dotazování a transformaci dat v SQL Database, ADO .NET datové sady, dokumentů XML a datových proudů a kolekcí .NET.

Můžete zápis dotazů LINQ v jazyce C# pro databáze serveru SQL Server, dokumenty XML, datovými sadami ADO.NET a kolekce objektů, který podporuje <xref:System.Collections.IEnumerable> nebo Obecné <xref:System.Collections.Generic.IEnumerable%601> rozhraní. Podpora LINQ se také poskytuje třetími stranami pro mnoho webových služeb a jiné implementace databáze.  

Následující příklad znázorňuje operaci úplného dotazu. Dokončení operace zahrnuje vytvoření zdroje dat, definující výraz dotazu a zpracování dotazu v `foreach` příkazu.

[!code-csharp[csProgGuideLINQ#11](../../../../../samples/snippets/csharp/concepts/linq/index_1.cs)]

 Na následujícím obrázku ze sady Visual Studio ukazuje dotaz LINQ částečně dokončeno databázi SQL serveru v obou C# a Visual Basic s úplným typem kontrolu a podporu technologie IntelliSense:  
  
 ![Diagram, který ukazuje dotaz LINQ s podporou technologie Intellisense.](./media/introduction-to-linq/linq-query-intellisense.png)  
  
## <a name="query-expression-overview"></a>Přehled výrazu dotazu

- Výrazy dotazu lze použít k dotazování a transformaci dat z libovolného zdroje data povolenými LINQ. Pomocí jediného dotazu můžete například načtení dat z SQL database a vytvořit datový proud XML jako výstup.  
  
- Výrazy dotazu představují snadný na hlavní server, protože používají řadu známých konstrukcí jazyka C#.  
  
- Proměnné ve výrazu dotazu jsou všechny silného typu, ale v mnoha případech není nutné explicitně zadat typ, protože kompilátor může odvodit ho. Další informace najdete v tématu [vztahy typů v LINQ dotaz operace](type-relationships-in-linq-query-operations.md).  
  
- Dotaz není spuštěn, dokud neprovedete iteraci v proměnné dotazu, například v `foreach` příkazu. Další informace najdete v tématu [Úvod do dotazů LINQ](introduction-to-linq-queries.md).  
  
- V době kompilace jsou výrazy dotazu převedeny na volání metody standardního operátoru dotazu podle pravidel specifikace jazyka C#. Jakýkoli dotaz, který lze vyjádřit pomocí syntaxe dotazu lze také vyjádřit pomocí syntaxe metody. Ale ve většině případů je syntaxe dotazu čitelný a výstižně. Další informace najdete v tématu [specifikace jazyka C#](~/_csharplang/spec/expressions.md#query-expressions) a [přehled standardních operátorů dotazu](standard-query-operators-overview.md).  
  
- Zpravidla při psaní dotazů LINQ, doporučujeme použít syntaxi dotazů, kdykoli je to možné a syntaxe využívající metody kdykoli je to zapotřebí. Neexistuje žádné sémantické nebo výkonu rozdíl mezi dvě různými formami jiný. Výrazy dotazů jsou často čitelnější než ekvivalentní výrazy, které jsou napsané v syntaxe metody.  
  
- Některé operace, například dotazování <xref:System.Linq.Enumerable.Count%2A> nebo <xref:System.Linq.Enumerable.Max%2A>, mít žádná klauzule výrazu dotazu odpovídá a proto musí být vyjádřena jako volání metody. Syntaxe využívající metody můžete kombinovat pomocí syntaxe dotazu různými způsoby. Další informace najdete v tématu [syntaxe využívající dotazy a syntaxe využívající metody v LINQ](query-syntax-and-method-syntax-in-linq.md).  
  
- Výrazy dotazu může být zkompilován na stromy výrazů nebo na delegáty, v závislosti na typu použitého dotazu. <xref:System.Collections.Generic.IEnumerable%601> dotazy jsou kompilovány do delegátů. <xref:System.Linq.IQueryable> a <xref:System.Linq.IQueryable%601> dotazy se kompilují na stromy výrazů. Další informace najdete v tématu [stromů výrazů](../../../expression-trees.md).  

## <a name="next-steps"></a>Další kroky

Další informace o dotazech technologie LINQ, začněte se seznamovat s některé základní pojmy v [základy výrazů dotazů](../../../linq/query-expression-basics.md), a pak si můžete přečíst dokumentaci k technologie LINQ, který vás zajímá:   
- Dokumenty XML: [LINQ to XML](linq-to-xml.md)  
  
- ADO.NET Entity Framework: [Technologie LINQ to entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md)  
  
- Kolekce .NET, soubory, řetězce a tak dále: [LINQ na objekty](linq-to-objects.md)

Získání hlubší pochopení LINQ obecně získáte [LINQ v JAZYKU C#](../../../linq/linq-in-csharp.md).

Pokud chcete začít pracovat s dotazy LINQ v C#, najdete v kurzu [práce s jazykem LINQ](../../../tutorials/working-with-linq.md).

## <a name="see-also"></a>Viz také:

- [Language-Integrated Query (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
