---
title: Dotazy v LINQ na DataSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c1a78fa8-9f0c-40bc-a372-5575a48708fe
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 7e07da38f7a75226d48ef84cc8d2dafd48f6e795
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="queries-in-linq-to-dataset"></a>Dotazy v LINQ na DataSet
Dotaz je výraz, který načte data z datového zdroje. Dotazy jsou obvykle vyjádřeny v specializované dotazovací jazyk, například SQL pro relační databáze a XQuery pro formát XML. Vývojáři mají proto byl Další informace o nový jazyk dotazu pro každý typ zdroje dat nebo formát dat, která dotazy. [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]nabízí jednodušší a konzistentní model pro práci s daty mezi různé druhy zdrojů dat a formáty. V [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] dotaz, vždy pracujete s programováním objekty.  
  
 A [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] dotazu operace se skládá ze tří akcí: získat zdroj dat nebo zdroje, vytvořte dotaz a provést dotaz.  
  
 Zdroje dat, které implementují <xref:System.Collections.Generic.IEnumerable%601> obecné rozhraní můžete vyhledávat pomocí [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]. Volání metody <xref:System.Data.DataTableExtensions.AsEnumerable%2A> na <xref:System.Data.DataTable> vrátí objekt, který implementuje obecné <xref:System.Collections.Generic.IEnumerable%601> rozhraní, které slouží jako zdroj dat pro [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazy.  
  
 V dotazu je zadat přesně informace, které chcete načíst z datového zdroje. Dotaz můžete také určit, jak tyto informace by měl být seřazeny, seskupené a ve tvaru před vrácením. V [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], dotazu je uložené v proměnné. Pokud dotaz je navržená tak, že se vrátíte pořadí hodnot, proměnné v dotazu sám sebe musí být typu vyčíslitelná. Tato proměnná dotazu neprovede žádnou akci a vrátí žádná data; ukládá jenom informace o dotazu. Po vytvoření dotazu je třeba spustit tento dotaz pro načtení žádná data.  
  
 V dotazu, který vrací pořadí hodnot proměnné v dotazu samotné nikdy obsahuje výsledky dotazu a ukládá jenom příkazy dotazu. Spuštění dotazu je odložení, dokud proměnnou dotazu je vstupní přes `foreach` nebo `For Each` smyčky. To se označuje jako *odložené spouštění*; to znamená, dotaz provádění dojde k delší dobu, po dotazu je vytvořený. To znamená, že je spuštěn dotaz tak často, jak chcete. To je užitečné, pokud například máte databázi, která se právě aktualizuje jiné aplikace. V aplikaci můžete vytvořit dotaz, který získat nejnovější informace a opakovaně spuštění dotazu a vrácení aktualizované informace o každém.  
  
 Na rozdíl od odložené dotazy, které vrací pořadí hodnot, jsou okamžitě provede dotazů, které vrátí hodnotu typu singleton. Některé příklady dotazů singleton <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Average%2A>, a <xref:System.Linq.Enumerable.First%2A>. Tyto spustit okamžitě protože výsledky dotazu jsou potřeba k výpočtu výsledek typu singleton. Například a hledat tak průměr výsledky dotazu dotaz musí provést tak, aby průměrný funkce obsahuje vstupní data pro práci s. Můžete také <xref:System.Linq.Enumerable.ToList%2A> nebo <xref:System.Linq.Enumerable.ToArray%2A> metody na dotazu chcete vynutit okamžitou provádění dotazu, který nevytváří hodnotu singleton. Tyto postupy, chcete-li vynutit okamžitou provádění může být užitečné, pokud chcete pro ukládání do mezipaměti výsledků dotazu. Další informace o spuštění dotazu odložené a okamžitou najdete v tématu [Začínáme s dotazy LINQ](http://msdn.microsoft.com/library/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9).  
  
## <a name="queries"></a>Dotazy  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]dotazy můžete ve dvou různých syntaxí úpravě: výraz syntaxe využívající dotazy a syntaxe dotazu na základě metod.  
  
### <a name="query-expression-syntax"></a>Syntaxe výrazu dotazu  
 Výrazy dotazů jsou syntaxe deklarativní dotazu. Tuto syntaxi umožňuje vývojáři psát dotazy v C# nebo Visual Basic ve formátu, podobně jako SQL. Pomocí syntaxe výrazu dotazu, můžete provést i komplexní filtrování, řazení a seskupování operací na zdroje dat s minimálním kódu. Další informace najdete v tématu [LINQ – výrazy dotazů](http://msdn.microsoft.com/library/40638f19-fb46-4d26-a2d9-a383b48f5ed4) a [základní operace dotazů (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/linq/basic-query-operations.md).  
  
 Syntaxe výrazu dotazu je nové v C# 3.0 a [!INCLUDE[vb_orcas_long](../../../../includes/vb-orcas-long-md.md)]. Ale [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] modul common language runtime (CLR) nelze přečíst syntaxe výrazu dotazu, sám sebe. Při kompilaci, tedy výrazy dotazů jsou převedeny na něco, co pochopit modulu CLR: volání metody. Tyto metody jsou označovány jako *standardní operátory dotazu*. Jako vývojář máte možnost volání je přímo pomocí syntaxe využívající metody, místo použití syntaxe dotazu. Další informace najdete v tématu [syntaxe dotazů a syntaxe využívající metody v technologii LINQ](~/docs/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md). Další informace o tom, jak používat standardní operátory dotazu najdete v tématu [NOT IN sestavení: Obecné LINQ Průvodce programováním](http://msdn.microsoft.com/library/609c7a6b-cbdd-429d-99f3-78d13d3bc049).  
  
 Následující příklad používá <xref:System.Linq.Enumerable.Select%2A> k vrátí všechny řádky z `Product` tabulky a zobrazení názvy produktů.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="method-based-query-syntax"></a>Syntaxe dotazu na základě – metoda  
 Druhý způsob formulovali [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazy je pomocí dotazů na základě metod. Syntaxe dotazu na základě metod je posloupnost volání přímá metoda [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] operátor metody, předávání výrazy lambda jako parametry. Další informace najdete v tématu [výrazy Lambda](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Tento příklad používá <xref:System.Linq.Enumerable.Select%2A> k vrátí všechny řádky z `Product` a zobrazit názvy produktů.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
## <a name="composing-queries"></a>Skládání dotazy  
 Jak je uvedeno výše v tomto tématu, proměnné v dotazu samotné pouze ukládá příkazů dotazů při dotazu slouží k vrácení pořadí hodnot. Pokud dotaz neobsahuje metodu, která způsobí okamžité spuštění, je skutečný spuštění dotazu odloženo, dokud iterace v proměnné dotazu v `foreach` nebo `For Each` smyčky. Odložené provedení umožňuje více dotazů a nelze jej zkombinovat nebo dotaz, který rozšířit. Jakmile se rozšíří dotazu, se mění zahrnout nových operací a případné provádění se projeví změny. V následujícím příkladu první dotaz vrátí všechny produkty. Druhý dotazu rozšiřuje první pomocí `Where` vrátit všechny produkty velikosti "L":  
  
 [!code-csharp[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#composing)]
 [!code-vb[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#composing)]  
  
 Po provedení dotazu, může být složené žádné další dotazy a všechny následné dotazy budou používat v paměťově [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] operátory. Při provádění dotazu se stane, když iterace v proměnné dotazu v `foreach` nebo `For Each` prohlášení, nebo volání mezi [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] operátory převodu, které způsobí okamžité spuštění. Tyto operátory patří: <xref:System.Linq.Enumerable.ToList%2A>, <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToLookup%2A>, a <xref:System.Linq.Enumerable.ToDictionary%2A>.  
  
 V následujícím příkladu první dotaz vrátí všechny produkty, které jsou seřazené podle seznamu ceny. <xref:System.Linq.Enumerable.ToArray%2A> Metoda slouží k vynucení spuštění okamžitou dotazu:  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray2)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray2)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
 [Dotazy na datové sady](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [Začínáme s dotazy LINQ v jazyce C#](~/docs/csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Začínáme s dotazy LINQ v jazyku Visual Basic](~/docs/visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
