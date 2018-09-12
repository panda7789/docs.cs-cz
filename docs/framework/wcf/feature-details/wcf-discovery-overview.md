---
title: Přehled zjišťování WCF
ms.date: 03/30/2017
ms.assetid: 84fad0e4-23b1-45b5-a2d4-c9cdf90bbb22
ms.openlocfilehash: 24d758502e360a8368be25c506b8648b12a3eb20
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44494249"
---
# <a name="wcf-discovery-overview"></a><span data-ttu-id="de115-102">Přehled zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="de115-102">WCF Discovery Overview</span></span>
<span data-ttu-id="de115-103">Rozhraní API zjišťování poskytují jednotný programovací model pro dynamické publikace a zjišťování webové služby pomocí protokolu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="de115-103">The Discovery APIs provide a unified programming model for the dynamic publication and discovery of Web services using the WS-Discovery protocol.</span></span> <span data-ttu-id="de115-104">Tato rozhraní API umožňují služby sami a klientům nalezení služeb publikovaných na publikovat.</span><span class="sxs-lookup"><span data-stu-id="de115-104">These APIs allow services to publish themselves and clients to find published services.</span></span> <span data-ttu-id="de115-105">Jakmile proběhne zjistitelné služby, služby má možnost odesílat zprávy oznámení také naslouchat a reagovat na požadavky na zjišťování.</span><span class="sxs-lookup"><span data-stu-id="de115-105">Once a service is made discoverable, the service has the ability to send announcement messages as well as listen for and respond to discovery requests.</span></span> <span data-ttu-id="de115-106">Zjistitelné služby může odesílat zprávy Hello oznamujeme jejich doručení na síť a zprávy Bye oznamujeme jejich odeslání ze sítě.</span><span class="sxs-lookup"><span data-stu-id="de115-106">Discoverable services can send Hello messages to announce their arrival on a network and Bye messages to announce their departure from a network.</span></span> <span data-ttu-id="de115-107">K vyhledání služby klienty odeslat `Probe` žádost, která obsahuje určitá kritéria, například typ kontraktu služby, klíčová slova a oboru v síti.</span><span class="sxs-lookup"><span data-stu-id="de115-107">To find a service, clients send a `Probe` request that contains specific criteria such as service contract type, keywords, and scope on the network.</span></span> <span data-ttu-id="de115-108">Přijímat služby `Probe` žádosti a určit, zda kritériím neodpovídají.</span><span class="sxs-lookup"><span data-stu-id="de115-108">Services receive the `Probe` request and determine whether they match the criteria.</span></span> <span data-ttu-id="de115-109">Pokud služba odpovídá, odpovídá odesláním `ProbeMatch` zprávy zpět do klienta o informace nezbytné pro kontaktování služby.</span><span class="sxs-lookup"><span data-stu-id="de115-109">If a service matches, it responds by sending a `ProbeMatch` message back to the client with the information necessary to contact the service.</span></span> <span data-ttu-id="de115-110">Klienti mohou také odesílat `Resolve` požadavků, které zajistí, aby hledání mohlo dojít ke změně jejich adresa koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="de115-110">Clients can also send `Resolve` requests that allow them to find services that may have changed their endpoint address.</span></span> <span data-ttu-id="de115-111">Odpovídající služby reagovat na `Resolve` odesláním žádosti `ResolveMatch` zpráv zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="de115-111">Matching services respond to `Resolve` requests by sending a `ResolveMatch` message back to the client.</span></span>  
  
