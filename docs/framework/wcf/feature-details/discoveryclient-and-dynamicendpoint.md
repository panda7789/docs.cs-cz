---
title: Objekty DiscoveryClient a DynamicEndpoint
ms.date: 03/30/2017
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
ms.openlocfilehash: 455ccc7f09c13a33b4034099b16b116fd3a8dbdf
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895297"
---
# <a name="discoveryclient-and-dynamicendpoint"></a><span data-ttu-id="41cf7-102">Objekty DiscoveryClient a DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="41cf7-102">DiscoveryClient and DynamicEndpoint</span></span>
<span data-ttu-id="41cf7-103"><xref:System.ServiceModel.Discovery.DiscoveryClient>a <xref:System.ServiceModel.Discovery.DynamicEndpoint> jsou dvě třídy, které se používají na straně klienta pro hledání služeb.</span><span class="sxs-lookup"><span data-stu-id="41cf7-103"><xref:System.ServiceModel.Discovery.DiscoveryClient> and <xref:System.ServiceModel.Discovery.DynamicEndpoint> are two classes used on the client side to search for services.</span></span> <span data-ttu-id="41cf7-104"><xref:System.ServiceModel.Discovery.DiscoveryClient>poskytuje seznam služeb, které odpovídají určité sadě kritérií, a umožňuje se připojit ke službám.</span><span class="sxs-lookup"><span data-stu-id="41cf7-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> provides you with a list of services that match a specific set of criteria and allows you to connect to the services.</span></span> <span data-ttu-id="41cf7-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint>provede stejnou operaci a navíc se automaticky připojí k jedné ze služeb, které byly nalezeny.</span><span class="sxs-lookup"><span data-stu-id="41cf7-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint> performs the same operation and in addition, automatically connects to one of the services that was found.</span></span> <span data-ttu-id="41cf7-106">Libovolný koncový bod lze navázat do <xref:System.ServiceModel.Discovery.DynamicEndpoint>konfigurace, kritéria hledání je také možné přidat v konfiguraci, což <xref:System.ServiceModel.Discovery.DynamicEndpoint> je užitečné v případě, že budete potřebovat zjišťování ve vašem řešení, ale nechcete měnit klientskou logiku – stačí pouze upravit koncové body.</span><span class="sxs-lookup"><span data-stu-id="41cf7-106">Any endpoint can be made into a <xref:System.ServiceModel.Discovery.DynamicEndpoint>, the search criteria can also be added in configuration, thus <xref:System.ServiceModel.Discovery.DynamicEndpoint> is useful when you need discovery in your solution but do not want to modify the client logic – you only need to modify the endpoints.</span></span> <span data-ttu-id="41cf7-107"><xref:System.ServiceModel.Discovery.DiscoveryClient>na druhé straně je možné použít k získání přesnější kontroly nad operací vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="41cf7-107"><xref:System.ServiceModel.Discovery.DiscoveryClient> on the other hand can be used to gain finer control over your search operation.</span></span> <span data-ttu-id="41cf7-108">Využití a výhody z nich jsou vypracované níže.</span><span class="sxs-lookup"><span data-stu-id="41cf7-108">The uses and benefits of each are elaborated below.</span></span>  
  
