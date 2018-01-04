---
title: Dotazy v technologii LINQ to Entities
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c015a609-29eb-4e95-abb1-2ca721c6e2ad
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6fe20fd26b78bde19ed73e2415b1b5c283a0d1f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="queries-in-linq-to-entities"></a>Dotazy v technologii LINQ to Entities
Dotaz je výraz, který načte data z datového zdroje. Dotazy jsou obvykle vyjádřeny v specializované dotazovací jazyk, například SQL pro relační databáze a XQuery pro formát XML. Vývojáři mají proto byl Další informace o nový jazyk dotazu pro každý typ zdroje dat nebo formát dat, která dotazy. Language-Integrated Query (LINQ) nabízí jednodušší a konzistentní model pro práci s daty mezi různé druhy zdrojů dat a formáty. V dotazu LINQ vždy pracujete s programováním objekty.  
  
 Operace dotazu LINQ se skládá ze tří akcí: získat zdroj dat nebo zdroje, vytvořte dotaz a provést dotaz.  
  
 Zdroje dat, které implementují <xref:System.Collections.Generic.IEnumerable%601> obecné rozhraní nebo <xref:System.Linq.IQueryable%601> obecné rozhraní můžete vyhledávat pomocí LINQ. Instance obecná <xref:System.Data.Objects.ObjectQuery%601> třídy, která implementuje obecná <xref:System.Linq.IQueryable%601> rozhraní, sloužit jako zdroj dat pro [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy. <xref:System.Data.Objects.ObjectQuery%601> Obecná třída reprezentuje dotaz, který vrátí kolekce nula nebo více zadaných objektů. Můžete také nechat kompilátoru odvození typu entity pomocí klíčového slova jazyka C# `var` (dimenze v jazyce Visual Basic).  
  
 V dotazu je zadat přesně informace, které chcete načíst z datového zdroje. Dotaz můžete také určit, jak tyto informace by měl být seřazeny, seskupené a ve tvaru před vrácením. Dotaz je v technologii LINQ, uložené v proměnné. Pokud dotaz vrátí pořadí hodnot, proměnné v dotazu sám sebe musí být typu dotazovatelnosti. Tato proměnná dotazu neprovede žádnou akci a vrátí žádná data; ukládá jenom informace o dotazu. Po vytvoření dotazu je třeba spustit tento dotaz pro načtení žádná data.  
  
## <a name="query-syntax"></a>Syntaxe dotazu  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]dotazy můžete sestavit v dva různé syntaxe: výraz syntaxe využívající dotazy a syntaxe dotazu na základě metod. Syntaxe výrazu dotazu je nového v C# 3.0 a 9.0 Visual Basic a skládá se ze sady klauzule napsané v deklarativní syntaxi podobné Transact-SQL nebo XQuery. Ale [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] modul common language runtime (CLR) nelze přečíst syntaxe výrazu dotazu, sám sebe. Při kompilaci, tedy výrazy dotazů jsou převedeny na něco, co pochopit modulu CLR: volání metody. Tyto metody se označují jako *standardní operátory dotazu*. Jako vývojář máte možnost volání je přímo pomocí syntaxe využívající metody, místo použití syntaxe dotazu. Další informace najdete v tématu [syntaxe dotazů a syntaxe využívající metody v technologii LINQ](~/docs/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
### <a name="query-expression-syntax"></a>Syntaxe výrazu dotazu  
 Výrazy dotazů jsou syntaxe deklarativní dotazu. Tuto syntaxi umožňuje vývojáři psát dotazy v jazyce vysoké úrovně, který je naformátovaný podobná Transact-SQL. Pomocí syntaxe výrazu dotazu, můžete provést i komplexní filtrování, řazení a seskupování operací na zdroje dat s minimálním kódu. Další informace najdete [základní operace dotazů (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/linq/basic-query-operations.md). Příklady, které ukazují, jak pomocí syntaxe výrazu dotazu najdete v následujících tématech:  
  
-   [Příklady syntaxe výrazů dotazů: Projekce](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-projection.md)  
  
-   [Příklady syntaxe výrazů dotazů: Filtrování](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-filtering.md)  
  
-   [Příklady syntaxe výrazů dotazů: Řazení](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-ordering.md)  
  
-   [Příklady syntaxe výrazů dotazů: Agregační operátory](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-aggregate-operators.md)  
  
-   [Příklady syntaxe výrazů dotazů: Dělení](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-partitioning.md)  
  
-   [Příklady syntaxe výrazů dotazů: Operátory spojení](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-join-operators.md)  
  
-   [Příklady syntaxe výrazů dotazů: Operátory elementů](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-element-operators.md)  
  
-   [Příklady syntaxe výrazů dotazů: Seskupení](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-grouping.md)  
  
-   [Příklady syntaxe výrazů dotazů: Navigace v relacích](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expression-syntax-examples-navigating-relationships.md)  
  
### <a name="method-based-query-syntax"></a>Syntaxe dotazu na základě – metoda  
 Jiný způsob, jak vytvořit [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy je pomocí dotazů na základě metod. Syntaxe dotazu na základě metod je posloupnost přímá metoda volání metod operátor LINQ, předávání výrazy lambda jako parametry. Další informace najdete v tématu [výrazy Lambda](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md). Příklady, které ukazují, jak na základě metod syntaxí najdete v následujících tématech:  
  
-   [Příklady syntaxe dotazů založených na volání metody: Projekce](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-projection.md)  
  
-   [Příklady syntaxe dotazů založených na volání metody: Filtrování](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-filtering.md)  
  
-   [Příklady syntaxe dotazů založených na volání metody: Řazení](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-ordering.md)  
  
-   [Příklady syntaxe dotazů založených na volání metody: Agregační operátory](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-aggregate-operators.md)  
  
-   [Příklady syntaxe dotazů založených na volání metody: Dělení](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-partitioning.md)  
  
-   [Příklady syntaxe dotazů založených na volání metody: Převod](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-conversion.md)  
  
-   [Příklady syntaxe dotazů založených na volání metody: Operátory spojení](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-join-operators.md)  
  
-   [Příklady syntaxe dotazů založených na volání metody: Operátory elementů](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-element-operators.md)  
  
-   [Příklady syntaxe dotazů založených na volání metody: Seskupení](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-grouping.md)  
  
-   [Příklady syntaxe dotazů založených na volání metody: Navigace v relacích](../../../../../../docs/framework/data/adonet/ef/language-reference/method-based-query-syntax-examples-navigating-relationships.md)  
  
## <a name="see-also"></a>Viz také  
 [LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)  
 [Začínáme s dotazy LINQ v jazyce C#](~/docs/csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Začínáme s dotazy LINQ v jazyku Visual Basic](~/docs/visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Rozhraní Entity Framework možnosti sloučení a zkompilovat dotazy](http://go.microsoft.com/fwlink/?LinkId=199591)
