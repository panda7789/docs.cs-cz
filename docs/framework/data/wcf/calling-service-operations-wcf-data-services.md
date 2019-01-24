---
title: Operace volání služeb (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1767f3a7-29d2-4834-a763-7d169693fa8b
ms.openlocfilehash: c11fe4176ee770e39abcab612e26e496aa2a1457
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543510"
---
# <a name="calling-service-operations-wcf-data-services"></a>Operace volání služeb (WCF Data Services)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Definuje operace služby pro službu data. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Umožňuje definovat tyto operace jako metody na datovou službu. Stejně jako ostatní prostředkům datové služby se tak vyřeší tyto operace služby pomocí identifikátorů URI. Operace služby může vrátit kolekce typů entit, instance typu jednu entitu a primitivní typy, jako je například celé číslo a řetězec. Operace služby mohou také vrátit `null` (`Nothing` v jazyce Visual Basic). [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klientské knihovny lze použít pro přístup k operace služby, které podporují požadavky HTTP GET. Tyto druhy operací služby jsou definovány jako metody, které mají <xref:System.ServiceModel.Web.WebGetAttribute> použít. Další informace najdete v tématu [operací služby](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).  
  
 Operace služby jsou přístupné v metadatech vrácené službou data, která implementuje [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. V metadatech operací služby jsou reprezentovány ve formě `FunctionImport` elementy. Při generování silných <xref:System.Data.Services.Client.DataServiceContext>, nástroje pro přidání odkazu na službu a DataSvcUtil.exe Ignorovat tento element. Z tohoto důvodu nebude najít metodu pro daný kontext, který slouží k volání operace služby přímo. Ale můžete pořád použít [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klienta k volání operací služby v jednom z těchto dvou způsobů:  
  
-   Při volání <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> metodu na <xref:System.Data.Services.Client.DataServiceContext>, poskytnutí identifikátoru URI operace služby, spolu s žádné parametry. Tato metoda se používá k volání jakékoli operace služby GET.  
  
-   Pomocí <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> k vytvoření <xref:System.Data.Services.Client.DataServiceQuery%601> objektu. Při volání metody <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>, je součástí názvu operace služby `entitySetName` parametru. Tato metoda vrátí hodnotu <xref:System.Data.Services.Client.DataServiceQuery%601> objekt, který při výčtu nebo při volání operace služby <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> metoda je volána. Tato metoda se používá k volání operací služby GET, které vracejí kolekce. Jeden parametr lze zadat pomocí <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metody. <xref:System.Data.Services.Client.DataServiceQuery%601> Objekt vrácený touto metodou mohou být dále složené proti jako jakýkoliv jiný objekt dotazu. Další informace najdete v tématu [dotazování v datové službě](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
## <a name="considerations-for-calling-service-operations"></a>Důležité informace týkající se volání operací služby  
 Při použití, platí následující aspekty [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klienta k volání operací služby.  
  
-   Při přístupu ke službě data asynchronně, je nutné použít asynchronní ekvivalent <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> metody <xref:System.Data.Services.Client.DataServiceContext> nebo <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> metody <xref:System.Data.Services.Client.DataServiceQuery%601>.  
  
-   [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klientské knihovny nelze sloučit výsledky z operace služby, který vrátí kolekce primitivních typů.  
  
-   [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klientská knihovna nepodporuje volání operací služby POST. Operace služby, které jsou volány metody POST protokolu HTTP jsou definované pomocí <xref:System.ServiceModel.Web.WebInvokeAttribute> s `Method="POST"` parametru. Volání operace služby pomocí požadavku HTTP POST, je nutné místo toho použít <xref:System.Net.HttpWebRequest>.  
  
-   Nemůžete použít <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> volat operaci GET služby, který vrací jeden výsledek, entitu nebo primitivní typ, nebo která vyžaduje více než jeden vstupní parametr. Je nutné místo toho volat <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> metody.  
  
-   Zvažte možnost vytvořit metodu rozšíření na silných <xref:System.Data.Services.Client.DataServiceContext> částečné třídy, která se generují pomocí nástrojů, využívající buď <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> nebo <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> metodu chce volat operace služby. To umožňuje volání operací služby přímo z daného kontextu. Další informace naleznete v příspěvku blogu [operací služby a klienta WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=215668).  
  
-   Při použití <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> volat operace služby, klientské knihovny automaticky řídicí sekvence znaků, které jsou předány <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> provedením procent kódování vyhrazené znaky, jako je například ampersand (&) a uvozovací znaky uvozovek jedním v řetězce. Ale při volání mezi *Execute* metod k volání operace služby, nesmíte zapomenout provést toto uvození žádné uživatelem zadané řetězcové hodnoty. Jedním uvozovky na identifikátory URI jsou uvozeny řídicími znaky jako páry uvozovek jednou.  
  
## <a name="examples-of-calling-service-operations"></a>Příklady volání operací služby  
 Tato část obsahuje následující příklady toho, jak pomocí volání operací služby [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klientská knihovna:  
  
-   [Spustit volání&lt;T&gt; vrátit kolekci entit](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteIQueryable)  
  
-   [Pomocí CreateQuery&lt;T&gt; vrátit kolekci entit](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#CreateQueryIQueryable)  
  
-   [Spustit volání&lt;T&gt; vrátit jednu entitu](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteSingleEntity)  
  
-   [Spustit volání&lt;T&gt; vrátit kolekce primitivních hodnot](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecutePrimitiveCollection)  
  
-   [Spustit volání&lt;T&gt; k vrácení jednoho primitivní hodnoty](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecutePrimitiveValue)  
  
-   [Volání operace služby, která nevrátí žádná Data](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteVoid)  
  
-   [Asynchronní volání operací služby](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteAsync)  
  
<a name="ExecuteIQueryable"></a>   
### <a name="calling-executet-to-return-a-collection-of-entities"></a>Spustit volání\<T > k vrácení kolekce entit  
 Následující příklad volá operace služby s názvem GetOrdersByCity, která přebírá parametr řetězce `city` a vrátí <xref:System.Linq.IQueryable%601>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationiqueryable)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationiqueryable)]  
  
 V tomto příkladu vrácení operace služby kolekce `Order` objekty se související `Order_Detail` objekty.  
  
<a name="CreateQueryIQueryable"></a>   
### <a name="using-createqueryt-to-return-a-collection-of-entities"></a>Pomocí CreateQuery\<T > k vrácení kolekce entit  
 V následujícím příkladu <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> se vraťte <xref:System.Data.Services.Client.DataServiceQuery%601> , který slouží k volání stejné operace GetOrdersByCity služby:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationcreatequery)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationcreatequery)]  
  
 V tomto příkladu <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metoda se používá k přidání parametru do dotazu a <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> metoda se používá k zahrnují souvisejícími Order_Details objekty ve výsledcích.  
  
<a name="ExecuteSingleEntity"></a>   
### <a name="calling-executet-to-return-a-single-entity"></a>Spustit volání\<T > k vrácení jedné Entity  
 V následujícím příkladu volání operace služby s názvem GetNewestOrder, který vrátí pouze jednu entitu pořadí:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationsingleentity)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationsingleentity)]  
  
 V tomto příkladu <xref:System.Linq.Enumerable.FirstOrDefault%2A> metody slouží k vyžádání jenom jedné entitě objednávka na spuštění.  
  
