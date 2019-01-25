---
title: Objekty DiscoveryClient a DynamicEndpoint
ms.date: 03/30/2017
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
ms.openlocfilehash: 6e7b1cf13309ba6fc1da424649c667efe255278e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709985"
---
# <a name="discoveryclient-and-dynamicendpoint"></a>Objekty DiscoveryClient a DynamicEndpoint
<xref:System.ServiceModel.Discovery.DiscoveryClient> a <xref:System.ServiceModel.Discovery.DynamicEndpoint> jsou dvě třídy použitá k vyhledání služby na straně klienta. <xref:System.ServiceModel.Discovery.DiscoveryClient> poskytuje seznam služeb, které odpovídají konkrétní sadu kritérií a umožňuje vám umožní připojit se ke službám. <xref:System.ServiceModel.Discovery.DynamicEndpoint> provede stejné operace a kromě toho se automaticky připojí k jedné ze služeb, které se nacházejí. Lze je převést libovolný koncový bod <xref:System.ServiceModel.Discovery.DynamicEndpoint>, kritéria hledání je možné přidat i v konfiguraci, proto <xref:System.ServiceModel.Discovery.DynamicEndpoint> je užitečné, když potřebujete zjišťování ve vašem řešení, ale nechcete, aby k úpravě klienta logiky – je potřeba jenom změnit koncových bodů. <xref:System.ServiceModel.Discovery.DiscoveryClient> na druhé straně může použít k získání lepší kontrolu nad vyhledávací operace. Použití a výhodami každého z nich jsou rozpracovaného níže.  
  
## <a name="discoveryclient"></a>DiscoveryClient  
 <xref:System.ServiceModel.Discovery.DiscoveryClient> Definuje synchronní a asynchronní metody najít <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> události.  Také definuje synchronní a asynchronní metody řešení a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> událostí. Použití <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> nebo <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> metod pro vyhledání služeb. Obě tyto metody trvat <xref:System.ServiceModel.Discovery.FindCriteria> instanci, která umožňuje zadat názvy typů kontraktu, obory, maximální počet výsledků požadované a pravidel oboru. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> události lze použít při volání <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> metody. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> se aktivuje vždy, když <xref:System.ServiceModel.Discovery.DiscoveryClient> obdrží odpověď ze služby. Slouží k zobrazení průběhu zobrazuje průběh operace find. To lze také tak, aby fungoval na najít odpovědi přijaté. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> Událost je aktivována po dokončení operace find. K tomu může dojít, protože maximální počet odpovědi byla přijata nebo pokud <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> uplynul. Po dokončení operace find výsledky jsou vráceny v <xref:System.ServiceModel.Discovery.FindResponse> instance. <xref:System.ServiceModel.Discovery.FindResponse> Obsahuje kolekci <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> obsahující adresy, názvy typů kontraktu, rozšíření, vlastností listenurimode nastavenou na identifikátory URI a obory odpovídající služby. Pak můžete tyto informace k připojení a volání jednoho z odpovídající služby. Následující příklad ukazuje, jak volat metodu System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) a použití vrácených metadat pro volání nalezené služby. Výhodou použití <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> je, že můžete ukládat do mezipaměti seznamu koncových bodů našli a využít později. S touto mezipamětí můžete vytvořit vlastní logiky, která by různé podmínky při selhání.  
  
```  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
FindCriteria criteria = new FindCriteria(typeof(ICalculatorService));  
FindResponse fr = dc.Find(criteria);  
  
if (fr.Endpoints.Count > 0)  
{  
   EndpointAddress ep = fr.Endpoints[0].Address;  
   CalculatorServiceClient client = new CalculatorServiceClient();  
  
    // Connect to the discovered service endpoint  
   client.Endpoint.Address = endpointAddress;  
   Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
   double value1 = 100.00D;  
   double value2 = 15.99D;  
  
   // Call the Add service operation.  
   double result = client.Add(value1, value2);  
   Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
}  
else  
   Console.WriteLine("No matching endpoints found");  
```  
  
 Následující příklad ukazuje, jak provádět operace find asynchronně.  
  
```  
static void FindServiceAsync()  
{  
   DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());   
   dc.FindCompleted += new EventHandler<FindCompletedEventArgs>( discoveryClient_FindCompleted);  
   dc.FindProgressChanged += new EventHandler<FindProgressChangedEventArgs>(discoveryClient_FindProgressChanged);  
   dc.FindAsync(new FindCriteria(typeof(ICalculatorService)));   
}   
static void discoveryClient_FindProgressChanged(object sender, FindProgressChangedEventArgs e)  
{  
   Console.WriteLine("Found service at: " + e.EndpointDiscoveryMetadata.Address  
}   
  
static void discoveryClient_FindCompleted(object sender, FindCompletedEventArgs e)  
{    
      if (e.Result.Endpoints.Count > 0)  
            {  
                EndpointAddress ep = e.Result.Endpoints[0].Address;  
                CalculatorServiceClient client = new CalculatorServiceClient();  
  
                // Connect to the discovered service endpoint  
                client.Endpoint.Address = ep;  
                Console.WriteLine("Invoking CalculatorService at {0}", ep);  
  
                double value1 = 100.00D;  
                double value2 = 15.99D;  
  
                double result = client.Add(value1, value2);  
                Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
            }  
            else  
                Console.WriteLine("No matching endpoints found");  
  
        }  
```
  
 Použití <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> metody k vyhledání služby závisí na jeho adresa koncového bodu. To je užitečné, pokud adresa koncového bodu není adresovatelný síti. Metody Resolve trvat instance <xref:System.ServiceModel.Discovery.ResolveCriteria> které můžete zadat adresu koncového bodu služby jsou řešení maximální doba trvání operace řešení a sadu rozšíření. Následující příklad ukazuje způsob použití <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> metody řešení služby.  
  
```  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a>DynamicEndpoint  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint> je standardní koncový bod (Další informace najdete v tématu [standardních koncových bodů](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) který provádí zjišťování a automaticky vybere odpovídající službu. Stačí vytvořit jenom <xref:System.ServiceModel.Discovery.DynamicEndpoint> předávání v kontraktu pro hledání a vazba k použití a předat <xref:System.ServiceModel.Discovery.DynamicEndpoint> instanci klienta WCF. Následující příklad ukazuje, jak vytvořit a používat <xref:System.ServiceModel.Discovery.DynamicEndpoint> volat službu kalkulačky. Zjišťují se pokaždé, když se klient je otevřen. Libovolný koncový bod definovaný v konfiguraci je možné zapnout také do <xref:System.ServiceModel.Discovery.DynamicEndpoint> tak, že přidáte `kind ="dynamicEndpoint"` atribut na element konfigurace koncového bodu.  
  
```  
DynamicEndpoint dynamicEndpoint = new DynamicEndpoint(ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
CalculatorServiceClient client = new CalculatorServiceClient(dynamicEndpoint);  
  
Console.WriteLine("Invoking CalculatorService");  
Console.WriteLine();  
  
double value1 = 100.00D;  
double value2 = 15.99D;  
  
double result = client.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
## <a name="see-also"></a>Viz také:
- [Zjišťování pomocí oborů](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)
- [Základy](../../../../docs/framework/wcf/samples/basic-sample.md)
