---
title: "Přehled zjišťování WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84fad0e4-23b1-45b5-a2d4-c9cdf90bbb22
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1afd3d94ceb3389a7d87528371925120f3c92764
ms.sourcegitcommit: e99dfadbca1992c187179b6a3b42bef44534ebb6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2017
---
# <a name="wcf-discovery-overview"></a><span data-ttu-id="832ff-102">Přehled zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="832ff-102">WCF Discovery Overview</span></span>
<span data-ttu-id="832ff-103">Zjišťování rozhraní API poskytuje jednotný programovací model pro dynamické publikace a zjišťování webové služby pomocí protokolu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="832ff-103">The Discovery APIs provide a unified programming model for the dynamic publication and discovery of Web services using the WS-Discovery protocol.</span></span> <span data-ttu-id="832ff-104">Tato rozhraní API umožňují služby k publikování sami a klienti najít publikované služby.</span><span class="sxs-lookup"><span data-stu-id="832ff-104">These APIs allow services to publish themselves and clients to find published services.</span></span> <span data-ttu-id="832ff-105">Jakmile služba je k zjistitelný, služba má možnost zasílání oznámení a také naslouchat a reagovat na požadavky na zjišťování.</span><span class="sxs-lookup"><span data-stu-id="832ff-105">Once a service is made discoverable, the service has the ability to send announcement messages as well as listen for and respond to discovery requests.</span></span> <span data-ttu-id="832ff-106">Zjistitelný služby může odesílat zprávy Hello oznamujeme jejich přijetí v síti a zprávy Bye oznamujeme jejich přesun ze sítě.</span><span class="sxs-lookup"><span data-stu-id="832ff-106">Discoverable services can send Hello messages to announce their arrival on a network and Bye messages to announce their departure from a network.</span></span> <span data-ttu-id="832ff-107">Pokud chcete vyhledat služby, klienti odesílají `Probe` požadavek, který obsahuje určitá kritéria, například typ kontraktu služby, klíčová slova a oboru v síti.</span><span class="sxs-lookup"><span data-stu-id="832ff-107">To find a service, clients send a `Probe` request that contains specific criteria such as service contract type, keywords, and scope on the network.</span></span> <span data-ttu-id="832ff-108">Přijímat služby `Probe` žádosti a určit, zda se shodují se kritéria.</span><span class="sxs-lookup"><span data-stu-id="832ff-108">Services receive the `Probe` request and determine whether they match the criteria.</span></span> <span data-ttu-id="832ff-109">Pokud služba odpovídá, odpoví odesláním `ProbeMatch` zprávy zpět do klienta se informace potřebné k kontaktovat službu.</span><span class="sxs-lookup"><span data-stu-id="832ff-109">If a service matches, it responds by sending a `ProbeMatch` message back to the client with the information necessary to contact the service.</span></span> <span data-ttu-id="832ff-110">Klienty můžete také odeslat `Resolve` požadavků, které mohly najít služby, které mohl změnit jejich adresa koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="832ff-110">Clients can also send `Resolve` requests that allow them to find services that may have changed their endpoint address.</span></span> <span data-ttu-id="832ff-111">Odpovídající služby reagovat na `Resolve` požadavky odesláním `ResolveMatch` zprávy zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="832ff-111">Matching services respond to `Resolve` requests by sending a `ResolveMatch` message back to the client.</span></span>  
  
