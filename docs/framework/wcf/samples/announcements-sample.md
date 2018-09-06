---
title: Ukázka oznámení
ms.date: 03/30/2017
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
ms.openlocfilehash: a82056844c9ec8f77bce4b0adec481a025894d1f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865719"
---
# <a name="announcements-sample"></a><span data-ttu-id="6c637-102">Ukázka oznámení</span><span class="sxs-lookup"><span data-stu-id="6c637-102">Announcements Sample</span></span>
<span data-ttu-id="6c637-103">Tento příklad ukazuje, jak používat funkci oznámení funkci zjišťování.</span><span class="sxs-lookup"><span data-stu-id="6c637-103">This sample shows how to use the Announcement functionality of the Discovery feature.</span></span> <span data-ttu-id="6c637-104">Oznámení povolte službám posílat zprávy oznámení, které obsahují metadata týkající se služby.</span><span class="sxs-lookup"><span data-stu-id="6c637-104">Announcements allow services to send out announcement messages that contain metadata about the service.</span></span> <span data-ttu-id="6c637-105">Ve výchozím nastavení hello oznámení se odešle, když služba po spuštění a bye oznámení se odešle, když je služba ukončena.</span><span class="sxs-lookup"><span data-stu-id="6c637-105">By default a hello announcement is sent when the service starts up and a bye announcement is sent when the service shuts down.</span></span> <span data-ttu-id="6c637-106">Tato oznámení mohou být vícesměrového vysílání nebo mohou být odesílány typu point-to-point.</span><span class="sxs-lookup"><span data-stu-id="6c637-106">These announcements can be multicast or they can be sent point-to-point.</span></span> <span data-ttu-id="6c637-107">Tento příklad se skládá z klienta a služby dva projekty.</span><span class="sxs-lookup"><span data-stu-id="6c637-107">This sample consists of two projects service and client.</span></span>  
  
## <a name="service"></a><span data-ttu-id="6c637-108">Služba</span><span class="sxs-lookup"><span data-stu-id="6c637-108">Service</span></span>  
 <span data-ttu-id="6c637-109">Tento projekt obsahuje službu kalkulačky v místním prostředí.</span><span class="sxs-lookup"><span data-stu-id="6c637-109">This project contains a self-hosted calculator service.</span></span> <span data-ttu-id="6c637-110">V `Main` metody vytvoření hostitele služby a koncového bodu služby se přidá do ní.</span><span class="sxs-lookup"><span data-stu-id="6c637-110">In the `Main` method, a service host is created and a service endpoint is added to it.</span></span> <span data-ttu-id="6c637-111">Další, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> se vytvoří.</span><span class="sxs-lookup"><span data-stu-id="6c637-111">Next, a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is created.</span></span> <span data-ttu-id="6c637-112">Pokud chcete povolit oznámení, musí koncový bod oznámení přidaný do <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span><span class="sxs-lookup"><span data-stu-id="6c637-112">To enable announcements, an announcement endpoint must be added to the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span> <span data-ttu-id="6c637-113">V tomto případě je standardní koncový bod, používat UDP, vícesměrového vysílání se přidá jako koncový bod oznámení.</span><span class="sxs-lookup"><span data-stu-id="6c637-113">In this case a standard endpoint, using UDP multicast is added as the announcement endpoint.</span></span> <span data-ttu-id="6c637-114">Toto oznámení vysílá prostřednictvím dobře známé adrese UDP.</span><span class="sxs-lookup"><span data-stu-id="6c637-114">This broadcasts the announcements over a well-known UDP address.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="6c637-115">Klient</span><span class="sxs-lookup"><span data-stu-id="6c637-115">Client</span></span>  
 <span data-ttu-id="6c637-116">V tomto projektu, Všimněte si, že hostitele klienta <xref:System.ServiceModel.Discovery.AnnouncementService>.</span><span class="sxs-lookup"><span data-stu-id="6c637-116">In this project, note that the client hosts an <xref:System.ServiceModel.Discovery.AnnouncementService>.</span></span> <span data-ttu-id="6c637-117">Kromě toho jsou registrovány dvou delegátů událostí.</span><span class="sxs-lookup"><span data-stu-id="6c637-117">Furthermore, two delegates are registered with events.</span></span> <span data-ttu-id="6c637-118">Tyto události určují, co klient nemá při přijetí oznámení týkající se online i offline.</span><span class="sxs-lookup"><span data-stu-id="6c637-118">These events dictate what the client does when online and offline announcements are received.</span></span>  
  
```  
// Create an AnnouncementService instance  
AnnouncementService announcementService = new AnnouncementService();  
  
// Subscribe the announcement events  
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;  
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;  
```  
  
 <span data-ttu-id="6c637-119">`OnOnlineEvent` a `OnOfflineEvent` metody zpracovávají hello a bye zprávy oznámení v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="6c637-119">The `OnOnlineEvent` and `OnOfflineEvent` methods handle the hello and bye announcement messages respectively.</span></span>  
  
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
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="6c637-120">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="6c637-120">To use this sample</span></span>  
  
1.  <span data-ttu-id="6c637-121">Tato ukázka používá koncové body HTTP a použít tuto ukázku, správné seznamy ACL adresy URL musí být přidán viz [konfigurace HTTP a HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="6c637-121">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) for details.</span></span> <span data-ttu-id="6c637-122">Provádění se zvýšenými oprávněními následující příkaz by měl přidat příslušné seznamy ACL.</span><span class="sxs-lookup"><span data-stu-id="6c637-122">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="6c637-123">Můžete nahradit doména a uživatelské jméno pro následující argumenty, pokud příkaz nefunguje, jak je.</span><span class="sxs-lookup"><span data-stu-id="6c637-123">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  <span data-ttu-id="6c637-124">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="6c637-124">Build the solution.</span></span>  
  
3.  <span data-ttu-id="6c637-125">Spusťte aplikaci client.exe.</span><span class="sxs-lookup"><span data-stu-id="6c637-125">Run the client.exe application.</span></span>  
  
4.  <span data-ttu-id="6c637-126">Spusťte aplikaci service.exe.</span><span class="sxs-lookup"><span data-stu-id="6c637-126">Run the service.exe application.</span></span> <span data-ttu-id="6c637-127">Všimněte si, že klient obdrží oznámení online.</span><span class="sxs-lookup"><span data-stu-id="6c637-127">Note the client receives an online announcement.</span></span>  
  
5.  <span data-ttu-id="6c637-128">Ukončete aplikaci service.exe.</span><span class="sxs-lookup"><span data-stu-id="6c637-128">Close the service.exe application.</span></span> <span data-ttu-id="6c637-129">Všimněte si, že klient obdrží oznámení v režimu offline.</span><span class="sxs-lookup"><span data-stu-id="6c637-129">Note the client receives an offline announcement.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6c637-130">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="6c637-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6c637-131">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="6c637-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6c637-132">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="6c637-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6c637-133">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="6c637-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`  
  
## <a name="see-also"></a><span data-ttu-id="6c637-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c637-134">See Also</span></span>
