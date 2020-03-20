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
# <a name="discoveryclient-and-dynamicendpoint"></a><span data-ttu-id="7e1a7-102">Objekty DiscoveryClient a DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="7e1a7-102">DiscoveryClient and DynamicEndpoint</span></span>
<span data-ttu-id="7e1a7-103"><xref:System.ServiceModel.Discovery.DiscoveryClient>a <xref:System.ServiceModel.Discovery.DynamicEndpoint> jsou dvě třídy používané na straně klienta k vyhledávání služeb.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-103"><xref:System.ServiceModel.Discovery.DiscoveryClient> and <xref:System.ServiceModel.Discovery.DynamicEndpoint> are two classes used on the client side to search for services.</span></span> <span data-ttu-id="7e1a7-104"><xref:System.ServiceModel.Discovery.DiscoveryClient>Poskytuje seznam služeb, které odpovídají určité sadě kritérií a umožňují připojení ke službám.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> provides you with a list of services that match a specific set of criteria and allows you to connect to the services.</span></span> <span data-ttu-id="7e1a7-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint>provádí stejnou operaci a navíc se automaticky připojí k jedné ze služeb, které byly nalezeny.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint> performs the same operation and in addition, automatically connects to one of the services that was found.</span></span> <span data-ttu-id="7e1a7-106">Libovolný koncový bod lze <xref:System.ServiceModel.Discovery.DynamicEndpoint>provést do , kritéria vyhledávání lze <xref:System.ServiceModel.Discovery.DynamicEndpoint> také přidat v konfiguraci, tedy je užitečné, když potřebujete zjišťování ve vašem řešení, ale nechcete změnit logiku klienta – stačí upravit koncové body.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-106">Any endpoint can be made into a <xref:System.ServiceModel.Discovery.DynamicEndpoint>, the search criteria can also be added in configuration, thus <xref:System.ServiceModel.Discovery.DynamicEndpoint> is useful when you need discovery in your solution but do not want to modify the client logic – you only need to modify the endpoints.</span></span> <span data-ttu-id="7e1a7-107"><xref:System.ServiceModel.Discovery.DiscoveryClient>na druhé straně lze získat jemnější kontrolu nad vaší vyhledávací operací.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-107"><xref:System.ServiceModel.Discovery.DiscoveryClient> on the other hand can be used to gain finer control over your search operation.</span></span> <span data-ttu-id="7e1a7-108">Použití a výhody každého z nich jsou zpracovány níže.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-108">The uses and benefits of each are elaborated below.</span></span>  
  
## <a name="discoveryclient"></a><span data-ttu-id="7e1a7-109">Klient zjišťování</span><span class="sxs-lookup"><span data-stu-id="7e1a7-109">DiscoveryClient</span></span>  
 <span data-ttu-id="7e1a7-110">Definuje <xref:System.ServiceModel.Discovery.DiscoveryClient> synchronní a asynchronní Find metody <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> a události.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-110">The <xref:System.ServiceModel.Discovery.DiscoveryClient> defines synchronous and asynchronous Find methods, <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events.</span></span>  <span data-ttu-id="7e1a7-111">Definuje také synchronní a asynchronní Resolve metody <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> a událost.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-111">It also defines synchronous and asynchronous Resolve methods and a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> event.</span></span> <span data-ttu-id="7e1a7-112">Pomocí <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metod <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> or vyhledejte služby.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-112">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> or <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> methods to search for services.</span></span> <span data-ttu-id="7e1a7-113">Obě tyto metody <xref:System.ServiceModel.Discovery.FindCriteria> přijmout instanci, která umožňuje zadat názvy typů smlouvy, obory, maximální počet požadovaných výsledků a pravidla pro porovnávání oboru.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-113">Both of these methods take a <xref:System.ServiceModel.Discovery.FindCriteria> instance that allows you to specify contract type names, scopes, maximum number of results requested, and scope matching rules.</span></span> <span data-ttu-id="7e1a7-114">A <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> události lze použít při <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> volání metody.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-114">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events can be used when calling the <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> method.</span></span> <span data-ttu-id="7e1a7-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged>je aktivována <xref:System.ServiceModel.Discovery.DiscoveryClient> vždy, když obdrží odpověď ze služby.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> is fired whenever the <xref:System.ServiceModel.Discovery.DiscoveryClient> receives a response from a service.</span></span> <span data-ttu-id="7e1a7-116">Lze jej použít k zobrazení indikátoru průběhu zobrazujícího průběh operace hledání.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-116">It can be used to display a progress bar showing the progress of the find operation.</span></span> <span data-ttu-id="7e1a7-117">Může být také použit k jednání o hledání odpovědí, jak jsou přijímány.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-117">It can also be used to act on find responses as they are received.</span></span> <span data-ttu-id="7e1a7-118">Událost <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> je aktivována po dokončení operace hledání.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-118">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> event is fired when the find operation completes.</span></span> <span data-ttu-id="7e1a7-119">K tomu může dojít, protože byl přijat maximální <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> počet odpovědí nebo pokud uplynula.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-119">This may happen because the maximum number of responses has been received or if the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> has elapsed.</span></span> <span data-ttu-id="7e1a7-120">Po dokončení operace hledání jsou vráceny <xref:System.ServiceModel.Discovery.FindResponse> výsledky v instanci.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-120">When the find operation completes the results are returned in a <xref:System.ServiceModel.Discovery.FindResponse> instance.</span></span> <span data-ttu-id="7e1a7-121">Obsahuje <xref:System.ServiceModel.Discovery.FindResponse> kolekci, <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> která obsahuje adresy, názvy typů smlouvy, rozšíření, poslouchat identifikátory URI a obory odpovídajících služeb.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-121">The <xref:System.ServiceModel.Discovery.FindResponse> contains a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> which contains the addresses, contract type names, extensions, listen URIs, and scopes of the matching services.</span></span> <span data-ttu-id="7e1a7-122">Tyto informace pak můžete použít k připojení a volání jedné z odpovídajících služeb.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-122">You can then use this information to connect to and call one of the matching services.</span></span> <span data-ttu-id="7e1a7-123">Následující příklad ukazuje, jak volat metodu System.ServiceModel.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) a použít vrácená metadata k volání nalezené služby.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-123">The following example shows how to call the System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) method and use the returned metadata to call the found service.</span></span> <span data-ttu-id="7e1a7-124">Výhodou použití <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> je, že můžete uložit do mezipaměti seznam koncových bodů, které jste našli, a použít je později.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-124">A benefit of using <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> is that you can cache the list of endpoints you’ve found and use them at a later time.</span></span> <span data-ttu-id="7e1a7-125">Pomocí této mezipaměti můžete vytvořit vlastní logiku pro zpracování různých podmínek selhání.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-125">With this cache, you can build custom logic to handle various failure conditions.</span></span>  
  
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
  
 <span data-ttu-id="7e1a7-126">Následující příklad ukazuje, jak provést operaci hledání asynchronně.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-126">The following example shows how to perform a find operation asynchronously.</span></span>  
  
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
  
 <span data-ttu-id="7e1a7-127">Pomocí <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> metod <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> a vyhledejte službu na základě její adresy koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-127">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> and <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> methods to locate a service based on its endpoint address.</span></span> <span data-ttu-id="7e1a7-128">To je užitečné v případě, že adresa koncového bodu není adresovatelná v síti.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-128">This is useful when the endpoint address is not network addressable.</span></span> <span data-ttu-id="7e1a7-129">Resolve Metody trvat <xref:System.ServiceModel.Discovery.ResolveCriteria> instance, která umožňuje zadat adresu koncového bodu služby, kterou řešíte, maximální dobu trvání operace resolve a sadu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-129">The Resolve methods take an instance of <xref:System.ServiceModel.Discovery.ResolveCriteria> which allows you to specify the endpoint address of the service you are resolving, the maximum duration of the resolve operation, and a set of extensions.</span></span> <span data-ttu-id="7e1a7-130">Následující příklad ukazuje, jak <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> použít metodu k vyřešení služby.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-130">The following example shows how to use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> method to resolve a service.</span></span>  
  
