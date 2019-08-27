---
title: Ukázka oznámení
ms.date: 03/30/2017
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
ms.openlocfilehash: 1acf51ebe36872424be1e0fdda65a7d18aa737f2
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045799"
---
# <a name="announcements-sample"></a>Ukázka oznámení

V této ukázce se dozvíte, jak používat funkci oznámení funkce zjišťování. Oznámení umožňují službám posílat zprávy oznámení, které obsahují metadata o službě. Ve výchozím nastavení se při spuštění služby pošle oznámení o signálu Hello a pošle se oznámení bye při ukončení služby. Tato oznámení můžou být vícesměrové vysílání nebo se můžou poslat Point-to-Point. Tato ukázka se skládá ze dvou projektů služby a klienta.

## <a name="service"></a>Služba

Tento projekt obsahuje službu kalkulačky s místním hostováním. `Main` V metodě se vytvoří hostitel služby a do něj se přidá koncový bod služby. Dále se vytvoří <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> . Chcete-li povolit oznámení, je nutné do <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>přidat koncový bod oznámení. V tomto případě se jako koncový bod oznámení přidá standardní koncový bod pomocí vícesměrového vysílání UDP. Vysílá oznámení přes dobře známou adresu UDP.

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

V tomto projektu si všimněte, že klient hostuje <xref:System.ServiceModel.Discovery.AnnouncementService>. Kromě toho jsou pro události registrovány dva Delegáti. Tyto události určují, co klient provede při přijetí online a offline oznámení.

```csharp
// Create an AnnouncementService instance
AnnouncementService announcementService = new AnnouncementService();

// Subscribe the announcement events
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;
```

Metody `OnOnlineEvent` a`OnOfflineEvent` zpracovávají zprávy o oznámeních Hello a bye v uvedeném pořadí.

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

#### <a name="to-use-this-sample"></a>Použití této ukázky

1. V této ukázce se používají koncové body HTTP a ke spuštění této ukázky se musí přidat správné seznamy ACL adres URL. Podrobnosti najdete v tématu [Konfigurace HTTP a HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) . Spuštění následujícího příkazu u zvýšeného oprávnění by mělo přidat příslušné seznamy ACL. Pokud příkaz nefunguje tak, jak je, je vhodné nahradit doménu a uživatelské jméno pro následující argumenty. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. Sestavte řešení.

3. Spusťte aplikaci Client. exe.

4. Spusťte aplikaci Service. exe. Všimněte si, že klient obdrží online oznámení.

5. Zavřete aplikaci Service. exe. Všimněte si, že klient obdrží oznámení v režimu offline.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`
