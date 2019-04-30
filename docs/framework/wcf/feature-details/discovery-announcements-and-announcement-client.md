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
# <a name="discovery-announcements-and-announcement-client"></a>Oznámení zjišťování a klient oznámení
Funkce zjišťování WCF umožňuje součásti oznamujeme jejich dostupnost. Pokud nakonfigurované k tomu, odešle služba Hello a Bye oznámení. Klienti ani jiné součásti může naslouchat zprávám takové oznámení a na jejich základě reagovat. To poskytuje alternativní metoda pro klienty, je potřeba vědět služby. Funkce oznámení má několik využití, například pokud služby vstupu a opuštění síti často, oznámení může být lepší alternativou než hledání služeb. S tímto přístupem snižuje síťový provoz a klient se můžou seznámit přítomnost nebo odeslání služby co nejdříve po přijetí oznámení.  
  
## <a name="discovery-announcements"></a>Oznámení zjišťování  
 Když služba nakonfigurována pro oznámení týkající se připojí k síti a stane zjistitelné, odešle do služby zprávu Hello oznamujeme dostupnost naslouchání klientů. Zpráva obsahuje spojené obory a související informace o službě, jako je například její smlouvy, adresa koncového bodu zjišťování. Můžete určit, kde je odeslána zpráva oznámení s <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> třídy. Pokud je koncový bod oznámení <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> potom Hello a Bye jsou odpovídajícím způsobem vícesměrového vysílání, nebo pokud je koncový bod oznámení jednosměrového vysílání, zprávy se odešlou přímo na zadaný koncový bod.  
  
> [!NOTE]
>  Oznámení jsou odesílána při otevření hostitele služby a zavře. Pokud tato volání nebylo dokončeno správně nemusí posílat zprávy oznámení. Například pokud služba chyb stránkování, pak nejsou odesílány zprávy oznámení Bye.  
  
> [!TIP]
>  Můžete přizpůsobit funkce oznámení umožňuje posílat oznámení pokaždé, když zvolíte.  
  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] definuje <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> jako standardní koncové body k povolení služeb a klientů snadno odesílat Hello a Bye oznámení.  
  
### <a name="announcements-on-the-service"></a>Oznámení služby  
 Pokud chcete nakonfigurovat službu pro odeslání oznámení, přidat <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> pomocí koncového bodu oznámení. Následující příklad ukazuje, jak programově přidat toto chování k hostiteli služby. V tomto příkladu `UdpAnnouncementEndpoint`, což znamená, že jsou oznámení vícesměrového vysílání do umístění určeného proměnnou tohoto standardního koncového bodu.  
  
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
  
 V předchozích příkladech konfigurace automaticky odesílat zprávy oznámení ve službě. Můžete také odeslat oznámení zprávy explicitně pomocí <xref:System.ServiceModel.Discovery.AnnouncementClient> třídy.  
  
### <a name="announcements-on-the-client"></a>Oznámení na straně klienta  
 Klientská aplikace musí být hostitelem služby oznámení můžete reagovat na zprávy Hello a Bye a přihlaste se k odběru <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> a <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> události. Následující příklad ukazuje, jak to provést.  
  
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
  
 Při doručení zprávy do Hello nebo Bye, lze použít koncový bod metadat zjišťování prostřednictvím <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> jak je znázorněno v následujícím příkladu.  
  
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
