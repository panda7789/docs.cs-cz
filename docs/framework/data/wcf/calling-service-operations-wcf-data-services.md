---
title: "Volání operace služby (služby WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 1767f3a7-29d2-4834-a763-7d169693fa8b
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1480047f14d9528d4d498b417e5d0b4a0f87a622
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="calling-service-operations-wcf-data-services"></a>Volání operace služby (služby WCF Data Services)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Definuje operací služby pro službu data. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Umožňuje definovat tyto operace jako metody pro službu data. Jako další prostředky služby dat jsou tyto operace služby řešit pomocí identifikátory URI. Operace služby může vrátit kolekce typů entit, instance typu jedné entity a primitivní typy, jako je celé číslo a řetězec. Můžete se taky vrátit operaci služby `null` (`Nothing` v jazyce Visual Basic). [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klientské knihovny lze použít pro přístup k operace služby, které podporují požadavky HTTP GET. Tyto typy operací služby jsou definované jako metody, které mají <xref:System.ServiceModel.Web.WebGetAttribute> použít. Další informace najdete v tématu [operací služby](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).  
  
 Operace služby, které jsou zveřejněné v metadata vrácená data službu, která implementuje [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. V metadatech, jsou vyjádřené operací služby `FunctionImport` elementy. Při generování silného typu <xref:System.Data.Services.Client.DataServiceContext>, nástroje Přidat odkaz na službu a DataSvcUtil.exe ignorovat tohoto elementu. Z tohoto důvodu nebude možné najít metodu v kontextu, které je možné volat operace služby přímo. Ale když můžete nadále používat [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klienta k volání operací služby v jednom z těchto způsobů:  
  
-   Při volání <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> metodu <xref:System.Data.Services.Client.DataServiceContext>, zadávání identifikátor URI operace služby, spolu s parametry. Tato metoda se používá k volání všechny operace GET service.  
  
-   Pomocí <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> k vytvoření <xref:System.Data.Services.Client.DataServiceQuery%601> objektu. Při volání metody <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>, zadán název operace služby, na `entitySetName` parametr. Tato metoda vrátí hodnotu <xref:System.Data.Services.Client.DataServiceQuery%601> objekt, který volá operace služby, když ve výčtu nebo když <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> metoda je volána. Tato metoda se používá k volání operací služby GET, které vrací kolekce. Jeden parametr lze zadat pomocí <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metoda. <xref:System.Data.Services.Client.DataServiceQuery%601> Tato metoda vrátí objekt můžete dále skládat proti jako libovolného objektu dotazu. Další informace najdete v tématu [dotaz na službu Data](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
## <a name="considerations-for-calling-service-operations"></a>Důležité informace týkající se volání operací služby  
 Při použití, platí následující aspekty [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klienta k volání operací služby.  
  
-   Při přístupu ke službě data asynchronně, je nutné použít asynchronní ekvivalentní <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> metody na <xref:System.Data.Services.Client.DataServiceContext> nebo <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> metody na <xref:System.Data.Services.Client.DataServiceQuery%601>.  
  
-   [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klientské knihovny nelze vyhodnotit výsledků operace služby, která vrátí kolekci primitivní typy.  
  
-   [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klientské knihovny nepodporuje volání operací služby POST. Operace služby, které jsou volány HTTP POST jsou definované pomocí <xref:System.ServiceModel.Web.WebInvokeAttribute> s `Method="POST"` parametr. Chcete-li požadavek HTTP POST pro volání operace služby, musíte místo toho použít <xref:System.Net.HttpWebRequest>.  
  
-   Nemůžete použít <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> volat operace GET služby, který vrací jeden výsledek, entity nebo primitivní typ, nebo který vyžaduje více než jeden vstupní parametr. Místo toho musí volat <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> metoda.  
  
-   Zvažte vytvoření metody rozšíření na silného typu <xref:System.Data.Services.Client.DataServiceContext> třídu, která se generují pomocí nástrojů, která používá buď <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> nebo <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> metoda k volání operace služby. To umožňuje volání operací služby přímo z kontextu. Další informace naleznete v příspěvku blogu [operací služby a klienta WCF Data Services](http://go.microsoft.com/fwlink/?LinkId=215668).  
  
-   Při použití <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> volat operace služby, knihovny klienta automaticky řídicí sekvence znaků zadané <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> provedením procent kódování vyhrazené znaky, jako je například ampersand (&) a uvozovací znaky uvozovek jedním v řetězce. Ale při volání mezi *Execute* metod k volání operace služby, nezapomeňte provést tento uvozovací znaky žádné uživatelem zadané řetězcové hodnoty. Single uvozovky mají v identifikátory URI jsou uvozeny uvozovacím znakem jako dvojice jedním uvozovky.  
  
## <a name="examples-of-calling-service-operations"></a>Příklady volání operací služby  
 Tato část obsahuje následující příklady jak volání operací služby pomocí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientské knihovny:  
  
-   [Provést volání&lt;T&gt; vrátit kolekci entit](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteIQueryable)  
  
-   [Pomocí CreateQuery&lt;T&gt; vrátit kolekci entit](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#CreateQueryIQueryable)  
  
-   [Provést volání&lt;T&gt; vrátit jedné Entity](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteSingleEntity)  
  
-   [Provést volání&lt;T&gt; vrátit kolekce primitivní hodnoty](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecutePrimitiveCollection)  
  
-   [Provést volání&lt;T&gt; vrátit jednu hodnotu primitivní](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecutePrimitiveValue)  
  
-   [Volání operace služby, která nevrátí žádná Data](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteVoid)  
  
-   [Asynchronní volání operace služby](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md#ExecuteAsync)  
  
<a name="ExecuteIQueryable"></a>   
### <a name="calling-executet-to-return-a-collection-of-entities"></a>Provést volání\<T > vrátit kolekci entit  
 V následujícím příkladu volání operace služby s názvem GetOrdersByCity, který přebírá parametr řetězce `city` a vrátí <xref:System.Linq.IQueryable%601>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationiqueryable)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationiqueryable)]  
  
 V tomto příkladu vrací operace služby kolekce `Order` objekty s související `Order_Detail` objekty.  
  
<a name="CreateQueryIQueryable"></a>   
### <a name="using-createqueryt-to-return-a-collection-of-entities"></a>Pomocí CreateQuery\<T > vrátit kolekci entit  
 Následující příklad používá <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> vrátit <xref:System.Data.Services.Client.DataServiceQuery%601> který se používá k volání stejné operace služby GetOrdersByCity:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationcreatequery)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationcreatequery)]  
  
 V tomto příkladu <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metoda se používá k přidání parametru do dotazu a <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> metoda se používá k zahrnout související objekty Order_Details ve výsledcích.  
  
<a name="ExecuteSingleEntity"></a>   
### <a name="calling-executet-to-return-a-single-entity"></a>Provést volání\<T > vrátit jedné Entity  
 V následujícím příkladu volání operace služby s názvem GetNewestOrder, který vrátí jenom jedné entitě pořadí:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationsingleentity)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationsingleentity)]  
  
 V tomto příkladu <xref:System.Linq.Enumerable.FirstOrDefault%2A> metoda slouží k vyžádání jenom jedné entitě pořadí na provedení.  
  
<a name="ExecutePrimitiveCollection"></a>   
### <a name="calling-executet-to-return-a-collection-of-primitive-values"></a>Provést volání\<T > vrátit kolekce primitivní hodnoty  
 V následujícím příkladu volání operace služby, která vrátí kolekci řetězcové hodnoty:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationEnumString](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationenumstring)]  
  
