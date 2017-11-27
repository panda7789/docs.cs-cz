---
title: "Automatické konfigurace protokolu IPv6"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 581c1d21-1013-43a3-bf3e-2d9ead62b79c
caps.latest.revision: "5"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 0332bca146041aa955ea000cfeee78d3f5287036
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ipv6-auto-configuration"></a><span data-ttu-id="68657-102">Automatické konfigurace protokolu IPv6</span><span class="sxs-lookup"><span data-stu-id="68657-102">IPv6 Auto-Configuration</span></span>
<span data-ttu-id="68657-103">Jeden cíl důležité pro protokol IPv6 je podpora uzlu technologie Plug and Play.</span><span class="sxs-lookup"><span data-stu-id="68657-103">One important goal for IPv6 is to support node Plug and Play.</span></span> <span data-ttu-id="68657-104">To znamená musí být možné připojit k síti IPv6 uzlu a automaticky konfigurace bez lidského zásahu.</span><span class="sxs-lookup"><span data-stu-id="68657-104">That is, it should be possible to plug a node into an IPv6 network and have it automatically configured without any human intervention.</span></span>  
  
## <a name="type-of-auto-configuration"></a><span data-ttu-id="68657-105">Typ automatické konfigurace</span><span class="sxs-lookup"><span data-stu-id="68657-105">Type of Auto-Configuration</span></span>  
 <span data-ttu-id="68657-106">IPv6 podporuje následující typy automatické konfigurace:</span><span class="sxs-lookup"><span data-stu-id="68657-106">IPv6 supports the following types of auto-configuration:</span></span>  
  
-   <span data-ttu-id="68657-107">**Stavová automatické konfigurace**.</span><span class="sxs-lookup"><span data-stu-id="68657-107">**Stateful auto-configuration**.</span></span> <span data-ttu-id="68657-108">Tento typ konfigurace vyžaduje určitou úroveň lidského zásahu, protože je nutné Dynamic Host Configuration Protocol pro protokol IPv6 (DHCPv6) server pro instalaci a správu uzlů.</span><span class="sxs-lookup"><span data-stu-id="68657-108">This type of configuration requires a certain level of human intervention because it needs a Dynamic Host Configuration Protocol for IPv6 (DHCPv6) server for the installation and administration of the nodes.</span></span> <span data-ttu-id="68657-109">DHCPv6 server udržuje seznam uzlů, na které poskytne informace o konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="68657-109">The DHCPv6 server keeps a list of nodes to which it supplies configuration information.</span></span> <span data-ttu-id="68657-110">Také udržuje informace o stavu, aby server věděli, jak dlouho každou adresu se používá, a když může být k dispozici pro změnu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="68657-110">It also maintains state information so the server knows how long each address is in use, and when it might be available for reassignment.</span></span>  
  
-   <span data-ttu-id="68657-111">**Bezstavové automatické konfigurace**.</span><span class="sxs-lookup"><span data-stu-id="68657-111">**Stateless auto-configuration**.</span></span> <span data-ttu-id="68657-112">Tento typ konfigurace je vhodná pro malé organizace a jednotlivci.</span><span class="sxs-lookup"><span data-stu-id="68657-112">This type of configuration is suitable for small organizations and individuals.</span></span> <span data-ttu-id="68657-113">V takovém případě každý hostitel Určuje jeho adresy z obsahu přijaté zprávy o trasách.</span><span class="sxs-lookup"><span data-stu-id="68657-113">In this case, each host determines its addresses from the contents of received router advertisements.</span></span> <span data-ttu-id="68657-114">Standard IEEE EUI-64 používá k definování části ID sítě adresy, je možné logicky předpokládat, že jedinečnost adresy hostitele na odkaz.</span><span class="sxs-lookup"><span data-stu-id="68657-114">Using the IEEE EUI-64 standard to define the network ID portion of the address, it is reasonable to assume the uniqueness of the host address on the link.</span></span>  
  
 <span data-ttu-id="68657-115">Bez ohledu na to, jakým způsobem je určován adresu musí uzel ověřte, zda je jedinečný místní odkaz na jeho potenciální adresa.</span><span class="sxs-lookup"><span data-stu-id="68657-115">Regardless of how the address is determined, the node must verify that its potential address is unique to the local link.</span></span> <span data-ttu-id="68657-116">K tomu je potřeba odesílání sousedním oslovení zprávu na adresu potenciální.</span><span class="sxs-lookup"><span data-stu-id="68657-116">This is done by sending a neighbor solicitation message to the potential address.</span></span> <span data-ttu-id="68657-117">Pokud uzel přijme všechny odpovědi, ví, že adresa je již používán a musí určit jinou adresu.</span><span class="sxs-lookup"><span data-stu-id="68657-117">If the node receives any response, it knows that the address is already in use and must determine another address.</span></span>  
  
## <a name="ipv6-mobility"></a><span data-ttu-id="68657-118">IPv6 Mobility</span><span class="sxs-lookup"><span data-stu-id="68657-118">IPv6 Mobility</span></span>  
 <span data-ttu-id="68657-119">Jak narůstá počet mobilních zařízení, zavádí nový požadavek: zařízení musí být schopen libovolně změnit umístění na Internetu s protokolem IPv6 a přitom zachovat stávající připojení.</span><span class="sxs-lookup"><span data-stu-id="68657-119">The proliferation of mobile devices has introduced a new requirement: A device must be able to arbitrarily change locations on the IPv6 Internet and still maintain existing connections.</span></span> <span data-ttu-id="68657-120">Tuto funkčnost poskytovaly mobilní uzlu přiřazena domovské adresy, kde ji můžete vždy dostupný.</span><span class="sxs-lookup"><span data-stu-id="68657-120">To provide this functionality, a mobile node is assigned a home address at which it can always be reached.</span></span> <span data-ttu-id="68657-121">Když mobilní uzlu v domácnostech, připojí k odkaz na domovskou a používá svůj domácí adresu.</span><span class="sxs-lookup"><span data-stu-id="68657-121">When the mobile node is at home, it connects to the home link and uses its home address.</span></span> <span data-ttu-id="68657-122">Po mimo domov uzlu Mobilní domácí agenta, který je obvykle směrovač, předává zprávy mezi mobilní uzlů a uzly, se kterými je komunikaci.</span><span class="sxs-lookup"><span data-stu-id="68657-122">When the mobile node is away from home, a home agent, which is usually a router, relays messages between the mobile node and nodes with which it is communicating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68657-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="68657-123">See Also</span></span>  
 [<span data-ttu-id="68657-124">Protokol IP verze 6</span><span class="sxs-lookup"><span data-stu-id="68657-124">Internet Protocol Version 6</span></span>](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [<span data-ttu-id="68657-125">Sokety</span><span class="sxs-lookup"><span data-stu-id="68657-125">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