## <a name="ad-hoc-and-managed-modes"></a><span data-ttu-id="832ff-112">Ad Hoc a spravované režimy</span><span class="sxs-lookup"><span data-stu-id="832ff-112">Ad-Hoc and Managed Modes</span></span>  
 <span data-ttu-id="832ff-113">Zjišťování rozhraní API podporuje dvou různých režimech: spravované a Ad-Hoc.</span><span class="sxs-lookup"><span data-stu-id="832ff-113">The Discovery API supports two different modes: Managed and Ad-Hoc.</span></span> <span data-ttu-id="832ff-114">V režimu spravované je centralizovaný server volá zjišťování proxy server, který uchovává informace o dostupných služeb.</span><span class="sxs-lookup"><span data-stu-id="832ff-114">In Managed mode there is a centralized server called a discovery proxy that maintains information about available services.</span></span> <span data-ttu-id="832ff-115">Zjišťování proxy možné naplnit informace o službách v mnoha různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="832ff-115">The discovery proxy can be populated with information about services in a variety of ways.</span></span> <span data-ttu-id="832ff-116">Například služby mohou zasílat zprávy oznámení během spuštění až zjišťování proxy server nebo proxy server může číst data z databáze nebo konfigurační soubor k určení, které služby jsou dostupné.</span><span class="sxs-lookup"><span data-stu-id="832ff-116">For example, services can send announcement messages during start up to the discovery proxy or the proxy may read data from a database or a configuration file to determine what services are available.</span></span> <span data-ttu-id="832ff-117">Jak se naplní zjišťování proxy je zcela až vývojář.</span><span class="sxs-lookup"><span data-stu-id="832ff-117">How the discovery proxy is populated is completely up to the developer.</span></span> <span data-ttu-id="832ff-118">Klienti používají zjišťování proxy k načtení informací o dostupných služeb.</span><span class="sxs-lookup"><span data-stu-id="832ff-118">Clients use the discovery proxy to retrieve information about available services.</span></span> <span data-ttu-id="832ff-119">Když klient vyhledá službu se zasílá `Probe` zprávu zjišťování proxy a proxy určuje, zda se shodují služeb ví o služby je hledání klienta.</span><span class="sxs-lookup"><span data-stu-id="832ff-119">When a client searches for a service it sends a `Probe` message to the discovery proxy and the proxy determines whether any of the services it knows about match the service the client is searching for.</span></span> <span data-ttu-id="832ff-120">Pokud existují odpovídá zasílá proxy zjišťování `ProbeMatch` odpověď zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="832ff-120">If there are matches the discovery proxy sends a `ProbeMatch` response back to the client.</span></span> <span data-ttu-id="832ff-121">Klient může poté kontaktovat službu přímo pomocí vrácené z proxy serveru služby informace.</span><span class="sxs-lookup"><span data-stu-id="832ff-121">The client can then contact the service directly using the service information returned from the proxy.</span></span> <span data-ttu-id="832ff-122">Klíčovým principem za spravovaný režim je, že jsou v režimu jednosměrového vysílání jeden autoritě zjišťování proxy odeslání požadavků zjišťování.</span><span class="sxs-lookup"><span data-stu-id="832ff-122">The key principle behind Managed mode is that the discovery requests are sent in a unicast manner to one authority, the discovery proxy.</span></span> <span data-ttu-id="832ff-123">Rozhraní .NET Framework obsahuje klíčové komponenty, které vám umožňují vytvářet vlastní proxy server.</span><span class="sxs-lookup"><span data-stu-id="832ff-123">The .NET Framework contains key components that allow you to build your own proxy.</span></span> <span data-ttu-id="832ff-124">Služby a klienti mohou vyhledat proxy server pomocí několik metod:</span><span class="sxs-lookup"><span data-stu-id="832ff-124">Clients and services can locate the proxy by multiple methods:</span></span>  
  
-   <span data-ttu-id="832ff-125">Proxy server může reagovat na ad hoc zprávy.</span><span class="sxs-lookup"><span data-stu-id="832ff-125">The proxy can respond to ad-hoc messages.</span></span>  
  
-   <span data-ttu-id="832ff-126">Proxy server můžete odeslat zprávu oznámení během spuštění.</span><span class="sxs-lookup"><span data-stu-id="832ff-126">The proxy can send an announcement message during start up.</span></span>  
  
