---
title: Oznámení zjišťování a klient oznámení
ms.date: 03/30/2017
ms.assetid: 426c6437-f8d2-4968-b23a-18afd671aa4b
ms.openlocfilehash: c32aca5e6deab01423d61c516ee924d00bc041ee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61856582"
---
# <a name="discovery-announcements-and-announcement-client"></a><span data-ttu-id="a8f7b-102">Oznámení zjišťování a klient oznámení</span><span class="sxs-lookup"><span data-stu-id="a8f7b-102">Discovery Announcements and Announcement Client</span></span>
<span data-ttu-id="a8f7b-103">Funkce zjišťování WCF umožňuje součásti oznamujeme jejich dostupnost.</span><span class="sxs-lookup"><span data-stu-id="a8f7b-103">The WCF discovery feature enables components to announce their availability.</span></span> <span data-ttu-id="a8f7b-104">Pokud nakonfigurované k tomu, odešle služba Hello a Bye oznámení.</span><span class="sxs-lookup"><span data-stu-id="a8f7b-104">If configured to do so, a service sends Hello and Bye announcements.</span></span> <span data-ttu-id="a8f7b-105">Klienti ani jiné součásti může naslouchat zprávám takové oznámení a na jejich základě reagovat.</span><span class="sxs-lookup"><span data-stu-id="a8f7b-105">Clients or other components can listen for such announcement messages and act on them.</span></span> <span data-ttu-id="a8f7b-106">To poskytuje alternativní metoda pro klienty, je potřeba vědět služby.</span><span class="sxs-lookup"><span data-stu-id="a8f7b-106">This provides an alternative method for clients to be aware of services.</span></span> <span data-ttu-id="a8f7b-107">Funkce oznámení má několik využití, například pokud služby vstupu a opuštění síti často, oznámení může být lepší alternativou než hledání služeb.</span><span class="sxs-lookup"><span data-stu-id="a8f7b-107">Announcement functionality has several uses, for example, if the services enter and leave a network frequently, announcements may be a better alternative than searching for services.</span></span> <span data-ttu-id="a8f7b-108">S tímto přístupem snižuje síťový provoz a klient se můžou seznámit přítomnost nebo odeslání služby co nejdříve po přijetí oznámení.</span><span class="sxs-lookup"><span data-stu-id="a8f7b-108">With this approach, the network traffic is reduced and the client can learn about the presence or departure of the service as soon as announcements are received.</span></span>  
  
## <a name="discovery-announcements"></a><span data-ttu-id="a8f7b-109">Oznámení zjišťování</span><span class="sxs-lookup"><span data-stu-id="a8f7b-109">Discovery Announcements</span></span>  
 <span data-ttu-id="a8f7b-110">Když služba nakonfigurována pro oznámení týkající se připojí k síti a stane zjistitelné, odešle do služby zprávu Hello oznamujeme dostupnost naslouchání klientů.</span><span class="sxs-lookup"><span data-stu-id="a8f7b-110">When a service configured for announcements joins a network and becomes discoverable, it sends a Hello message announcing its availability to listening clients.</span></span> <span data-ttu-id="a8f7b-111">Zpráva obsahuje spojené obory a související informace o službě, jako je například její smlouvy, adresa koncového bodu zjišťování.</span><span class="sxs-lookup"><span data-stu-id="a8f7b-111">The message contains discovery related information about the service, such as its contract, endpoint address and associated scopes.</span></span> <span data-ttu-id="a8f7b-112">Můžete určit, kde je odeslána zpráva oznámení s <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> třídy.</span><span class="sxs-lookup"><span data-stu-id="a8f7b-112">You can specify where the announcement message is sent with the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> class.</span></span> <span data-ttu-id="a8f7b-113">Pokud je koncový bod oznámení <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> potom Hello a Bye jsou odpovídajícím způsobem vícesměrového vysílání, nebo pokud je koncový bod oznámení jednosměrového vysílání, zprávy se odešlou přímo na zadaný koncový bod.</span><span class="sxs-lookup"><span data-stu-id="a8f7b-113">If the announcement endpoint is a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> then the Hello and Bye are multicast appropriately, or if the announcement endpoint is unicast, the messages are sent directly to the specified endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8f7b-114">Oznámení jsou odesílána při otevření hostitele služby a zavře.</span><span class="sxs-lookup"><span data-stu-id="a8f7b-114">Announcements are sent when the service host opens and closes.</span></span> <span data-ttu-id="a8f7b-115">Pokud tato volání nebylo dokončeno správně nemusí posílat zprávy oznámení. Například pokud služba chyb stránkování, pak nejsou odesílány zprávy oznámení Bye.</span><span class="sxs-lookup"><span data-stu-id="a8f7b-115">If these calls do not finish properly the announcement message may not be sent out. For example if the service faults, then the Bye announcement message is not sent.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="a8f7b-116">Můžete přizpůsobit funkce oznámení umožňuje posílat oznámení pokaždé, když zvolíte.</span><span class="sxs-lookup"><span data-stu-id="a8f7b-116">You can customize the announcement functionality, allowing you to send announcements whenever you choose.</span></span>  
  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="a8f7b-117">definuje <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> jako standardní koncové body k povolení služeb a klientů snadno odesílat Hello a Bye oznámení.</span><span class="sxs-lookup"><span data-stu-id="a8f7b-117">defines the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> and <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> as standard endpoints to allow services and clients to easily send Hello and Bye announcements.</span></span>  
  