## <a name="discoveryclient"></a><span data-ttu-id="41cf7-109">Objektem DiscoveryClient zahozena</span><span class="sxs-lookup"><span data-stu-id="41cf7-109">DiscoveryClient</span></span>  
 <span data-ttu-id="41cf7-110">Definuje synchronní a asynchronní <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> metody Find a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> události. <xref:System.ServiceModel.Discovery.DiscoveryClient></span><span class="sxs-lookup"><span data-stu-id="41cf7-110">The <xref:System.ServiceModel.Discovery.DiscoveryClient> defines synchronous and asynchronous Find methods, <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events.</span></span>  <span data-ttu-id="41cf7-111">Definuje také synchronní a asynchronní metody Resolve a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> událost.</span><span class="sxs-lookup"><span data-stu-id="41cf7-111">It also defines synchronous and asynchronous Resolve methods and a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> event.</span></span> <span data-ttu-id="41cf7-112">Pomocí metod <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A>nebovyhledejteslužby. <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A></span><span class="sxs-lookup"><span data-stu-id="41cf7-112">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> or <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> methods to search for services.</span></span> <span data-ttu-id="41cf7-113">Obě tyto metody přijímají <xref:System.ServiceModel.Discovery.FindCriteria> instanci, která umožňuje zadat názvy typů kontraktů, obory, maximální počet požadovaných výsledků a pravidla pro porovnání oboru.</span><span class="sxs-lookup"><span data-stu-id="41cf7-113">Both of these methods take a <xref:System.ServiceModel.Discovery.FindCriteria> instance that allows you to specify contract type names, scopes, maximum number of results requested, and scope matching rules.</span></span> <span data-ttu-id="41cf7-114">Události <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> lze použít při volání metody.</span><span class="sxs-lookup"><span data-stu-id="41cf7-114">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events can be used when calling the <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> method.</span></span> <span data-ttu-id="41cf7-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged>se aktivuje pokaždé, <xref:System.ServiceModel.Discovery.DiscoveryClient> když přijme odpověď ze služby.</span><span class="sxs-lookup"><span data-stu-id="41cf7-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> is fired whenever the <xref:System.ServiceModel.Discovery.DiscoveryClient> receives a response from a service.</span></span> <span data-ttu-id="41cf7-116">Dá se použít k zobrazení indikátoru průběhu znázorňujícího průběh operace Find.</span><span class="sxs-lookup"><span data-stu-id="41cf7-116">It can be used to display a progress bar showing the progress of the find operation.</span></span> <span data-ttu-id="41cf7-117">Dá se použít i k tomu, aby se při přijetí odpovědi vypracovaly.</span><span class="sxs-lookup"><span data-stu-id="41cf7-117">It can also be used to act on find responses as they are received.</span></span> <span data-ttu-id="41cf7-118"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> Událost se aktivuje po dokončení operace Find.</span><span class="sxs-lookup"><span data-stu-id="41cf7-118">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> event is fired when the find operation completes.</span></span> <span data-ttu-id="41cf7-119">K tomu může dojít, protože byl přijat maximální počet odpovědí nebo pokud <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> uplynula platnost.</span><span class="sxs-lookup"><span data-stu-id="41cf7-119">This may happen because the maximum number of responses has been received or if the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> has elapsed.</span></span> <span data-ttu-id="41cf7-120">Po dokončení operace Find se výsledky vrátí do <xref:System.ServiceModel.Discovery.FindResponse> instance.</span><span class="sxs-lookup"><span data-stu-id="41cf7-120">When the find operation completes the results are returned in a <xref:System.ServiceModel.Discovery.FindResponse> instance.</span></span> <span data-ttu-id="41cf7-121"><xref:System.ServiceModel.Discovery.FindResponse> Obsahuje kolekci,kteráobsahujeadresy,názvytypůkontraktů,rozšíření,identifikátorůURInasloucháníaobory<xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> odpovídajícího služby.</span><span class="sxs-lookup"><span data-stu-id="41cf7-121">The <xref:System.ServiceModel.Discovery.FindResponse> contains a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> which contains the addresses, contract type names, extensions, listen URIs, and scopes of the matching services.</span></span> <span data-ttu-id="41cf7-122">Tyto informace pak můžete použít k připojení a volání jedné z těchto služeb.</span><span class="sxs-lookup"><span data-stu-id="41cf7-122">You can then use this information to connect to and call one of the matching services.</span></span> <span data-ttu-id="41cf7-123">Následující příklad ukazuje, jak zavolat metodu System. ServiceModel. Discovery. objektem DiscoveryClient zahozena. Find (System. ServiceModel. Discovery. kritéria hledání) a použít vracená metadata pro volání nalezené služby.</span><span class="sxs-lookup"><span data-stu-id="41cf7-123">The following example shows how to call the System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) method and use the returned metadata to call the found service.</span></span> <span data-ttu-id="41cf7-124">Výhodou použití <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> je, že můžete seznam koncových bodů, které jste našli, ukládat do mezipaměti a později je použít.</span><span class="sxs-lookup"><span data-stu-id="41cf7-124">A benefit of using <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> is that you can cache the list of endpoints you’ve found and use them at a later time.</span></span> <span data-ttu-id="41cf7-125">Pomocí této mezipaměti můžete vytvořit vlastní logiku, která bude zpracovávat různé stavy selhání.</span><span class="sxs-lookup"><span data-stu-id="41cf7-125">With this cache, you can build custom logic to handle various failure conditions.</span></span>  
  
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
  
 <span data-ttu-id="41cf7-126">Následující příklad ukazuje, jak provést asynchronní operaci Find.</span><span class="sxs-lookup"><span data-stu-id="41cf7-126">The following example shows how to perform a find operation asynchronously.</span></span>  
  
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
  
 <span data-ttu-id="41cf7-127">Použijte metody <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> a k vyhledání služby na základě adresy jejího koncového bodu. <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A></span><span class="sxs-lookup"><span data-stu-id="41cf7-127">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> and <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> methods to locate a service based on its endpoint address.</span></span> <span data-ttu-id="41cf7-128">To je užitečné, když adresa koncového bodu není síťová adresa.</span><span class="sxs-lookup"><span data-stu-id="41cf7-128">This is useful when the endpoint address is not network addressable.</span></span> <span data-ttu-id="41cf7-129">Metody Resolve přebírají instanci <xref:System.ServiceModel.Discovery.ResolveCriteria> , která umožňuje zadat adresu koncového bodu služby, kterou řešíte, maximální dobu trvání operace řešení a sadu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="41cf7-129">The Resolve methods take an instance of <xref:System.ServiceModel.Discovery.ResolveCriteria> which allows you to specify the endpoint address of the service you are resolving, the maximum duration of the resolve operation, and a set of extensions.</span></span> <span data-ttu-id="41cf7-130">Následující příklad ukazuje, jak použít <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> metodu k vyřešení služby.</span><span class="sxs-lookup"><span data-stu-id="41cf7-130">The following example shows how to use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> method to resolve a service.</span></span>  
  
