---
title: Volání operací služby (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1767f3a7-29d2-4834-a763-7d169693fa8b
ms.openlocfilehash: f838cbd0a1884d9fca1f12398b996cde93af453a
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937565"
---
# <a name="calling-service-operations-wcf-data-services"></a>Volání operací služby (WCF Data Services)
Protokol OData (Open Data Protocol) definuje operace služeb pro datovou službu. WCF Data Services umožňuje definovat takové operace jako metody pro datovou službu. Podobně jako u jiných prostředků datové služby se tyto operace služby řeší pomocí identifikátorů URI. Operace služby může vracet kolekce typů entit, instance typu jedna entita a primitivní typy, jako je například celé číslo a řetězec. Operace služby může také vracet `null` (`Nothing` v Visual Basic). Klientská knihovna WCF Data Services se dá použít pro přístup k operacím služby, které podporují požadavky HTTP GET. Tyto druhy operací služby jsou definovány jako metody, které používají <xref:System.ServiceModel.Web.WebGetAttribute>. Další informace najdete v tématu [provozní operace](service-operations-wcf-data-services.md).  
  
 Operace služby jsou zpřístupněny v metadatech vrácených datovou službou, která implementuje OData. V metadatech se operace služby reprezentují jako `FunctionImport` prvky. Při generování silně typovaného <xref:System.Data.Services.Client.DataServiceContext>nástroje Přidat odkaz na službu a DataSvcUtil. exe ignorují tento prvek. Z tohoto důvodu nenajdete metodu v kontextu, který lze použít k přímému volání operace služby. Můžete ale i nadále používat klienta WCF Data Services k volání operací služby jedním z těchto dvou způsobů:  
  
- Voláním metody <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> v <xref:System.Data.Services.Client.DataServiceContext>zadejte identifikátor URI operace služby spolu s případnými parametry. Tato metoda se používá pro volání jakékoli operace GET Service.  
  
- Pomocí metody <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> v <xref:System.Data.Services.Client.DataServiceContext> vytvořit objekt <xref:System.Data.Services.Client.DataServiceQuery%601>. Při volání <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>je název operace služby zadán do parametru `entitySetName`. Tato metoda vrací objekt <xref:System.Data.Services.Client.DataServiceQuery%601>, který volá operaci služby při vyčíslení nebo při volání metody <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A>. Tato metoda se používá k volání operace GET Service, která vrací kolekci. Jeden parametr lze zadat pomocí metody <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A>. Objekt <xref:System.Data.Services.Client.DataServiceQuery%601> vrácený touto metodou lze dále sestavovat proti podobně jako jakýkoli objekt dotazu. Další informace najdete v tématu [dotazování datové služby](querying-the-data-service-wcf-data-services.md).  
  
## <a name="considerations-for-calling-service-operations"></a>Předpoklady pro volání operací služby  
 Při použití klienta WCF Data Services k volání operací služby platí následující požadavky.  
  
- Při asynchronním přístupu k datové službě je nutné použít ekvivalentní asynchronní <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A>/<xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> metody v <xref:System.Data.Services.Client.DataServiceContext> nebo <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A>/<xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> <xref:System.Data.Services.Client.DataServiceQuery%601>metody na.  
  
- Klientská knihovna WCF Data Services nemůže vyhodnotit výsledky z operace služby, která vrací kolekci primitivních typů.  
  
- Klientská knihovna WCF Data Services nepodporuje volání operací POST Service. Operace služby, které jsou volány serverem HTTP POST, jsou definovány pomocí <xref:System.ServiceModel.Web.WebInvokeAttribute> s parametrem `Method="POST"`. Chcete-li volat operaci služby pomocí požadavku HTTP POST, je místo toho nutné použít <xref:System.Net.HttpWebRequest>.  
  
- <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> nelze použít k volání operace GET Service, která vrací jeden výsledek, z entity nebo primitivního typu nebo který vyžaduje více než jeden vstupní parametr. Místo toho je nutné volat metodu <xref:System.Data.Services.Client.DataServiceContext.Execute%2A>.  
  
- Zvažte vytvoření metody rozšíření pro silně typované <xref:System.Data.Services.Client.DataServiceContext> částečné třídy, které jsou generovány nástroji, které používají <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> nebo metodu <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> pro volání operace služby. To umožňuje volat operace služby přímo z kontextu. Další informace najdete v blogu [operace služby a klient WCF Data Services](https://docs.microsoft.com/archive/blogs/astoriateam/service-operations-and-the-wcf-data-services-client).  
  
- Použijete-li <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> k volání operace služby, Klientská knihovna automaticky řídí znaky dodané do <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> tím, že provádí procentuální kódování rezervovaných znaků, jako je ampersand (&) a uvozovací znaky jednoduchých uvozovek v řetězcích. Když však zavoláte jednu z metod *Execute* pro volání operace služby, musíte si pamatovat, že chcete provést tyto uvozovací znaky všech uživatelem zadaných hodnot řetězce. Jednoduché uvozovky v identifikátorech URI jsou řídicí znaky jako páry jednoduchých uvozovek.  
  
## <a name="examples-of-calling-service-operations"></a>Příklady volání operací služby  
 Tato část obsahuje následující příklady volání operací služby pomocí klientské knihovny WCF Data Services:  
  
- [Volání metody Execute&lt;T&gt; k vrácení kolekce entit](calling-service-operations-wcf-data-services.md#ExecuteIQueryable)  
  
- [Použití CreateQuery&lt;T&gt; k vrácení kolekce entit](calling-service-operations-wcf-data-services.md#CreateQueryIQueryable)  
  
- [Volání metody Execute&lt;T&gt; k vrácení jedné entity](calling-service-operations-wcf-data-services.md#ExecuteSingleEntity)  
  
- [Volání metody Execute&lt;T&gt; k vrácení kolekce primitivních hodnot](calling-service-operations-wcf-data-services.md#ExecutePrimitiveCollection)  
  
- [Volání metody Execute&lt;T&gt; k vrácení jednoduché primitivní hodnoty](calling-service-operations-wcf-data-services.md#ExecutePrimitiveValue)  
  
- [Volání operace služby, která nevrací žádná data](calling-service-operations-wcf-data-services.md#ExecuteVoid)  
  
- [Asynchronní volání operace služby](calling-service-operations-wcf-data-services.md#ExecuteAsync)  
  
<a name="ExecuteIQueryable"></a>   
### <a name="calling-executet-to-return-a-collection-of-entities"></a>Volání metody Execute\<T > k vrácení kolekce entit  
 Následující příklad volá operaci služby s názvem GetOrdersByCity, která používá řetězcový parametr `city` a vrátí <xref:System.Linq.IQueryable%601>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationiqueryable)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationiqueryable)]  
  
 V tomto příkladu operace služby vrátí kolekci `Order` objektů se souvisejícími `Order_Detail` objekty.  
  
<a name="CreateQueryIQueryable"></a>   
### <a name="using-createqueryt-to-return-a-collection-of-entities"></a>Použití CreateQuery\<T > k vrácení kolekce entit  
 Následující příklad používá <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> k vrácení <xref:System.Data.Services.Client.DataServiceQuery%601>, který se používá k volání stejné operace služby GetOrdersByCity:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationcreatequery)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationcreatequery)]  
  
 V tomto příkladu je použita metoda <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> pro přidání parametru do dotazu a metoda <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> se používá k zahrnutí souvisejících Order_Details objektů do výsledků.  
  
<a name="ExecuteSingleEntity"></a>   
### <a name="calling-executet-to-return-a-single-entity"></a>Volání metody Execute\<T > k vrácení jedné entity  
 Následující příklad volá operaci služby s názvem GetNewestOrder, která vrací pouze jednu entitu objednávky:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleentity)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleentity)]  
  
 V tomto příkladu je metoda <xref:System.Linq.Enumerable.FirstOrDefault%2A> použita k vyžádání pouze jedné entity objednávky při spuštění.  
  