-   <span data-ttu-id="832ff-127">Služby a klienti je možné zapsat do vyhledejte konkrétní dobře známé koncový bod.</span><span class="sxs-lookup"><span data-stu-id="832ff-127">Clients and services can be written to look for a specific well-known endpoint.</span></span>  
  
 <span data-ttu-id="832ff-128">V režimu Ad Hoc není žádný centrální server.</span><span class="sxs-lookup"><span data-stu-id="832ff-128">In Ad-Hoc mode, there is no centralized server.</span></span> <span data-ttu-id="832ff-129">Všechny zprávy zjišťování například oznámení týkající se služeb a požadavky klientů jsou odesílány způsobem vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="832ff-129">All discovery messages such as service announcements and client requests are sent in a multicast fashion.</span></span> <span data-ttu-id="832ff-130">Ve výchozím nastavení rozhraní .NET Framework obsahuje podporu pro zjišťování Ad-Hoc přes protokol UDP.</span><span class="sxs-lookup"><span data-stu-id="832ff-130">By default the .NET Framework contains support for Ad-Hoc discovery over the UDP protocol.</span></span> <span data-ttu-id="832ff-131">Například pokud služba je nakonfigurovaný k odeslání oznámení Hello na spouštění, odešle se přes adresu dobře známé a vícesměrového vysílání pomocí protokolu UDP.</span><span class="sxs-lookup"><span data-stu-id="832ff-131">For example, if a service is configured to send out a Hello announcement on start up, it sends it out over a well-known, multicast address using the UDP protocol.</span></span> <span data-ttu-id="832ff-132">Klienti mají aktivně naslouchat těchto oznámení a jejich zpracování odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="832ff-132">Clients have to actively listen for these announcements and process them accordingly.</span></span> <span data-ttu-id="832ff-133">Když klient odešle `Probe` zpráva pro službu odesláním přes síť pomocí protokolu vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="832ff-133">When a client sends a `Probe` message for a service it is sent over the network using a multicast protocol.</span></span> <span data-ttu-id="832ff-134">Každá služba, která obdrží požadavek určuje, zda je odpovídá kritérií `Probe` zprávy a odpovídá přímo na klienta se `ProbeMatch` zpráv, pokud služba odpovídá kritérii zadanými v `Probe` zprávy.</span><span class="sxs-lookup"><span data-stu-id="832ff-134">Each service that receives the request determines whether it matches the criteria in the `Probe` message and responds directly to the client with a `ProbeMatch` message if the service matches the criteria specified in the `Probe` message.</span></span>  
  
## <a name="benefits-of-using-wcf-discovery"></a><span data-ttu-id="832ff-135">Výhody použití zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="832ff-135">Benefits of Using WCF Discovery</span></span>  
 <span data-ttu-id="832ff-136">Protože zjišťování WCF je implementovaná pomocí protokolu WS-Discovery je umožňuje vzájemnou spolupráci s jinými klienty, služby a proxy servery, které implementují WS-Discovery také.</span><span class="sxs-lookup"><span data-stu-id="832ff-136">Because WCF Discovery is implemented using the WS-Discovery protocol it is interoperable with other clients, services, and proxies that implement WS-Discovery as well.</span></span> <span data-ttu-id="832ff-137">Zjišťování WCF je založena na stávajících WCF rozhraní API, který umožňuje snadno přidat další funkce zjišťování vaší existující služeb a klientů.</span><span class="sxs-lookup"><span data-stu-id="832ff-137">WCF Discovery is built upon the existing WCF APIs, which makes it easy to add Discovery functionality to your existing services and clients.</span></span> <span data-ttu-id="832ff-138">Možnosti rozpoznání služby lze snadno přidat prostřednictvím nastavení konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="832ff-138">Service discoverability can be easily added through the application configuration settings.</span></span> <span data-ttu-id="832ff-139">Kromě toho zjišťování WCF podporuje také pomocí protokolu zjišťování přes ostatní přenosy, například sdílené sítě, pojmenování překrytí a HTTP.</span><span class="sxs-lookup"><span data-stu-id="832ff-139">In addition, WCF Discovery also supports using the discovery protocol over other transports such as peer net, naming overlay, and HTTP.</span></span> <span data-ttu-id="832ff-140">Zjišťování WCF poskytuje podporu pro spravovaný režim operace, kde se používá zjišťování proxy.</span><span class="sxs-lookup"><span data-stu-id="832ff-140">WCF Discovery provides support for a Managed mode of operation where a discovery proxy is used.</span></span> <span data-ttu-id="832ff-141">To může snížit síťový provoz, jako jsou zprávy odesílány přímo do zjišťování proxy místo odesílání zpráv vícesměrového vysílání k celé síti.</span><span class="sxs-lookup"><span data-stu-id="832ff-141">This can reduce network traffic as messages are sent directly to the discovery proxy instead of sending multicast messages to the entire network.</span></span> <span data-ttu-id="832ff-142">Zjišťování WCF taky umožňuje větší flexibilitu při práci s webovými službami.</span><span class="sxs-lookup"><span data-stu-id="832ff-142">WCF Discovery also allows for more flexibility when working with Web services.</span></span> <span data-ttu-id="832ff-143">Například můžete změnit adresu služby bez nutnosti znovu nakonfigurovat klienta nebo službu.</span><span class="sxs-lookup"><span data-stu-id="832ff-143">For example, you can change the address of a service without having to reconfigure the client or the service.</span></span> <span data-ttu-id="832ff-144">Když klient musí přístup ke službě mohla vystavovat `Probe` zprávy prostřednictvím `Find` žádosti a očekávají, že služba odpovědět s aktuální adresy.</span><span class="sxs-lookup"><span data-stu-id="832ff-144">When a client must access the service it can issue a `Probe` message through a `Find` request and expect the service to respond with its current address.</span></span> <span data-ttu-id="832ff-145">Zjišťování WCF umožňuje klienta pro vyhledávání na základě různých kritérií, například typy kontraktů, prvky vazby, obor názvů, oboru a klíčová slova nebo čísla verzí služby.</span><span class="sxs-lookup"><span data-stu-id="832ff-145">WCF Discovery allows a client to search for a service based on different criteria including contract types, binding elements, namespace, scope, and keywords or version numbers.</span></span> <span data-ttu-id="832ff-146">Zjišťování WCF umožňuje modulu runtime a návrhu dobu zjišťování.</span><span class="sxs-lookup"><span data-stu-id="832ff-146">WCF Discovery enables runtime and design time discovery.</span></span> <span data-ttu-id="832ff-147">Přidání zjišťování tak, aby vaše aplikace umožňuje povolit další scénáře, jako je odolnost proti chybám a automatické konfigurace.</span><span class="sxs-lookup"><span data-stu-id="832ff-147">Adding discovery to your application can be used to enable other scenarios such as fault tolerance and auto configuration.</span></span>  
  
