---
title: Objekty DiscoveryClient a DynamicEndpoint
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e3ac334d53480ba8b63cc8e8f117dd74315963c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="discoveryclient-and-dynamicendpoint"></a>Objekty DiscoveryClient a DynamicEndpoint
<xref:System.ServiceModel.Discovery.DiscoveryClient>a <xref:System.ServiceModel.Discovery.DynamicEndpoint> jsou dvě třídy používané na straně klienta pro vyhledání služeb. <xref:System.ServiceModel.Discovery.DiscoveryClient>poskytuje seznam služeb, které odpovídají konkrétní nastavení kritérií a umožňuje vám umožní připojit se ke službám. <xref:System.ServiceModel.Discovery.DynamicEndpoint>provádí stejné operace a kromě toho se automaticky připojí k jedné ze služeb, které byl nalezen. Žádný koncový bod, mohou být provedeny do <xref:System.ServiceModel.Discovery.DynamicEndpoint>, kritéria hledání se dá přidat taky v konfiguraci, proto <xref:System.ServiceModel.Discovery.DynamicEndpoint> je užitečné, když potřebujete zjišťování ve vašem řešení, ale nechcete, aby k úpravě klienta logiku – potřebujete upravit koncových bodů. <xref:System.ServiceModel.Discovery.DiscoveryClient>na druhé straně může použít k získání lepší kontrolu nad vaše operace vyhledávání. K použití a výhody jednotlivých jsou podrobně uvedeno níže.  
  
## <a name="discoveryclient"></a>Objekty DiscoveryClient  
 <xref:System.ServiceModel.Discovery.DiscoveryClient> Definuje synchronní a asynchronní metody najít <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> události.  Definuje také synchronní a asynchronní metody řešení a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> událostí. Použití <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> nebo <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> metody pro vyhledání služeb. Obě tyto metody trvat <xref:System.ServiceModel.Discovery.FindCriteria> instanci, která umožňuje zadat názvy typů kontrakt, obory, maximální počet výsledků požadovaný a oboru odpovídající pravidla. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> události lze použít při volání <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> metoda. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged>vždy, když je aktivována například <xref:System.ServiceModel.Discovery.DiscoveryClient> přijme odpověď ze služby. Slouží k zobrazení indikátor průběhu znázorňující průběh operace hledání. Ho lze také tak, aby fungoval na najít odpovědi přijaté. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> Událost je aktivována například po dokončení operace hledání. K tomu může dojít, protože byla přijata maximálního počtu odpovědí, nebo pokud <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> uplynul. Po dokončení operace hledání v budou vráceny výsledky <xref:System.ServiceModel.Discovery.FindResponse> instance. <xref:System.ServiceModel.Discovery.FindResponse> Obsahuje kolekci <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> obsahující adresy, názvy typů kontrakt, rozšíření, naslouchání identifikátory URI a obory odpovídající služby. Pak můžete tyto informace pro připojení k a volání jednoho z odpovídající služby. Následující příklad ukazuje, jak volat metodu System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) a použít Vrácená metadata k volání služby nalezen. Výhodou použití <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> je, že můžete mezipaměti seznamu koncových bodů našli jste a použít je později. Pomocí této mezipaměti můžete vytvořit vlastní logiky pro zpracování různých podmínky při selhání.  
  
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
  
 Následující příklad ukazuje, jak provést operaci hledání asynchronně.  
  
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]provedení asynchronní najít volání najdete v tématu [asynchronní najít](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md).  
  
 Použití <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> metody najít službu, závisí na jeho adresa koncového bodu. To je užitečné, když adresa koncového bodu není adresovatelné sítě. Vyřešte metody přijímají instanci <xref:System.ServiceModel.Discovery.ResolveCriteria> který umožňuje zadat adresu koncového bodu služby se řešení, maximální délka trvání operace řešení a sadu rozšíření. Následující příklad ukazuje způsob použití <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> metoda řešení služby.  
  
```  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a>DynamicEndpoint  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>je standardní koncový bod ([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [standardní koncové body](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) který provádí zjišťování a automaticky vybere odpovídající služby. Jenom vytvářet <xref:System.ServiceModel.Discovery.DynamicEndpoint> předávání v kontrakt pro hledání a vazba k použití a předávat <xref:System.ServiceModel.Discovery.DynamicEndpoint> instance pro klienta WCF. Následující příklad ukazuje, jak vytvořit a použít <xref:System.ServiceModel.Discovery.DynamicEndpoint> volat službu kalkulačky. Pokaždé, když je otevřen klienta se provádí zjišťování. Žádný koncový bod definované v konfiguraci můžete také změnit na <xref:System.ServiceModel.Discovery.DynamicEndpoint> přidáním `kind ="dynamicEndpoint"` atribut element konfigurace koncového bodu.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Zjišťování pomocí oborů](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)  
 [Asynchronní hledání](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md)  
 [Základy](../../../../docs/framework/wcf/samples/basic-sample.md)
