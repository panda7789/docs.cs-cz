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
# <a name="discovery-announcements-and-announcement-client"></a>Oznámení zjišťování a klient oznámení

Funkce zjišťování WCF umožňuje součástem oznamovat dostupnost. Pokud je tato služba nakonfigurovaná, pošle vám oznámení Hello a bye. Klienti nebo jiné součásti mohou naslouchat takovým zprávám oznámení a reagovat na ně. To poskytuje alternativní způsob, jak mohou klienti znát služby. Funkce oznámení má několik použití, například pokud služba zadává a opouští síť často, může být oznámení lepší alternativou než hledání služeb. S tímto přístupem se snižuje síťový provoz a klient se může dozvědět o přítomnosti nebo odchodu služby hned po přijetí oznámení.

## <a name="discovery-announcements"></a>Oznámení zjišťování

Když je služba nakonfigurovaná pro oznámení připojená k síti a může být zjistitelná, pošle zprávu Hello s oznámením o jeho dostupnosti pro naslouchající klienty. Zpráva obsahuje informace o službě související se zjišťováním, jako je například její smlouva, adresa koncového bodu a přidružené obory. Můžete určit, kam se zpráva oznámení pošle s <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> třídou. Pokud je <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> koncovým bodem oznámení, že Hello a bye jsou vhodné pro vícesměrové vysílání, nebo pokud je koncový bod oznámení jednosměrovým vysíláním, zprávy se odesílají přímo do určeného koncového bodu.

> [!NOTE]
> Oznámení se odesílají při otevření a ukončení hostitele služby. Pokud tato volání nejsou správně dokončena, zpráva oznámení nemusí být odeslána. Například pokud dojde k chybám služby, zpráva oznámení bye se nepošle.

> [!TIP]
> Můžete přizpůsobit funkce oznámení, což vám umožní posílat oznámení, kdykoli si zvolíte.

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]definuje koncové body <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> standard a,kteréumožňujíslužbámaklientůmsnadnoodesílatoznámeníHelloabye.<xref:System.ServiceModel.Discovery.AnnouncementEndpoint>

### <a name="announcements-on-the-service"></a>Oznámení na službě

Pokud chcete službu nakonfigurovat tak, aby odesílala oznámení <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> , přidejte s koncovým bodem oznámení. Následující příklad ukazuje, jak programově přidat toto chování k hostiteli služby. V `UdpAnnouncementEndpoint`tomto příkladu se používá, což znamená, že oznámení jsou vícesměrové vysílání do umístění určeného tímto standardním koncovým bodem.

```csharp
ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());
serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
```

Chování lze nakonfigurovat také v konfiguračním souboru, jak je znázorněno v následujícím příkladu.

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

Předchozí příklady nakonfigurují službu tak, aby automaticky odesílala oznamovací zprávy. Zprávy oznámení můžete také odesílat explicitně pomocí <xref:System.ServiceModel.Discovery.AnnouncementClient> třídy.

### <a name="announcements-on-the-client"></a>Oznámení na klientovi

Klientská aplikace musí hostovat službu oznámení, aby reagovala na zprávy Hello a bye a aby se <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> přihlásila k odběru událostí a <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> . Následující příklad ukazuje, jak to provést.

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

Když se přijme zpráva Hello nebo Bye, můžete získat přístup k metadatům zjišťování koncových bodů prostřednictvím <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> , jak je znázorněno v následujícím příkladu.

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