```csharp  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a><span data-ttu-id="41cf7-131">DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="41cf7-131">DynamicEndpoint</span></span>  
 <span data-ttu-id="41cf7-132"><xref:System.ServiceModel.Discovery.DynamicEndpoint>je standardním koncovým bodem (Další informace naleznete v tématu [Standardní koncové body](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)), který provádí zjišťování a automaticky vybere vyhovující službu.</span><span class="sxs-lookup"><span data-stu-id="41cf7-132"><xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint (For more information, see [Standard Endpoints](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) which performs discovery and automatically selects a matching service.</span></span> <span data-ttu-id="41cf7-133">Stačí vytvořit <xref:System.ServiceModel.Discovery.DynamicEndpoint> předávání v kontraktu pro vyhledání a vazba pro použití a <xref:System.ServiceModel.Discovery.DynamicEndpoint> předání instance klientovi WCF.</span><span class="sxs-lookup"><span data-stu-id="41cf7-133">Just create a <xref:System.ServiceModel.Discovery.DynamicEndpoint> passing in the contract to search for and the binding to use and pass the <xref:System.ServiceModel.Discovery.DynamicEndpoint> instance to the WCF client.</span></span> <span data-ttu-id="41cf7-134">Následující příklad ukazuje, jak vytvořit a použít <xref:System.ServiceModel.Discovery.DynamicEndpoint> pro volání služby kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="41cf7-134">The following example shows how to create and use a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to call the calculator service.</span></span> <span data-ttu-id="41cf7-135">Zjišťování se provádí při každém otevření klienta.</span><span class="sxs-lookup"><span data-stu-id="41cf7-135">The discovery is performed every time the client is opened.</span></span> <span data-ttu-id="41cf7-136">Libovolný koncový bod definovaný v konfiguraci lze také zapnout <xref:System.ServiceModel.Discovery.DynamicEndpoint> `kind ="dynamicEndpoint"` přidáním atributu do konfiguračního elementu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="41cf7-136">Any endpoint defined in configuration can also be turned into a <xref:System.ServiceModel.Discovery.DynamicEndpoint> by adding the `kind ="dynamicEndpoint"` attribute to the endpoint configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="41cf7-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="41cf7-137">See also</span></span>

- [<span data-ttu-id="41cf7-138">Zjišťování pomocí oborů</span><span class="sxs-lookup"><span data-stu-id="41cf7-138">Discovery with Scopes</span></span>](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)
- [<span data-ttu-id="41cf7-139">Základy</span><span class="sxs-lookup"><span data-stu-id="41cf7-139">Basic</span></span>](../../../../docs/framework/wcf/samples/basic-sample.md)
