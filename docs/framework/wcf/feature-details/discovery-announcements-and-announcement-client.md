---
title: "Oznámení zjišťování a klient oznámení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 426c6437-f8d2-4968-b23a-18afd671aa4b
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 67eab6a5b35e29fe3df09ab286090433d25e8ca3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="discovery-announcements-and-announcement-client"></a><span data-ttu-id="534dd-102">Oznámení zjišťování a klient oznámení</span><span class="sxs-lookup"><span data-stu-id="534dd-102">Discovery Announcements and Announcement Client</span></span>
<span data-ttu-id="534dd-103">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Zjišťování funkce umožňuje součásti oznamujeme jejich dostupnost.</span><span class="sxs-lookup"><span data-stu-id="534dd-103">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] discovery feature enables components to announce their availability.</span></span> <span data-ttu-id="534dd-104">Pokud je nakonfigurovaná tak, odešle služba Hello a Bye oznámení.</span><span class="sxs-lookup"><span data-stu-id="534dd-104">If configured to do so, a service sends Hello and Bye announcements.</span></span> <span data-ttu-id="534dd-105">Klienti ani jiné součásti může sledovat takové zprávy oznámení a s nimi pracovat.</span><span class="sxs-lookup"><span data-stu-id="534dd-105">Clients or other components can listen for such announcement messages and act on them.</span></span> <span data-ttu-id="534dd-106">To poskytuje alternativní metoda pro klienty vědět služeb.</span><span class="sxs-lookup"><span data-stu-id="534dd-106">This provides an alternative method for clients to be aware of services.</span></span> <span data-ttu-id="534dd-107">Funkce oznámení má několika způsoby, například pokud služby zadejte a nechat síť často, oznámení může být lepší alternativou než hledání pro služby.</span><span class="sxs-lookup"><span data-stu-id="534dd-107">Announcement functionality has several uses, for example, if the services enter and leave a network frequently, announcements may be a better alternative than searching for services.</span></span> <span data-ttu-id="534dd-108">S tímto přístupem se snižuje síťový provoz a klient se dozvíte přítomnosti nebo odeslání služby při přijímání oznámení.</span><span class="sxs-lookup"><span data-stu-id="534dd-108">With this approach, the network traffic is reduced and the client can learn about the presence or departure of the service as soon as announcements are received.</span></span>  
  
## <a name="discovery-announcements"></a><span data-ttu-id="534dd-109">Oznámení zjišťování</span><span class="sxs-lookup"><span data-stu-id="534dd-109">Discovery Announcements</span></span>  
 <span data-ttu-id="534dd-110">Když služba nakonfigurována pro oznámení připojí k síti a že bude jasné, odešle zprávu Hello klientům naslouchání uvedení jeho dostupnost.</span><span class="sxs-lookup"><span data-stu-id="534dd-110">When a service configured for announcements joins a network and becomes discoverable, it sends a Hello message announcing its availability to listening clients.</span></span> <span data-ttu-id="534dd-111">Zpráva obsahuje zjišťování související informace o službě, například jeho kontrakt, adresa koncového bodu a související obory.</span><span class="sxs-lookup"><span data-stu-id="534dd-111">The message contains discovery related information about the service, such as its contract, endpoint address and associated scopes.</span></span> <span data-ttu-id="534dd-112">Můžete určit, kam je odeslána zpráva oznámení s <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> třídy.</span><span class="sxs-lookup"><span data-stu-id="534dd-112">You can specify where the announcement message is sent with the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> class.</span></span> <span data-ttu-id="534dd-113">Pokud má koncový bod oznámení <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> pak Hello a Bye jsou správně vícesměrového vysílání, nebo pokud koncový bod oznámení není jednosměrového vysílání, jsou zprávy odesílány přímo na zadaný koncový bod.</span><span class="sxs-lookup"><span data-stu-id="534dd-113">If the announcement endpoint is a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> then the Hello and Bye are multicast appropriately, or if the announcement endpoint is unicast, the messages are sent directly to the specified endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="534dd-114">Oznámení se odesílají, pokud hostitel služby otevře a zavře.</span><span class="sxs-lookup"><span data-stu-id="534dd-114">Announcements are sent when the service host opens and closes.</span></span> <span data-ttu-id="534dd-115">Pokud tyto volání se nedokončí správně nemusí odeslaná zpráva oznámení. Například pokud službu chyb, pak zpráva sdělení. Bye nebude odeslána.</span><span class="sxs-lookup"><span data-stu-id="534dd-115">If these calls do not finish properly the announcement message may not be sent out. For example if the service faults, then the Bye announcement message is not sent.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="534dd-116">Můžete přizpůsobit funkce oznámení umožňuje odesílat oznámení vždy, když zvolíte.</span><span class="sxs-lookup"><span data-stu-id="534dd-116">You can customize the announcement functionality, allowing you to send announcements whenever you choose.</span></span>  
  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="534dd-117">definuje <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> jako standardní koncové body k povolení služeb a klientů snadno odeslat Hello a Bye oznámení.</span><span class="sxs-lookup"><span data-stu-id="534dd-117"> defines the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> and <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> as standard endpoints to allow services and clients to easily send Hello and Bye announcements.</span></span>  
  
