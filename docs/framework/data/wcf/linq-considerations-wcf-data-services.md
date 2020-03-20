---
title: Důležité informace linq (WCF datové služby)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ
- querying the data service [WCF Data Services]
- WCF Data Services, querying
ms.assetid: cc4ec9e9-348f-42a6-a78e-1cd40e370656
ms.openlocfilehash: 6c0cd7dcebb46b5408079848862ef4da1bb7f0a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174664"
---
# <a name="linq-considerations-wcf-data-services"></a>Důležité informace linq (WCF datové služby)
Toto téma obsahuje informace o způsobu, jakým jsou skládat a spouštěny dotazy LINQ při použití klienta WCF Data Services, a omezení použití LINQ k dotazování datové služby, která implementuje protokol OData (Open Data Protocol). Další informace o vytváření a provádění dotazů na datovou službu založenou na odatavce naleznete v [tématu Dotaz ování datové služby](querying-the-data-service-wcf-data-services.md).  
  
## <a name="composing-linq-queries"></a>Vytváření dotazů LINQ  
 LINQ umožňuje vytvářet dotazy proti kolekci objektů, <xref:System.Collections.Generic.IEnumerable%601>které implementuje . Dialogové okno **Přidat odkaz na službu** v sadě Visual Studio i nástroj DataSvcUtil.exe se používají ke generování <xref:System.Data.Services.Client.DataServiceContext>reprezentace služby OData jako třídy kontejneru entit, která dědí z , a také k objektům, které představují entity vrácené v informačních kanálech. Tyto nástroje také generovat vlastnosti na třídu kontejneru entity pro kolekce, které jsou vystaveny jako informační kanály službou. Každá z těchto vlastností třídy, která zapouzdřuje datovou službu, <xref:System.Data.Services.Client.DataServiceQuery%601>vrátí . Vzhledem <xref:System.Data.Services.Client.DataServiceQuery%601> k tomu, že třída implementuje <xref:System.Linq.IQueryable%601> rozhraní definované LINQ, můžete vytvořit linq dotaz proti informační kanály vystavené datové služby, které jsou přeloženy klientskou knihovnou do požadavku na dotaz URI, který je odeslán do datové služby při spuštění.  
  
> [!IMPORTANT]
> Sada dotazů, které lze vyjádřit v syntaxi LINQ, je širší než ty, které jsou povoleny v syntaxi IDENTIFIKÁTORURI, kterou používají datové služby OData. A <xref:System.NotSupportedException> je aktivována, když dotaz nelze mapovat na identifikátor URI v cílové datové službě. Další informace naleznete [v nepodporovaných metodách LINQ](linq-considerations-wcf-data-services.md#unsupportedMethods) v tomto tématu.  
  
 Následující příklad je dotaz LINQ, který vrací, `Orders` které mají náklady na dopravu vyšší než $30 a seřadí výsledky podle data expedice, počínaje nejnovějším datem expedice:  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqspecific)]
  
 Tento dotaz LINQ je přeložen do následujícího identifikátoru URI dotazu, který je spuštěn proti datové službě [quickstart](quickstart-wcf-data-services.md) založené na northwind:  
  
