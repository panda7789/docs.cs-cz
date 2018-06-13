---
title: Aspekty LINQ (služby WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ
- querying the data service [WCF Data Services]
- WCF Data Services, querying
ms.assetid: cc4ec9e9-348f-42a6-a78e-1cd40e370656
ms.openlocfilehash: 030c8e12b45cfc11d1440a410c69d8bc911c56c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365966"
---
# <a name="linq-considerations-wcf-data-services"></a>Aspekty LINQ (služby WCF Data Services)
Toto téma obsahuje informace o způsobu, jakým sestavit a spustit, když používáte dotazy které LINQ [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klienta a omezení použití LINQ pro dotaz na data služby, který implementuje [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]. Další informace o vytvoření a spuštění dotazů vůči [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]– na základě dat služby, najdete v části [dotaz na službu Data](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
## <a name="composing-linq-queries"></a>Vytváření dotazů LINQ  
 LINQ umožňuje vytvořit dotazy na kolekci objektů, který implementuje <xref:System.Collections.Generic.IEnumerable%601>. Obě **přidat odkaz na službu** dialogové okno v sadě Visual Studio a nástroj DataSvcUtil.exe se používají ke generování reprezentace [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služby jako třída kontejneru entit, která dědí z <xref:System.Data.Services.Client.DataServiceContext>, a také objekty, které představují entity, vrátí se v informačních kanálů. Tyto nástroje generovat také vlastnosti pro třídu kontejneru entity pro kolekce, které jsou zveřejněné jako kanály službou. Každý z těchto vlastností třídy, který zapouzdřuje službu data návratový <xref:System.Data.Services.Client.DataServiceQuery%601>. Protože <xref:System.Data.Services.Client.DataServiceQuery%601> třída implementuje <xref:System.Linq.IQueryable%601> rozhraní definované LINQ, můžete vytvořit dotaz LINQ proti informační kanály vystavené službu data, které jsou přeložit pomocí klientské knihovny na žádost dotazu URI, který je odešle do služby data na provádění.  
  
> [!IMPORTANT]
>  Sada vyjádřit kombinací v syntaxi LINQ dotazů je širší než ty, které v syntaxe identifikátoru URI, který je používán povolené [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] datové služby. A <xref:System.NotSupportedException> se vyvolá, když dotaz nelze mapovat na ve službě data cílový identifikátor URI. Další informace najdete v tématu [nepodporovaných metod LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md#unsupportedMethods) v tomto tématu.  
  
 Následující příklad je dotaz LINQ, který vrátí `Orders` který máte nákladní náklady více než 30 $ a seřadí výsledky podle data přesouvání počínaje nejnovější datum expedice:  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinqspecific)]      
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinqspecific)]    
  
 Tento dotaz LINQ je přeložit na následující dotaz identifikátor URI, který se spustí na základě Northwind [rychlý Start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) služba dat:  
  
```  
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
 Další obecné informace o jazyku LINQ najdete v tématu [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).  
  
 LINQ umožňuje vytvořit dotazy pomocí obou konkrétní jazyk deklarativní syntaxi dotazu, uvedené v předchozím příkladu, jakož i sadu metody dotazů známé jako standardní operátory dotazu. Dotaz ekvivalentní v předchozím příkladu se může skládat pouze s syntaxí na základě metod, jak je znázorněno v následujícím příkladu:  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinqexpressionspecific)]      
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinqexpressionspecific)]    
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klienta se bude moct překládat oba druhy složený dotazy do dotazu identifikátoru URI a dotaz LINQ můžete rozšířit přidáním metody dotazů do výrazu dotazu. Při vytváření dotazů LINQ připojením syntaxe využívající metody do výrazu dotazu nebo <xref:System.Data.Services.Client.DataServiceQuery%601>, operace, které jsou přidány do identifikátoru URI dotazu v pořadí, ve kterém jsou volány metody. Jde o ekvivalent volání <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metodu pro přidání do dotazu identifikátoru URI jednotlivé možnosti dotazu.  
  
## <a name="executing-linq-queries"></a>Provádění dotazů LINQ  
 Některé LINQ dotaz metody, jako například <xref:System.Linq.Enumerable.First%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> nebo <xref:System.Linq.Enumerable.Single%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>, když se připojí k dotazu, způsobit provedení dotazu. Dotaz se rovněž provádí výsledky jsou výčtové implicitně, jako třeba při `foreach` smyčky nebo když je přiřazená dotaz `List` kolekce. Další informace najdete v tématu [dotaz na službu Data](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 Klient provede dotaz LINQ ve dvou částech. Kdykoli je to možné, LINQ – výrazy v dotazu se nejprve vyhodnocují na straně klienta, a potom dotaz na základě identifikátoru URI je generována a odešle do služby data pro vyhodnocení proti data ve službě. Další informace najdete v části [klienta a Server spuštění](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md#executingQueries) v [dotaz na službu Data](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 Pokud dotaz LINQ nelze přeložit v [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-vyhovující dotazu URI, výjimku se vyvolá, když dojde k pokusu o spuštění. Další informace najdete v tématu [dotaz na službu Data](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
## <a name="linq-query-examples"></a>Příklady dotazů LINQ  
 Typy dotazů LINQ, které mohou být provedeny proti ukazují příklady v následujících částech [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služby.  
  
<a name="filtering"></a>   
### <a name="filtering"></a>Filtrování  
 Příklady dotazů LINQ v této části filtrování dat v informačním kanálu vrácený službou.  
  
 Následující příklady jsou ekvivalentní dotazy, které filtrovat vrácený `Orders` se vrátí entity, který řadí pouze s větší než 30 $ nákladní náklady:  
  
-   Pomocí syntaxe dotazů LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqwhereclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqwhereclausespecific)]     
  
-   Pomocí metody dotazů LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqwheremethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqwheremethodspecific)]       
  
-   Řetězci dotazu identifikátoru URI `$filter` možnost:  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#explicitquerywheremethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#explicitquerywheremethodspecific)]       
  
 Všechny v předchozích příkladech jsou převedeny na identifikátoru URI dotazu: `http://localhost:12345/northwind.svc/Orders()?$filter=Freight gt 30M`.  
  
<a name="sorting"></a>   
### <a name="sorting"></a>Řazení  
 Následující příklady ukazují ekvivalentní dotazy, které podle názvu společnosti a podle PSČ, sestupné řazení vrácená data:  
  
-   Pomocí syntaxe dotazů LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqorderbyclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqorderbyclausespecific)]        
  