## <a name="ad-hoc-and-managed-modes"></a><span data-ttu-id="de115-112">Ad-Hoc a spravované režimy</span><span class="sxs-lookup"><span data-stu-id="de115-112">Ad-Hoc and Managed Modes</span></span>  
 <span data-ttu-id="de115-113">Zjišťování rozhraní API podporuje dva různé režimy: spravované a Ad Hoc.</span><span class="sxs-lookup"><span data-stu-id="de115-113">The Discovery API supports two different modes: Managed and Ad-Hoc.</span></span> <span data-ttu-id="de115-114">Spravovaný režim je centralizovaná serveru s názvem proxy zjišťování, která uchovává informace o dostupných služeb.</span><span class="sxs-lookup"><span data-stu-id="de115-114">In Managed mode there is a centralized server called a discovery proxy that maintains information about available services.</span></span> <span data-ttu-id="de115-115">Zjišťování proxy je možné naplnit informace o službách v mnoha různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="de115-115">The discovery proxy can be populated with information about services in a variety of ways.</span></span> <span data-ttu-id="de115-116">Například služby odesílat zprávy o oznámení při spuštění až po zjišťování proxy serveru nebo proxy server může číst data z databáze nebo konfiguračního souboru k určení, jaké služby jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="de115-116">For example, services can send announcement messages during start up to the discovery proxy or the proxy may read data from a database or a configuration file to determine what services are available.</span></span> <span data-ttu-id="de115-117">Jak se vyplní proxy zjišťování je zcela na vývojáře.</span><span class="sxs-lookup"><span data-stu-id="de115-117">How the discovery proxy is populated is completely up to the developer.</span></span> <span data-ttu-id="de115-118">Klienti používají proxy zjišťování k načtení informací o dostupných služeb.</span><span class="sxs-lookup"><span data-stu-id="de115-118">Clients use the discovery proxy to retrieve information about available services.</span></span> <span data-ttu-id="de115-119">Když klient vyhledává služby se odešle `Probe` zprávy zjišťování proxy serveru a proxy server určuje shodu kterékoli ze služeb ví o služby, bude klient Hledat.</span><span class="sxs-lookup"><span data-stu-id="de115-119">When a client searches for a service it sends a `Probe` message to the discovery proxy and the proxy determines whether any of the services it knows about match the service the client is searching for.</span></span> <span data-ttu-id="de115-120">Pokud existují odešle proxy zjišťování shody `ProbeMatch` odpověď zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="de115-120">If there are matches the discovery proxy sends a `ProbeMatch` response back to the client.</span></span> <span data-ttu-id="de115-121">Klient pak může kontaktovat službu přímo pomocí služby informace vrácené z proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="de115-121">The client can then contact the service directly using the service information returned from the proxy.</span></span> <span data-ttu-id="de115-122">Klíčovým principem za spravovaný režim je odeslání žádosti o zjištění způsobem jednosměrového vysílání jeden úřadu, za proxy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="de115-122">The key principle behind Managed mode is that the discovery requests are sent in a unicast manner to one authority, the discovery proxy.</span></span> <span data-ttu-id="de115-123">Rozhraní .NET Framework obsahuje klíčových komponent, které umožňují vytvářet vlastní proxy server.</span><span class="sxs-lookup"><span data-stu-id="de115-123">The .NET Framework contains key components that allow you to build your own proxy.</span></span> <span data-ttu-id="de115-124">Služby a klienti najdou proxy server pomocí několika metod:</span><span class="sxs-lookup"><span data-stu-id="de115-124">Clients and services can locate the proxy by multiple methods:</span></span>  
  
-   <span data-ttu-id="de115-125">Proxy server můžou reagovat na ad-hoc zprávy.</span><span class="sxs-lookup"><span data-stu-id="de115-125">The proxy can respond to ad-hoc messages.</span></span>  
  
-   <span data-ttu-id="de115-126">Proxy server můžete odeslat zprávu oznámení při spuštění.</span><span class="sxs-lookup"><span data-stu-id="de115-126">The proxy can send an announcement message during start up.</span></span>  
  
