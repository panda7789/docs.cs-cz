---
title: Objekty DiscoveryClient a DynamicEndpoint
ms.date: 03/30/2017
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
ms.openlocfilehash: 6144a3fb528e64fd55fa125b6254d415ec3e8b26
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599162"
---
# <a name="discoveryclient-and-dynamicendpoint"></a><span data-ttu-id="3a6ed-102">Objekty DiscoveryClient a DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="3a6ed-102">DiscoveryClient and DynamicEndpoint</span></span>
<span data-ttu-id="3a6ed-103"><xref:System.ServiceModel.Discovery.DiscoveryClient>a <xref:System.ServiceModel.Discovery.DynamicEndpoint> jsou dvě třídy, které se používají na straně klienta pro hledání služeb.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-103"><xref:System.ServiceModel.Discovery.DiscoveryClient> and <xref:System.ServiceModel.Discovery.DynamicEndpoint> are two classes used on the client side to search for services.</span></span> <span data-ttu-id="3a6ed-104"><xref:System.ServiceModel.Discovery.DiscoveryClient>poskytuje seznam služeb, které odpovídají určité sadě kritérií, a umožňuje se připojit ke službám.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> provides you with a list of services that match a specific set of criteria and allows you to connect to the services.</span></span> <span data-ttu-id="3a6ed-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint>provede stejnou operaci a navíc se automaticky připojí k jedné ze služeb, které byly nalezeny.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint> performs the same operation and in addition, automatically connects to one of the services that was found.</span></span> <span data-ttu-id="3a6ed-106">Libovolný koncový bod lze navázat do <xref:System.ServiceModel.Discovery.DynamicEndpoint> konfigurace, kritéria hledání je také možné přidat v konfiguraci, což <xref:System.ServiceModel.Discovery.DynamicEndpoint> je užitečné v případě, že budete potřebovat zjišťování ve vašem řešení, ale nechcete měnit klientskou logiku – stačí pouze upravit koncové body.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-106">Any endpoint can be made into a <xref:System.ServiceModel.Discovery.DynamicEndpoint>, the search criteria can also be added in configuration, thus <xref:System.ServiceModel.Discovery.DynamicEndpoint> is useful when you need discovery in your solution but do not want to modify the client logic – you only need to modify the endpoints.</span></span> <span data-ttu-id="3a6ed-107"><xref:System.ServiceModel.Discovery.DiscoveryClient>na druhé straně je možné použít k získání přesnější kontroly nad operací vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-107"><xref:System.ServiceModel.Discovery.DiscoveryClient> on the other hand can be used to gain finer control over your search operation.</span></span> <span data-ttu-id="3a6ed-108">Využití a výhody z nich jsou vypracované níže.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-108">The uses and benefits of each are elaborated below.</span></span>  
  