## <a name="service-publication"></a><span data-ttu-id="832ff-148">Služba publikace</span><span class="sxs-lookup"><span data-stu-id="832ff-148">Service Publication</span></span>  
 <span data-ttu-id="832ff-149">Zjistitelnost služby <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> musí být přidán pro hostitele služby a zjišťování musí být přidaný koncový bod, kde chcete přijímat zprávy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="832ff-149">To make a service discoverable, a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> must be added to the service host and a discovery endpoint must be added to specify where to listen for discovery messages.</span></span> <span data-ttu-id="832ff-150">Následující příklad kódu ukazuje, jak lze upravit služba s vlastním hostováním zjistitelnost.</span><span class="sxs-lookup"><span data-stu-id="832ff-150">The following code example shows how a self-hosted service can be modified to make it discoverable.</span></span>  
  
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
  
 <span data-ttu-id="832ff-151">A <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance musí být přidán k popisu služby pro službu zjistitelné.</span><span class="sxs-lookup"><span data-stu-id="832ff-151">A <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance must be added to a service description for the service to be discoverable.</span></span> <span data-ttu-id="832ff-152">A <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance musí být přidaný do hostitele služby říct službu, kde k naslouchání požadavkům zjišťování.</span><span class="sxs-lookup"><span data-stu-id="832ff-152">A <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance must be added to the service host to tell the service where to listen for discovery requests.</span></span> <span data-ttu-id="832ff-153">V tomto příkladu <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (který je odvozen z <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>) se přidá k určení, že služba má naslouchat žádostem zjišťování přes protokol UDP. přenos vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="832ff-153">In this example, a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (which is derived from <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>) is added to specify that the service should listen for discovery requests over the UDP multicast transport.</span></span> <span data-ttu-id="832ff-154"><xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Se používá pro zjištění Ad-Hoc, všechny zprávy jsou odesílány způsobem vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="832ff-154">The <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is used for Ad-Hoc discovery because all messages are sent in a multicast fashion.</span></span>  
  
## <a name="announcement"></a><span data-ttu-id="832ff-155">Oznámení</span><span class="sxs-lookup"><span data-stu-id="832ff-155">Announcement</span></span>  
 <span data-ttu-id="832ff-156">Ve výchozím nastavení služba publikace neodešle se zprávy oznámení.</span><span class="sxs-lookup"><span data-stu-id="832ff-156">By default, service publication does not send out announcement messages.</span></span> <span data-ttu-id="832ff-157">Služba musí být nakonfigurována k odeslání zprávy oznámení.</span><span class="sxs-lookup"><span data-stu-id="832ff-157">The service must be configured to send out announcement messages.</span></span> <span data-ttu-id="832ff-158">To poskytuje větší flexibilita pro služby zapisovače vzhledem k tomu, že může informovat službu odděleně od naslouchání pro zjišťování zprávy.</span><span class="sxs-lookup"><span data-stu-id="832ff-158">This provides additional flexibility for service writers because they can announce the service separately from listening for discovery messages.</span></span> <span data-ttu-id="832ff-159">Oznámení služby mohou sloužit také jako mechanismus pro registraci služby zjišťování proxy nebo jiné služby registrech.</span><span class="sxs-lookup"><span data-stu-id="832ff-159">Service announcement can also be used as a mechanism for registering services with a discovery proxy or other service registries.</span></span> <span data-ttu-id="832ff-160">Následující kód ukazuje, jak nakonfigurovat službu pro odeslání zpráv oznámení vazbu UDP.</span><span class="sxs-lookup"><span data-stu-id="832ff-160">The following code shows how to configure a service to send announcement messages over a UDP binding.</span></span>  
  
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
  
