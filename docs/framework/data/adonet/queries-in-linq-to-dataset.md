---
title: Dotazy v LINQ to DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c1a78fa8-9f0c-40bc-a372-5575a48708fe
ms.openlocfilehash: f6677e894e09b41e1f406d6b6485abf4168b5d6e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946262"
---
# <a name="queries-in-linq-to-dataset"></a>Dotazy v LINQ to DataSet
Dotaz je výraz, který načítá data ze zdroje dat. Dotazy jsou obvykle vyjádřené ve specializovaném dotazovacím jazyce, jako je SQL pro relační databáze a XQuery pro XML. Proto se vývojářům musel naučit nový dotazovací jazyk pro každý typ zdroje dat nebo formátu dat, který dotazuje. [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]nabízí jednodušší a konzistentní model pro práci s daty napříč různými druhy datových zdrojů a formátů. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] V dotazu vždy pracujete s programováním objektů.  
  
 Operace [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] dotazu se skládá ze tří akcí: získat zdroje dat nebo zdroje, vytvořit dotaz a spustit dotaz.  
  
 Zdroje dat, které implementují <xref:System.Collections.Generic.IEnumerable%601> obecné rozhraní, lze dotazovat prostřednictvím. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] Volání <xref:System.Data.DataTableExtensions.AsEnumerable%2A> funkce vrátí objekt, který implementuje obecné <xref:System.Collections.Generic.IEnumerable%601> rozhraní, které slouží jako zdroj dat pro LINQ to DataSet dotazy. <xref:System.Data.DataTable>  
  
 V dotazu zadáte přesně informace, které chcete načíst ze zdroje dat. Dotaz může také určit, jak se mají tyto informace seřadit, seskupit a tvarovat před tím, než se vrátí. V [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]nástroji je dotaz uložen v proměnné. Pokud je dotaz navržen tak, aby vracel sekvenci hodnot, proměnná dotazu musí být vyčíslitelného typu. Tato proměnná dotazu neprovádí žádnou akci a nevrátí žádná data. ukládá pouze informace o dotazu. Po vytvoření dotazu musíte spustit dotaz, aby se načetla nějaká data.  
  
 V dotazu, který vrací sekvenci hodnot, samotná proměnná dotazu nikdy nedrží výsledky dotazu a ukládá pouze příkazy dotazu. Provedení dotazu je odloženo, dokud se proměnná dotazu neopakuje v `foreach` rámci smyčky or. `For Each` Tato operace se nazývá *odložené provedení*; To znamená, že provádění dotazů probíhá určitou dobu po sestavení dotazu. To znamená, že můžete spustit dotaz tak často, jak chcete. To je užitečné, když například máte databázi, která je aktualizována jinými aplikacemi. V aplikaci můžete vytvořit dotaz, který načte nejnovější informace a opakovaně spustí dotaz, a to tak, že se aktualizované informace pokaždé vrátí.  
  
 Na rozdíl od odložených dotazů, které vracejí sekvenci hodnot, se okamžitě spustí dotazy, které vracejí hodnotu typu singleton. Příklady dotazů typu Singleton <xref:System.Linq.Enumerable.Count%2A>jsou, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Average%2A>a <xref:System.Linq.Enumerable.First%2A>. Provede se okamžitě, protože výsledky dotazu se vyžadují k výpočtu typu singleton. Například aby bylo možné najít průměr výsledků dotazu, musí být proveden dotaz, aby funkce průměrně fungovala se vstupními daty. Můžete také použít <xref:System.Linq.Enumerable.ToList%2A> metody nebo <xref:System.Linq.Enumerable.ToArray%2A> pro dotaz k vynucení okamžitého provedení dotazu, který nevytváří hodnotu typu singleton. Tyto techniky pro vynucení okamžitého provedení mohou být užitečné, pokud chcete výsledky dotazu ukládat do mezipaměti.
  
