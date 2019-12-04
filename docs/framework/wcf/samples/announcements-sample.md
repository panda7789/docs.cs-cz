---
title: Ukázka oznámení
ms.date: 03/30/2017
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
ms.openlocfilehash: 57b61dbd82338aafd248285c9cb11ecdf58d25bb
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716153"
---
# <a name="announcements-sample"></a><span data-ttu-id="f6c08-102">Ukázka oznámení</span><span class="sxs-lookup"><span data-stu-id="f6c08-102">Announcements Sample</span></span>

<span data-ttu-id="f6c08-103">V této ukázce se dozvíte, jak používat funkci oznámení funkce zjišťování.</span><span class="sxs-lookup"><span data-stu-id="f6c08-103">This sample shows how to use the Announcement functionality of the Discovery feature.</span></span> <span data-ttu-id="f6c08-104">Oznámení umožňují službám posílat zprávy oznámení, které obsahují metadata o službě.</span><span class="sxs-lookup"><span data-stu-id="f6c08-104">Announcements allow services to send out announcement messages that contain metadata about the service.</span></span> <span data-ttu-id="f6c08-105">Ve výchozím nastavení se při spuštění služby pošle oznámení o signálu Hello a pošle se oznámení bye při ukončení služby.</span><span class="sxs-lookup"><span data-stu-id="f6c08-105">By default a hello announcement is sent when the service starts up and a bye announcement is sent when the service shuts down.</span></span> <span data-ttu-id="f6c08-106">Tato oznámení můžou být vícesměrové vysílání nebo se můžou poslat Point-to-Point.</span><span class="sxs-lookup"><span data-stu-id="f6c08-106">These announcements can be multicast or they can be sent point-to-point.</span></span> <span data-ttu-id="f6c08-107">Tato ukázka se skládá ze dvou projektů služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="f6c08-107">This sample consists of two projects service and client.</span></span>

## <a name="service"></a><span data-ttu-id="f6c08-108">Service</span><span class="sxs-lookup"><span data-stu-id="f6c08-108">Service</span></span>

<span data-ttu-id="f6c08-109">Tento projekt obsahuje službu kalkulačky s místním hostováním.</span><span class="sxs-lookup"><span data-stu-id="f6c08-109">This project contains a self-hosted calculator service.</span></span> <span data-ttu-id="f6c08-110">V metodě `Main` se vytvoří hostitel služby a do něj se přidá koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="f6c08-110">In the `Main` method, a service host is created and a service endpoint is added to it.</span></span> <span data-ttu-id="f6c08-111">V dalším kroku se vytvoří <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span><span class="sxs-lookup"><span data-stu-id="f6c08-111">Next, a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is created.</span></span> <span data-ttu-id="f6c08-112">Aby bylo možné povolit oznámení, musí být do <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>přidán koncový bod oznámení.</span><span class="sxs-lookup"><span data-stu-id="f6c08-112">To enable announcements, an announcement endpoint must be added to the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span> <span data-ttu-id="f6c08-113">V tomto případě se jako koncový bod oznámení přidá standardní koncový bod pomocí vícesměrového vysílání UDP.</span><span class="sxs-lookup"><span data-stu-id="f6c08-113">In this case a standard endpoint, using UDP multicast is added as the announcement endpoint.</span></span> <span data-ttu-id="f6c08-114">Vysílá oznámení přes dobře známou adresu UDP.</span><span class="sxs-lookup"><span data-stu-id="f6c08-114">This broadcasts the announcements over a well-known UDP address.</span></span>

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

## <a name="client"></a><span data-ttu-id="f6c08-115">Klient</span><span class="sxs-lookup"><span data-stu-id="f6c08-115">Client</span></span>

<span data-ttu-id="f6c08-116">V tomto projektu si všimněte, že klient hostuje <xref:System.ServiceModel.Discovery.AnnouncementService>.</span><span class="sxs-lookup"><span data-stu-id="f6c08-116">In this project, note that the client hosts an <xref:System.ServiceModel.Discovery.AnnouncementService>.</span></span> <span data-ttu-id="f6c08-117">Kromě toho jsou pro události registrovány dva Delegáti.</span><span class="sxs-lookup"><span data-stu-id="f6c08-117">Furthermore, two delegates are registered with events.</span></span> <span data-ttu-id="f6c08-118">Tyto události určují, co klient provede při přijetí online a offline oznámení.</span><span class="sxs-lookup"><span data-stu-id="f6c08-118">These events dictate what the client does when online and offline announcements are received.</span></span>

```csharp
// Create an AnnouncementService instance
AnnouncementService announcementService = new AnnouncementService();

// Subscribe the announcement events
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;
```

<span data-ttu-id="f6c08-119">Metody `OnOnlineEvent` a `OnOfflineEvent` zpracovávají zprávy o oznámeních Hello a bye v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="f6c08-119">The `OnOnlineEvent` and `OnOfflineEvent` methods handle the hello and bye announcement messages respectively.</span></span>

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

#### <a name="to-use-this-sample"></a><span data-ttu-id="f6c08-120">Použití této ukázky</span><span class="sxs-lookup"><span data-stu-id="f6c08-120">To use this sample</span></span>

1. <span data-ttu-id="f6c08-121">V této ukázce se používají koncové body HTTP a ke spuštění této ukázky se musí přidat správné seznamy ACL adres URL. Podrobnosti najdete v tématu [Konfigurace HTTP a HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) .</span><span class="sxs-lookup"><span data-stu-id="f6c08-121">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) for details.</span></span> <span data-ttu-id="f6c08-122">Spuštění následujícího příkazu u zvýšeného oprávnění by mělo přidat příslušné seznamy ACL.</span><span class="sxs-lookup"><span data-stu-id="f6c08-122">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="f6c08-123">Pokud příkaz nefunguje tak, jak je, je vhodné nahradit doménu a uživatelské jméno pro následující argumenty.</span><span class="sxs-lookup"><span data-stu-id="f6c08-123">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. <span data-ttu-id="f6c08-124">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="f6c08-124">Build the solution.</span></span>

3. <span data-ttu-id="f6c08-125">Spusťte aplikaci Client. exe.</span><span class="sxs-lookup"><span data-stu-id="f6c08-125">Run the client.exe application.</span></span>

4. <span data-ttu-id="f6c08-126">Spusťte aplikaci Service. exe.</span><span class="sxs-lookup"><span data-stu-id="f6c08-126">Run the service.exe application.</span></span> <span data-ttu-id="f6c08-127">Všimněte si, že klient obdrží online oznámení.</span><span class="sxs-lookup"><span data-stu-id="f6c08-127">Note the client receives an online announcement.</span></span>

5. <span data-ttu-id="f6c08-128">Zavřete aplikaci Service. exe.</span><span class="sxs-lookup"><span data-stu-id="f6c08-128">Close the service.exe application.</span></span> <span data-ttu-id="f6c08-129">Všimněte si, že klient obdrží oznámení v režimu offline.</span><span class="sxs-lookup"><span data-stu-id="f6c08-129">Note the client receives an offline announcement.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f6c08-130">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="f6c08-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f6c08-131">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="f6c08-131">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="f6c08-132">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="f6c08-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f6c08-133">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f6c08-133">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`