-   <span data-ttu-id="de115-127">Služby a klienti mohou napsané pro vyhledání určitého dobře známé koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="de115-127">Clients and services can be written to look for a specific well-known endpoint.</span></span>  
  
 <span data-ttu-id="de115-128">V režimu Ad Hoc není žádný centrální server.</span><span class="sxs-lookup"><span data-stu-id="de115-128">In Ad-Hoc mode, there is no centralized server.</span></span> <span data-ttu-id="de115-129">Všechny zprávy zjišťování například oznámení o službách a požadavky na klienta se posílají způsobem vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="de115-129">All discovery messages such as service announcements and client requests are sent in a multicast fashion.</span></span> <span data-ttu-id="de115-130">Rozhraní .NET Framework ve výchozím nastavení obsahuje podporu pro Ad-Hoc zjišťování přes protokol UDP.</span><span class="sxs-lookup"><span data-stu-id="de115-130">By default the .NET Framework contains support for Ad-Hoc discovery over the UDP protocol.</span></span> <span data-ttu-id="de115-131">Například pokud služba je konfigurován pro posílat oznámení Hello z po spuštění, odešle je prostřednictvím dobře známé, vícesměrového vysílání adres pomocí protokolu UDP.</span><span class="sxs-lookup"><span data-stu-id="de115-131">For example, if a service is configured to send out a Hello announcement on start up, it sends it out over a well-known, multicast address using the UDP protocol.</span></span> <span data-ttu-id="de115-132">Klienti mají aktivně naslouchat těchto oznámeních a odpovídajícím způsobem zpracovat.</span><span class="sxs-lookup"><span data-stu-id="de115-132">Clients have to actively listen for these announcements and process them accordingly.</span></span> <span data-ttu-id="de115-133">Když klient odešle `Probe` zprávu pro službu je odeslán přes síť pomocí vícesměrového vysílání protokolu.</span><span class="sxs-lookup"><span data-stu-id="de115-133">When a client sends a `Probe` message for a service it is sent over the network using a multicast protocol.</span></span> <span data-ttu-id="de115-134">Každá služba, která bude přijímat žádosti Určuje, zda odpovídá kritériím `Probe` zpráv a odpovídá přímo do klienta se `ProbeMatch` zprávu, pokud služba odpovídá kritérii zadanými v `Probe` zprávy.</span><span class="sxs-lookup"><span data-stu-id="de115-134">Each service that receives the request determines whether it matches the criteria in the `Probe` message and responds directly to the client with a `ProbeMatch` message if the service matches the criteria specified in the `Probe` message.</span></span>  
  
