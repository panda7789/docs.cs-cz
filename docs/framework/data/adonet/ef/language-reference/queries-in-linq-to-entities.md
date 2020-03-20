---
title: Dotazy v technologii LINQ to Entities
ms.date: 03/30/2017
ms.assetid: c015a609-29eb-4e95-abb1-2ca721c6e2ad
ms.openlocfilehash: 3144796dfb1a970152d8ae56424aa37592d5da09
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78848779"
---
# <a name="queries-in-linq-to-entities"></a>Dotazy v technologii LINQ to Entities
Dotaz je výraz, který načítá data ze zdroje dat. Dotazy jsou obvykle vyjádřeny ve specializovaném dotazovacím jazyce, například SQL pro relační databáze a XQuery pro XML. Proto vývojáři museli naučit nový dotazovací jazyk pro každý typ zdroje dat nebo formát dat, které dotaz. Jazykově integrovaný dotaz (LINQ) nabízí jednodušší a konzistentní model pro práci s daty napříč různými druhy zdrojů dat a formátů. V dotazu LINQ vždy pracujete s programovacími objekty.  
  
 Operace dotazu LINQ se skládá ze tří akcí: získat zdroj dat nebo zdroje, vytvořit dotaz a spustit dotaz.  
  
 Zdroje dat, <xref:System.Collections.Generic.IEnumerable%601> které implementují obecné rozhraní nebo <xref:System.Linq.IQueryable%601> obecné rozhraní lze dotazovat prostřednictvím LINQ. Instance obecné <xref:System.Data.Objects.ObjectQuery%601> třídy, která implementuje obecné <xref:System.Linq.IQueryable%601> rozhraní, slouží jako zdroj dat pro dotazy LINQ entity. Obecná <xref:System.Data.Objects.ObjectQuery%601> třída představuje dotaz, který vrací kolekci objektů typu nula nebo více. Můžete také nechat kompilátor odvodit typ entity pomocí `var` c# klíčové slovo (Dim v jazyce Visual Basic).  
  
 V dotazu zadáte přesně informace, které chcete načíst ze zdroje dat. Dotaz může také určit, jak mají být tyto informace seřazeny, seskupeny a tvarovány před jejich vrácením. V LINQ dotaz je uložen v proměnné. Pokud dotaz vrátí posloupnost hodnot, samotná proměnná dotazu musí být dotazovatelný typ. Tato proměnná dotazu neprovede žádnou akci a vrátí žádná data. ukládá pouze informace o dotazu. Po vytvoření dotazu je nutné spustit tento dotaz k načtení všech dat.  
  
## <a name="query-syntax"></a>Syntaxe dotazů  
 Dotazy LINQ to Entities lze skládat ve dvou různých syntaxích: syntaxi výrazu dotazu a syntaxi dotazu založené na metodě. Syntaxe výrazu dotazu je nová v jazyce C# 3.0 a visual basicu 9.0 a skládá se ze sady klauzulí napsaných v deklarativní syntaxi podobné Transact-SQL nebo XQuery. Runtime clr rozhraní .NET Framework common language však nemůže číst samotnou syntaxi výrazu dotazu. Proto v době kompilace výrazy dotazu jsou přeloženy na něco, co CLR nerozumí: volání metody. Tyto metody jsou označovány jako *standardní operátory dotazu*. Jako vývojář máte možnost volat je přímo pomocí syntaxe metody, namísto použití syntaxe dotazu. Další informace naleznete [v tématu Syntaxe dotazu a syntaxe metody v LINQ](../../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
### <a name="query-expression-syntax"></a>Syntaxe výrazu dotazu  
 Výrazy dotazu jsou syntaxí deklarativního dotazu. Tato syntaxe umožňuje vývojáři psát dotazy v jazyce vysoké úrovně, který je formátován podobně jako Transact-SQL. Pomocí syntaxe výrazu dotazu můžete provádět i složité operace filtrování, řazení a seskupování na zdrojích dat s minimálním kódem. Další informace, [základní operace dotazu (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md). Příklady, které ukazují, jak používat syntaxi výrazu dotazu, naleznete v následujících tématech:  
  
- [Příklady syntaxe výrazů dotazů: Projekce](query-expression-syntax-examples-projection.md)  
  
- [Příklady syntaxe výrazů dotazů: Filtrování](query-expression-syntax-examples-filtering.md)  
  
- [Příklady syntaxe výrazů dotazů: Řazení](query-expression-syntax-examples-ordering.md)  
  
- [Příklady syntaxe výrazů dotazů: Agregační operátory](query-expression-syntax-examples-aggregate-operators.md)  
  
- [Příklady syntaxe výrazů dotazů: Dělení](query-expression-syntax-examples-partitioning.md)  
  
- [Příklady syntaxe výrazů dotazů: Operátory spojení](query-expression-syntax-examples-join-operators.md)  
  
- [Příklady syntaxe výrazů dotazů: Operátory elementů](query-expression-syntax-examples-element-operators.md)  
  
- [Příklady syntaxe výrazů dotazů: Seskupení](query-expression-syntax-examples-grouping.md)  
  
- [Příklady syntaxe výrazů dotazů: Navigace v relacích](query-expression-syntax-examples-navigating-relationships.md)  
  
### <a name="method-based-query-syntax"></a>Syntaxe dotazu založeného na metodě  
 Dalším způsobem, jak vytvořit linq na entity dotazy je pomocí dotazů založených na metodách. Syntaxe dotazu založené na metodě je posloupnost přímé metody volání linq operátor metody, předávání lambda výrazy jako parametry. Další informace naleznete v tématu [Lambda Expressions](../../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md). Příklady, které ukazují, jak používat syntaxi založenou na metodách, naleznete v následujících tématech:  
  
- [Příklady syntaxe dotazů založených na volání metody: Projekce](method-based-query-syntax-examples-projection.md)  
  
- [Příklady syntaxe dotazů založených na volání metody: Filtrování](method-based-query-syntax-examples-filtering.md)  
  
- [Příklady syntaxe dotazů založených na volání metody: Řazení](method-based-query-syntax-examples-ordering.md)  
  
- [Příklady syntaxe dotazů založených na volání metody: Agregační operátory](method-based-query-syntax-examples-aggregate-operators.md)  
  
- [Příklady syntaxe dotazů založených na volání metody: Dělení](method-based-query-syntax-examples-partitioning.md)  
  
- [Příklady syntaxe dotazů založených na volání metody: Převod](method-based-query-syntax-examples-conversion.md)  
  
- [Příklady syntaxe dotazů založených na volání metody: Operátory spojení](method-based-query-syntax-examples-join-operators.md)  
  
- [Příklady syntaxe dotazů založených na volání metody: Operátory elementů](method-based-query-syntax-examples-element-operators.md)  
  
- [Příklady syntaxe dotazů založených na volání metody: Seskupení](method-based-query-syntax-examples-grouping.md)  
  
- [Příklady syntaxe dotazů založených na volání metody: Navigace v relacích](method-based-query-syntax-examples-navigating-relationships.md)  
  
## <a name="see-also"></a>Viz také

- [LINQ to Entities](linq-to-entities.md)
- [Začínáme s dotazy LINQ v jazyce C#](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [Začínáme s dotazy LINQ v jazyce Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Možnosti sloučení EF a zkompilované dotazy](https://docs.microsoft.com/archive/blogs/dsimmons/ef-merge-options-and-compiled-queries)