## <a name="service-discovery"></a><span data-ttu-id="832ff-161">Zjišťování služby</span><span class="sxs-lookup"><span data-stu-id="832ff-161">Service Discovery</span></span>  
 <span data-ttu-id="832ff-162">Klientská aplikace můžete použít <xref:System.ServiceModel.Discovery.DiscoveryClient> třída k vyhledání služeb.</span><span class="sxs-lookup"><span data-stu-id="832ff-162">A client application can use the <xref:System.ServiceModel.Discovery.DiscoveryClient> class to find services.</span></span> <span data-ttu-id="832ff-163">Vývojář vytvoří instanci <xref:System.ServiceModel.Discovery.DiscoveryClient> třídu, která předá koncový bod zjišťování, která určuje, kam má posílat `Probe` nebo `Resolve` zprávy.</span><span class="sxs-lookup"><span data-stu-id="832ff-163">The developer creates an instance of the <xref:System.ServiceModel.Discovery.DiscoveryClient> class that passes in a discovery endpoint that specifies where to send `Probe` or `Resolve` messages.</span></span> <span data-ttu-id="832ff-164">Klient pak zavolá <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> , určuje kritéria vyhledávání v rámci <xref:System.ServiceModel.Discovery.FindCriteria> instance.</span><span class="sxs-lookup"><span data-stu-id="832ff-164">The client then calls <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> that specifies search criteria within a <xref:System.ServiceModel.Discovery.FindCriteria> instance.</span></span> <span data-ttu-id="832ff-165">Pokud se najdou odpovídající služby, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> vrátí kolekci <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>.</span><span class="sxs-lookup"><span data-stu-id="832ff-165">If matching services are found, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> returns a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>.</span></span> <span data-ttu-id="832ff-166">Následující kód ukazuje způsob volání `Find` metoda a připojte se k zjištěnou službu.</span><span class="sxs-lookup"><span data-stu-id="832ff-166">The following code shows how to call the `Find` method and then connect to a discovered service.</span></span>  
  
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
  