```http
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
 Obecnější informace o LINQ naleznete v [tématu Jazyk integrovaný dotaz (LINQ) - C#](../../../csharp/programming-guide/concepts/linq/index.md) nebo [jazykově integrovaný dotaz (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).  
  
 LINQ umožňuje vytvářet dotazy pomocí syntaxe deklarativního dotazu specifického pro jazyk, která je zobrazena v předchozím příkladu, a také pomocí sady metod dotazů označovaných jako standardní operátory dotazů. Ekvivalentní dotaz k předchozímu příkladu lze vytvořit pouze pomocí syntaxe založené na metodě, jak je znázorněno v následujícím příkladu:  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqexpressionspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqexpressionspecific)]
  
 Klient WCF Data Services je schopen přeložit oba druhy složených dotazů do identifikátoru URI dotazu a můžete rozšířit dotaz LINQ připojením metod dotazu k výrazu dotazu. Při skládání linq dotazů připojením syntaxe metody k <xref:System.Data.Services.Client.DataServiceQuery%601>výrazu dotazu nebo , operace jsou přidány do uri dotazu v pořadí, ve kterém jsou volány metody. To je ekvivalentní <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> volání metody pro přidání každé možnosti dotazu do identifikátoru URI dotazu.  
  
## <a name="executing-linq-queries"></a>Provádění dotazů LINQ  
 Některé metody dotazu LINQ, například <xref:System.Linq.Enumerable.First%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> nebo <xref:System.Linq.Enumerable.Single%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>, při připojení k dotazu, způsobit spuštění dotazu. Dotaz je také spuštěn, když jsou implicitně výčty `foreach` výsledků, například během smyčky `List` nebo při přiřazení dotazu ke kolekci. Další informace naleznete v [tématu Dotaz na datovou službu](querying-the-data-service-wcf-data-services.md).  
  
 Klient provede dotaz LINQ ve dvou částech. Kdykoli je to možné, výrazy LINQ v dotazu jsou nejprve vyhodnoceny na straně klienta a pak je generován dotaz založený na uri a odeslán datové službě pro vyhodnocení dat ve službě. Další informace naleznete v části [Klient versus spuštění serveru](querying-the-data-service-wcf-data-services.md#executingQueries) v [tématu Dotazování na datovou službu](querying-the-data-service-wcf-data-services.md).  
  
 Pokud dotaz LINQ nelze přeložit v identifikátoru URI kompatibilního s OData, je při pokusu o spuštění vyvolána výjimka. Další informace naleznete v [tématu Dotaz na datovou službu](querying-the-data-service-wcf-data-services.md).  
  
## <a name="linq-query-examples"></a>Příklady dotazů LINQ  
 Příklady v následujících částech ukazují druhy linq dotazů, které mohou být provedeny proti službě OData.  
  
<a name="filtering"></a>
### <a name="filtering"></a>Filtrování  
 Příklady dotazu LINQ v této části filtrují data v informačním kanálu vráceném službou.  
  
 Následující příklady jsou ekvivalentní dotazy, `Orders` které filtrují vrácené entity tak, aby byly vráceny pouze objednávky s náklady na dopravné vyšší než $30:  
  
- Použití syntaxe dotazu LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqwhereclausespecific)]
[!code-vb[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqwhereclausespecific)]
  
- Použití metod dotazu LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqwheremethodspecific)]
[!code-vb[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqwheremethodspecific)]
  
- Možnost řetězce `$filter` dotazu URI:  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitquerywheremethodspecific)]
[!code-vb[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitquerywheremethodspecific)]
  
 Všechny předchozí příklady jsou přeloženy do `http://localhost:12345/northwind.svc/Orders()?$filter=Freight gt 30M`identifikátoru URI dotazu: .  
  
<a name="sorting"></a>
### <a name="sorting"></a>Řazení  
 Následující příklady ukazují ekvivalentní dotazy, které seřadí vrácená data podle názvu společnosti a podle PSČ sestupně:  
  
- Použití syntaxe dotazu LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqorderbyclausespecific)]
[!code-vb[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqorderbyclausespecific)]
  
- Použití metod dotazu LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqorderbymethodspecific)]
[!code-vb[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqorderbymethodspecific)]
  
- Možnost řetězce `$orderby` dotazu URI):  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitqueryorderbymethodspecific)]
[!code-vb[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitqueryorderbymethodspecific)]
  
 Všechny předchozí příklady jsou přeloženy do `http://localhost:12345/northwind.svc/Customers()?$orderby=CompanyName,PostalCode desc`identifikátoru URI dotazu: .  
  
<a name="projection"></a>
### <a name="projection"></a>Projekce  
 Následující příklady ukazují ekvivalentní dotazy, které projekt `CustomerAddress` vrátil data do užšího typu:  
  
- Použití syntaxe dotazu LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqselectclausespecific)]
[!code-vb[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqselectclausespecific)]
  
- Použití metod dotazu LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqselectmethodspecific)]
[!code-vb[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqselectmethodspecific)]

> [!NOTE]
> Možnost `$select` dotazu nelze přidat do identifikátoru <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> URI dotazu pomocí metody. Doporučujeme použít metodu <xref:System.Linq.Enumerable.Select%2A> LINQ, aby klient `$select` vygeneroval možnost dotazu v identifikátoru URI požadavku.  
  
 Oba předchozí příklady jsou přeloženy do `"http://localhost:12345/northwind.svc/Customers()?$filter=Country eq 'GerGerm'&$select=CustomerID,Address,City,Region,PostalCode,Country"`identifikátoru URI dotazu: .  
  
<a name="paging"></a>
### <a name="client-paging"></a>Stránkování klienta  
 Následující příklady ukazují ekvivalentní dotazy, které požadují stránku seřazených entit objednávky, která obsahuje 25 objednávek, přeskočení prvních 50 objednávek:  
  
- Použití metod dotazu na dotaz LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqskiptakemethodspecific)]
[!code-vb[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqskiptakemethodspecific)]
  
- Řetězec `$skip` a `$top` možnosti dotazu URI):  
  
