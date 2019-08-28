---
title: Oznámení zjišťování a klient oznámení
ms.date: 03/30/2017
ms.assetid: 426c6437-f8d2-4968-b23a-18afd671aa4b
ms.openlocfilehash: 4ad0b3ea5c257fa3117c426391bd59ad7b560d4f
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040172"
---
# <a name="discovery-announcements-and-announcement-client"></a><span data-ttu-id="26927-102">Oznámení zjišťování a klient oznámení</span><span class="sxs-lookup"><span data-stu-id="26927-102">Discovery Announcements and Announcement Client</span></span>

<span data-ttu-id="26927-103">Funkce zjišťování WCF umožňuje součástem oznamovat dostupnost.</span><span class="sxs-lookup"><span data-stu-id="26927-103">The WCF discovery feature enables components to announce their availability.</span></span> <span data-ttu-id="26927-104">Pokud je tato služba nakonfigurovaná, pošle vám oznámení Hello a bye.</span><span class="sxs-lookup"><span data-stu-id="26927-104">If configured to do so, a service sends Hello and Bye announcements.</span></span> <span data-ttu-id="26927-105">Klienti nebo jiné součásti mohou naslouchat takovým zprávám oznámení a reagovat na ně.</span><span class="sxs-lookup"><span data-stu-id="26927-105">Clients or other components can listen for such announcement messages and act on them.</span></span> <span data-ttu-id="26927-106">To poskytuje alternativní způsob, jak mohou klienti znát služby.</span><span class="sxs-lookup"><span data-stu-id="26927-106">This provides an alternative method for clients to be aware of services.</span></span> <span data-ttu-id="26927-107">Funkce oznámení má několik použití, například pokud služba zadává a opouští síť často, může být oznámení lepší alternativou než hledání služeb.</span><span class="sxs-lookup"><span data-stu-id="26927-107">Announcement functionality has several uses, for example, if the services enter and leave a network frequently, announcements may be a better alternative than searching for services.</span></span> <span data-ttu-id="26927-108">S tímto přístupem se snižuje síťový provoz a klient se může dozvědět o přítomnosti nebo odchodu služby hned po přijetí oznámení.</span><span class="sxs-lookup"><span data-stu-id="26927-108">With this approach, the network traffic is reduced and the client can learn about the presence or departure of the service as soon as announcements are received.</span></span>

## <a name="discovery-announcements"></a><span data-ttu-id="26927-109">Oznámení zjišťování</span><span class="sxs-lookup"><span data-stu-id="26927-109">Discovery Announcements</span></span>

<span data-ttu-id="26927-110">Když je služba nakonfigurovaná pro oznámení připojená k síti a může být zjistitelná, pošle zprávu Hello s oznámením o jeho dostupnosti pro naslouchající klienty.</span><span class="sxs-lookup"><span data-stu-id="26927-110">When a service configured for announcements joins a network and becomes discoverable, it sends a Hello message announcing its availability to listening clients.</span></span> <span data-ttu-id="26927-111">Zpráva obsahuje informace o službě související se zjišťováním, jako je například její smlouva, adresa koncového bodu a přidružené obory.</span><span class="sxs-lookup"><span data-stu-id="26927-111">The message contains discovery related information about the service, such as its contract, endpoint address and associated scopes.</span></span> <span data-ttu-id="26927-112">Můžete určit, kam se zpráva oznámení pošle s <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> třídou.</span><span class="sxs-lookup"><span data-stu-id="26927-112">You can specify where the announcement message is sent with the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> class.</span></span> <span data-ttu-id="26927-113">Pokud je <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> koncovým bodem oznámení, že Hello a bye jsou vhodné pro vícesměrové vysílání, nebo pokud je koncový bod oznámení jednosměrovým vysíláním, zprávy se odesílají přímo do určeného koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="26927-113">If the announcement endpoint is a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> then the Hello and Bye are multicast appropriately, or if the announcement endpoint is unicast, the messages are sent directly to the specified endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="26927-114">Oznámení se odesílají při otevření a ukončení hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="26927-114">Announcements are sent when the service host opens and closes.</span></span> <span data-ttu-id="26927-115">Pokud tato volání nejsou správně dokončena, zpráva oznámení nemusí být odeslána. Například pokud dojde k chybám služby, zpráva oznámení bye se nepošle.</span><span class="sxs-lookup"><span data-stu-id="26927-115">If these calls do not finish properly the announcement message may not be sent out. For example if the service faults, then the Bye announcement message is not sent.</span></span>

