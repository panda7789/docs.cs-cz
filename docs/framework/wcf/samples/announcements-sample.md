---
title: Ukázka oznámení
ms.date: 03/30/2017
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
ms.openlocfilehash: c3824fb0dc7ab4169c309d1a5154127d6bc3b78f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747000"
---
# <a name="announcements-sample"></a>Ukázka oznámení

V této ukázce se dozvíte, jak používat funkci oznámení funkce zjišťování. Oznámení umožňují službám posílat zprávy oznámení, které obsahují metadata o službě. Ve výchozím nastavení se při spuštění služby pošle oznámení o signálu Hello a pošle se oznámení bye při ukončení služby. Tato oznámení můžou být vícesměrové vysílání nebo se můžou poslat Point-to-Point. Tato ukázka se skládá ze dvou projektů služby a klienta.

## <a name="service"></a>Service

Tento projekt obsahuje službu kalkulačky s místním hostováním. V metodě `Main` se vytvoří hostitel služby a do něj se přidá koncový bod služby. V dalším kroku se vytvoří <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>. Aby bylo možné povolit oznámení, musí být do <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>přidán koncový bod oznámení. V tomto případě se jako koncový bod oznámení přidá standardní koncový bod pomocí vícesměrového vysílání UDP. Vysílá oznámení přes dobře známou adresu UDP.

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

Metody `OnOnlineEvent` a `OnOfflineEvent` zpracovávají zprávy o oznámeních Hello a bye v uvedeném pořadí.

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

1. Tato ukázka používá koncové body HTTP a ke spuštění této ukázky musí být přidány správné seznamy ACL adres URL. Další informace najdete v tématu [Konfigurace HTTP a HTTPS](../feature-details/configuring-http-and-https.md). Spuštění následujícího příkazu u zvýšeného oprávnění by mělo přidat příslušné seznamy ACL. Pokud příkaz nefunguje tak, jak je, je vhodné nahradit doménu a uživatelské jméno pro následující argumenty. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. Sestavte řešení.

3. Spusťte aplikaci Client. exe.

4. Spusťte aplikaci Service. exe. Všimněte si, že klient obdrží online oznámení.

5. Zavřete aplikaci Service. exe. Všimněte si, že klient obdrží oznámení v režimu offline.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`