### <a name="announcements-on-the-service"></a><span data-ttu-id="534dd-118">Oznámení služby</span><span class="sxs-lookup"><span data-stu-id="534dd-118">Announcements on the Service</span></span>  
 <span data-ttu-id="534dd-119">Chcete-li nakonfigurovat službu pro odeslání oznámení, přidejte <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> s koncový bod oznámení.</span><span class="sxs-lookup"><span data-stu-id="534dd-119">To configure the service to send announcements, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> with an announcement endpoint.</span></span> <span data-ttu-id="534dd-120">Následující příklad ukazuje, jak toto chování prostřednictvím kódu programu přidat do hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="534dd-120">The following example shows how to programmatically add this behavior to the service host.</span></span> <span data-ttu-id="534dd-121">Tento příklad používá `UdpAnnouncementEndpoint`, což znamená, že jsou hlášení vícesměrového vysílání do umístění určeného tohoto standardní koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="534dd-121">This example uses the `UdpAnnouncementEndpoint`, which implies that the announcements are multicast to a location specified by that standard endpoint.</span></span>  
  
```  
ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());
serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
```  
  
 <span data-ttu-id="534dd-122">Chování lze nastavit v konfiguračním souboru i, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="534dd-122">The behavior can be configured in the configuration file as well, as shown in the following example.</span></span>  
  
```xml  
<services>
  <service behaviorConfiguration="CalculatorBehavior" name="Microsoft.Samples.Discovery.CalculatorService">
    <!--Add Discovery Endpoint-->
    <endpoint name="udpDiscoveryEpt" kind="udpDiscoveryEndpoint" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorBehavior">
      <!--Add Discovery behavior-->
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint kind="udpAnnouncementEndpoint" />
        </announcementEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
 <span data-ttu-id="534dd-123">V předchozích příkladech konfiguraci služby automaticky odesílat zprávy oznámení.</span><span class="sxs-lookup"><span data-stu-id="534dd-123">The preceding examples configure a service to automatically send announcement messages.</span></span> <span data-ttu-id="534dd-124">Můžete také odeslat oznámení zprávy explicitně pomocí <xref:System.ServiceModel.Discovery.AnnouncementClient> třídy.</span><span class="sxs-lookup"><span data-stu-id="534dd-124">You can also send announcement messages explicitly by using the <xref:System.ServiceModel.Discovery.AnnouncementClient> class.</span></span>  
  
### <a name="announcements-on-the-client"></a><span data-ttu-id="534dd-125">Oznámení na straně klienta</span><span class="sxs-lookup"><span data-stu-id="534dd-125">Announcements on the Client</span></span>  
 <span data-ttu-id="534dd-126">Klientská aplikace musí být hostitelem služby oznámení odpovězte na otázky Hello a Bye a přihlášení k odběru <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> a <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> události.</span><span class="sxs-lookup"><span data-stu-id="534dd-126">A client application must host an announcement service to respond to the Hello and Bye messages and subscribe to the <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> and <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> events.</span></span> <span data-ttu-id="534dd-127">Následující příklad ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="534dd-127">The following example shows how to do this.</span></span>  
  
```  
// Create an AnnouncementService instance
AnnouncementService announcementService = new AnnouncementService();
  
// Subscribe the announcement events
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;
  
// Create ServiceHost for the AnnouncementService
using (ServiceHost announcementServiceHost = new ServiceHost(announcementService))
{  
    // Listen for the announcements sent over UDP multicast
    announcementServiceHost.AddServiceEndpoint(new UdpAnnouncementEndpoint());
    announcementServiceHost.Open();
  
    Console.WriteLine("Press <ENTER> to terminate.");
    Console.ReadLine();
}  
```  
  
 <span data-ttu-id="534dd-128">Po přijetí zprávy Hello nebo Bye můžete získat přístup k metadatům zjišťování koncový bod prostřednictvím <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="534dd-128">When a Hello or Bye message is received, you can access the endpoint discovery metadata through <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> as shown in the following example.</span></span>  
  
```  
static void OnOnlineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine("Received an online announcement from {0}", 
e.EndpointDiscoveryMetadata.Address);
}

static void OnOfflineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine("Received an offline announcement from {0}", 
e.EndpointDiscoveryMetadata.Address);
}
```
