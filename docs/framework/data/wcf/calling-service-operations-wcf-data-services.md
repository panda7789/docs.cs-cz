---
title: Operace volání služby (wcf datové služby)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1767f3a7-29d2-4834-a763-7d169693fa8b
ms.openlocfilehash: 41aac38cec97ae1afdd3c3c051d04ff242e7729d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174352"
---
# <a name="calling-service-operations-wcf-data-services"></a>Operace volání služby (wcf datové služby)
Protokol OData (Open Data Protocol) definuje operace služby pro datovou službu. WCF Data Services umožňuje definovat tyto operace jako metody v datové službě. Stejně jako ostatní prostředky datové služby jsou tyto operace služby řešeny pomocí identifikátorů URI. Operace služby může vrátit kolekce typů entit, instance typu jedné entity a primitivní typy, například celé číslo a řetězec. Operace služby může `null` `Nothing` také vrátit (v jazyce Visual Basic). Klientskou knihovnu WCF Data Services lze použít pro přístup k operacím služby, které podporují požadavky HTTP GET. Tyto druhy operací služby jsou definovány jako metody, které mají <xref:System.ServiceModel.Web.WebGetAttribute> použít. Další informace naleznete v tématu [Service Operations](service-operations-wcf-data-services.md).  
  
 Operace služby jsou vystaveny v metadatech vrácených datovou službou, která implementuje OData. V metadatech jsou operace služby reprezentovány jako `FunctionImport` prvky. Při generování silného typu <xref:System.Data.Services.Client.DataServiceContext>nástroje Add Service Reference a DataSvcUtil.exe tento prvek ignorují. Z tohoto důvodu nenajdete metodu v kontextu, který lze použít k přímému volání operace služby. Klienta wcf datové služby však můžete stále používat k volání operací služby jedním z těchto dvou způsobů:  
  
- Voláním <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> metody na <xref:System.Data.Services.Client.DataServiceContext>, poskytování URI operace služby, spolu s všechny parametry. Tato metoda se používá k volání jakékoli operace služby GET.  
  
- Pomocí <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> metody na <xref:System.Data.Services.Client.DataServiceContext> vytvoření objektu. <xref:System.Data.Services.Client.DataServiceQuery%601> Při <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>volání je parametru dodán název `entitySetName` operace služby. Tato metoda <xref:System.Data.Services.Client.DataServiceQuery%601> vrátí objekt, který volá operaci služby <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> při výčtu nebo při volání metody. Tato metoda se používá k volání operace služby GET, které vracejí kolekci. Pomocí <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metody lze zadat jeden parametr. Objekt <xref:System.Data.Services.Client.DataServiceQuery%601> vrácený touto metodou lze dále skládá proti jako jakýkoli objekt dotazu. Další informace naleznete v [tématu Dotaz na datovou službu](querying-the-data-service-wcf-data-services.md).  
  
## <a name="considerations-for-calling-service-operations"></a>Důležité informace pro operace volání služby  
 Následující důležité informace platí při použití klienta WCF Data Services ke volání operací služby.  
  
- Při přístupu k datové službě asynchronně je nutné použít <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> ekvivalentní <xref:System.Data.Services.Client.DataServiceContext> asynchronní metody nebo metody <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> na <xref:System.Data.Services.Client.DataServiceQuery%601>.  
  
- Klientská knihovna WCF Data Services nemůže zhmotnit výsledky operace služby, která vrací kolekci primitivních typů.  
  
- Klientská knihovna WCF Data Services nepodporuje volání operací služby POST. Operace služby, které jsou volány HTTP <xref:System.ServiceModel.Web.WebInvokeAttribute> POST `Method="POST"` jsou definovány pomocí s parametrem. Chcete-li volat operaci služby pomocí požadavku HTTP <xref:System.Net.HttpWebRequest>POST, musíte místo toho použít .  
  
- Nelze použít <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> k volání operace služby GET, která vrací jeden výsledek buď entity nebo primitivní typ, nebo který vyžaduje více než jeden vstupní parametr. Místo toho je <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> nutné volat metodu.  
  
