---
title: 'Postupy: Test proxy zjišťování'
ms.date: 03/30/2017
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
ms.openlocfilehash: 13d2e8ca46e634e3b27c8eb967d89d860df1c72d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176277"
---
# <a name="how-to-test-the-discovery-proxy"></a><span data-ttu-id="a7f62-102">Postupy: Test proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="a7f62-102">How to: Test the Discovery Proxy</span></span>
<span data-ttu-id="a7f62-103">Toto je čtvrtý čtyři témat, která ukazuje, jak implementace zjišťování proxy.</span><span class="sxs-lookup"><span data-stu-id="a7f62-103">This is the fourth of four topics that shows how to implement a discovery proxy.</span></span> <span data-ttu-id="a7f62-104">V předchozím tématu [jak: Implementace klientské aplikace používající zjišťování Proxy k vyhledání služby](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), jste implementovali WCF klientská aplikace, která používá proxy zjišťování k vyhledání služby a pak zavolá služba.</span><span class="sxs-lookup"><span data-stu-id="a7f62-104">In the previous topic, [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), you implemented a WCF client application that uses the discovery proxy to find a service and then calls the service.</span></span> <span data-ttu-id="a7f62-105">Toto téma popisuje postup pro ověření proxy zjišťování, služby a pracovní aplikace klienta podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="a7f62-105">This topic describes how to verify the discovery proxy, the service, and the client application work as expected.</span></span>  
  
### <a name="run-the-discovery-proxy"></a><span data-ttu-id="a7f62-106">Spustit zjišťování Proxy</span><span class="sxs-lookup"><span data-stu-id="a7f62-106">Run the Discovery Proxy</span></span>  
  
1.  <span data-ttu-id="a7f62-107">Otevřete příkazový řádek jako správce.</span><span class="sxs-lookup"><span data-stu-id="a7f62-107">Open a command prompt as an administrator.</span></span>  
  
2.  <span data-ttu-id="a7f62-108">Může se zobrazit dialogové okno s upozorněním: Brána Windows Firewall zablokovala některé funkce tohoto programu.</span><span class="sxs-lookup"><span data-stu-id="a7f62-108">You may see a dialog that says: Windows Firewall has blocked some features of this program.</span></span> <span data-ttu-id="a7f62-109">Pokud se zobrazí tato zpráva, klikněte na tlačítko **Odblokovat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="a7f62-109">If you see this message, click the **Unblock** button.</span></span>  
  
3.  <span data-ttu-id="a7f62-110">V příkazovém řádku spusťte zjišťování proxy DiscoveryProxy.exe.</span><span class="sxs-lookup"><span data-stu-id="a7f62-110">Within the command prompt, run the discovery proxy, DiscoveryProxy.exe.</span></span>  
  
4.  <span data-ttu-id="a7f62-111">Aplikace by měly zobrazit následující text: `Proxy started. Hit Enter to exit`.</span><span class="sxs-lookup"><span data-stu-id="a7f62-111">The application should display the following text: `Proxy started. Hit Enter to exit`.</span></span>  
  
### <a name="run-the-discoverable-service"></a><span data-ttu-id="a7f62-112">Spustit zjistitelné služby</span><span class="sxs-lookup"><span data-stu-id="a7f62-112">Run the Discoverable Service</span></span>  
  
1.  <span data-ttu-id="a7f62-113">Otevřete příkazový řádek jako správce.</span><span class="sxs-lookup"><span data-stu-id="a7f62-113">Open a command prompt as an administrator.</span></span>  
  
2.  <span data-ttu-id="a7f62-114">V příkazovém řádku spusťte Service.exe zjistitelné služby.</span><span class="sxs-lookup"><span data-stu-id="a7f62-114">Within the command prompt, run the Service.exe discoverable service.</span></span>  
  
3.  <span data-ttu-id="a7f62-115">DiscoveryProxy.exe by měly zobrazit následující text: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span><span class="sxs-lookup"><span data-stu-id="a7f62-115">The DiscoveryProxy.exe should display the following text: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span></span>  
  
### <a name="run-the-client-application"></a><span data-ttu-id="a7f62-116">Spuštění klientské aplikace</span><span class="sxs-lookup"><span data-stu-id="a7f62-116">Run the Client Application</span></span>  
  
1.  <span data-ttu-id="a7f62-117">Otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="a7f62-117">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="a7f62-118">V příkazovém řádku spusťte client.exe aplikace.</span><span class="sxs-lookup"><span data-stu-id="a7f62-118">Within the command prompt, run the client.exe application.</span></span>  
  
3.  <span data-ttu-id="a7f62-119">Klientská aplikace po několik sekund zobrazí následující text: Připojení k [Service-Endpoint].</span><span class="sxs-lookup"><span data-stu-id="a7f62-119">After a few seconds the client application displays the following text: Connecting to [Service-Endpoint].</span></span>  
  
4.  <span data-ttu-id="a7f62-120">Service.exe by pak zobrazí následující text: Byla přijata žádost o pozdrav, můžu odpoví.</span><span class="sxs-lookup"><span data-stu-id="a7f62-120">The service.exe should then display the following text: Greeting request received, I will respond.</span></span>  
  
5.  <span data-ttu-id="a7f62-121">Client.exe by pak zobrazí následující text: Klient Hello!</span><span class="sxs-lookup"><span data-stu-id="a7f62-121">The client.exe should then display the following text: Hello Client!</span></span>  
  
### <a name="shut-down-the-applications"></a><span data-ttu-id="a7f62-122">Ukončení aplikace</span><span class="sxs-lookup"><span data-stu-id="a7f62-122">Shut Down the Applications</span></span>  
  
1.  <span data-ttu-id="a7f62-123">Vypněte klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="a7f62-123">Shut down the client application.</span></span>  
  
2.  <span data-ttu-id="a7f62-124">Vypnutí služby.</span><span class="sxs-lookup"><span data-stu-id="a7f62-124">Shut down the service.</span></span> <span data-ttu-id="a7f62-125">Proxy zjišťování se zobrazí následující text: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span><span class="sxs-lookup"><span data-stu-id="a7f62-125">The discovery proxy displays the following text: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span></span>  
  
3.  <span data-ttu-id="a7f62-126">Vypněte proxy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="a7f62-126">Shut down the discovery proxy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7f62-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a7f62-127">See also</span></span>

- [<span data-ttu-id="a7f62-128">Přehled zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="a7f62-128">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [<span data-ttu-id="a7f62-129">Postupy: Implementace zjišťování proxy</span><span class="sxs-lookup"><span data-stu-id="a7f62-129">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)
- [<span data-ttu-id="a7f62-130">Postupy: Implementace zjistitelné služby, která se registruje pomocí proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="a7f62-130">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)
- [<span data-ttu-id="a7f62-131">Postupy: Implementace klientské aplikace používající zjišťování proxy k vyhledání služby</span><span class="sxs-lookup"><span data-stu-id="a7f62-131">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