-   Pomocí metody dotazů LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqorderbymethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqorderbymethodspecific)]        
  
-   Řetězce dotazu URI `$orderby` možnost):  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#explicitqueryorderbymethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#explicitqueryorderbymethodspecific)]         
  
 Všechny v předchozích příkladech jsou převedeny na identifikátoru URI dotazu: `http://localhost:12345/northwind.svc/Customers()?$orderby=CompanyName,PostalCode desc`.  
  
<a name="projection"></a>   
### <a name="projection"></a>Projekce  
 Následující příklady ukazují ekvivalentní dotazy, které projektu vrácená data do užší `CustomerAddress` typu:  
  
-   Pomocí syntaxe dotazů LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqselectclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqselectclausespecific)]         
  
-   Pomocí metody dotazů LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqselectmethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqselectmethodspecific)]         
 
  
> [!NOTE]
>  `$select` Možnost dotazu nelze přidat do dotazu identifikátoru URI pomocí <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metoda. Doporučujeme použít LINQ <xref:System.Linq.Enumerable.Select%2A> metoda váš klient bude generovat `$select` dotaz v identifikátoru URI požadavku možnost.  
  
 Obě v předchozích příkladech jsou převedeny na identifikátoru URI dotazu: `"http://localhost:12345/northwind.svc/Customers()?$filter=Country eq 'GerGerm'&$select=CustomerID,Address,City,Region,PostalCode,Country"`.  
  
<a name="paging"></a>   
### <a name="client-paging"></a>Klient stránkování  
 Následující příklady ukazují ekvivalentní dotazy, které požadavku stránky seřazené pořadí entit, který zahrnuje 25 objednávky, přeskočení prvních 50 objednávky:  
  
-   Použití metody dotazů LINQ dotazu:  
  
[!code-csharp[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqskiptakemethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqskiptakemethodspecific)]     
  
-   Řetězce dotazu URI `$skip` a `$top` možnosti):  
  
