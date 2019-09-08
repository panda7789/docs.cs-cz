---
title: Volání operací služby (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1767f3a7-29d2-4834-a763-7d169693fa8b
ms.openlocfilehash: 21ae73054935373607909902e0b3e82ba5146f43
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791144"
---
# <a name="calling-service-operations-wcf-data-services"></a>Volání operací služby (WCF Data Services)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Definuje operace služby pro datovou službu. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]slouží k definování takových operací jako metod pro datovou službu. Podobně jako u jiných prostředků datové služby se tyto operace služby řeší pomocí identifikátorů URI. Operace služby může vracet kolekce typů entit, instance typu jedna entita a primitivní typy, jako je například celé číslo a řetězec. Operace služby může také vracet `null` (`Nothing` v Visual Basic). [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klientská knihovna se dá použít pro přístup k operacím služby, které podporují požadavky HTTP GET. Tyto druhy operací služby jsou definovány jako metody, které mají <xref:System.ServiceModel.Web.WebGetAttribute> použitu. Další informace najdete v tématu [provozní operace](service-operations-wcf-data-services.md).  
  
 Operace služby jsou zpřístupněny v metadatech vrácených datovou službou, která [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]implementuje rozhraní. V metadatech se operace služby reprezentují `FunctionImport` jako prvky. Při generování silně typované <xref:System.Data.Services.Client.DataServiceContext>nástroje Přidat odkaz na službu a DataSvcUtil. exe ignorují tento prvek. Z tohoto důvodu nenajdete metodu v kontextu, který lze použít k přímému volání operace služby. Můžete ale i nadále používat [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klienta k volání operací služby jedním z těchto dvou způsobů:  
  
- Voláním <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> metody <xref:System.Data.Services.Client.DataServiceContext>na, poskytnutím identifikátoru URI operace služby spolu s parametry. Tato metoda se používá pro volání jakékoli operace GET Service.  
  
- Pomocí <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> metody <xref:System.Data.Services.Client.DataServiceContext> pro vytvoření<xref:System.Data.Services.Client.DataServiceQuery%601> objektu. Při volání <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>do `entitySetName` parametru je zadán název operace služby. Tato metoda vrátí <xref:System.Data.Services.Client.DataServiceQuery%601> objekt, který volá operaci služby při vyčíslení nebo <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> při volání metody. Tato metoda se používá k volání operace GET Service, která vrací kolekci. Jeden parametr lze zadat pomocí <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metody. <xref:System.Data.Services.Client.DataServiceQuery%601> Objekt vrácený touto metodou lze dále sestavovat proti podobně jako jakýkoli objekt dotazu. Další informace najdete v tématu [dotazování datové služby](querying-the-data-service-wcf-data-services.md).  
  
## <a name="considerations-for-calling-service-operations"></a>Předpoklady pro volání operací služby  
 Následující požadavky platí při použití [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klienta k volání operací služby.  
  
- Při asynchronním přístupu <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> k datové službě je nutné použít ekvivalentní asynchronní / <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> metody na <xref:System.Data.Services.Client.DataServiceContext> nebo <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> metody na <xref:System.Data.Services.Client.DataServiceQuery%601>.  
  
- [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klientská knihovna nemůže vyhodnotit výsledky z operace služby, která vrací kolekci primitivních typů.  
  
- [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klientská knihovna nepodporuje volání operací post Service. Operace služby, které jsou volány serverem HTTP POST, jsou definovány pomocí <xref:System.ServiceModel.Web.WebInvokeAttribute> `Method="POST"` parametru s parametrem. Chcete-li volat operaci služby pomocí požadavku HTTP POST, je nutné místo toho použít <xref:System.Net.HttpWebRequest>.  
  
- Nemůžete <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> použít k volání operace Get Service, která vrací jeden výsledek, z entity nebo primitivního typu nebo který vyžaduje více než jeden vstupní parametr. Místo toho je nutné volat <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> metodu.  
  
- Zvažte vytvoření metody rozšíření pro částečnou třídu silného <xref:System.Data.Services.Client.DataServiceContext> typu, která je generována nástroji, která používá <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> buď <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> metodu, nebo k volání operace služby. To umožňuje volat operace služby přímo z kontextu. Další informace najdete v blogu [operace služby a klient WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=215668).  
  
- Když použijete <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> k volání operace služby, Klientská knihovna automaticky řídí znaky, které jsou <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> dodány do, tím, že provádí procentuální kódování rezervovaných znaků, jako je ampersand (&) a uvozovací znaky jednoduchých uvozovek v. zobrazen. Když však zavoláte jednu z metod *Execute* pro volání operace služby, musíte si pamatovat, že chcete provést tyto uvozovací znaky všech uživatelem zadaných hodnot řetězce. Jednoduché uvozovky v identifikátorech URI jsou řídicí znaky jako páry jednoduchých uvozovek.  
  
## <a name="examples-of-calling-service-operations"></a>Příklady volání operací služby  
 Tato část obsahuje následující příklady volání operací služby pomocí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientské knihovny:  
  
- [Volání metody&lt;Execute&gt; T pro vrácení kolekce entit](calling-service-operations-wcf-data-services.md#ExecuteIQueryable)  
  
- [Vrácení kolekce&lt;entit&gt; pomocí CreateQuery T](calling-service-operations-wcf-data-services.md#CreateQueryIQueryable)  
  
- [Volání metody&lt;Execute&gt; T pro vrácení jedné entity](calling-service-operations-wcf-data-services.md#ExecuteSingleEntity)  
  
- [Volání metody&lt;Execute&gt; T pro vrácení kolekce primitivních hodnot](calling-service-operations-wcf-data-services.md#ExecutePrimitiveCollection)  
  
- [Volání metody&lt;Execute&gt; T pro vrácení jednoduché primitivní hodnoty](calling-service-operations-wcf-data-services.md#ExecutePrimitiveValue)  
  
- [Volání operace služby, která nevrací žádná data](calling-service-operations-wcf-data-services.md#ExecuteVoid)  
  
- [Asynchronní volání operace služby](calling-service-operations-wcf-data-services.md#ExecuteAsync)  
  
<a name="ExecuteIQueryable"></a>   
### <a name="calling-executet-to-return-a-collection-of-entities"></a>Volání metody\<Execute T > pro vrácení kolekce entit  
 Následující příklad volá operaci služby s názvem GetOrdersByCity, která přijímá řetězcový parametr `city` a <xref:System.Linq.IQueryable%601>vrátí:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationiqueryable)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationiqueryable)]  
  
 V tomto příkladu operace služby vrátí kolekci `Order` objektů se souvisejícími `Order_Detail` objekty.  
  
<a name="CreateQueryIQueryable"></a>   
### <a name="using-createqueryt-to-return-a-collection-of-entities"></a>Použití CreateQuery\<T > k vrácení kolekce entit  
 Následující příklad používá <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> k vrácení typu <xref:System.Data.Services.Client.DataServiceQuery%601> , který se používá k volání stejné operace služby GetOrdersByCity:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationcreatequery)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationcreatequery)]  
  
 V tomto příkladu <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metoda slouží k přidání parametru do dotazu <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> a metoda slouží k zahrnutí souvisejících objektů Order_Details ve výsledcích.  
  
<a name="ExecuteSingleEntity"></a>   
### <a name="calling-executet-to-return-a-single-entity"></a>Volání metody\<Execute T > pro vrácení jedné entity  
 Následující příklad volá operaci služby s názvem GetNewestOrder, která vrací pouze jednu entitu objednávky:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleentity)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleentity)]  
  
 V tomto příkladu <xref:System.Linq.Enumerable.FirstOrDefault%2A> se metoda používá k vyžádání pouze jedné entity objednávky při spuštění.  
  
<a name="ExecutePrimitiveCollection"></a>   
### <a name="calling-executet-to-return-a-collection-of-primitive-values"></a>Volání metody\<Execute T > pro vrácení kolekce primitivních hodnot  
 Následující příklad volá operaci služby, která vrací kolekci řetězcových hodnot:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationEnumString](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationenumstring)]  
  
<a name="ExecutePrimitiveValue"></a>   
### <a name="calling-executet-to-return-a-single-primitive-value"></a>Volání metody\<Execute T > pro vrácení jednoduché primitivní hodnoty  
 Následující příklad volá operaci služby, která vrací jednu řetězcovou hodnotu:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleint)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleint)]  
  
 V tomto příkladu <xref:System.Linq.Enumerable.FirstOrDefault%2A> se metoda používá k vyžádání pouze jedné celočíselné hodnoty při spuštění.  
  
<a name="ExecuteVoid"></a>   
### <a name="calling-a-service-operation-that-returns-no-data"></a>Volání operace služby, která nevrací žádná data  
 Následující příklad volá operaci služby, která nevrací žádná data:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationvoid)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationvoid)]  
  
 Vzhledem k tomu, že nejsou vracena data, není hodnota provedení přiřazena. Jediným náznakem, že žádost byla úspěšná, je to <xref:System.Data.Services.Client.DataServiceQueryException> , že se neaktivuje.  
  
<a name="ExecuteAsync"></a>   
### <a name="calling-a-service-operation-asynchronously"></a>Asynchronní volání operace služby  
 Následující příklad volá asynchronní operaci služby voláním <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> a: <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncexecutioncomplete)]  
  
 Vzhledem k tomu, že nejsou vracena žádná data, hodnota vrácená spuštěním není přiřazena. Jediným náznakem, že žádost byla úspěšná, je to <xref:System.Data.Services.Client.DataServiceQueryException> , že se neaktivuje.  
  
 Následující příklad volá stejnou operaci služby asynchronně pomocí <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationqueryasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationqueryasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncqueryexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncqueryexecutioncomplete)]  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