- Zvažte vytvoření metody rozšíření na <xref:System.Data.Services.Client.DataServiceContext> částečnou třídu silného typu, která je <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> generována <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> nástroji, která používá buď metodu nebo pro volání operace služby. To umožňuje volat operace služby přímo z kontextu. Další informace naleznete v příspěvku blogu [Service Operations a WCF Data Services Client](https://docs.microsoft.com/archive/blogs/astoriateam/service-operations-and-the-wcf-data-services-client).  
  
- Při volání <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> operace služby klientská knihovna automaticky unikne znaky dodané <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> provede procentuální kódování vyhrazených znaků, jako je ampersand (&) a unikání jednotlivých uvozovek v řetězcích. Však při volání jedné z *Execute* metody volat operaci služby, je nutné mít na paměti, provést toto úniku všechny hodnoty řetězce zadané uživatelem. Jednotlivé uvozovky v identifikátorech URI jsou uvozeny jako dvojice jednotlivých uvozovek.  
  
## <a name="examples-of-calling-service-operations"></a>Příklady volacích operací služby  
 Tato část obsahuje následující příklady volání operací služby pomocí klientské knihovny WCF Data Services:  
  
- [Volání&lt;spuštění&gt; T vrátit kolekci entit](calling-service-operations-wcf-data-services.md#ExecuteIQueryable)  
  
- [Vrácení kolekce&lt;&gt; entit pomocí příkazu CreateQuery T](calling-service-operations-wcf-data-services.md#CreateQueryIQueryable)  
  
- [Volání&lt;spuštění&gt; T k vrácení jedné entity](calling-service-operations-wcf-data-services.md#ExecuteSingleEntity)  
  
- [Volání&lt;spuštění&gt; T vrátit kolekci primitivních hodnot](calling-service-operations-wcf-data-services.md#ExecutePrimitiveCollection)  
  
- [Volání&lt;spuštění&gt; T vrátit jednu primitivní hodnotu](calling-service-operations-wcf-data-services.md#ExecutePrimitiveValue)  
  
- [Volání operace služby, která vrací žádná data](calling-service-operations-wcf-data-services.md#ExecuteVoid)  
  
- [Asynchronní volání servisní operace](calling-service-operations-wcf-data-services.md#ExecuteAsync)  
  
<a name="ExecuteIQueryable"></a>
### <a name="calling-executet-to-return-a-collection-of-entities"></a>Volání\<příkazu T> k vrácení kolekce entit  
 Následující příklad volá operaci služby s názvem GetOrdersByCity, která přebírá parametr řetězce `city` a vrátí <xref:System.Linq.IQueryable%601>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationiqueryable)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationiqueryable)]  
  
 V tomto příkladu vrátí operace `Order` služby `Order_Detail` kolekci objektů se souvisejícími objekty.  
  
<a name="CreateQueryIQueryable"></a>
### <a name="using-createqueryt-to-return-a-collection-of-entities"></a>Použití>\<CreateQuery T k vrácení kolekce entit  
 Následující příklad používá <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> k <xref:System.Data.Services.Client.DataServiceQuery%601> vrácení a, který se používá k volání stejné operace služby GetOrdersByCity:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationcreatequery)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationcreatequery)]  
  
 V tomto příkladu <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> se metoda používá k přidání parametru do dotazu a <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> metoda se používá k zahrnutí souvisejících Order_Details objektů ve výsledcích.  
  
<a name="ExecuteSingleEntity"></a>
### <a name="calling-executet-to-return-a-single-entity"></a>Volání\<spuštění T> k vrácení jedné entity  
 Následující příklad volá operaci služby s názvem GetNewestOrder, která vrací pouze jednu entitu Objednávka:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleentity)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleentity)]  
  
 V tomto příkladu <xref:System.Linq.Enumerable.FirstOrDefault%2A> se metoda používá k vyžádání pouze jedné entity Objednávky při provádění.  
  
<a name="ExecutePrimitiveCollection"></a>
### <a name="calling-executet-to-return-a-collection-of-primitive-values"></a>Volání\<spuštění T> vrátit kolekci primitivních hodnot  
 Následující příklad volá operaci služby, která vrací kolekci řetězcových hodnot:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationEnumString](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationenumstring)]  
  
<a name="ExecutePrimitiveValue"></a>
### <a name="calling-executet-to-return-a-single-primitive-value"></a>Volání\<spuštění T> vrátit jednu primitivní hodnotu  
 Následující příklad volá operaci služby, která vrací hodnotu jednoho řetězce:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleint)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleint)]  
  
 Opět v tomto <xref:System.Linq.Enumerable.FirstOrDefault%2A> příkladu metoda se používá k vyžádání pouze jednu celou hodnotu při spuštění.  
  
<a name="ExecuteVoid"></a>
### <a name="calling-a-service-operation-that-returns-no-data"></a>Volání operace služby, která vrací žádná data  
 Následující příklad volá operaci služby, která vrací žádná data:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationvoid)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationvoid)]  
  
 Protože nejsou vrácena data, není přiřazena hodnota spuštění. Jediným ukazatelem, že požadavek byl <xref:System.Data.Services.Client.DataServiceQueryException> úspěšný, je, že ne je vyvolána.  
  
<a name="ExecuteAsync"></a>
### <a name="calling-a-service-operation-asynchronously"></a>Asynchronní volání servisní operace  
 Následující příklad volá operaci služby asynchronně <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>voláním a :  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncexecutioncomplete)]  
  
 Vzhledem k tomu, že jsou vrácena žádná data, není přiřazena hodnota vrácená spuštěním. Jediným ukazatelem, že požadavek byl <xref:System.Data.Services.Client.DataServiceQueryException> úspěšný, je, že ne je vyvolána.  
  
 Následující příklad volá stejnou operaci služby asynchronně pomocí <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>:  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationqueryasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationqueryasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncqueryexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncqueryexecutioncomplete)]  
  
## <a name="see-also"></a>Viz také

- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