```csharp  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a><span data-ttu-id="7e1a7-131">DynamicKá koncový bod</span><span class="sxs-lookup"><span data-stu-id="7e1a7-131">DynamicEndpoint</span></span>  
 <span data-ttu-id="7e1a7-132"><xref:System.ServiceModel.Discovery.DynamicEndpoint>je standardní koncový bod (Další informace naleznete v [tématu Standardní koncové body),](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)který provádí zjišťování a automaticky vybere odpovídající službu.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-132"><xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint (For more information, see [Standard Endpoints](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) which performs discovery and automatically selects a matching service.</span></span> <span data-ttu-id="7e1a7-133">Stačí vytvořit <xref:System.ServiceModel.Discovery.DynamicEndpoint> předávání ve smlouvě hledat a vazbu použít <xref:System.ServiceModel.Discovery.DynamicEndpoint> a předat instanci wcf klienta.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-133">Just create a <xref:System.ServiceModel.Discovery.DynamicEndpoint> passing in the contract to search for and the binding to use and pass the <xref:System.ServiceModel.Discovery.DynamicEndpoint> instance to the WCF client.</span></span> <span data-ttu-id="7e1a7-134">Následující příklad ukazuje, jak vytvořit <xref:System.ServiceModel.Discovery.DynamicEndpoint> a použít k volání služby kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-134">The following example shows how to create and use a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to call the calculator service.</span></span> <span data-ttu-id="7e1a7-135">Zjišťování se provádí při každém otevření klienta.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-135">The discovery is performed every time the client is opened.</span></span> <span data-ttu-id="7e1a7-136">Libovolný koncový bod definovaný v konfiguraci <xref:System.ServiceModel.Discovery.DynamicEndpoint> lze `kind ="dynamicEndpoint"` také převést na a přidáním atributu do prvku konfigurace koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="7e1a7-136">Any endpoint defined in configuration can also be turned into a <xref:System.ServiceModel.Discovery.DynamicEndpoint> by adding the `kind ="dynamicEndpoint"` attribute to the endpoint configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7e1a7-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e1a7-137">See also</span></span>

- [<span data-ttu-id="7e1a7-138">Zjišťování pomocí oborů</span><span class="sxs-lookup"><span data-stu-id="7e1a7-138">Discovery with Scopes</span></span>](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)
- [<span data-ttu-id="7e1a7-139">Basic</span><span class="sxs-lookup"><span data-stu-id="7e1a7-139">Basic</span></span>](../../../../docs/framework/wcf/samples/basic-sample.md)
