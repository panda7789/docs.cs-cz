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
# <a name="announcements-sample"></a><span data-ttu-id="dbaca-102">Ukázka oznámení</span><span class="sxs-lookup"><span data-stu-id="dbaca-102">Announcements Sample</span></span>

<span data-ttu-id="dbaca-103">V této ukázce se dozvíte, jak používat funkci oznámení funkce zjišťování.</span><span class="sxs-lookup"><span data-stu-id="dbaca-103">This sample shows how to use the Announcement functionality of the Discovery feature.</span></span> <span data-ttu-id="dbaca-104">Oznámení umožňují službám posílat zprávy oznámení, které obsahují metadata o službě.</span><span class="sxs-lookup"><span data-stu-id="dbaca-104">Announcements allow services to send out announcement messages that contain metadata about the service.</span></span> <span data-ttu-id="dbaca-105">Ve výchozím nastavení se při spuštění služby pošle oznámení o signálu Hello a pošle se oznámení bye při ukončení služby.</span><span class="sxs-lookup"><span data-stu-id="dbaca-105">By default a hello announcement is sent when the service starts up and a bye announcement is sent when the service shuts down.</span></span> <span data-ttu-id="dbaca-106">Tato oznámení můžou být vícesměrové vysílání nebo se můžou poslat Point-to-Point.</span><span class="sxs-lookup"><span data-stu-id="dbaca-106">These announcements can be multicast or they can be sent point-to-point.</span></span> <span data-ttu-id="dbaca-107">Tato ukázka se skládá ze dvou projektů služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="dbaca-107">This sample consists of two projects service and client.</span></span>

## <a name="service"></a><span data-ttu-id="dbaca-108">Služba</span><span class="sxs-lookup"><span data-stu-id="dbaca-108">Service</span></span>

<span data-ttu-id="dbaca-109">Tento projekt obsahuje službu kalkulačky s místním hostováním.</span><span class="sxs-lookup"><span data-stu-id="dbaca-109">This project contains a self-hosted calculator service.</span></span> <span data-ttu-id="dbaca-110">`Main` V metodě se vytvoří hostitel služby a do něj se přidá koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="dbaca-110">In the `Main` method, a service host is created and a service endpoint is added to it.</span></span> <span data-ttu-id="dbaca-111">Dále se vytvoří <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> .</span><span class="sxs-lookup"><span data-stu-id="dbaca-111">Next, a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is created.</span></span> <span data-ttu-id="dbaca-112">Chcete-li povolit oznámení, je nutné do <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>přidat koncový bod oznámení.</span><span class="sxs-lookup"><span data-stu-id="dbaca-112">To enable announcements, an announcement endpoint must be added to the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span> <span data-ttu-id="dbaca-113">V tomto případě se jako koncový bod oznámení přidá standardní koncový bod pomocí vícesměrového vysílání UDP.</span><span class="sxs-lookup"><span data-stu-id="dbaca-113">In this case a standard endpoint, using UDP multicast is added as the announcement endpoint.</span></span> <span data-ttu-id="dbaca-114">Vysílá oznámení přes dobře známou adresu UDP.</span><span class="sxs-lookup"><span data-stu-id="dbaca-114">This broadcasts the announcements over a well-known UDP address.</span></span>

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

## <a name="client"></a><span data-ttu-id="dbaca-115">Klient</span><span class="sxs-lookup"><span data-stu-id="dbaca-115">Client</span></span>

<span data-ttu-id="dbaca-116">V tomto projektu si všimněte, že klient hostuje <xref:System.ServiceModel.Discovery.AnnouncementService>.</span><span class="sxs-lookup"><span data-stu-id="dbaca-116">In this project, note that the client hosts an <xref:System.ServiceModel.Discovery.AnnouncementService>.</span></span> <span data-ttu-id="dbaca-117">Kromě toho jsou pro události registrovány dva Delegáti.</span><span class="sxs-lookup"><span data-stu-id="dbaca-117">Furthermore, two delegates are registered with events.</span></span> <span data-ttu-id="dbaca-118">Tyto události určují, co klient provede při přijetí online a offline oznámení.</span><span class="sxs-lookup"><span data-stu-id="dbaca-118">These events dictate what the client does when online and offline announcements are received.</span></span>

```csharp
// Create an AnnouncementService instance
AnnouncementService announcementService = new AnnouncementService();

// Subscribe the announcement events
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;
```

<span data-ttu-id="dbaca-119">Metody `OnOnlineEvent` a`OnOfflineEvent` zpracovávají zprávy o oznámeních Hello a bye v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="dbaca-119">The `OnOnlineEvent` and `OnOfflineEvent` methods handle the hello and bye announcement messages respectively.</span></span>

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

#### <a name="to-use-this-sample"></a><span data-ttu-id="dbaca-120">Použití této ukázky</span><span class="sxs-lookup"><span data-stu-id="dbaca-120">To use this sample</span></span>

1. <span data-ttu-id="dbaca-121">V této ukázce se používají koncové body HTTP a ke spuštění této ukázky se musí přidat správné seznamy ACL adres URL. Podrobnosti najdete v tématu [Konfigurace HTTP a HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) .</span><span class="sxs-lookup"><span data-stu-id="dbaca-121">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) for details.</span></span> <span data-ttu-id="dbaca-122">Spuštění následujícího příkazu u zvýšeného oprávnění by mělo přidat příslušné seznamy ACL.</span><span class="sxs-lookup"><span data-stu-id="dbaca-122">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="dbaca-123">Pokud příkaz nefunguje tak, jak je, je vhodné nahradit doménu a uživatelské jméno pro následující argumenty.</span><span class="sxs-lookup"><span data-stu-id="dbaca-123">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. <span data-ttu-id="dbaca-124">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="dbaca-124">Build the solution.</span></span>

3. <span data-ttu-id="dbaca-125">Spusťte aplikaci Client. exe.</span><span class="sxs-lookup"><span data-stu-id="dbaca-125">Run the client.exe application.</span></span>

4. <span data-ttu-id="dbaca-126">Spusťte aplikaci Service. exe.</span><span class="sxs-lookup"><span data-stu-id="dbaca-126">Run the service.exe application.</span></span> <span data-ttu-id="dbaca-127">Všimněte si, že klient obdrží online oznámení.</span><span class="sxs-lookup"><span data-stu-id="dbaca-127">Note the client receives an online announcement.</span></span>

5. <span data-ttu-id="dbaca-128">Zavřete aplikaci Service. exe.</span><span class="sxs-lookup"><span data-stu-id="dbaca-128">Close the service.exe application.</span></span> <span data-ttu-id="dbaca-129">Všimněte si, že klient obdrží oznámení v režimu offline.</span><span class="sxs-lookup"><span data-stu-id="dbaca-129">Note the client receives an offline announcement.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dbaca-130">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="dbaca-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="dbaca-131">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="dbaca-131">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="dbaca-132">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="dbaca-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dbaca-133">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="dbaca-133">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`