[!code-csharp[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#explicitqueryskiptakemethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#explicitqueryskiptakemethodspecific)]     
  
 Obě v předchozích příkladech jsou převedeny na identifikátoru URI dotazu: `http://localhost:12345/northwind.svc/Orders()?$orderby=OrderDate desc&$skip=50&$top=25`.  
  
<a name="expand"></a>   
### <a name="expand"></a>Rozbalte položku  
 Když dotazujete [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služba dat můžete požádat o obsahovat entity související entity necílila dotazu vrácená informačního kanálu. <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> Metoda je volána na <xref:System.Data.Services.Client.DataServiceQuery%601> pro sadu entity necílila dotaz LINQ s související entity nastavit jako zadaný název `path` parametr. Další informace najdete v tématu [načítání odložení obsahu](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 Následující příklady ukazují ekvivalentní způsoby použití <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> metoda v dotazu:  
  
-   V syntaxi dotazu LINQ:  
  
[!code-csharp[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqqueryexpandspecific)]      
[!code-vb[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqqueryexpandspecific)]  
  
-   Pomocí metody dotazů LINQ:  

[!code-csharp[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqqueryexpandmethodspecific)]       
[!code-vb[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqqueryexpandmethodspecific)]       
  
  
 Obě v předchozích příkladech jsou převedeny na identifikátoru URI dotazu: `http://localhost:12345/northwind.svc/Orders()?$filter=CustomerID eq 'ALFKI'&$expand=Order_Details`.  
  
<a name="unsupportedMethods"></a>   
## <a name="unsupported-linq-methods"></a>Metody nepodporované LINQ  
 Následující tabulka obsahuje třídy LINQ metody nejsou podporovány a nemůže být zahrnut v dotazu prováděné vůči [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služby:  
  
|Typ operace|Nepodporované – metoda|  
|--------------------|------------------------|  
|Operátory set|Všechny operátory set jsou nepodporované proti <xref:System.Data.Services.Client.DataServiceQuery%601>, které součástí následující:<br /><br /> -   <xref:System.Linq.Enumerable.All%2A><br />-   <xref:System.Linq.Enumerable.Any%2A><br />-   <xref:System.Linq.Enumerable.Concat%2A><br />-   <xref:System.Linq.Enumerable.DefaultIfEmpty%2A><br />-   <xref:System.Linq.Enumerable.Distinct%2A><br />-   <xref:System.Linq.Enumerable.Except%2A><br />-   <xref:System.Linq.Enumerable.Intersect%2A><br />-   <xref:System.Linq.Enumerable.Union%2A><br />-   <xref:System.Linq.Enumerable.Zip%2A>|  
|Řazení operátory|Následující řazení operátory, které vyžadují <xref:System.Collections.Generic.IComparer%601> jsou nepodporované proti <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29>|  
|Projekce a filtrování operátory|Následující projekce a filtrování operátory, které přijímají poziční argument jsou nepodporované proti <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2C%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Where%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29>|  
|Seskupení operátory|Nejsou podporovány pro všechny operátory seskupení <xref:System.Data.Services.Client.DataServiceQuery%601>, včetně následujících:<br /><br /> -   <xref:System.Linq.Enumerable.GroupBy%2A><br />-   <xref:System.Linq.Enumerable.GroupJoin%2A><br /><br /> Operace seskupení musí provést na straně klienta.|  
|Agregační operátory|Všechny agregační operace jsou nepodporované proti <xref:System.Data.Services.Client.DataServiceQuery%601>, včetně následujících:<br /><br /> -   <xref:System.Linq.Enumerable.Aggregate%2A><br />-   <xref:System.Linq.Enumerable.Average%2A><br />-   <xref:System.Linq.Enumerable.Count%2A><br />-   <xref:System.Linq.Enumerable.LongCount%2A><br />-   <xref:System.Linq.Enumerable.Max%2A><br />-   <xref:System.Linq.Enumerable.Min%2A><br />-   <xref:System.Linq.Enumerable.Sum%2A><br /><br /> Agregační operace musí být provedeny buď na klientovi nebo se zapouzdřené pomocí operace služby.|  
|Operátory stránkování|Následující stránkování operátory nejsou podporovány u <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.ElementAt%2A><br />-   <xref:System.Linq.Enumerable.Last%2A><br />-   <xref:System.Linq.Enumerable.LastOrDefault%2A><br />-   <xref:System.Linq.Enumerable.SkipWhile%2A><br />-   <xref:System.Linq.Enumerable.TakeWhile%2A> **Poznámka:** stránkování operátory, které jsou spouštěny na prázdnou sekvencí vrátit hodnotu null.|  
|Jiné operátory|Následující dalšími operátory nejsou podporovány u <xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> 1.  <xref:System.Linq.Enumerable.Empty%2A><br />2.  <xref:System.Linq.Enumerable.Range%2A><br />3.  <xref:System.Linq.Enumerable.Repeat%2A><br />4.  <xref:System.Linq.Enumerable.ToDictionary%2A><br />5.  <xref:System.Linq.Enumerable.ToLookup%2A>|  
  
<a name="supportedExpressions"></a>   
## <a name="supported-expression-functions"></a>Funkce podporované výraz  
 Následující metody common language runtime (CLR) a vlastnosti jsou podporována, protože může být přeložit ve výrazu dotazu pro zahrnutí v identifikátoru URI požadavku na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] služby:  
  
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
  
 <sup>1</sup>ekvivalentní datum a čas vlastnosti <xref:Microsoft.VisualBasic.DateAndTime?displayProperty=nameWithType>, a taky <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> jsou podporovány také metody v jazyce Visual Basic.  
  
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
  
 Klient také možné vyhodnotit další funkce CLR na straně klienta. A <xref:System.NotSupportedException> se vyvolá pro jakýkoli výraz, který nelze vyhodnotit v klientovi a nejde přeložit na platný žádost o identifikátor URI pro vyhodnocení na serveru.  
  
## <a name="see-also"></a>Viz také  
 [Dotazování v datové službě](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 [Projekce dotazů](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)  
 [Materializace objektů](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)  
 [OData: Konvence prostředí identifikátor URI](http://go.microsoft.com/fwlink/?LinkID=185564)