### <a name="announcements-on-the-service"></a><span data-ttu-id="a8f7b-118">Oznámení služby</span><span class="sxs-lookup"><span data-stu-id="a8f7b-118">Announcements on the Service</span></span>  
 <span data-ttu-id="a8f7b-119">Pokud chcete nakonfigurovat službu pro odeslání oznámení, přidat <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> pomocí koncového bodu oznámení.</span><span class="sxs-lookup"><span data-stu-id="a8f7b-119">To configure the service to send announcements, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> with an announcement endpoint.</span></span> <span data-ttu-id="a8f7b-120">Následující příklad ukazuje, jak programově přidat toto chování k hostiteli služby.</span><span class="sxs-lookup"><span data-stu-id="a8f7b-120">The following example shows how to programmatically add this behavior to the service host.</span></span> <span data-ttu-id="a8f7b-121">V tomto příkladu `UdpAnnouncementEndpoint`, což znamená, že jsou oznámení vícesměrového vysílání do umístění určeného proměnnou tohoto standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="a8f7b-121">This example uses the `UdpAnnouncementEndpoint`, which implies that the announcements are multicast to a location specified by that standard endpoint.</span></span>  
  
```  
ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());
serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
```  
  
 <span data-ttu-id="a8f7b-122">Chování lze nastavit v konfiguračním souboru i, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a8f7b-122">The behavior can be configured in the configuration file as well, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="a8f7b-123">V předchozích příkladech konfigurace automaticky odesílat zprávy oznámení ve službě.</span><span class="sxs-lookup"><span data-stu-id="a8f7b-123">The preceding examples configure a service to automatically send announcement messages.</span></span> <span data-ttu-id="a8f7b-124">Můžete také odeslat oznámení zprávy explicitně pomocí <xref:System.ServiceModel.Discovery.AnnouncementClient> třídy.</span><span class="sxs-lookup"><span data-stu-id="a8f7b-124">You can also send announcement messages explicitly by using the <xref:System.ServiceModel.Discovery.AnnouncementClient> class.</span></span>  
  
### <a name="announcements-on-the-client"></a><span data-ttu-id="a8f7b-125">Oznámení na straně klienta</span><span class="sxs-lookup"><span data-stu-id="a8f7b-125">Announcements on the Client</span></span>  
 <span data-ttu-id="a8f7b-126">Klientská aplikace musí být hostitelem služby oznámení můžete reagovat na zprávy Hello a Bye a přihlaste se k odběru <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> a <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> události.</span><span class="sxs-lookup"><span data-stu-id="a8f7b-126">A client application must host an announcement service to respond to the Hello and Bye messages and subscribe to the <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> and <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> events.</span></span> <span data-ttu-id="a8f7b-127">Následující příklad ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="a8f7b-127">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="a8f7b-128">Při doručení zprávy do Hello nebo Bye, lze použít koncový bod metadat zjišťování prostřednictvím <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a8f7b-128">When a Hello or Bye message is received, you can access the endpoint discovery metadata through <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> as shown in the following example.</span></span>  
  
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