## <a name="benefits-of-using-wcf-discovery"></a><span data-ttu-id="de115-135">Výhody použití zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="de115-135">Benefits of Using WCF Discovery</span></span>  
 <span data-ttu-id="de115-136">Protože zjišťování WCF je implementována pomocí protokolu WS-Discovery je interoperabilní s dalšími klienty, službami a proxy servery, které také implementují WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="de115-136">Because WCF Discovery is implemented using the WS-Discovery protocol it is interoperable with other clients, services, and proxies that implement WS-Discovery as well.</span></span> <span data-ttu-id="de115-137">Zjišťování WCF je postavena stávajících rozhraní API WCF, které umožňuje snadno přidat funkce zjišťování na vašich stávajících služeb a klientů.</span><span class="sxs-lookup"><span data-stu-id="de115-137">WCF Discovery is built upon the existing WCF APIs, which makes it easy to add Discovery functionality to your existing services and clients.</span></span> <span data-ttu-id="de115-138">Zjistitelnost služby je možné snadno přidat prostřednictvím nastavení konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="de115-138">Service discoverability can be easily added through the application configuration settings.</span></span> <span data-ttu-id="de115-139">Zjišťování WCF kromě toho také podporuje pomocí protokolu zjišťování přes jiné přenosy, jako jsou sdílené net, pojmenování překrytí a HTTP.</span><span class="sxs-lookup"><span data-stu-id="de115-139">In addition, WCF Discovery also supports using the discovery protocol over other transports such as peer net, naming overlay, and HTTP.</span></span> <span data-ttu-id="de115-140">Zjišťování WCF poskytuje podporu pro spravovaný režim operace, kde se používá proxy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="de115-140">WCF Discovery provides support for a Managed mode of operation where a discovery proxy is used.</span></span> <span data-ttu-id="de115-141">To může snížit síťový provoz, jako jsou zprávy odesílány přímo do proxy zjišťování místo odesílání zprávy vícesměrového vysílání k celé síti.</span><span class="sxs-lookup"><span data-stu-id="de115-141">This can reduce network traffic as messages are sent directly to the discovery proxy instead of sending multicast messages to the entire network.</span></span> <span data-ttu-id="de115-142">Zjišťování WCF také umožňuje větší flexibilitu při práci s webovými službami.</span><span class="sxs-lookup"><span data-stu-id="de115-142">WCF Discovery also allows for more flexibility when working with Web services.</span></span> <span data-ttu-id="de115-143">Můžete například změnit adresu služby bez nutnosti znovu nakonfigurovat klienta nebo službě.</span><span class="sxs-lookup"><span data-stu-id="de115-143">For example, you can change the address of a service without having to reconfigure the client or the service.</span></span> <span data-ttu-id="de115-144">Když klient musí přístup ke službě, můžete vydat `Probe` zpráv prostřednictvím `Find` žádosti a očekávají, že služba odpověděla s její aktuální adresu.</span><span class="sxs-lookup"><span data-stu-id="de115-144">When a client must access the service it can issue a `Probe` message through a `Find` request and expect the service to respond with its current address.</span></span> <span data-ttu-id="de115-145">Zjišťování WCF umožňuje klienta k vyhledání služby na základě různých kritérií, včetně typy kontraktů, elementy vazby, obor názvů, oboru a klíčová slova nebo čísla verzí.</span><span class="sxs-lookup"><span data-stu-id="de115-145">WCF Discovery allows a client to search for a service based on different criteria including contract types, binding elements, namespace, scope, and keywords or version numbers.</span></span> <span data-ttu-id="de115-146">Zjišťování WCF umožňuje modulu runtime a návrhu doba zjišťování.</span><span class="sxs-lookup"><span data-stu-id="de115-146">WCF Discovery enables runtime and design time discovery.</span></span> <span data-ttu-id="de115-147">Přidání zjišťování tak, aby vaše aplikace slouží k povolení dalších scénářů, jako je odolnost proti chybám a automatické konfigurace.</span><span class="sxs-lookup"><span data-stu-id="de115-147">Adding discovery to your application can be used to enable other scenarios such as fault tolerance and auto configuration.</span></span>  
  
## <a name="service-publication"></a><span data-ttu-id="de115-148">Služba publikace</span><span class="sxs-lookup"><span data-stu-id="de115-148">Service Publication</span></span>  
 <span data-ttu-id="de115-149">Zjistitelnost služby <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> musí být přidané do hostitele služby a zjišťování. musí být koncový bod přidán do zadejte, kam chcete přijímat zprávy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="de115-149">To make a service discoverable, a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> must be added to the service host and a discovery endpoint must be added to specify where to listen for discovery messages.</span></span> <span data-ttu-id="de115-150">Následující příklad kódu ukazuje, jak služba v místním prostředí můžete upravit tak, aby zjistitelnost.</span><span class="sxs-lookup"><span data-stu-id="de115-150">The following code example shows how a self-hosted service can be modified to make it discoverable.</span></span>  
  
```csharp  
Uri baseAddress = new Uri(string.Format("http://{0}:8000/discovery/scenarios/calculatorservice/{1}/",  
        System.Net.Dns.GetHostName(), Guid.NewGuid().ToString()));

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());

    // ** DISCOVERY ** //
    // Add the discovery endpoint that specifies where to publish the services
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());

    // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();

    // The service can now be accessed.
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
}
```  
  
 <span data-ttu-id="de115-151">A <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance musí být přidané do popisu služby pro službu zjistitelné.</span><span class="sxs-lookup"><span data-stu-id="de115-151">A <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance must be added to a service description for the service to be discoverable.</span></span> <span data-ttu-id="de115-152">A <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance musí být přidané do tohoto hostitele služby službu zjistit, kde k naslouchání požadavkům zjišťování.</span><span class="sxs-lookup"><span data-stu-id="de115-152">A <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance must be added to the service host to tell the service where to listen for discovery requests.</span></span> <span data-ttu-id="de115-153">V tomto příkladu <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (který je odvozen z <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>) se přidá k určení, že služba naslouchat požadavkům pro požadavky na zjišťování přes port UDP přenos vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="de115-153">In this example, a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (which is derived from <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>) is added to specify that the service should listen for discovery requests over the UDP multicast transport.</span></span> <span data-ttu-id="de115-154"><xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Se používá pro zjištění Ad-Hoc, protože jsou všechny zprávy odeslané způsobem vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="de115-154">The <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is used for Ad-Hoc discovery because all messages are sent in a multicast fashion.</span></span>  
  
