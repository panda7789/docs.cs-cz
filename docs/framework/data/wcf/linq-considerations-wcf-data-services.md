---
title: Aspekty LINQ (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ
- querying the data service [WCF Data Services]
- WCF Data Services, querying
ms.assetid: cc4ec9e9-348f-42a6-a78e-1cd40e370656
ms.openlocfilehash: 92b3444f81f00ee709c22836126073d342c6fa05
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43394637"
---
# <a name="linq-considerations-wcf-data-services"></a>Aspekty LINQ (WCF Data Services)
Toto téma obsahuje informace o způsobu, jakým skládá a spustí se, když používáte dotazů LINQ, který [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klienta a omezeními pomocí jazyka LINQ k datové služby, který implementuje dotazování [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]. Další informace o vytváření a spouštění dotazů vůči [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]– na základě dat služby, najdete v článku [dotazování v datové službě](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
## <a name="composing-linq-queries"></a>Vytváření dotazů LINQ  
 LINQ umožňuje vytvořit dotazy na kolekce objektů, který implementuje <xref:System.Collections.Generic.IEnumerable%601>. Oba **přidat odkaz na službu** dialogové okno v sadě Visual Studio a nástroj DataSvcUtil.exe slouží ke generování reprezentace [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] formou třídu kontejneru entity, která dědí z <xref:System.Data.Services.Client.DataServiceContext>, stejně jako objekty, které představují entity, které vrátil v informačních kanálech. Tyto nástroje také generovat vlastnosti ve třídě kontejneru entity pro kolekce, které jsou vystaveny jako k datovým kanálům služby. Každá z těchto vlastností třídy, která zapouzdřuje návratový datové služby <xref:System.Data.Services.Client.DataServiceQuery%601>. Protože <xref:System.Data.Services.Client.DataServiceQuery%601> implementuje třída <xref:System.Linq.IQueryable%601> rozhraní určené LINQ, můžete vytvořit dotaz LINQ na informační kanály vystavené datové služby, které jsou přeloženy knihovnou klienta do dotazu žádosti o identifikátor URI, který je odeslána do služby data pro spuštění.  
  
> [!IMPORTANT]
>  Je širší než ty, které povolené v syntaxe identifikátoru URI, který používá sadu dotazů v syntaxi LINQ anyAttribute [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] datové služby. A <xref:System.NotSupportedException> se vyvolá, když dotaz nelze namapovat na identifikátor URI v cílové datové služby. Další informace najdete v tématu [nepodporované metody LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md#unsupportedMethods) v tomto tématu.  
  
 V následujícím příkladu je dotaz LINQ, který vrátí `Orders` , který se účtuje freight z více než 30 USD a řadí výsledky podle data, přesouvání, počínaje nejnovější termín:  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinqspecific)]      
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinqspecific)]    
  
 Tento dotaz LINQ, je přeložen do následujícího dotazu identifikátoru URI, který se provede na základě Northwind [rychlý Start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) datové služby:  
  