[!code-csharp[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitqueryskiptakemethodspecific)]
[!code-vb[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitqueryskiptakemethodspecific)]
  
 Oba předchozí příklady jsou přeloženy do `http://localhost:12345/northwind.svc/Orders()?$orderby=OrderDate desc&$skip=50&$top=25`identifikátoru URI dotazu: .  
  
<a name="expand"></a>
### <a name="expand"></a>Rozbalit  
 Při dotazování datové služby OData můžete požadovat, aby entity související s entitou, na kterou dotaz cílí dotaz, byly zahrnuty do vráceného informačního kanálu. Metoda <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> je volána <xref:System.Data.Services.Client.DataServiceQuery%601> na sadu entit, na kterou se dotaz LINQ `path` zaměřuje, přičemž jako parametr je zadán název sady souvisejících entit. Další informace naleznete v [tématu Loading Odložené obsah](loading-deferred-content-wcf-data-services.md).  
  
 Následující příklady ukazují ekvivalentní způsoby použití <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> metody v dotazu:  
  
- V syntaxi dotazu LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryexpandspecific)]
[!code-vb[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryexpandspecific)]  
  
- S metodami dotazu LINQ:  

[!code-csharp[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryexpandmethodspecific)]
[!code-vb[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryexpandmethodspecific)]

 Oba předchozí příklady jsou přeloženy do `http://localhost:12345/northwind.svc/Orders()?$filter=CustomerID eq 'ALFKI'&$expand=Order_Details`identifikátoru URI dotazu: .  
  
<a name="unsupportedMethods"></a>
## <a name="unsupported-linq-methods"></a>Nepodporované metody LINQ  
 Následující tabulka obsahuje třídy LINQ metody nejsou podporovány a nemohou být zahrnuty do dotazu provedeného proti službě OData:  
  
|Typ operace|Nepodporovaná metoda|  
|--------------------|------------------------|  
|Nastavit operátory|Všechny operátory sady nejsou <xref:System.Data.Services.Client.DataServiceQuery%601>podporovány proti , který zahrnoval následující:<br /><br /> -   <xref:System.Linq.Enumerable.All%2A><br />-   <xref:System.Linq.Enumerable.Any%2A><br />-   <xref:System.Linq.Enumerable.Concat%2A><br />-   <xref:System.Linq.Enumerable.DefaultIfEmpty%2A><br />-   <xref:System.Linq.Enumerable.Distinct%2A><br />-   <xref:System.Linq.Enumerable.Except%2A><br />-   <xref:System.Linq.Enumerable.Intersect%2A><br />-   <xref:System.Linq.Enumerable.Union%2A><br />-   <xref:System.Linq.Enumerable.Zip%2A>|  
|Objednávání operátorů|Následující operátory řazení, které vyžadují, <xref:System.Collections.Generic.IComparer%601> nejsou podporovány <xref:System.Data.Services.Client.DataServiceQuery%601>proti :<br /><br /> -   <xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29>|  
|Projekční a filtrační operátory|Následující operátory projekce a filtrování, které přijímají poziční argument, nejsou podporovány <xref:System.Data.Services.Client.DataServiceQuery%601>proti :<br /><br /> -   <xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2C%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Where%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29>|  
|Seskupování operátorů|Všechny operátory seskupení nejsou <xref:System.Data.Services.Client.DataServiceQuery%601>podporovány proti a , včetně následujících:<br /><br /> -   <xref:System.Linq.Enumerable.GroupBy%2A><br />-   <xref:System.Linq.Enumerable.GroupJoin%2A><br /><br /> Operace seskupování musí být provedeny na straně klienta.|  
|Agregované operátory|Všechny agregační operace <xref:System.Data.Services.Client.DataServiceQuery%601>nejsou podporovány proti a , včetně následujících:<br /><br /> -   <xref:System.Linq.Enumerable.Aggregate%2A><br />-   <xref:System.Linq.Enumerable.Average%2A><br />-   <xref:System.Linq.Enumerable.Count%2A><br />-   <xref:System.Linq.Enumerable.LongCount%2A><br />-   <xref:System.Linq.Enumerable.Max%2A><br />-   <xref:System.Linq.Enumerable.Min%2A><br />-   <xref:System.Linq.Enumerable.Sum%2A><br /><br /> Agregační operace musí být provedeny na straně klienta nebo musí být zapouzdřeny operací služby.|  
|Operátory stránkování|Následující operátory stránkování nejsou <xref:System.Data.Services.Client.DataServiceQuery%601>podporovány proti :<br /><br /> -   <xref:System.Linq.Enumerable.ElementAt%2A><br />-   <xref:System.Linq.Enumerable.Last%2A><br />-   <xref:System.Linq.Enumerable.LastOrDefault%2A><br />-   <xref:System.Linq.Enumerable.SkipWhile%2A><br />-   <xref:System.Linq.Enumerable.TakeWhile%2A><br/><br/>**Poznámka:**  Paging operátory, které jsou provedeny na prázdnou sekvenci vrátí null.|  
|Ostatní operátoři|Následující operátory také nejsou <xref:System.Data.Services.Client.DataServiceQuery%601>podporovány proti :<br /><br /> - <xref:System.Linq.Enumerable.Empty%2A><br />- <xref:System.Linq.Enumerable.Range%2A><br />- <xref:System.Linq.Enumerable.Repeat%2A><br />- <xref:System.Linq.Enumerable.ToDictionary%2A><br />- <xref:System.Linq.Enumerable.ToLookup%2A>|  
  