<a name="ExecutePrimitiveCollection"></a>   
### <a name="calling-executet-to-return-a-collection-of-primitive-values"></a>Spustit volání\<T > k vrácení kolekce primitivních hodnot  
 V následujícím příkladu volání operace služby, která vrací kolekci hodnot řetězce:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationEnumString](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationenumstring)]  
  
<a name="ExecutePrimitiveValue"></a>   
### <a name="calling-executet-to-return-a-single-primitive-value"></a>Spustit volání\<T > k vrácení jednoho primitivní hodnoty  
 V následujícím příkladu volání operace služby, který vrací jedinou hodnotu řetězce:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationsingleint)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationsingleint)]  
  
 Znovu v tomto příkladu <xref:System.Linq.Enumerable.FirstOrDefault%2A> metody slouží k vyžádání pouze jednu celočíselnou hodnotu na spuštění.  
  
<a name="ExecuteVoid"></a>   
### <a name="calling-a-service-operation-that-returns-no-data"></a>Volání operace služby, která nevrátí žádná Data  
 V následujícím příkladu volání operace služby, která nevrátí žádná data:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationvoid)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationvoid)]  
  
 Protože data nejsou nevrátí, není přiřazena hodnota provádění. Jediné, co zjistí, která žádost proběhla úspěšně. je to, že žádné <xref:System.Data.Services.Client.DataServiceQueryException> je vyvolána.  
  
<a name="ExecuteAsync"></a>   
### <a name="calling-a-service-operation-asynchronously"></a>Asynchronní volání operací služby  
 Operace služby v následujícím příkladu asynchronně volá pomocí volání <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> a <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#onasyncexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#onasyncexecutioncomplete)]  
  
 Vzhledem k tomu, že nebudou vrácena žádná data, není přiřazená hodnota vrácená provádění. Jediné, co zjistí, která žádost proběhla úspěšně. je to, že žádné <xref:System.Data.Services.Client.DataServiceQueryException> je vyvolána.  
  
 Následující příklad asynchronně volá stejné operace služby s použitím <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationqueryasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationqueryasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#onasyncqueryexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#onasyncqueryexecutioncomplete)]  
  
## <a name="see-also"></a>Viz také:
- [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