> [!TIP]
> <span data-ttu-id="26927-116">Můžete přizpůsobit funkce oznámení, což vám umožní posílat oznámení, kdykoli si zvolíte.</span><span class="sxs-lookup"><span data-stu-id="26927-116">You can customize the announcement functionality, allowing you to send announcements whenever you choose.</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="26927-117">definuje koncové body <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> standard a,kteréumožňujíslužbámaklientůmsnadnoodesílatoznámeníHelloabye.<xref:System.ServiceModel.Discovery.AnnouncementEndpoint></span><span class="sxs-lookup"><span data-stu-id="26927-117">defines the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> and <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> as standard endpoints to allow services and clients to easily send Hello and Bye announcements.</span></span>

### <a name="announcements-on-the-service"></a><span data-ttu-id="26927-118">Oznámení na službě</span><span class="sxs-lookup"><span data-stu-id="26927-118">Announcements on the Service</span></span>

<span data-ttu-id="26927-119">Pokud chcete službu nakonfigurovat tak, aby odesílala oznámení <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> , přidejte s koncovým bodem oznámení.</span><span class="sxs-lookup"><span data-stu-id="26927-119">To configure the service to send announcements, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> with an announcement endpoint.</span></span> <span data-ttu-id="26927-120">Následující příklad ukazuje, jak programově přidat toto chování k hostiteli služby.</span><span class="sxs-lookup"><span data-stu-id="26927-120">The following example shows how to programmatically add this behavior to the service host.</span></span> <span data-ttu-id="26927-121">V `UdpAnnouncementEndpoint`tomto příkladu se používá, což znamená, že oznámení jsou vícesměrové vysílání do umístění určeného tímto standardním koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="26927-121">This example uses the `UdpAnnouncementEndpoint`, which implies that the announcements are multicast to a location specified by that standard endpoint.</span></span>

```csharp
ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());
serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
```

<span data-ttu-id="26927-122">Chování lze nakonfigurovat také v konfiguračním souboru, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="26927-122">The behavior can be configured in the configuration file as well, as shown in the following example.</span></span>

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

<span data-ttu-id="26927-123">Předchozí příklady nakonfigurují službu tak, aby automaticky odesílala oznamovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="26927-123">The preceding examples configure a service to automatically send announcement messages.</span></span> <span data-ttu-id="26927-124">Zprávy oznámení můžete také odesílat explicitně pomocí <xref:System.ServiceModel.Discovery.AnnouncementClient> třídy.</span><span class="sxs-lookup"><span data-stu-id="26927-124">You can also send announcement messages explicitly by using the <xref:System.ServiceModel.Discovery.AnnouncementClient> class.</span></span>

### <a name="announcements-on-the-client"></a><span data-ttu-id="26927-125">Oznámení na klientovi</span><span class="sxs-lookup"><span data-stu-id="26927-125">Announcements on the Client</span></span>

<span data-ttu-id="26927-126">Klientská aplikace musí hostovat službu oznámení, aby reagovala na zprávy Hello a bye a aby se <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> přihlásila k odběru událostí a <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> .</span><span class="sxs-lookup"><span data-stu-id="26927-126">A client application must host an announcement service to respond to the Hello and Bye messages and subscribe to the <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> and <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> events.</span></span> <span data-ttu-id="26927-127">Následující příklad ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="26927-127">The following example shows how to do this.</span></span>

```csharp
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

<span data-ttu-id="26927-128">Když se přijme zpráva Hello nebo Bye, můžete získat přístup k metadatům zjišťování koncových bodů prostřednictvím <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> , jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="26927-128">When a Hello or Bye message is received, you can access the endpoint discovery metadata through <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> as shown in the following example.</span></span>

```csharp
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
