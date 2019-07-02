---
title: Dotazy v LINQ to DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c1a78fa8-9f0c-40bc-a372-5575a48708fe
ms.openlocfilehash: f8fabd38ec49070bc588196b38ec64942feab93f
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504706"
---
# <a name="queries-in-linq-to-dataset"></a>Dotazy v LINQ to DataSet
Dotaz je výraz, který načítá data z datového zdroje. Dotazy jsou obvykle vyjádřeny v specializovaném dotazovacím jazyce, jako je například SQL pro relační databáze a XQuery pro XML. Proto vývojáři měli získat nový dotazovací jazyk pro každý typ zdroje dat nebo formátu dat, který dotazy. [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] nabízí jednodušší a konzistentní model pro práci s daty napříč různými druhy datových zdrojů a formátů. V [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] dotazu, vždy pracujete s programovacích objektech.  
  
 A [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] dotazu operace se skládá ze tří akcí: získání datového zdroje nebo zdrojů, vytvořte dotaz a spusťte dotaz.  
  
 Zdroje dat, které implementují <xref:System.Collections.Generic.IEnumerable%601> obecné rozhraní může být dotázán pomocí [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]. Volání <xref:System.Data.DataTableExtensions.AsEnumerable%2A> na <xref:System.Data.DataTable> vrátí objekt, který implementuje obecné <xref:System.Collections.Generic.IEnumerable%601> rozhraní, které slouží jako zdroj dat pro funkci LINQ do datové sady dotazů.  
  
 V dotazu je zadat přesně informace, které chcete načíst ze zdroje dat. Dotaz můžete také určit, jak tyto informace by měl být seřazeny, seskupeny a tvarovány dříve, než se vrátí. V [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], dotaz je uložen v proměnné. Pokud dotaz byl navržen k vrácení sekvence hodnot, proměnná dotazu sama musí být typu výčtu. Tato proměnná dotazu neprovede žádnou akci a nevrátí žádná data; ukládá pouze informace o dotazu. Po vytvoření dotazu je třeba spustit tento dotaz pro načtení žádná data.  
  
 V dotazu, který vrací posloupnost hodnot že proměnné dotazu samy nikdy neobsahují výsledky dotazu a ukládá pouze příkazy dotazu. Provádění dotazu je odloženo, dokud proměnná dotazu je procházena `foreach` nebo `For Each` smyčky. Tento postup se nazývá *odložené provedení*; to znamená, dotaz spuštěn nějakou dobu, po dotazu je vytvořený. To znamená, že můžete spustit dotaz tak často, jak chcete. To je užitečné, pokud například máte databázi, která se aktualizuje jiné aplikace. Ve vaší aplikaci můžete vytvořit dotaz pro načtení nejnovějších informací a opakovaně spustit dotaz, vrácení aktualizované informace pokaždé, když.  
  
 Na rozdíl od odložené dotazy, které vracejí posloupnost hodnot, jsou dotazy, které vracejí hodnotu singleton spuštěna ihned. Tady je několik příkladů dotazů singleton <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Average%2A>, a <xref:System.Linq.Enumerable.First%2A>. Provádějí se okamžitě vzhledem k tomu, že výsledky dotazu jsou nutné k výpočtu jednoznačný výsledek. Například pokud chcete zjistit průměr z výsledků dotazu dotaz musí provést tak, aby průměrované funkce obsahuje vstupní data pro práci s. Můžete také použít <xref:System.Linq.Enumerable.ToList%2A> nebo <xref:System.Linq.Enumerable.ToArray%2A> metod v dotazu, chcete-li vynutit okamžité spuštění dotazu, který nevytváří hodnotu singleton. Tyto postupy, chcete-li vynutit okamžité spuštění může být užitečné, pokud chcete výsledky dotazu do mezipaměti.
  
## <a name="queries"></a>Dotazy  
 Se dají formulovat technologie LINQ to DataSet dotazy ve dvou různých syntaxí: výraz syntaxe využívající dotazy a syntaxe dotazů založených na volání metody.  
  
