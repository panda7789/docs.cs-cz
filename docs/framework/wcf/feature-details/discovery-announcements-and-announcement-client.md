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
ms.openlocfilehash: a6da9c2e251a6592bb0af039d552d02e7e4fd3fd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="discovery-announcements-and-announcement-client"></a>Oznámení zjišťování a klient oznámení
[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Zjišťování funkce umožňuje součásti oznamujeme jejich dostupnost. Pokud je nakonfigurovaná tak, odešle služba Hello a Bye oznámení. Klienti ani jiné součásti může sledovat takové zprávy oznámení a s nimi pracovat. To poskytuje alternativní metoda pro klienty vědět služeb. Funkce oznámení má několika způsoby, například pokud služby zadejte a nechat síť často, oznámení může být lepší alternativou než hledání pro služby. S tímto přístupem se snižuje síťový provoz a klient se dozvíte přítomnosti nebo odeslání služby při přijímání oznámení.  
  
## <a name="discovery-announcements"></a>Oznámení zjišťování  
 Když služba nakonfigurována pro oznámení připojí k síti a že bude jasné, odešle zprávu Hello klientům naslouchání uvedení jeho dostupnost. Zpráva obsahuje zjišťování související informace o službě, například jeho kontrakt, adresa koncového bodu a související obory. Můžete určit, kam je odeslána zpráva oznámení s <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> třídy. Pokud má koncový bod oznámení <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> pak Hello a Bye jsou správně vícesměrového vysílání, nebo pokud koncový bod oznámení není jednosměrového vysílání, jsou zprávy odesílány přímo na zadaný koncový bod.  
  
> [!NOTE]
>  Oznámení se odesílají, pokud hostitel služby otevře a zavře. Pokud tyto volání se nedokončí správně nemusí odeslaná zpráva oznámení. Například pokud službu chyb, pak zpráva sdělení. Bye nebude odeslána.  
  
> [!TIP]
>  Můžete přizpůsobit funkce oznámení umožňuje odesílat oznámení vždy, když zvolíte.  
  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]definuje <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> jako standardní koncové body k povolení služeb a klientů snadno odeslat Hello a Bye oznámení.  
  
### <a name="announcements-on-the-service"></a>Oznámení služby  
 Chcete-li nakonfigurovat službu pro odeslání oznámení, přidejte <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> s koncový bod oznámení. Následující příklad ukazuje, jak toto chování prostřednictvím kódu programu přidat do hostitele služby. Tento příklad používá `UdpAnnouncementEndpoint`, což znamená, že jsou hlášení vícesměrového vysílání do umístění určeného tohoto standardní koncového bodu.  
  
```  
ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());
serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
```  
  
 Chování lze nastavit v konfiguračním souboru i, jak je znázorněno v následujícím příkladu.  
  
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
  
 V předchozích příkladech konfiguraci služby automaticky odesílat zprávy oznámení. Můžete také odeslat oznámení zprávy explicitně pomocí <xref:System.ServiceModel.Discovery.AnnouncementClient> třídy.  
  
### <a name="announcements-on-the-client"></a>Oznámení na straně klienta  
 Klientská aplikace musí být hostitelem služby oznámení odpovězte na otázky Hello a Bye a přihlášení k odběru <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> a <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> události. Následující příklad ukazuje, jak to provést.  
  
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
  
 Po přijetí zprávy Hello nebo Bye můžete získat přístup k metadatům zjišťování koncový bod prostřednictvím <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> jak je znázorněno v následujícím příkladu.  
  
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