```  
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
 Další obecné informace o dotazech technologie LINQ, naleznete v tématu [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).  
  
 LINQ umožňuje vytváření dotazů s použitím obou specifické pro jazyk deklarativní syntaxe dotazu, je znázorněno v předchozím příkladu také sadu metod dotazu označované jako standardní operátory dotazu. Ekvivalentní dotaz v předchozím příkladu se může skládat jenom s syntaxí založených na volání metody, jak je znázorněno v následujícím příkladu:  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinqexpressionspecific)]      
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinqexpressionspecific)]    
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klienta se bude moct přeložit oba druhy složené dotazy do identifikátoru URI dotazu a dotaz LINQ můžete rozšířit přidáním metody dotazu výrazu dotazu. Při psaní dotazů LINQ přidáním syntaxe využívající metody na výrazu dotazu nebo <xref:System.Data.Services.Client.DataServiceQuery%601>, operace se přidají do dotazu identifikátoru URI v pořadí, ve kterém jsou volány metody. To je ekvivalentní volání <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> způsob, jak přidat jednotlivé možnosti dotazu identifikátoru URI dotazu.  
  
## <a name="executing-linq-queries"></a>Provádění dotazů LINQ  
 Určité LINQ dotaz metody, jako například <xref:System.Linq.Enumerable.First%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> nebo <xref:System.Linq.Enumerable.Single%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>, když se připojí k dotazování, způsobit provedení dotazu. Dotaz je také proveden, pokud jsou výsledky implicitně, jako Výčtový během `foreach` smyčky nebo když je přiřazen dotaz `List` kolekce. Další informace najdete v tématu [dotazování v datové službě](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 Klient spustí dotaz LINQ ve dvou částech. Kdykoli je to možné, LINQ – výrazy v dotazu se nejdřív vyhodnotit na straně klienta, a pak vygeneruje a odešle do služby data pro vyhodnocení s daty ve službě dotazů založených na identifikátor URI. Další informace najdete v části [klienta a spuštění serveru](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md#executingQueries) v [dotazování v datové službě](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 Pokud není možné přeložit dotazu LINQ v [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-kompatibilní dotazu identifikátoru URI, výjimka je vyvolána, když dojde k pokusu o spuštění. Další informace najdete v tématu [dotazování v datové službě](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
## <a name="linq-query-examples"></a>Příklady dotazů LINQ  
 Příklady v následujících částech ukazují druhy LINQ dotazy, které jde provést proti [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služby.  
  
<a name="filtering"></a>   
### <a name="filtering"></a>Filtrování  
 Příklady dotazů LINQ v této části filtrování dat v informačním kanálu vrácené službou.  
  
 Následující příklady jsou ekvivalentní dotazů, které filtrují vráceného `Orders` se vrátí entity tak, která řadí pouze s větší než 30 USD freight náklady:  
  
-   Pomocí syntaxe dotazu LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqwhereclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqwhereclausespecific)]     
  
-   Použití metody dotazu LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqwheremethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqwheremethodspecific)]       
  
-   Řetězci dotazu identifikátoru URI `$filter` možnost:  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#explicitquerywheremethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#explicitquerywheremethodspecific)]       
  
 Všechny předchozí příklady jsou přeloženy do dotazu identifikátoru URI: `http://localhost:12345/northwind.svc/Orders()?$filter=Freight gt 30M`.  
  
<a name="sorting"></a>   
### <a name="sorting"></a>Řazení  
 Následující příklady ukazují ekvivalentní dotazy, které seřaďte vrácená data podle názvu společnosti a podle PSČ, sestupně:  
  
-   Pomocí syntaxe dotazu LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqorderbyclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqorderbyclausespecific)]        
  
-   Použití metody dotazu LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqorderbymethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqorderbymethodspecific)]        
  
-   Řetězec dotazu identifikátoru URI `$orderby` možnost):  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#explicitqueryorderbymethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#explicitqueryorderbymethodspecific)]         
  
 Všechny předchozí příklady jsou přeloženy do dotazu identifikátoru URI: `http://localhost:12345/northwind.svc/Customers()?$orderby=CompanyName,PostalCode desc`.  
  
<a name="projection"></a>   
### <a name="projection"></a>Projekce  
 Následující příklady ukazují ekvivalentní dotazy, které vrácená data projektu do užší `CustomerAddress` typu:  
  
-   Pomocí syntaxe dotazu LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqselectclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqselectclausespecific)]         
  
-   Použití metody dotazu LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqselectmethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqselectmethodspecific)]         
 
  
> [!NOTE]
>  `$select` Povolena možnost dotazu nelze přidat do dotazu identifikátoru URI pomocí <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metody. Doporučujeme použít LINQ <xref:System.Linq.Enumerable.Select%2A> metoda může mít klienta generovat `$select` možnosti v identifikátoru URI požadavku dotazu.  
  
 Oba předchozí příklady jsou přeloženy do dotazu identifikátoru URI: `"http://localhost:12345/northwind.svc/Customers()?$filter=Country eq 'GerGerm'&$select=CustomerID,Address,City,Region,PostalCode,Country"`.  
  