<a name="supportedExpressions"></a>
## <a name="supported-expression-functions"></a>Podporované funkce výrazu  
 Následující metody a vlastnosti clr (common-language language runtime) jsou podporovány, protože je lze přeložit do výrazu dotazu pro zahrnutí do identifikátoru URI požadavku do služby OData:  
  
|<xref:System.String>Členské|Podporovaná funkce OData|  
|-----------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.String.Concat%28System.String%2CSystem.String%29>|`string concat(string p0, string p1)`|  
|<xref:System.String.Contains%28System.String%29>|`bool substringof(string p0, string p1)`|  
|<xref:System.String.EndsWith%28System.String%29>|`bool endswith(string p0, string p1)`|  
|<xref:System.String.IndexOf%28System.String%2CSystem.Int32%29>|`int indexof(string p0, string p1)`|  
|<xref:System.String.Length>|`int length(string p0)`|  
|<xref:System.String.Replace%28System.String%2CSystem.String%29>|`string replace(string p0, string find, string replace)`|  
|<xref:System.String.Substring%28System.Int32%29>|`string substring(string p0, int pos)`|  
|<xref:System.String.Substring%28System.Int32%2CSystem.Int32%29>|`string substring(string p0, int pos, int length)`|  
|<xref:System.String.ToLower>|`string tolower(string p0)`|  
|<xref:System.String.ToUpper>|`string toupper(string p0)`|  
|<xref:System.String.Trim>|`string trim(string p0)`|  
  
|<xref:System.DateTime>Člen<sup>1</sup>|Podporovaná funkce OData|  
|-------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Day>|`int day(DateTime p0)`|  
|<xref:System.DateTime.Hour>|`int hour(DateTime p0)`|  
|<xref:System.DateTime.Minute>|`int minute(DateTime p0)`|  
|<xref:System.DateTime.Month>|`int month(DateTime p0)`|  
|<xref:System.DateTime.Second>|`int second(DateTime p0)`|  
|<xref:System.DateTime.Year>|`int year(DateTime p0)`|  
  
 <sup>1.</sup> Ekvivalentní vlastnosti data <xref:Microsoft.VisualBasic.DateAndTime?displayProperty=nameWithType> a <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> času a metody v jazyce Visual Basic jsou také podporovány.  
  
|<xref:System.Math>Členské|Podporovaná funkce OData|  
|---------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Math.Ceiling%28System.Decimal%29>|`decimal ceiling(decimal p0)`|  
|<xref:System.Math.Ceiling%28System.Double%29>|`double ceiling(double p0)`|  
|<xref:System.Math.Floor%28System.Decimal%29>|`decimal floor(decimal p0)`|  
|<xref:System.Math.Floor%28System.Double%29>|`double floor(double p0)`|  
|<xref:System.Math.Round%28System.Decimal%29>|`decimal round(decimal p0)`|  
|<xref:System.Math.Round%28System.Double%29>|`double round(double p0)`|  
  
|<xref:System.Linq.Expressions.Expression>Členské|Podporovaná funkce OData|  
|---------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Linq.Expressions.Expression.TypeIs%28System.Linq.Expressions.Expression%2CSystem.Type%29>|`bool isof(type p0)`|  
  
 Klient může být také schopen vyhodnotit další funkce CLR na straně klienta. A <xref:System.NotSupportedException> je aktivována pro jakýkoli výraz, který nelze vyhodnotit na straně klienta a nelze převést na platný požadavek URI pro vyhodnocení na serveru.  
  
## <a name="see-also"></a>Viz také

- [Dotazování v datové službě](querying-the-data-service-wcf-data-services.md)
- [Projekce dotazů](query-projections-wcf-data-services.md)
- [Materializace objektů](object-materialization-wcf-data-services.md)
- [OData: Konvence identifikátorů URI](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/)
