---
title: "Postupy: testování zjišťování Proxy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e6494a96f5e7e3a420c8443eff767b0e86d3bc25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-test-the-discovery-proxy"></a><span data-ttu-id="2a63f-102">Postupy: testování zjišťování Proxy</span><span class="sxs-lookup"><span data-stu-id="2a63f-102">How to: Test the Discovery Proxy</span></span>
<span data-ttu-id="2a63f-103">Toto je čtvrtý čtyři témata, která ukazuje, jak implementace zjišťování proxy.</span><span class="sxs-lookup"><span data-stu-id="2a63f-103">This is the fourth of four topics that shows how to implement a discovery proxy.</span></span> <span data-ttu-id="2a63f-104">V předchozích tématu [postupy: Implementace klientské aplikace používající zjišťování Proxy k vyhledání služby](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), můžete implementovat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientskou aplikaci, která používá zjišťování proxy k vyhledání služby a potom zavolá Služba.</span><span class="sxs-lookup"><span data-stu-id="2a63f-104">In the previous topic, [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), you implemented a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application that uses the discovery proxy to find a service and then calls the service.</span></span> <span data-ttu-id="2a63f-105">Toto téma popisuje postup ověření zjišťování proxy, služby a pracovní aplikace klienta podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="2a63f-105">This topic describes how to verify the discovery proxy, the service, and the client application work as expected.</span></span>  
  
### <a name="run-the-discovery-proxy"></a><span data-ttu-id="2a63f-106">Spustit zjišťování Proxy</span><span class="sxs-lookup"><span data-stu-id="2a63f-106">Run the Discovery Proxy</span></span>  
  
1.  <span data-ttu-id="2a63f-107">Otevřete příkazový řádek jako správce.</span><span class="sxs-lookup"><span data-stu-id="2a63f-107">Open a command prompt as an administrator.</span></span>  
  
2.  <span data-ttu-id="2a63f-108">Mohou se zobrazit dialogové okno s upozorněním: brány Windows Firewall zablokovala některé funkce tohoto programu.</span><span class="sxs-lookup"><span data-stu-id="2a63f-108">You may see a dialog that says: Windows Firewall has blocked some features of this program.</span></span> <span data-ttu-id="2a63f-109">Pokud se zobrazí tato zpráva, klikněte **Odblokovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="2a63f-109">If you see this message, click the **Unblock** button.</span></span>  
  
3.  <span data-ttu-id="2a63f-110">V příkazovém řádku spusťte zjišťování proxy, DiscoveryProxy.exe.</span><span class="sxs-lookup"><span data-stu-id="2a63f-110">Within the command prompt, run the discovery proxy, DiscoveryProxy.exe.</span></span>  
  
4.  <span data-ttu-id="2a63f-111">Aplikace by měl zobrazit následující text: `Proxy started. Hit Enter to exit`.</span><span class="sxs-lookup"><span data-stu-id="2a63f-111">The application should display the following text: `Proxy started. Hit Enter to exit`.</span></span>  
  
### <a name="run-the-discoverable-service"></a><span data-ttu-id="2a63f-112">Spusťte službu zjistitelný</span><span class="sxs-lookup"><span data-stu-id="2a63f-112">Run the Discoverable Service</span></span>  
  
1.  <span data-ttu-id="2a63f-113">Otevřete příkazový řádek jako správce.</span><span class="sxs-lookup"><span data-stu-id="2a63f-113">Open a command prompt as an administrator.</span></span>  
  
2.  <span data-ttu-id="2a63f-114">V příkazovém řádku spusťte službu Service.exe zjistitelný.</span><span class="sxs-lookup"><span data-stu-id="2a63f-114">Within the command prompt, run the Service.exe discoverable service.</span></span>  
  
3.  <span data-ttu-id="2a63f-115">DiscoveryProxy.exe by měl zobrazit následující text: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span><span class="sxs-lookup"><span data-stu-id="2a63f-115">The DiscoveryProxy.exe should display the following text: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span></span>  
  
### <a name="run-the-client-application"></a><span data-ttu-id="2a63f-116">Spustit klientskou aplikaci</span><span class="sxs-lookup"><span data-stu-id="2a63f-116">Run the Client Application</span></span>  
  
1.  <span data-ttu-id="2a63f-117">Otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="2a63f-117">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="2a63f-118">V příkazovém řádku spusťte aplikaci client.exe.</span><span class="sxs-lookup"><span data-stu-id="2a63f-118">Within the command prompt, run the client.exe application.</span></span>  
  
3.  <span data-ttu-id="2a63f-119">Za několik sekund klientská aplikace zobrazí následující text: připojení k [koncový bod služby].</span><span class="sxs-lookup"><span data-stu-id="2a63f-119">After a few seconds the client application displays the following text: Connecting to [Service-Endpoint].</span></span>  
  
4.  <span data-ttu-id="2a63f-120">Service.exe pak by měl zobrazit následující text: s pozdravem přišel požadavek, I bude odpovídat.</span><span class="sxs-lookup"><span data-stu-id="2a63f-120">The service.exe should then display the following text: Greeting request received, I will respond.</span></span>  
  
5.  <span data-ttu-id="2a63f-121">Client.exe pak by měl zobrazit následující text: Hello klienta!</span><span class="sxs-lookup"><span data-stu-id="2a63f-121">The client.exe should then display the following text: Hello Client!</span></span>  
  
### <a name="shut-down-the-applications"></a><span data-ttu-id="2a63f-122">Vypnout aplikace</span><span class="sxs-lookup"><span data-stu-id="2a63f-122">Shut Down the Applications</span></span>  
  
1.  <span data-ttu-id="2a63f-123">Vypněte klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="2a63f-123">Shut down the client application.</span></span>  
  
2.  <span data-ttu-id="2a63f-124">Vypnutí služby.</span><span class="sxs-lookup"><span data-stu-id="2a63f-124">Shut down the service.</span></span> <span data-ttu-id="2a63f-125">Zjišťování proxy zobrazí následující text: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span><span class="sxs-lookup"><span data-stu-id="2a63f-125">The discovery proxy displays the following text: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span></span>  
  
3.  <span data-ttu-id="2a63f-126">Vypněte zjišťování proxy.</span><span class="sxs-lookup"><span data-stu-id="2a63f-126">Shut down the discovery proxy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a63f-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a63f-127">See Also</span></span>  
 [<span data-ttu-id="2a63f-128">Přehled zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="2a63f-128">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [<span data-ttu-id="2a63f-129">Postupy: Implementace proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="2a63f-129">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 [<span data-ttu-id="2a63f-130">Postupy: Implementace zjistitelné služby, která se registruje pomocí proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="2a63f-130">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 [<span data-ttu-id="2a63f-131">Postupy: Implementace klientské aplikace používající proxy zjišťování k vyhledání služby</span><span class="sxs-lookup"><span data-stu-id="2a63f-131">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
