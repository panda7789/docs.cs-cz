---
title: Objekty DiscoveryClient a DynamicEndpoint
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3e7c8c5700159b5568a5a455b21f738d1be43dfe
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="discoveryclient-and-dynamicendpoint"></a><span data-ttu-id="f652b-102">Objekty DiscoveryClient a DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="f652b-102">DiscoveryClient and DynamicEndpoint</span></span>
<span data-ttu-id="f652b-103"><xref:System.ServiceModel.Discovery.DiscoveryClient> a <xref:System.ServiceModel.Discovery.DynamicEndpoint> jsou dvě třídy používané na straně klienta pro vyhledání služeb.</span><span class="sxs-lookup"><span data-stu-id="f652b-103"><xref:System.ServiceModel.Discovery.DiscoveryClient> and <xref:System.ServiceModel.Discovery.DynamicEndpoint> are two classes used on the client side to search for services.</span></span> <span data-ttu-id="f652b-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> poskytuje seznam služeb, které odpovídají konkrétní nastavení kritérií a umožňuje vám umožní připojit se ke službám.</span><span class="sxs-lookup"><span data-stu-id="f652b-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> provides you with a list of services that match a specific set of criteria and allows you to connect to the services.</span></span> <span data-ttu-id="f652b-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint> provádí stejné operace a kromě toho se automaticky připojí k jedné ze služeb, které byl nalezen.</span><span class="sxs-lookup"><span data-stu-id="f652b-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint> performs the same operation and in addition, automatically connects to one of the services that was found.</span></span> <span data-ttu-id="f652b-106">Žádný koncový bod, mohou být provedeny do <xref:System.ServiceModel.Discovery.DynamicEndpoint>, kritéria hledání se dá přidat taky v konfiguraci, proto <xref:System.ServiceModel.Discovery.DynamicEndpoint> je užitečné, když potřebujete zjišťování ve vašem řešení, ale nechcete, aby k úpravě klienta logiku – potřebujete upravit koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="f652b-106">Any endpoint can be made into a <xref:System.ServiceModel.Discovery.DynamicEndpoint>, the search criteria can also be added in configuration, thus <xref:System.ServiceModel.Discovery.DynamicEndpoint> is useful when you need discovery in your solution but do not want to modify the client logic – you only need to modify the endpoints.</span></span> <span data-ttu-id="f652b-107"><xref:System.ServiceModel.Discovery.DiscoveryClient> na druhé straně může použít k získání lepší kontrolu nad vaše operace vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="f652b-107"><xref:System.ServiceModel.Discovery.DiscoveryClient> on the other hand can be used to gain finer control over your search operation.</span></span> <span data-ttu-id="f652b-108">K použití a výhody jednotlivých jsou podrobně uvedeno níže.</span><span class="sxs-lookup"><span data-stu-id="f652b-108">The uses and benefits of each are elaborated below.</span></span>  
  
