---
title: Language-Integrated Query (LINQ) (C#)
ms.date: 02/02/2017
ms.assetid: 19dd1782-905b-4a9d-a3e9-618453037fa2
ms.openlocfilehash: c19e0eb658c428a3e511251f4851868de676d887
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="language-integrated-query-linq"></a>Jazyk integrovaného dotazu (LINQ)

Language-Integrated Query (LINQ) je název pro sadu technologií, v závislosti na integraci funkcí dotaz přímo do jazyka C#. Dotazy na data jsou tradičně, vyjádřené jako jednoduchý řetězce bez kontrolu typu v kompilaci čas nebo podporu technologie IntelliSense. Kromě toho budete muset další různých dotazovací jazyk pro každý typ zdroje dat: SQL databáze, dokumentů XML, různé webové služby a tak dále. S dotazy LINQ dotazu je první třídy jazyka konstrukce, stejně jako tříd, metod, události.

Pro vývojáře, který zapíše dotazy je většina viditelná "language-integrated" část LINQ výrazu dotazu. Výrazy dotazů jsou zapsány v deklarativní *syntaxe dotazu*. Pomocí syntaxe dotazů můžete provést filtrování, řazení a seskupování operací na zdroje dat s minimální kódu. Použijete stejný výraz vzory základního dotazu pro dotazování a transformovat data v databází SQL, ADO .NET datové sady, dokumentů XML a datových proudů a kolekcí .NET.

Následující příklad ukazuje operaci dokončení dotazu. Dokončení operace zahrnuje vytváření zdroje dat, definování výrazu dotazu a provádění dotazu v `foreach` příkaz.

[!code-csharp[csProgGuideLINQ#11](../../../../../samples/snippets/csharp/concepts/linq/index_1.cs)]

## <a name="query-expression-overview"></a>Přehled výraz dotazu

-   Výrazy dotazů lze použít k dotazování a který umožňuje transformovat data ze zdroje dat podporující LINQ. Například jeden dotaz můžete načíst data z databáze SQL a vytvoří datový proud XML jako výstup.  
  
-   Výrazy dotazů lze snadno na hlavní server, protože používají mnoho známých C# jazykové konstrukty.  
  
-   Proměnné ve výrazu dotazu jsou všechny silného typu, i když v mnoha případech není nutné explicitně zadat typ protože kompilátor lze odvodit ho. Další informace najdete v tématu [vztahy typů v LINQ dotazu operations](type-relationships-in-linq-query-operations.md).  
  
-   Dotaz není provést, dokud iterace v proměnné v dotazu, například v `foreach` příkaz. Další informace najdete v tématu [Úvod do dotazů LINQ](introduction-to-linq-queries.md).  
  
-   Při kompilaci jsou výrazy dotazu převedeny na standardní – operátor dotazu volání metod souladu s pravidly uvedenými v specifikace jazyka C#. Pomocí syntaxe využívající metody lze také vyjádřit dotaz, který lze vyjádřit pomocí syntaxe dotazu. Ve většině případů však syntaxe dotazu je čitelnější a stručné sdělení. Další informace najdete v tématu [specifikace jazyka C#](../../../language-reference/language-specification/index.md) a [přehled standardních operátorů dotazu](standard-query-operators-overview.md).  
  
-   Jako pravidlo při zápis dotazů LINQ, doporučujeme použít syntaxi dotazu, pokud je to možné a syntaxe využívající metody kdykoli je to nezbytné. Neexistuje žádné sémantického nebo výkonu nesouhlasí dva různé formuláře. Výrazy dotazů jsou často čitelný než ekvivalentní výrazy, které jsou napsané v syntaxe využívající metody.  
  
-   Některé operace, jako například dotaz <xref:System.Linq.Enumerable.Count%2A> nebo <xref:System.Linq.Enumerable.Max%2A>, mít žádná ekvivalentní dotaz výrazu klauzule a proto musí být vyjádřena jako volání metody. Syntaxe využívající metody mohou být kombinovány s syntaxe dotazů různými způsoby. Další informace najdete v tématu [syntaxe využívající dotazy a syntaxe využívající metody v technologii LINQ](query-syntax-and-method-syntax-in-linq.md).  
  
-   Stromy výrazů nebo delegáti, v závislosti na typu, který je použit dotaz na, mohou být zkompilovány výrazy dotazů. <xref:System.Collections.Generic.IEnumerable%601> dotazy jsou kompilovány na delegáty. <xref:System.Linq.IQueryable> a <xref:System.Linq.IQueryable%601> dotazy jsou zkompilovány do stromů výrazů. Další informace najdete v tématu [stromů výrazů](../../../expression-trees.md).  

## <a name="next-steps"></a>Další kroky

Další podrobnosti o LINQ, spusťte Seznamte se s některé základní pojmy v [dotaz základy výrazů](../../../linq/query-expression-basics.md), a přečtěte si dokumentaci pro LINQ technologii, která vás zajímá:   
-   Dokumenty XML: [technologie LINQ to XML](linq-to-xml.md)  
  
-   ADO.NET Entity Framework: [technologie LINQ to entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md)  
  
-   Kolekcí .NET, soubory, a tak dále řetězce: [LINQ na objekty](linq-to-objects.md)

Pokud chcete pochopit hlubší LINQ obecně, najdete v části [LINQ v C#](../../../linq/linq-in-csharp.md).

Pokud chcete začít pracovat s dotazy LINQ v C#, najdete v části kurzu [práce s dotazy LINQ](../../../tutorials/working-with-linq.md).