### <a name="query-expression-syntax"></a>Syntaxe výrazu dotazu  
 Výrazy dotazu představují dotaz deklarativní syntaxe. Tato syntaxe umožňuje vývojářům psát dotazy v jazyce C# nebo Visual Basic v ve formátu podobném SQL. Pomocí syntaxe výrazu dotazu, můžete provádět, dokonce i složité filtrování, řazení a seskupení operací u zdrojů dat s minimem kódu. Další informace najdete v tématu [LINQ – výrazy dotazů](../../../csharp/linq/index.md#query-expression-overview) a [základní operace dotazů (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).
  
 Syntaxe výrazu dotazu je nového v jazyce C# 3.0 a [!INCLUDE[vb_orcas_long](../../../../includes/vb-orcas-long-md.md)]. Rozhraní .NET Framework common language runtime (CLR) však nelze číst syntaxe výrazu dotazu, samotného. V době kompilace, proto – výrazy dotazů jsou přeloženy na něco, co CLR chápe: volání metody. Tyto metody jsou označovány jako *standardních operátorů pro dotazování*. Jako vývojář máte možnost volání přímo pomocí syntaxe metody, namísto použití syntaxe dotazu. Další informace najdete v tématu [syntaxi dotazů a syntaxe využívající metody v jazyce LINQ](~/docs/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md). Další informace o standardních operátorů pro dotazování, naleznete v tématu [přehled standardních operátorů dotazu](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
 Následující příklad používá <xref:System.Linq.Enumerable.Select%2A> vrátit všechny řádky z `Product` tabulky a zobrazení názvů produktů.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="method-based-query-syntax"></a>Syntaxe dotazů založených na volání metody  
 Druhý způsob formulovat LINQ dotazy na datové sady je pomocí dotazů založených na volání metody. Syntaxe dotazů založených na volání metody je posloupnost volání přímé metody [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] metody operátoru předávání výrazy lambda jako parametry. Další informace najdete v tématu [výrazy Lambda](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Tento příklad používá <xref:System.Linq.Enumerable.Select%2A> vrátit všechny řádky z `Product` a zobrazení názvů produktů.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
## <a name="composing-queries"></a>Skládání dotazů  
 Jak je uvedeno výše v tomto tématu, proměnná dotazu sama se uchovávají pouze příkazy dotazu při dotazu slouží k vrácení sekvence hodnot. Pokud dotaz neobsahuje metodu, která způsobí, že okamžité spuštění, aktuální provádění dotazu je odloženo, dokud neprovedete iteraci v proměnné dotazu v `foreach` nebo `For Each` smyčky. Odložené provedení umožňuje více dotazů a nelze jej zkombinovat nebo dotaz, který rozšířit. Jakmile se rozšíří dotazu, dojde k úpravě zahrnout nové operace a konečný výsledek spuštění bude odrážet provedené změny. V následujícím příkladu první dotaz vrátí všechny produkty. Druhý dotaz rozšíří první pomocí `Where` vrátit všechny produkty o velikosti "L":  
  
 [!code-csharp[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#composing)]
 [!code-vb[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#composing)]  
  
 Poté, co provedl dotaz, může obsahovat žádné další dotazy a všech dalších dotazů použije v paměťově [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] operátory. Provádění dotazu se vyskytnou při iteraci v proměnné dotazu v `foreach` nebo `For Each` příkazu nebo volání na jednu z [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] operátory převodu, které způsobí okamžité spuštění. Tyto operátory patří: <xref:System.Linq.Enumerable.ToList%2A>, <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToLookup%2A>, a <xref:System.Linq.Enumerable.ToDictionary%2A>.  
  
 V následujícím příkladu první dotaz vrátí všechny produkty, které jsou seřazené podle ceníku. <xref:System.Linq.Enumerable.ToArray%2A> Metoda se používá k vynucení provedení okamžitého dotazu:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray2)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray2)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
- [Dotazy na datové sady](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [Začínáme s dotazy LINQ v jazyce C#](~/docs/csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Začínáme s dotazy LINQ v jazyce Visual Basic](~/docs/visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
