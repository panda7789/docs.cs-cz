---
title: Ukázka oznámení
ms.date: 03/30/2017
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
ms.openlocfilehash: 91422d9b625339236e3d8d09683deba18a24c9d4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814208"
---
# <a name="announcements-sample"></a>Ukázka oznámení
Tento příklad ukazuje, jak používat funkci oznámení funkci zjišťování. Oznámení povolte službám posílat zprávy oznámení, které obsahují metadata týkající se služby. Ve výchozím nastavení hello oznámení se odešle, když služba po spuštění a bye oznámení se odešle, když je služba ukončena. Tato oznámení mohou být vícesměrového vysílání nebo mohou být odesílány typu point-to-point. Tento příklad se skládá z klienta a služby dva projekty.  
  
## <a name="service"></a>Služba  
 Tento projekt obsahuje službu kalkulačky v místním prostředí. V `Main` metody vytvoření hostitele služby a koncového bodu služby se přidá do ní. Další, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> se vytvoří. Pokud chcete povolit oznámení, musí koncový bod oznámení přidaný do <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>. V tomto případě je standardní koncový bod, používat UDP, vícesměrového vysílání se přidá jako koncový bod oznámení. Toto oznámení vysílá prostřednictvím dobře známé adrese UDP.  
  
```csharp
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
 V tomto projektu, Všimněte si, že hostitele klienta <xref:System.ServiceModel.Discovery.AnnouncementService>. Kromě toho jsou registrovány dvou delegátů událostí. Tyto události určují, co klient nemá při přijetí oznámení týkající se online i offline.  
  
```csharp
// Create an AnnouncementService instance  
AnnouncementService announcementService = new AnnouncementService();  
  
// Subscribe the announcement events  
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;  
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;  
```  
  
 `OnOnlineEvent` a `OnOfflineEvent` metody zpracovávají hello a bye zprávy oznámení v uvedeném pořadí.  
  
```csharp
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
  
1.  Tato ukázka používá koncové body HTTP a použít tuto ukázku, správné seznamy ACL adresy URL musí být přidán viz [konfigurace HTTP a HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) podrobnosti. Provádění se zvýšenými oprávněními následující příkaz by měl přidat příslušné seznamy ACL. Můžete nahradit doména a uživatelské jméno pro následující argumenty, pokud příkaz nefunguje, jak je. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  Sestavte řešení.  
  
3.  Spusťte aplikaci client.exe.  
  
4.  Spusťte aplikaci service.exe. Všimněte si, že klient obdrží oznámení online.  
  
5.  Ukončete aplikaci service.exe. Všimněte si, že klient obdrží oznámení v režimu offline.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`  
  