## <a name="discoveryclient"></a><span data-ttu-id="3a6ed-109">Objektem DiscoveryClient zahozena</span><span class="sxs-lookup"><span data-stu-id="3a6ed-109">DiscoveryClient</span></span>  
 <span data-ttu-id="3a6ed-110"><xref:System.ServiceModel.Discovery.DiscoveryClient>Definuje synchronní a asynchronní metody Find <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> události.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-110">The <xref:System.ServiceModel.Discovery.DiscoveryClient> defines synchronous and asynchronous Find methods, <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events.</span></span>  <span data-ttu-id="3a6ed-111">Definuje také synchronní a asynchronní metody Resolve a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> událost.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-111">It also defines synchronous and asynchronous Resolve methods and a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> event.</span></span> <span data-ttu-id="3a6ed-112">Pomocí <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metod nebo <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> vyhledejte služby.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-112">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> or <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> methods to search for services.</span></span> <span data-ttu-id="3a6ed-113">Obě tyto metody přijímají <xref:System.ServiceModel.Discovery.FindCriteria> instanci, která umožňuje zadat názvy typů kontraktů, obory, maximální počet požadovaných výsledků a pravidla pro porovnání oboru.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-113">Both of these methods take a <xref:System.ServiceModel.Discovery.FindCriteria> instance that allows you to specify contract type names, scopes, maximum number of results requested, and scope matching rules.</span></span> <span data-ttu-id="3a6ed-114"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted>Události a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> lze použít při volání <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-114">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events can be used when calling the <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> method.</span></span> <span data-ttu-id="3a6ed-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged>se aktivuje pokaždé, když <xref:System.ServiceModel.Discovery.DiscoveryClient> přijme odpověď ze služby.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> is fired whenever the <xref:System.ServiceModel.Discovery.DiscoveryClient> receives a response from a service.</span></span> <span data-ttu-id="3a6ed-116">Dá se použít k zobrazení indikátoru průběhu znázorňujícího průběh operace Find.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-116">It can be used to display a progress bar showing the progress of the find operation.</span></span> <span data-ttu-id="3a6ed-117">Dá se použít i k tomu, aby se při přijetí odpovědi vypracovaly.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-117">It can also be used to act on find responses as they are received.</span></span> <span data-ttu-id="3a6ed-118"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted>Událost se aktivuje po dokončení operace Find.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-118">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> event is fired when the find operation completes.</span></span> <span data-ttu-id="3a6ed-119">K tomu může dojít, protože byl přijat maximální počet odpovědí nebo pokud <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> uplynula platnost.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-119">This may happen because the maximum number of responses has been received or if the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> has elapsed.</span></span> <span data-ttu-id="3a6ed-120">Po dokončení operace Find se výsledky vrátí do <xref:System.ServiceModel.Discovery.FindResponse> instance.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-120">When the find operation completes the results are returned in a <xref:System.ServiceModel.Discovery.FindResponse> instance.</span></span> <span data-ttu-id="3a6ed-121"><xref:System.ServiceModel.Discovery.FindResponse>Obsahuje kolekci, <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> která obsahuje adresy, názvy typů kontraktů, rozšíření, identifikátorů URI naslouchání a obory odpovídajícího služby.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-121">The <xref:System.ServiceModel.Discovery.FindResponse> contains a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> which contains the addresses, contract type names, extensions, listen URIs, and scopes of the matching services.</span></span> <span data-ttu-id="3a6ed-122">Tyto informace pak můžete použít k připojení a volání jedné z těchto služeb.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-122">You can then use this information to connect to and call one of the matching services.</span></span> <span data-ttu-id="3a6ed-123">Následující příklad ukazuje, jak zavolat metodu System. ServiceModel. Discovery. objektem DiscoveryClient zahozena. Find (System. ServiceModel. Discovery. kritéria hledání) a použít vracená metadata pro volání nalezené služby.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-123">The following example shows how to call the System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) method and use the returned metadata to call the found service.</span></span> <span data-ttu-id="3a6ed-124">Výhodou použití <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> je, že můžete seznam koncových bodů, které jste našli, ukládat do mezipaměti a později je použít.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-124">A benefit of using <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> is that you can cache the list of endpoints you’ve found and use them at a later time.</span></span> <span data-ttu-id="3a6ed-125">Pomocí této mezipaměti můžete vytvořit vlastní logiku, která bude zpracovávat různé stavy selhání.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-125">With this cache, you can build custom logic to handle various failure conditions.</span></span>  
  
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
  
 <span data-ttu-id="3a6ed-126">Následující příklad ukazuje, jak provést asynchronní operaci Find.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-126">The following example shows how to perform a find operation asynchronously.</span></span>  
  
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
  
 <span data-ttu-id="3a6ed-127">Použijte <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> metody a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> k vyhledání služby na základě adresy jejího koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-127">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> and <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> methods to locate a service based on its endpoint address.</span></span> <span data-ttu-id="3a6ed-128">To je užitečné, když adresa koncového bodu není síťová adresa.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-128">This is useful when the endpoint address is not network addressable.</span></span> <span data-ttu-id="3a6ed-129">Metody Resolve přebírají instanci <xref:System.ServiceModel.Discovery.ResolveCriteria> , která umožňuje zadat adresu koncového bodu služby, kterou řešíte, maximální dobu trvání operace řešení a sadu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-129">The Resolve methods take an instance of <xref:System.ServiceModel.Discovery.ResolveCriteria> which allows you to specify the endpoint address of the service you are resolving, the maximum duration of the resolve operation, and a set of extensions.</span></span> <span data-ttu-id="3a6ed-130">Následující příklad ukazuje, jak použít <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> metodu k vyřešení služby.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-130">The following example shows how to use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> method to resolve a service.</span></span>  
  
```csharp  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a><span data-ttu-id="3a6ed-131">DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="3a6ed-131">DynamicEndpoint</span></span>  
 <span data-ttu-id="3a6ed-132"><xref:System.ServiceModel.Discovery.DynamicEndpoint>je standardním koncovým bodem (Další informace naleznete v tématu [Standardní koncové body](standard-endpoints.md)), který provádí zjišťování a automaticky vybere vyhovující službu.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-132"><xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint (For more information, see [Standard Endpoints](standard-endpoints.md)) which performs discovery and automatically selects a matching service.</span></span> <span data-ttu-id="3a6ed-133">Stačí vytvořit <xref:System.ServiceModel.Discovery.DynamicEndpoint> předávání v kontraktu pro vyhledání a vazba pro použití a předání <xref:System.ServiceModel.Discovery.DynamicEndpoint> instance klientovi WCF.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-133">Just create a <xref:System.ServiceModel.Discovery.DynamicEndpoint> passing in the contract to search for and the binding to use and pass the <xref:System.ServiceModel.Discovery.DynamicEndpoint> instance to the WCF client.</span></span> <span data-ttu-id="3a6ed-134">Následující příklad ukazuje, jak vytvořit a použít <xref:System.ServiceModel.Discovery.DynamicEndpoint> pro volání služby kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-134">The following example shows how to create and use a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to call the calculator service.</span></span> <span data-ttu-id="3a6ed-135">Zjišťování se provádí při každém otevření klienta.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-135">The discovery is performed every time the client is opened.</span></span> <span data-ttu-id="3a6ed-136">Libovolný koncový bod definovaný v konfiguraci lze také zapnout <xref:System.ServiceModel.Discovery.DynamicEndpoint> přidáním `kind ="dynamicEndpoint"` atributu do konfiguračního elementu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="3a6ed-136">Any endpoint defined in configuration can also be turned into a <xref:System.ServiceModel.Discovery.DynamicEndpoint> by adding the `kind ="dynamicEndpoint"` attribute to the endpoint configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3a6ed-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a6ed-137">See also</span></span>

- [<span data-ttu-id="3a6ed-138">Zjišťování pomocí oborů</span><span class="sxs-lookup"><span data-stu-id="3a6ed-138">Discovery with Scopes</span></span>](../samples/discovery-with-scopes-sample.md)
- [<span data-ttu-id="3a6ed-139">Basic</span><span class="sxs-lookup"><span data-stu-id="3a6ed-139">Basic</span></span>](../samples/basic-sample.md)