<a name="ExecutePrimitiveValue"></a>   
### <a name="calling-executet-to-return-a-single-primitive-value"></a>Provést volání\<T > Chcete-li vrátit jednu hodnotu primitivní  
 V následujícím příkladu volání operace služby, který vrací jednu řetězcovou hodnotu:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationsingleint)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationsingleint)]  
  
 Znovu v tomto příkladu <xref:System.Linq.Enumerable.FirstOrDefault%2A> metoda slouží k vyžádání pouze jednu celočíselnou hodnotu na provedení.  
  
<a name="ExecuteVoid"></a>   
### <a name="calling-a-service-operation-that-returns-no-data"></a>Volání operace služby, která nevrátí žádná Data  
 V následujícím příkladu volání operace služby, která nevrátí žádná data:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationvoid)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationvoid)]  
  
 Protože není data jsou vrácena, hodnota spuštění není přiřazena. Jediné, požadavek byl úspěšný je, že žádné <xref:System.Data.Services.Client.DataServiceQueryException> je vyvolána.  
  
<a name="ExecuteAsync"></a>   
### <a name="calling-a-service-operation-asynchronously"></a>Asynchronní volání operace služby  
 V následujícím příkladu volání operace služby asynchronně voláním <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> a <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#onasyncexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#onasyncexecutioncomplete)]  
  
 Vzhledem k tomu, že nebudou vrácena žádná data, není přiřazena hodnoty vrácené provádění. Jediné, požadavek byl úspěšný je, že žádné <xref:System.Data.Services.Client.DataServiceQueryException> je vyvolána.  
  
 Následující příklad asynchronně volá stejné operace služby s použitím <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#callserviceoperationqueryasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#callserviceoperationqueryasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#onasyncqueryexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#onasyncqueryexecutioncomplete)]  
  
## <a name="see-also"></a>Viz také  
 [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