## <a name="announcement"></a><span data-ttu-id="de115-155">Oznámení</span><span class="sxs-lookup"><span data-stu-id="de115-155">Announcement</span></span>  
 <span data-ttu-id="de115-156">Ve výchozím nastavení služba publikace neodešle zprávy oznámení.</span><span class="sxs-lookup"><span data-stu-id="de115-156">By default, service publication does not send out announcement messages.</span></span> <span data-ttu-id="de115-157">Služba musí nakonfigurována na odeslání zprávy oznámení.</span><span class="sxs-lookup"><span data-stu-id="de115-157">The service must be configured to send out announcement messages.</span></span> <span data-ttu-id="de115-158">To poskytuje větší flexibilitu pro zápis služby vzhledem k tomu, že jsou oznámení služby odděleně od naslouchání pro vyhledávání zpráv.</span><span class="sxs-lookup"><span data-stu-id="de115-158">This provides additional flexibility for service writers because they can announce the service separately from listening for discovery messages.</span></span> <span data-ttu-id="de115-159">Oznámení služby také slouží jako mechanismus pro registraci služby pomocí proxy zjišťování nebo jiné služby registrů.</span><span class="sxs-lookup"><span data-stu-id="de115-159">Service announcement can also be used as a mechanism for registering services with a discovery proxy or other service registries.</span></span> <span data-ttu-id="de115-160">Následující kód ukazuje, jak nakonfigurovat službu pro odeslání zpráv oznámení UDP vazby.</span><span class="sxs-lookup"><span data-stu-id="de115-160">The following code shows how to configure a service to send announcement messages over a UDP binding.</span></span>  
  
```csharp  
Uri baseAddress = new Uri(string.Format("http://{0}:8000/discovery/scenarios/calculatorservice/{1}/",
        System.Net.Dns.GetHostName(), Guid.NewGuid().ToString()));

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    ServiceDiscoveryBehavior discoveryBehavior = new ServiceDiscoveryBehavior();
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());

    // Send announcements on UDP multicast transport
    discoveryBehavior.AnnouncementEndpoints.Add(
      new UdpAnnouncementEndpoint());

    // ** DISCOVERY ** //
    // Add the discovery endpoint that specifies where to publish the services
    serviceHost.Description.Endpoints.Add(new UdpDiscoveryEndpoint());

    // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();

    // The service can now be accessed.
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
}
```  
  
## <a name="service-discovery"></a><span data-ttu-id="de115-161">Zjišťování služby</span><span class="sxs-lookup"><span data-stu-id="de115-161">Service Discovery</span></span>  
 <span data-ttu-id="de115-162">Klientská aplikace můžete použít <xref:System.ServiceModel.Discovery.DiscoveryClient> třídy k nalezení služeb.</span><span class="sxs-lookup"><span data-stu-id="de115-162">A client application can use the <xref:System.ServiceModel.Discovery.DiscoveryClient> class to find services.</span></span> <span data-ttu-id="de115-163">Vytvoří instanci Vývojář <xref:System.ServiceModel.Discovery.DiscoveryClient> třídu, která se předá do koncového bodu zjišťování, která určuje, kam má odesílat `Probe` nebo `Resolve` zprávy.</span><span class="sxs-lookup"><span data-stu-id="de115-163">The developer creates an instance of the <xref:System.ServiceModel.Discovery.DiscoveryClient> class that passes in a discovery endpoint that specifies where to send `Probe` or `Resolve` messages.</span></span> <span data-ttu-id="de115-164">Klient pak zavolá <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> , který určuje kritéria vyhledávání v rámci <xref:System.ServiceModel.Discovery.FindCriteria> instance.</span><span class="sxs-lookup"><span data-stu-id="de115-164">The client then calls <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> that specifies search criteria within a <xref:System.ServiceModel.Discovery.FindCriteria> instance.</span></span> <span data-ttu-id="de115-165">Pokud se najdou odpovídající služby, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> vrátí kolekci <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>.</span><span class="sxs-lookup"><span data-stu-id="de115-165">If matching services are found, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> returns a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>.</span></span> <span data-ttu-id="de115-166">Následující kód ukazuje, jak volat `Find` metoda a připojte se k zjištěnou službu.</span><span class="sxs-lookup"><span data-stu-id="de115-166">The following code shows how to call the `Find` method and then connect to a discovered service.</span></span>  
  
