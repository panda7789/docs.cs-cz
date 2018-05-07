---
title: Ukázka oznámení
ms.date: 03/30/2017
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
ms.openlocfilehash: ee58a2fef970fa3e7936e2fc26a9e7fd31633347
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="announcements-sample"></a>Ukázka oznámení
Tento příklad ukazuje, jak používat funkci oznámení funkce zjišťování. Povolit oznámení služby k odeslání zprávy oznámení, které obsahují metadata týkající se služby. Ve výchozím nastavení je odeslána hello oznámení, když se služba spouští a bye oznámení se odesílají při vypnutí služby. Tato oznámení mohou být vícesměrového vysílání nebo mohou být odesílány typu point-to-point. Tato ukázka se skládá z klienta a služby dva projekty.  
  
## <a name="service"></a>Služba  
 Tento projekt obsahuje vlastním hostováním kalkulačky služby. V `Main` metody hostitele služby se vytvoří a koncový bod služby se přidá k němu. Další, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> je vytvořena. Pokud chcete povolit oznámení, musí být přidaný do koncového bodu oznámení <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>. Koncový bod standardní, používat UDP, vícesměrového vysílání v tomto případě se přidá jako koncový bod oznámení. Tato hlášení všesměrově přes známou adresu UDP.  
  
```  
Uri baseAddress = new Uri("http://localhost:8000/" + Guid.NewGuid().ToString());  
  
// Create a ServiceHost for the CalculatorService type.  
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))  
{  
     serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new WSHttpBinding(), String.Empty);  
  
     ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();  
  
     // Announce the availability of the service over UDP multicast  
    serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());  
  
    // Make the service discoverable over UDP multicast.  
    serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);                  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    serviceHost.Open();  
    // ...  
}  
```  
  
## <a name="client"></a>Klient  
 V tomto projektu, Všimněte si, že klient hostitelů <xref:System.ServiceModel.Discovery.AnnouncementService>. Kromě toho jsou dvě delegáti registrovány události. Tyto události určují, co klient nemá při přijetí oznámení online a offline.  
  
```  
// Create an AnnouncementService instance  
AnnouncementService announcementService = new AnnouncementService();  
  
// Subscribe the announcement events  
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;  
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;  
```  
  
 `OnOnlineEvent` a `OnOfflineEvent` metody zpracování zprávy oznámení hello a bye v uvedeném pořadí.  
  
```  
static void OnOnlineEvent(object sender, AnnouncementEventArgs e)  
{  
    Console.WriteLine();              
    Console.WriteLine("Received an online announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);  
PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);  
}  
  
static void OnOfflineEvent(object sender, AnnouncementEventArgs e)  
{  
    Console.WriteLine();  
    Console.WriteLine("Received an offline announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);  
            PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);  
}  
```  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Tato ukázka používá koncových bodů protokolu HTTP a použít tuto ukázku, správné seznamy ACL adresa URL musí být přidán najdete [konfigurace HTTP a HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) podrobnosti. Spuštěním následujícího příkazu na zvýšená oprávnění měli přidat příslušné seznamy ACL. Můžete nahradit domény a uživatelské jméno pro následující argumenty, pokud příkaz nefunguje, protože je. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  Sestavte řešení.  
  
3.  Spusťte aplikaci client.exe.  
  
4.  Spusťte aplikaci service.exe. Všimněte si, že klient obdrží oznámení online.  
  
5.  Zavřete aplikaci service.exe. Všimněte si, že klient obdrží oznámení v režimu offline.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`  
  
## <a name="see-also"></a>Viz také
