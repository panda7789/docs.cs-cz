---
title: Objekty DiscoveryClient a DynamicEndpoint
ms.date: 03/30/2017
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
ms.openlocfilehash: c6d87a04a6787725ad7c4546650485af932882b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185183"
---
# <a name="discoveryclient-and-dynamicendpoint"></a>Objekty DiscoveryClient a DynamicEndpoint
<xref:System.ServiceModel.Discovery.DiscoveryClient>a <xref:System.ServiceModel.Discovery.DynamicEndpoint> jsou dvě třídy používané na straně klienta k vyhledávání služeb. <xref:System.ServiceModel.Discovery.DiscoveryClient>Poskytuje seznam služeb, které odpovídají určité sadě kritérií a umožňují připojení ke službám. <xref:System.ServiceModel.Discovery.DynamicEndpoint>provádí stejnou operaci a navíc se automaticky připojí k jedné ze služeb, které byly nalezeny. Libovolný koncový bod lze <xref:System.ServiceModel.Discovery.DynamicEndpoint>provést do , kritéria vyhledávání lze <xref:System.ServiceModel.Discovery.DynamicEndpoint> také přidat v konfiguraci, tedy je užitečné, když potřebujete zjišťování ve vašem řešení, ale nechcete změnit logiku klienta – stačí upravit koncové body. <xref:System.ServiceModel.Discovery.DiscoveryClient>na druhé straně lze získat jemnější kontrolu nad vaší vyhledávací operací. Použití a výhody každého z nich jsou zpracovány níže.  
  
## <a name="discoveryclient"></a>Klient zjišťování  
 Definuje <xref:System.ServiceModel.Discovery.DiscoveryClient> synchronní a asynchronní Find metody <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> a události.  Definuje také synchronní a asynchronní Resolve metody <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> a událost. Pomocí <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metod <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> or vyhledejte služby. Obě tyto metody <xref:System.ServiceModel.Discovery.FindCriteria> přijmout instanci, která umožňuje zadat názvy typů smlouvy, obory, maximální počet požadovaných výsledků a pravidla pro porovnávání oboru. A <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> události lze použít při <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> volání metody. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged>je aktivována <xref:System.ServiceModel.Discovery.DiscoveryClient> vždy, když obdrží odpověď ze služby. Lze jej použít k zobrazení indikátoru průběhu zobrazujícího průběh operace hledání. Může být také použit k jednání o hledání odpovědí, jak jsou přijímány. Událost <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> je aktivována po dokončení operace hledání. K tomu může dojít, protože byl přijat maximální <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> počet odpovědí nebo pokud uplynula. Po dokončení operace hledání jsou vráceny <xref:System.ServiceModel.Discovery.FindResponse> výsledky v instanci. Obsahuje <xref:System.ServiceModel.Discovery.FindResponse> kolekci, <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> která obsahuje adresy, názvy typů smlouvy, rozšíření, poslouchat identifikátory URI a obory odpovídajících služeb. Tyto informace pak můžete použít k připojení a volání jedné z odpovídajících služeb. Následující příklad ukazuje, jak volat metodu System.ServiceModel.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) a použít vrácená metadata k volání nalezené služby. Výhodou použití <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> je, že můžete uložit do mezipaměti seznam koncových bodů, které jste našli, a použít je později. Pomocí této mezipaměti můžete vytvořit vlastní logiku pro zpracování různých podmínek selhání.  
  
```csharp
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
  
 Následující příklad ukazuje, jak provést operaci hledání asynchronně.  
  
```csharp
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
  
 Pomocí <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> metod <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> a vyhledejte službu na základě její adresy koncového bodu. To je užitečné v případě, že adresa koncového bodu není adresovatelná v síti. Resolve Metody trvat <xref:System.ServiceModel.Discovery.ResolveCriteria> instance, která umožňuje zadat adresu koncového bodu služby, kterou řešíte, maximální dobu trvání operace resolve a sadu rozšíření. Následující příklad ukazuje, jak <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> použít metodu k vyřešení služby.  
  
```csharp  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a>DynamicKá koncový bod  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>je standardní koncový bod (Další informace naleznete v [tématu Standardní koncové body),](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)který provádí zjišťování a automaticky vybere odpovídající službu. Stačí vytvořit <xref:System.ServiceModel.Discovery.DynamicEndpoint> předávání ve smlouvě hledat a vazbu použít <xref:System.ServiceModel.Discovery.DynamicEndpoint> a předat instanci wcf klienta. Následující příklad ukazuje, jak vytvořit <xref:System.ServiceModel.Discovery.DynamicEndpoint> a použít k volání služby kalkulačky. Zjišťování se provádí při každém otevření klienta. Libovolný koncový bod definovaný v konfiguraci <xref:System.ServiceModel.Discovery.DynamicEndpoint> lze `kind ="dynamicEndpoint"` také převést na a přidáním atributu do prvku konfigurace koncového bodu.  
  
```csharp  
DynamicEndpoint dynamicEndpoint = new DynamicEndpoint(ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
CalculatorServiceClient client = new CalculatorServiceClient(dynamicEndpoint);  
  
Console.WriteLine("Invoking CalculatorService");  
Console.WriteLine();  
  
double value1 = 100.00D;  
double value2 = 15.99D;  
  
double result = client.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
## <a name="see-also"></a>Viz také

- [Zjišťování pomocí oborů](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)
- [Basic](../../../../docs/framework/wcf/samples/basic-sample.md)