## <a name="discovery-and-message-level-security"></a><span data-ttu-id="832ff-167">Zjišťování a úrovně zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="832ff-167">Discovery and Message Level Security</span></span>  
 <span data-ttu-id="832ff-168">Při použití zabezpečení na úrovni zprávy je nutné zadat <xref:System.ServiceModel.EndpointIdentity> na koncový bod zjišťování služby a odpovídající <xref:System.ServiceModel.EndpointIdentity> na koncový bod zjišťování klienta.</span><span class="sxs-lookup"><span data-stu-id="832ff-168">When using message level security it is necessary to specify an <xref:System.ServiceModel.EndpointIdentity> on the service discovery endpoint and a matching <xref:System.ServiceModel.EndpointIdentity> on the client discovery endpoint.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="832ff-169">úroveň zabezpečení zpráv najdete v tématu [zabezpečení zpráv](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="832ff-169"> message level security, see [Message Security](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span></span>  
  
## <a name="discovery-and-web-hosted-services"></a><span data-ttu-id="832ff-170">Zjišťování a webové hostovaných služeb</span><span class="sxs-lookup"><span data-stu-id="832ff-170">Discovery and Web Hosted Services</span></span>  
 <span data-ttu-id="832ff-171">V pořadí pro služby WCF zjistitelné musí být spuštěn.</span><span class="sxs-lookup"><span data-stu-id="832ff-171">In order for WCF services to be discoverable they must be running.</span></span> <span data-ttu-id="832ff-172">Služby WCF hostované v rámci služby IIS nebo WAS se nespustí, dokud služba IIS / byl přijme zprávu o vázaný službu, takže nemohou být zjistitelný ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="832ff-172">WCF services hosted under IIS or WAS do not run until IIS/WAS receives a message bound for the service, so they cannot be discoverable by default.</span></span>  <span data-ttu-id="832ff-173">Existují dvě možnosti pro provádění zjistitelný hostované webové služby:</span><span class="sxs-lookup"><span data-stu-id="832ff-173">There are two options for making Web-Hosted services discoverable:</span></span>  
  
1.  <span data-ttu-id="832ff-174">Použít funkci systému Windows Server AppFabric automatického – spuštění</span><span class="sxs-lookup"><span data-stu-id="832ff-174">Use the Windows Server AppFabric Auto-Start feature</span></span>  
  
2.  <span data-ttu-id="832ff-175">Použít proxy server zjišťování komunikovat jménem služby</span><span class="sxs-lookup"><span data-stu-id="832ff-175">Use a discovery proxy to communicate on behalf of the service</span></span>  
  
 <span data-ttu-id="832ff-176">Windows Server AppFabric má o funkci automatického spuštění, která vám umožní službu spustit před příjmem všechny zprávy.</span><span class="sxs-lookup"><span data-stu-id="832ff-176">Windows Server AppFabric has an Auto-Start feature that will allow a service to be started before receiving any messages.</span></span> <span data-ttu-id="832ff-177">Pomocí automatického spuštění nastavit službu IIS nebo WAS hostované službu lze nakonfigurovat zjistitelné.</span><span class="sxs-lookup"><span data-stu-id="832ff-177">With this Auto-Start set, an IIS/WAS hosted service can be configured to be discoverable.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="832ff-178">Viz funkce automatického spuštění, [Windows Server AppFabric automatického – spuštění funkce](http://go.microsoft.com/fwlink/?LinkId=205545).</span><span class="sxs-lookup"><span data-stu-id="832ff-178"> the Auto-Start feature see, [Windows Server AppFabric Auto-Start Feature](http://go.microsoft.com/fwlink/?LinkId=205545).</span></span> <span data-ttu-id="832ff-179">Společně s zapnout funkci automatického spuštění, musíte nakonfigurovat službu pro zjišťování.</span><span class="sxs-lookup"><span data-stu-id="832ff-179">Along with turning on the Auto-Start feature, you must configure the service for discovery.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="832ff-180">[Postupy: programové přidání možností rozpoznání do klienta a služby WCF](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[konfigurace zjišťování v konfiguračním souboru](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="832ff-180"> [How to: Programmatically Add Discoverability to a WCF Service and Client](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[Configuring Discovery in a Configuration File](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md).</span></span>  
  
 <span data-ttu-id="832ff-181">Zjišťování proxy umožňuje komunikovat jménem služby WCF, pokud služba není spuštěna.</span><span class="sxs-lookup"><span data-stu-id="832ff-181">A discovery proxy can be used to communicate on behalf of the WCF service when the service is not running.</span></span> <span data-ttu-id="832ff-182">Proxy server může sledovat u testu paměti nebo vyřešit zprávy a reagovat na klientovi.</span><span class="sxs-lookup"><span data-stu-id="832ff-182">The proxy can listen for probe or resolve messages and respond to the client.</span></span> <span data-ttu-id="832ff-183">Klient pak může odesílat zprávy přímo ke službě.</span><span class="sxs-lookup"><span data-stu-id="832ff-183">The client can then send messages directly to the service.</span></span> <span data-ttu-id="832ff-184">Když klient odešle zprávu do služby bude vytvořena instance reagovat na zprávu.</span><span class="sxs-lookup"><span data-stu-id="832ff-184">When the client sends a message to the service it will be instantiated to respond to the message.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="832ff-185">implementace proxy zjišťování najdete [implementace Proxy zjišťování](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md).</span><span class="sxs-lookup"><span data-stu-id="832ff-185"> implementing a discovery proxy see, [Implementing a Discovery Proxy](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="832ff-186">Zjišťování WCF fungovat správně musí mít všechny síťové adaptéry (řadiče síťového rozhraní) pouze 1 IP adresu.</span><span class="sxs-lookup"><span data-stu-id="832ff-186">For WCF Discovery to work correctly, all NICs (Network Interface Controller) should only have 1 IP address.</span></span>
