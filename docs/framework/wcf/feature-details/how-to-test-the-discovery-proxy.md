---
title: 'Postupy: Test proxy zjišťování'
ms.date: 03/30/2017
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
ms.openlocfilehash: 78921d0a26f1116c87c2931b1472a161d6fed145
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592811"
---
# <a name="how-to-test-the-discovery-proxy"></a><span data-ttu-id="778be-102">Postupy: Test proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="778be-102">How to: Test the Discovery Proxy</span></span>
<span data-ttu-id="778be-103">Toto je čtvrtá část čtyř témat, která ukazuje, jak implementovat proxy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="778be-103">This is the fourth of four topics that shows how to implement a discovery proxy.</span></span> <span data-ttu-id="778be-104">V předchozím tématu [Postupy: implementace klientské aplikace, která používá proxy zjišťování k vyhledání služby](client-app-discovery-proxy-to-find-a-service.md), jste implementovali klientskou aplikaci WCF, která používá proxy zjišťování k vyhledání služby a následné volání služby.</span><span class="sxs-lookup"><span data-stu-id="778be-104">In the previous topic, [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](client-app-discovery-proxy-to-find-a-service.md), you implemented a WCF client application that uses the discovery proxy to find a service and then calls the service.</span></span> <span data-ttu-id="778be-105">Toto téma popisuje, jak ověřit proxy zjišťování, službu a klientská aplikace fungují podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="778be-105">This topic describes how to verify the discovery proxy, the service, and the client application work as expected.</span></span>  
  
### <a name="run-the-discovery-proxy"></a><span data-ttu-id="778be-106">Spustit proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="778be-106">Run the Discovery Proxy</span></span>  
  
1. <span data-ttu-id="778be-107">Otevřete příkazový řádek jako správce.</span><span class="sxs-lookup"><span data-stu-id="778be-107">Open a command prompt as an administrator.</span></span>  
  
2. <span data-ttu-id="778be-108">Může se zobrazit dialogové okno s upozorněním, že brána Windows Firewall zablokovala některé funkce tohoto programu.</span><span class="sxs-lookup"><span data-stu-id="778be-108">You may see a dialog that says: Windows Firewall has blocked some features of this program.</span></span> <span data-ttu-id="778be-109">Pokud se zobrazí tato zpráva, klikněte na tlačítko **odblokovat** .</span><span class="sxs-lookup"><span data-stu-id="778be-109">If you see this message, click the **Unblock** button.</span></span>  
  
3. <span data-ttu-id="778be-110">V příkazovém řádku spusťte proxy zjišťování objektu DiscoveryProxy. exe.</span><span class="sxs-lookup"><span data-stu-id="778be-110">Within the command prompt, run the discovery proxy, DiscoveryProxy.exe.</span></span>  
  
4. <span data-ttu-id="778be-111">Aplikace by měla zobrazit následující text: `Proxy started. Hit Enter to exit` .</span><span class="sxs-lookup"><span data-stu-id="778be-111">The application should display the following text: `Proxy started. Hit Enter to exit`.</span></span>  
  
### <a name="run-the-discoverable-service"></a><span data-ttu-id="778be-112">Spuštění zjistitelné služby</span><span class="sxs-lookup"><span data-stu-id="778be-112">Run the Discoverable Service</span></span>  
  
1. <span data-ttu-id="778be-113">Otevřete příkazový řádek jako správce.</span><span class="sxs-lookup"><span data-stu-id="778be-113">Open a command prompt as an administrator.</span></span>  
  
2. <span data-ttu-id="778be-114">V příkazovém řádku spusťte zjistitelnou službu Service. exe.</span><span class="sxs-lookup"><span data-stu-id="778be-114">Within the command prompt, run the Service.exe discoverable service.</span></span>  
  
3. <span data-ttu-id="778be-115">Objektu DiscoveryProxy. exe by měl zobrazit následující text: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span><span class="sxs-lookup"><span data-stu-id="778be-115">The DiscoveryProxy.exe should display the following text: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span></span>  
  
### <a name="run-the-client-application"></a><span data-ttu-id="778be-116">Spuštění klientské aplikace</span><span class="sxs-lookup"><span data-stu-id="778be-116">Run the Client Application</span></span>  
  
1. <span data-ttu-id="778be-117">Otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="778be-117">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="778be-118">V příkazovém řádku spusťte aplikaci Client. exe.</span><span class="sxs-lookup"><span data-stu-id="778be-118">Within the command prompt, run the client.exe application.</span></span>  
  
3. <span data-ttu-id="778be-119">Po několika sekundách se klientská aplikace zobrazí následující text: připojení ke službě [Service-Endpoint].</span><span class="sxs-lookup"><span data-stu-id="778be-119">After a few seconds the client application displays the following text: Connecting to [Service-Endpoint].</span></span>  
  
4. <span data-ttu-id="778be-120">V souboru Service. exe by se pak měl zobrazit následující text: přijatý požadavek na pozdrav, který reaguje.</span><span class="sxs-lookup"><span data-stu-id="778be-120">The service.exe should then display the following text: Greeting request received, I will respond.</span></span>  
  
5. <span data-ttu-id="778be-121">Soubor Client. exe by pak měl zobrazovat následující text: Hello Client!</span><span class="sxs-lookup"><span data-stu-id="778be-121">The client.exe should then display the following text: Hello Client!</span></span>  
  
### <a name="shut-down-the-applications"></a><span data-ttu-id="778be-122">Vypnutí aplikací</span><span class="sxs-lookup"><span data-stu-id="778be-122">Shut Down the Applications</span></span>  
  
1. <span data-ttu-id="778be-123">Ukončete klientskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="778be-123">Shut down the client application.</span></span>  
  
2. <span data-ttu-id="778be-124">Ukončete službu.</span><span class="sxs-lookup"><span data-stu-id="778be-124">Shut down the service.</span></span> <span data-ttu-id="778be-125">Proxy zjišťování zobrazí následující text: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******` .</span><span class="sxs-lookup"><span data-stu-id="778be-125">The discovery proxy displays the following text: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span></span>  
  
3. <span data-ttu-id="778be-126">Vypněte proxy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="778be-126">Shut down the discovery proxy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="778be-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="778be-127">See also</span></span>

- [<span data-ttu-id="778be-128">Přehled zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="778be-128">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)
- [<span data-ttu-id="778be-129">Postupy: Implementace zjišťování proxy</span><span class="sxs-lookup"><span data-stu-id="778be-129">How to: Implement a Discovery Proxy</span></span>](how-to-implement-a-discovery-proxy.md)
- [<span data-ttu-id="778be-130">Postupy: Implementace zjistitelné služby, která se registruje pomocí proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="778be-130">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](discoverable-service-that-registers-with-the-discovery-proxy.md)
- [<span data-ttu-id="778be-131">Postupy: Implementace klientské aplikace používající proxy zjišťování k vyhledání služby</span><span class="sxs-lookup"><span data-stu-id="778be-131">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](client-app-discovery-proxy-to-find-a-service.md)
