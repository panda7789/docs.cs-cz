---
title: Dotazy v technologii LINQ to Entities
ms.date: 03/30/2017
ms.assetid: c015a609-29eb-4e95-abb1-2ca721c6e2ad
ms.openlocfilehash: e8a3ce26c25bf8350460844110470d3a167c70ce
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65584607"
---
# <a name="queries-in-linq-to-entities"></a>Dotazy v technologii LINQ to Entities
Dotaz je výraz, který načítá data z datového zdroje. Dotazy jsou obvykle vyjádřeny v specializovaném dotazovacím jazyce, jako je například SQL pro relační databáze a XQuery pro XML. Proto vývojáři měli získat nový dotazovací jazyk pro každý typ zdroje dat nebo formátu dat, který dotazy. Language Integrated Query (LINQ) nabízí jednodušší a konzistentní model pro práci s daty napříč různými druhy datových zdrojů a formátů. V dotazu LINQ vždy pracujete s programovacích objektech.  
  
 Operace LINQ dotazu se skládá ze tří akcí: získání datového zdroje nebo zdrojů, vytvořte dotaz a spusťte dotaz.  
  
 Zdroje dat, které implementují <xref:System.Collections.Generic.IEnumerable%601> obecné rozhraní nebo <xref:System.Linq.IQueryable%601> obecné rozhraní může být dotázán pomocí LINQ. Instance obecného <xref:System.Data.Objects.ObjectQuery%601> třídy, která implementuje obecné <xref:System.Linq.IQueryable%601> rozhraní, bude sloužit jako zdroj dat pro [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy. <xref:System.Data.Objects.ObjectQuery%601> Generické třídě představuje dotaz, který vrátí kolekci objektů nula nebo více typem. Můžete také nechat kompilátor odvodit typ entity s použitím klíčového slova jazyka C# `var` (dimenze v jazyce Visual Basic).  
  
 V dotazu je zadat přesně informace, které chcete načíst ze zdroje dat. Dotaz můžete také určit, jak tyto informace by měl být seřazeny, seskupeny a tvarovány dříve, než se vrátí. V LINQ dotaz uložené v proměnné. Pokud dotaz vrací posloupnost hodnot, musí být proměnná dotazu sama dotazovatelného typu. Tato proměnná dotazu neprovede žádnou akci a nevrátí žádná data; ukládá pouze informace o dotazu. Po vytvoření dotazu je třeba spustit tento dotaz pro načtení žádná data.  
  
## <a name="query-syntax"></a>Syntaxe dotazů  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy mohou být složené ve dvou různých syntaxí: výraz syntaxe využívající dotazy a syntaxe dotazů založených na volání metody. Syntaxe výrazu dotazu je nového v jazyce C# 3.0 a Visual Basic 9.0 a skládá se ze sady klauzule napsané v deklarativní syntaxi podobnou jazyku Transact-SQL nebo výraz XQuery. Rozhraní .NET Framework common language runtime (CLR) však nelze číst syntaxe výrazu dotazu, samotného. V době kompilace, proto – výrazy dotazů jsou přeloženy na něco, co CLR chápe: volání metody. Tyto metody jsou označovány jako *standardních operátorů pro dotazování*. Jako vývojář máte možnost volání přímo pomocí syntaxe metody, namísto použití syntaxe dotazu. Další informace najdete v tématu [syntaxi dotazů a syntaxe využívající metody v jazyce LINQ](~/docs/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
### <a name="query-expression-syntax"></a>Syntaxe výrazu dotazu  
 Výrazy dotazu představují dotaz deklarativní syntaxe. Tato syntaxe umožňuje vývojářům psát dotazy v jazyce vysoké úrovně, který se naformátoval podobný příkazů jazyka Transact-SQL. Pomocí syntaxe výrazu dotazu, můžete provádět, dokonce i složité filtrování, řazení a seskupení operací u zdrojů dat s minimem kódu. Další informace najdete [základní operace dotazů (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/linq/basic-query-operations.md). Příklady, které ukazují, jak pomocí syntaxe výrazu dotazu naleznete v následujících tématech:  
  
- [Příklady syntaxe výrazů dotazů: Projekce](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-projection.md)  
  
- [Příklady syntaxe výrazů dotazů: Filtrování](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-filtering.md)  
  
- [Příklady syntaxe výrazů dotazů: Řazení](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-ordering.md)  
  
- [Příklady syntaxe výrazů dotazů: Agregační operátory](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-aggregate-operators.md)  
  
- [Příklady syntaxe výrazů dotazů: Vytváření oddílů](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-partitioning.md)  
  
- [Příklady syntaxe výrazů dotazů: Operátory spojení](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-join-operators.md)  
  
- [Příklady syntaxe výrazů dotazů: Operátory elementů](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-element-operators.md)  
  
- [Příklady syntaxe výrazů dotazů: Seskupení](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-grouping.md)  
  
- [Příklady syntaxe výrazů dotazů: Navigace v relacích](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-navigating-relationships.md)  
  
### <a name="method-based-query-syntax"></a>Syntaxe dotazů založených na volání metody  
 Dalším způsobem, jak vytvořit [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazů je pomocí dotazů založených na volání metody. Syntaxe dotazů založených na volání metody je posloupnost přímé metody volání metody operátorů LINQ, předávání výrazy lambda jako parametry. Další informace najdete v tématu [výrazy Lambda](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md). Příklady, které ukazují, jak používat syntaxi založených na volání metody naleznete v následujících tématech:  
  
- [Příklady syntaxe dotazů založených na volání metody: Projekce](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-projection.md)  
  
- [Příklady syntaxe dotazů založených na volání metody: Filtrování](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-filtering.md)  
  
- [Příklady syntaxe dotazů založených na volání metody: Řazení](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-ordering.md)  
  
- [Příklady syntaxe dotazů založených na volání metody: Agregační operátory](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-aggregate-operators.md)  
  
- [Příklady syntaxe dotazů založených na volání metody: Vytváření oddílů](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-partitioning.md)  
  
- [Příklady syntaxe dotazů založených na volání metody: Převod](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-conversion.md)  
  
- [Příklady syntaxe dotazů založených na volání metody: Operátory spojení](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-join-operators.md)  
  
- [Příklady syntaxe dotazů založených na volání metody: Operátory elementů](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-element-operators.md)  
  
- [Příklady syntaxe dotazů založených na volání metody: Seskupení](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-grouping.md)  
  
- [Příklady syntaxe dotazů založených na volání metody: Navigace v relacích](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-navigating-relationships.md)  
  
## <a name="see-also"></a>Viz také:

- [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
- [Začínáme s dotazy LINQ v jazyce C#](~/docs/csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Začínáme s dotazy LINQ v jazyce Visual Basic](~/docs/visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Možnosti sloučení Entity Framework a kompilované dotazy](https://go.microsoft.com/fwlink/?LinkId=199591)