## <a name="discoveryclient"></a><span data-ttu-id="f652b-109">Objekty DiscoveryClient</span><span class="sxs-lookup"><span data-stu-id="f652b-109">DiscoveryClient</span></span>  
 <span data-ttu-id="f652b-110"><xref:System.ServiceModel.Discovery.DiscoveryClient> Definuje synchronní a asynchronní metody najít <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> události.</span><span class="sxs-lookup"><span data-stu-id="f652b-110">The <xref:System.ServiceModel.Discovery.DiscoveryClient> defines synchronous and asynchronous Find methods, <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events.</span></span>  <span data-ttu-id="f652b-111">Definuje také synchronní a asynchronní metody řešení a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> událostí.</span><span class="sxs-lookup"><span data-stu-id="f652b-111">It also defines synchronous and asynchronous Resolve methods and a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> event.</span></span> <span data-ttu-id="f652b-112">Použití <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> nebo <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> metody pro vyhledání služeb.</span><span class="sxs-lookup"><span data-stu-id="f652b-112">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> or <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> methods to search for services.</span></span> <span data-ttu-id="f652b-113">Obě tyto metody trvat <xref:System.ServiceModel.Discovery.FindCriteria> instanci, která umožňuje zadat názvy typů kontrakt, obory, maximální počet výsledků požadovaný a oboru odpovídající pravidla.</span><span class="sxs-lookup"><span data-stu-id="f652b-113">Both of these methods take a <xref:System.ServiceModel.Discovery.FindCriteria> instance that allows you to specify contract type names, scopes, maximum number of results requested, and scope matching rules.</span></span> <span data-ttu-id="f652b-114"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> události lze použít při volání <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="f652b-114">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events can be used when calling the <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> method.</span></span> <span data-ttu-id="f652b-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> vždy, když je aktivována například <xref:System.ServiceModel.Discovery.DiscoveryClient> přijme odpověď ze služby.</span><span class="sxs-lookup"><span data-stu-id="f652b-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> is fired whenever the <xref:System.ServiceModel.Discovery.DiscoveryClient> receives a response from a service.</span></span> <span data-ttu-id="f652b-116">Slouží k zobrazení indikátor průběhu znázorňující průběh operace hledání.</span><span class="sxs-lookup"><span data-stu-id="f652b-116">It can be used to display a progress bar showing the progress of the find operation.</span></span> <span data-ttu-id="f652b-117">Ho lze také tak, aby fungoval na najít odpovědi přijaté.</span><span class="sxs-lookup"><span data-stu-id="f652b-117">It can also be used to act on find responses as they are received.</span></span> <span data-ttu-id="f652b-118"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> Událost je aktivována například po dokončení operace hledání.</span><span class="sxs-lookup"><span data-stu-id="f652b-118">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> event is fired when the find operation completes.</span></span> <span data-ttu-id="f652b-119">K tomu může dojít, protože byla přijata maximálního počtu odpovědí, nebo pokud <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> uplynul.</span><span class="sxs-lookup"><span data-stu-id="f652b-119">This may happen because the maximum number of responses has been received or if the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> has elapsed.</span></span> <span data-ttu-id="f652b-120">Po dokončení operace hledání v budou vráceny výsledky <xref:System.ServiceModel.Discovery.FindResponse> instance.</span><span class="sxs-lookup"><span data-stu-id="f652b-120">When the find operation completes the results are returned in a <xref:System.ServiceModel.Discovery.FindResponse> instance.</span></span> <span data-ttu-id="f652b-121"><xref:System.ServiceModel.Discovery.FindResponse> Obsahuje kolekci <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> obsahující adresy, názvy typů kontrakt, rozšíření, naslouchání identifikátory URI a obory odpovídající služby.</span><span class="sxs-lookup"><span data-stu-id="f652b-121">The <xref:System.ServiceModel.Discovery.FindResponse> contains a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> which contains the addresses, contract type names, extensions, listen URIs, and scopes of the matching services.</span></span> <span data-ttu-id="f652b-122">Pak můžete tyto informace pro připojení k a volání jednoho z odpovídající služby.</span><span class="sxs-lookup"><span data-stu-id="f652b-122">You can then use this information to connect to and call one of the matching services.</span></span> <span data-ttu-id="f652b-123">Následující příklad ukazuje, jak volat metodu System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) a použít Vrácená metadata k volání služby nalezen.</span><span class="sxs-lookup"><span data-stu-id="f652b-123">The following example shows how to call the System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) method and use the returned metadata to call the found service.</span></span> <span data-ttu-id="f652b-124">Výhodou použití <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> je, že můžete mezipaměti seznamu koncových bodů našli jste a použít je později.</span><span class="sxs-lookup"><span data-stu-id="f652b-124">A benefit of using <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> is that you can cache the list of endpoints you’ve found and use them at a later time.</span></span> <span data-ttu-id="f652b-125">Pomocí této mezipaměti můžete vytvořit vlastní logiky pro zpracování různých podmínky při selhání.</span><span class="sxs-lookup"><span data-stu-id="f652b-125">With this cache, you can build custom logic to handle various failure conditions.</span></span>  
  
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
  
 <span data-ttu-id="f652b-126">Následující příklad ukazuje, jak provést operaci hledání asynchronně.</span><span class="sxs-lookup"><span data-stu-id="f652b-126">The following example shows how to perform a find operation asynchronously.</span></span>  
  
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
  
 <span data-ttu-id="f652b-127">Další informace o tom, jak asynchronní najít volání najdete v tématu [asynchronní najít](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md).</span><span class="sxs-lookup"><span data-stu-id="f652b-127">For more information about making asynchronous find calls, see [Asynchronous Find](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md).</span></span>  
  
 <span data-ttu-id="f652b-128">Použití <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> metody najít službu, závisí na jeho adresa koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="f652b-128">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> and <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> methods to locate a service based on its endpoint address.</span></span> <span data-ttu-id="f652b-129">To je užitečné, když adresa koncového bodu není adresovatelné sítě.</span><span class="sxs-lookup"><span data-stu-id="f652b-129">This is useful when the endpoint address is not network addressable.</span></span> <span data-ttu-id="f652b-130">Vyřešte metody přijímají instanci <xref:System.ServiceModel.Discovery.ResolveCriteria> který umožňuje zadat adresu koncového bodu služby se řešení, maximální délka trvání operace řešení a sadu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="f652b-130">The Resolve methods take an instance of <xref:System.ServiceModel.Discovery.ResolveCriteria> which allows you to specify the endpoint address of the service you are resolving, the maximum duration of the resolve operation, and a set of extensions.</span></span> <span data-ttu-id="f652b-131">Následující příklad ukazuje způsob použití <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> metoda řešení služby.</span><span class="sxs-lookup"><span data-stu-id="f652b-131">The following example shows how to use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> method to resolve a service.</span></span>  
  