<a name="paging"></a>   
### <a name="client-paging"></a>Klient stránkování  
 Následující příklady ukazují ekvivalentní dotazů, které vyžadují stránku řazení entit, která zahrnuje 25 objednávky, přeskočí prvních 50 objednávky:  
  
-   Použití metody dotazu pro dotaz LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqskiptakemethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqskiptakemethodspecific)]     
  
-   Řetězec dotazu identifikátoru URI `$skip` a `$top` možnosti):  
  
[!code-csharp[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#explicitqueryskiptakemethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#explicitqueryskiptakemethodspecific)]     
  
 Oba předchozí příklady jsou přeloženy do dotazu identifikátoru URI: `http://localhost:12345/northwind.svc/Orders()?$orderby=OrderDate desc&$skip=50&$top=25`.  
  
<a name="expand"></a>   
### <a name="expand"></a>Rozbalte položku  
 Při dotazování [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] data service, můžete požádat o zahrnou entity související entita cílem dotaz vrácené informační kanál. <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> Metoda je volána na <xref:System.Data.Services.Client.DataServiceQuery%601> pro sadu entit, cílová pro dotaz LINQ, se související entitou nastavte název zadán jako `path` parametru. Další informace najdete v tématu [načítání odložené obsahu](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 Následující příklady ukazují ekvivalentní způsoby používání <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> metoda v dotazu:  
  
-   V syntaxi dotazů LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqqueryexpandspecific)]      
[!code-vb[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqqueryexpandspecific)]  
  
-   Pomocí metody dotazu LINQ:  

[!code-csharp[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqqueryexpandmethodspecific)]       
[!code-vb[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqqueryexpandmethodspecific)]       
  
  
 Oba předchozí příklady jsou přeloženy do dotazu identifikátoru URI: `http://localhost:12345/northwind.svc/Orders()?$filter=CustomerID eq 'ALFKI'&$expand=Order_Details`.  
  
<a name="unsupportedMethods"></a>   
## <a name="unsupported-linq-methods"></a>Metody nepodporované LINQ  
 Následující tabulka obsahuje třídy LINQ metody nejsou podporovány a nemůže být součástí pro dotaz [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služby:  
  
|Typ operace|Nepodporovaná – metoda|  
|--------------------|------------------------|  
|Množinové operátory|Všechny operátory set, které nejsou podporované proti <xref:System.Data.Services.Client.DataServiceQuery%601>, které zahrnuty následující:<br /><br /> -   <xref:System.Linq.Enumerable.All%2A><br />-   <xref:System.Linq.Enumerable.Any%2A><br />-   <xref:System.Linq.Enumerable.Concat%2A><br />-   <xref:System.Linq.Enumerable.DefaultIfEmpty%2A><br />-   <xref:System.Linq.Enumerable.Distinct%2A><br />-   <xref:System.Linq.Enumerable.Except%2A><br />-   <xref:System.Linq.Enumerable.Intersect%2A><br />-   <xref:System.Linq.Enumerable.Union%2A><br />-   <xref:System.Linq.Enumerable.Zip%2A>|  
|Operators setřiďovacího|Následující pořadí operátory, které vyžadují <xref:System.Collections.Generic.IComparer%601> nejsou podporovány proti <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29>|  
|Projekce a filtrování operátory|Následující projekce a filtrování operátory, které přijímají poziční argument nejsou podporovány proti <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2C%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Where%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29>|  
|Seskupení operátory|Všechny operátory seskupení nepodporované proti <xref:System.Data.Services.Client.DataServiceQuery%601>, včetně následujících:<br /><br /> -   <xref:System.Linq.Enumerable.GroupBy%2A><br />-   <xref:System.Linq.Enumerable.GroupJoin%2A><br /><br /> Operace seskupení musí provést u klienta.|  
|Agregační operátory|Všechny agregační operace nejsou podporovány proti <xref:System.Data.Services.Client.DataServiceQuery%601>, včetně následujících:<br /><br /> -   <xref:System.Linq.Enumerable.Aggregate%2A><br />-   <xref:System.Linq.Enumerable.Average%2A><br />-   <xref:System.Linq.Enumerable.Count%2A><br />-   <xref:System.Linq.Enumerable.LongCount%2A><br />-   <xref:System.Linq.Enumerable.Max%2A><br />-   <xref:System.Linq.Enumerable.Min%2A><br />-   <xref:System.Linq.Enumerable.Sum%2A><br /><br /> Agregační operace musí být provedeny buď na straně klienta nebo zapouzdřená pomocí operace služby.|  
|Operátory stránkování|Nejsou podporovány následující operátory stránkování <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.ElementAt%2A><br />-   <xref:System.Linq.Enumerable.Last%2A><br />-   <xref:System.Linq.Enumerable.LastOrDefault%2A><br />-   <xref:System.Linq.Enumerable.SkipWhile%2A><br />-   <xref:System.Linq.Enumerable.TakeWhile%2A> **Poznámka:** stránkování operátory, které se provádějí v prázdné sekvenci vrátit hodnotu null.|  
|Ostatní operátory|Následující další operátory nejsou podporovány u <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> 1.  <xref:System.Linq.Enumerable.Empty%2A><br />2.  <xref:System.Linq.Enumerable.Range%2A><br />3.  <xref:System.Linq.Enumerable.Repeat%2A><br />4.  <xref:System.Linq.Enumerable.ToDictionary%2A><br />5.  <xref:System.Linq.Enumerable.ToLookup%2A>|  
  
<a name="supportedExpressions"></a>   
## <a name="supported-expression-functions"></a>Funkce podporované výraz  
 Následující modul common language runtime (CLR), metody a vlastnosti jsou podporované, protože může být přeložen ve výrazu dotazu pro zahrnutí v identifikátoru URI žádosti do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služby:  
  
|<xref:System.String> Člen|Podporované [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] – funkce|  
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
  
|<xref:System.DateTime> Člen<sup>1</sup>|Podporované [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] – funkce|  
|-------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Day>|`int day(DateTime p0)`|  
|<xref:System.DateTime.Hour>|`int hour(DateTime p0)`|  
|<xref:System.DateTime.Minute>|`int minute(DateTime p0)`|  
|<xref:System.DateTime.Month>|`int month(DateTime p0)`|  
|<xref:System.DateTime.Second>|`int second(DateTime p0)`|  
|<xref:System.DateTime.Year>|`int year(DateTime p0)`|  
  
 <sup>1</sup>odpovídá datu a času vlastnosti <xref:Microsoft.VisualBasic.DateAndTime?displayProperty=nameWithType>, jakož i <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> metody v jazyce Visual Basic jsou také podporovány.  
  
|<xref:System.Math> Člen|Podporované [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] – funkce|  
|---------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Math.Ceiling%28System.Decimal%29>|`decimal ceiling(decimal p0)`|  
|<xref:System.Math.Ceiling%28System.Double%29>|`double ceiling(double p0)`|  
|<xref:System.Math.Floor%28System.Decimal%29>|`decimal floor(decimal p0)`|  
|<xref:System.Math.Floor%28System.Double%29>|`double floor(double p0)`|  
|<xref:System.Math.Round%28System.Decimal%29>|`decimal round(decimal p0)`|  
|<xref:System.Math.Round%28System.Double%29>|`double round(double p0)`|  
  
|<xref:System.Linq.Expressions.Expression> Člen|Podporované [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] – funkce|  
|---------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Linq.Expressions.Expression.TypeIs%28System.Linq.Expressions.Expression%2CSystem.Type%29>|`bool isof(type p0)`|  
  
 Klient může být také moci vyhodnocovat další funkce CLR na straně klienta. A <xref:System.NotSupportedException> se vyvolá pro libovolný výraz, který nelze vyhodnotit na straně klienta a nelze přeložit na platný žádost o identifikátor URI pro vyhodnocení na serveru.  
  
## <a name="see-also"></a>Viz také  
 [Dotazování v datové službě](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 [Projekce dotazů](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)  
 [Materializace objektů](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)  
 [Prostředí OData: Konvence identifikátor URI](https://go.microsoft.com/fwlink/?LinkID=185564)