<a name="ExecutePrimitiveCollection"></a>   
### <a name="calling-executet-to-return-a-collection-of-primitive-values"></a>Volání metody Execute\<T > k vrácení kolekce primitivních hodnot  
 Následující příklad volá operaci služby, která vrací kolekci řetězcových hodnot:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationEnumString](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationenumstring)]  
  
<a name="ExecutePrimitiveValue"></a>   
### <a name="calling-executet-to-return-a-single-primitive-value"></a>Volání metody Execute\<T > k vrácení jednoduché primitivní hodnoty  
 Následující příklad volá operaci služby, která vrací jednu řetězcovou hodnotu:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleint)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleint)]  
  
 V tomto příkladu je použita metoda <xref:System.Linq.Enumerable.FirstOrDefault%2A> k vyžádání pouze jedné celočíselné hodnoty při spuštění.  
  
<a name="ExecuteVoid"></a>   
### <a name="calling-a-service-operation-that-returns-no-data"></a>Volání operace služby, která nevrací žádná data  
 Následující příklad volá operaci služby, která nevrací žádná data:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationvoid)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationvoid)]  
  
 Vzhledem k tomu, že nejsou vracena data, není hodnota provedení přiřazena. Pouze indikaci, že žádost byla úspěšná, není vyvolána žádná <xref:System.Data.Services.Client.DataServiceQueryException>.  
  
<a name="ExecuteAsync"></a>   
### <a name="calling-a-service-operation-asynchronously"></a>Asynchronní volání operace služby  
 Následující příklad volá asynchronní operaci služby voláním <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> a <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncexecutioncomplete)]  
  
 Vzhledem k tomu, že nejsou vracena žádná data, hodnota vrácená spuštěním není přiřazena. Pouze indikaci, že žádost byla úspěšná, není vyvolána žádná <xref:System.Data.Services.Client.DataServiceQueryException>.  
  
 Následující příklad volá stejnou operaci služby asynchronně pomocí <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationqueryasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationqueryasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncqueryexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncqueryexecutioncomplete)]  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