```csharp  
class Client
{
    static EndpointAddress serviceAddress;
  
    static void Main()
    {  
        if (FindService()) 
        {
            InvokeService();
        }
    }  
  
    // ** DISCOVERY ** //  
    static bool FindService()  
    {  
        Console.WriteLine("\nFinding Calculator Service ..");  
        DiscoveryClient discoveryClient =   
            new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
        Collection<EndpointDiscoveryMetadata> calculatorServices =   
            (Collection<EndpointDiscoveryMetadata>)discoveryClient.Find(new FindCriteria(typeof(ICalculator))).Endpoints;  
  
        discoveryClient.Close();  
  
        if (calculatorServices.Count == 0)  
        {  
            Console.WriteLine("\nNo services are found.");  
            return false;  
        }  
        else  
        {  
            serviceAddress = calculatorServices[0].Address;  
            return true;  
        }  
    }  
  
    static void InvokeService()  
    {  
        Console.WriteLine("\nInvoking Calculator Service at {0}\n", serviceAddress);  
  
        // Create a client  
        CalculatorClient client = new CalculatorClient();  
        client.Endpoint.Address = serviceAddress;  
        client.Add(10,3);  
    }
}  
```  
  
## <a name="discovery-and-message-level-security"></a><span data-ttu-id="de115-167">Zjišťování a zabezpečení na úrovni zpráv</span><span class="sxs-lookup"><span data-stu-id="de115-167">Discovery and Message Level Security</span></span>  
 <span data-ttu-id="de115-168">Při použití zabezpečení na úrovni zpráv je potřeba zadat <xref:System.ServiceModel.EndpointIdentity> na koncový bod zjišťování služby a odpovídající <xref:System.ServiceModel.EndpointIdentity> na koncový bod zjišťování klienta.</span><span class="sxs-lookup"><span data-stu-id="de115-168">When using message level security it is necessary to specify an <xref:System.ServiceModel.EndpointIdentity> on the service discovery endpoint and a matching <xref:System.ServiceModel.EndpointIdentity> on the client discovery endpoint.</span></span> <span data-ttu-id="de115-169">Další informace o zabezpečení na úrovni zpráv, najdete v části [zabezpečení zpráv](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="de115-169">For more information about message level security, see [Message Security](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span></span>  
  
## <a name="discovery-and-web-hosted-services"></a><span data-ttu-id="de115-170">Zjišťování a Web hostovaných služeb</span><span class="sxs-lookup"><span data-stu-id="de115-170">Discovery and Web Hosted Services</span></span>  
 <span data-ttu-id="de115-171">V pořadí pro služby WCF zjistitelné musí být spuštěn.</span><span class="sxs-lookup"><span data-stu-id="de115-171">In order for WCF services to be discoverable they must be running.</span></span> <span data-ttu-id="de115-172">Služby WCF hostované v IIS nebo WAS se nespustí, dokud služba IIS / WAS přijme zprávu mez pro služby, proto nemohou být zjistitelné ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="de115-172">WCF services hosted under IIS or WAS do not run until IIS/WAS receives a message bound for the service, so they cannot be discoverable by default.</span></span>  <span data-ttu-id="de115-173">Existují dvě možnosti pro vytváření služeb hostovaných webových zjistitelné:</span><span class="sxs-lookup"><span data-stu-id="de115-173">There are two options for making Web-Hosted services discoverable:</span></span>  
  
1.  <span data-ttu-id="de115-174">Použít funkci systému Windows Server AppFabric automatické spuštění</span><span class="sxs-lookup"><span data-stu-id="de115-174">Use the Windows Server AppFabric Auto-Start feature</span></span>  
  
2.  <span data-ttu-id="de115-175">Komunikovat jménem službě pomocí proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="de115-175">Use a discovery proxy to communicate on behalf of the service</span></span>  
  
 <span data-ttu-id="de115-176">Windows Server AppFabric obsahuje funkci automatického spuštění, které vám umožní službu spustit před přijetím všechny zprávy.</span><span class="sxs-lookup"><span data-stu-id="de115-176">Windows Server AppFabric has an Auto-Start feature that will allow a service to be started before receiving any messages.</span></span> <span data-ttu-id="de115-177">Automatické spouštění nastavení IIS / WAS hostované služby je nakonfigurovat zjistitelné.</span><span class="sxs-lookup"><span data-stu-id="de115-177">With this Auto-Start set, an IIS/WAS hosted service can be configured to be discoverable.</span></span> <span data-ttu-id="de115-178">Další informace o najdete v tématu automatického spuštění funkce [funkce systému Windows Server AppFabric automatického spuštění](https://go.microsoft.com/fwlink/?LinkId=205545).</span><span class="sxs-lookup"><span data-stu-id="de115-178">For more information about the Auto-Start feature see, [Windows Server AppFabric Auto-Start Feature](https://go.microsoft.com/fwlink/?LinkId=205545).</span></span> <span data-ttu-id="de115-179">Spolu s povolením funkce Automatické spouštění, musíte nakonfigurovat službu pro zjišťování.</span><span class="sxs-lookup"><span data-stu-id="de115-179">Along with turning on the Auto-Start feature, you must configure the service for discovery.</span></span> <span data-ttu-id="de115-180">Další informace najdete v tématu [postupy: programové přidání zjistitelnosti do klienta a služby WCF](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[konfigurace zjišťování v konfiguračním souboru](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="de115-180">For more information, see [How to: Programmatically Add Discoverability to a WCF Service and Client](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[Configuring Discovery in a Configuration File](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md).</span></span>  
  
 <span data-ttu-id="de115-181">Zjišťování proxy serveru umožňuje komunikovat jménem služby WCF, když služba není spuštěná.</span><span class="sxs-lookup"><span data-stu-id="de115-181">A discovery proxy can be used to communicate on behalf of the WCF service when the service is not running.</span></span> <span data-ttu-id="de115-182">Proxy server může sledovat testu nebo vyřešit zprávy a reagovat na klientovi.</span><span class="sxs-lookup"><span data-stu-id="de115-182">The proxy can listen for probe or resolve messages and respond to the client.</span></span> <span data-ttu-id="de115-183">Klient pak může odesílat zprávy přímo ke službě.</span><span class="sxs-lookup"><span data-stu-id="de115-183">The client can then send messages directly to the service.</span></span> <span data-ttu-id="de115-184">Když klient odešle zprávu do služby bude vytvořena instance reagovat na zprávu.</span><span class="sxs-lookup"><span data-stu-id="de115-184">When the client sends a message to the service it will be instantiated to respond to the message.</span></span> <span data-ttu-id="de115-185">Další informace o implementace zjišťování proxy serveru najdete v [implementace Proxy zjišťování](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md).</span><span class="sxs-lookup"><span data-stu-id="de115-185">For more information about implementing a discovery proxy see, [Implementing a Discovery Proxy](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="de115-186">Zjišťování WCF fungovala správně měli všech síťových rozhraních (řadiče síťového rozhraní) mít jenom 1 IP adresu.</span><span class="sxs-lookup"><span data-stu-id="de115-186">For WCF Discovery to work correctly, all NICs (Network Interface Controller) should only have 1 IP address.</span></span>