```  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a><span data-ttu-id="f652b-132">DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="f652b-132">DynamicEndpoint</span></span>  
 <span data-ttu-id="f652b-133"><xref:System.ServiceModel.Discovery.DynamicEndpoint> je standardní koncový bod (Další informace najdete v tématu [standardní koncové body](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) který provádí zjišťování a automaticky vybere odpovídající služby.</span><span class="sxs-lookup"><span data-stu-id="f652b-133"><xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint (For more information, see [Standard Endpoints](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) which performs discovery and automatically selects a matching service.</span></span> <span data-ttu-id="f652b-134">Jenom vytvářet <xref:System.ServiceModel.Discovery.DynamicEndpoint> předávání v kontrakt pro hledání a vazba k použití a předávat <xref:System.ServiceModel.Discovery.DynamicEndpoint> instance pro klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="f652b-134">Just create a <xref:System.ServiceModel.Discovery.DynamicEndpoint> passing in the contract to search for and the binding to use and pass the <xref:System.ServiceModel.Discovery.DynamicEndpoint> instance to the WCF client.</span></span> <span data-ttu-id="f652b-135">Následující příklad ukazuje, jak vytvořit a použít <xref:System.ServiceModel.Discovery.DynamicEndpoint> volat službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="f652b-135">The following example shows how to create and use a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to call the calculator service.</span></span> <span data-ttu-id="f652b-136">Pokaždé, když je otevřen klienta se provádí zjišťování.</span><span class="sxs-lookup"><span data-stu-id="f652b-136">The discovery is performed every time the client is opened.</span></span> <span data-ttu-id="f652b-137">Žádný koncový bod definované v konfiguraci můžete také změnit na <xref:System.ServiceModel.Discovery.DynamicEndpoint> přidáním `kind ="dynamicEndpoint"` atribut element konfigurace koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="f652b-137">Any endpoint defined in configuration can also be turned into a <xref:System.ServiceModel.Discovery.DynamicEndpoint> by adding the `kind ="dynamicEndpoint"` attribute to the endpoint configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f652b-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="f652b-138">See Also</span></span>  
 [<span data-ttu-id="f652b-139">Zjišťování pomocí oborů</span><span class="sxs-lookup"><span data-stu-id="f652b-139">Discovery with Scopes</span></span>](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)  
 [<span data-ttu-id="f652b-140">Asynchronní hledání</span><span class="sxs-lookup"><span data-stu-id="f652b-140">Asynchronous Find</span></span>](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md)  
 [<span data-ttu-id="f652b-141">Základy</span><span class="sxs-lookup"><span data-stu-id="f652b-141">Basic</span></span>](../../../../docs/framework/wcf/samples/basic-sample.md)