## <a name="queries"></a>Dotazy  
 Dotazy LINQ to DataSet lze formulovat ve dvou různých syntaxech: Syntaxe výrazů dotazů a syntaxe dotazů založených na metodách.  
  
### <a name="query-expression-syntax"></a>Syntaxe výrazu dotazu  
 Výrazy dotazů jsou deklarativní syntaxí dotazu. Tato syntaxe umožňuje vývojářům psát dotazy v C# nebo Visual Basic ve formátu PODOBNÉm jazyku SQL. Pomocí syntaxe výrazu dotazu můžete provádět i složité filtrování, řazení a seskupování operací se zdroji dat s minimálním kódem. Další informace naleznete v tématu [výrazy dotazů LINQ](../../../csharp/linq/index.md#query-expression-overview) a [základní operace dotazů (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).
  
 .NET Framework Common Language Runtime (CLR) nemůže přečíst samotný syntax výrazu dotazu. Proto v době kompilace jsou výrazy dotazu přeloženy na něco, co aplikace CLR rozumí: volání metody. Tyto metody jsou označovány jako *standardní operátory dotazu*. Jako vývojář máte možnost je volat přímo pomocí syntaxe metody namísto použití syntaxe dotazu. Další informace naleznete v tématu [syntaxe dotazu a syntaxe metody v jazyce LINQ](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md). Další informace o standardních operátorech dotazu najdete v tématu [Přehled standardních operátorů dotazů](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
 Následující příklad používá <xref:System.Linq.Enumerable.Select%2A> k vrácení všech řádků z `Product` tabulky a zobrazení názvů produktů.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="method-based-query-syntax"></a>Syntaxe dotazů založená na metodách  
 Druhý způsob, jak formulovat LINQ to DataSet dotazy, je použití dotazů založených na metodách. Syntaxe dotazu založená na metodách je sekvence volání přímých metod na [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] metody operátoru a předávání výrazů lambda jako parametrů. Další informace naleznete v tématu [lambda výrazy](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Tento příklad používá <xref:System.Linq.Enumerable.Select%2A> k vrácení všech řádků ze `Product` a zobrazení názvů produktů.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
## <a name="composing-queries"></a>Vytváření dotazů  
 Jak bylo zmíněno výše v tomto tématu, proměnná dotazu sama ukládá pouze příkazy dotazu, pokud je dotaz navržen tak, aby vrátil sekvenci hodnot. Pokud dotaz neobsahuje metodu, která způsobí okamžité provedení, je skutečné provedení dotazu odloženo, dokud neprovedete iteraci nad proměnnou dotazu v rámci `foreach` smyčky nebo. `For Each` Odložené spouštění umožňuje kombinovat více dotazů nebo dotaz, který se má rozšířit. Když je dotaz rozšířený, je upravený tak, aby zahrnoval nové operace, a konečné spuštění projeví změny. V následujícím příkladu první dotaz vrátí všechny produkty. Druhý dotaz rozšiřuje první pomocí `Where` a vrátí všechny produkty velikosti "L":  
  
 [!code-csharp[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#composing)]
 [!code-vb[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#composing)]  
  
 Po provedení dotazu nelze sestavit žádné další dotazy a všechny následné dotazy budou používat operátory v paměti [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] . K provedení dotazu dojde při iteraci nad proměnnou dotazu v `foreach` příkazu nebo `For Each` nebo [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] voláním jednoho z operátorů převodu, které způsobují okamžité provedení. Tyto operátory zahrnují následující <xref:System.Linq.Enumerable.ToList%2A>:, <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToLookup%2A> <xref:System.Linq.Enumerable.ToDictionary%2A>a.  
  
 V následujícím příkladu vrátí první dotaz všechny produkty seřazené podle ceny seznamu. <xref:System.Linq.Enumerable.ToArray%2A> Metoda se používá k vynucení okamžitého provedení dotazu:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray2)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray2)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
- [Dotazy na datové sady](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [Začínáme s dotazy LINQ v jazyce C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Začínáme pomocí LINQ v Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
