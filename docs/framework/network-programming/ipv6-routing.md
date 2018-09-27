---
title: Směrování IPv6
ms.date: 03/30/2017
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 4ff5f131cfd9fac48e653b98e05d5e46dcfb0bec
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47399018"
---
# <a name="ipv6-routing"></a><span data-ttu-id="b2ac8-102">Směrování IPv6</span><span class="sxs-lookup"><span data-stu-id="b2ac8-102">IPv6 Routing</span></span>
<span data-ttu-id="b2ac8-103">Flexibilní mechanismus směrování je výhodou IPv6.</span><span class="sxs-lookup"><span data-stu-id="b2ac8-103">A flexible routing mechanism is a benefit of IPv6.</span></span> <span data-ttu-id="b2ac8-104">Kvůli způsobu, jakým IPv4, které byly ID sítě a jsou přidělené a velké směrovací tabulky musí být udržována směrovače, které jsou na Internetu páteřních.</span><span class="sxs-lookup"><span data-stu-id="b2ac8-104">Due to the way in which IPv4 network IDs were and are allocated, large routing tables need to be maintained by the routers that are on the Internet backbones.</span></span> <span data-ttu-id="b2ac8-105">Tyto směrovače, jestliže musíte znát všechny trasy k předávání paketů, které jsou potenciálně směrované do kteréhokoli uzlu na Internetu.</span><span class="sxs-lookup"><span data-stu-id="b2ac8-105">These routers must know all the routes in order to forward packets that are potentially directed to any node on the Internet.</span></span> <span data-ttu-id="b2ac8-106">S jeho schopnost agregační adresy IPv6 umožňuje flexibilní adresování a výrazně snižuje velikost směrovací tabulky.</span><span class="sxs-lookup"><span data-stu-id="b2ac8-106">With its ability to aggregate addresses, IPv6 allows flexible addressing and drastically reduces the size of routing tables.</span></span> <span data-ttu-id="b2ac8-107">V této nové architektuře adresování zprostředkující směrovače musí sledovat pouze místní část své síti pro předávání zpráv správně.</span><span class="sxs-lookup"><span data-stu-id="b2ac8-107">In this new addressing architecture, intermediate routers must keep track only of the local portion of their network in order to forward the messages appropriately.</span></span>  
  
## <a name="neighbor-discovery"></a><span data-ttu-id="b2ac8-108">ND</span><span class="sxs-lookup"><span data-stu-id="b2ac8-108">Neighbor Discovery</span></span>  
 <span data-ttu-id="b2ac8-109">Některé z funkcí poskytovaných službou ND jsou:</span><span class="sxs-lookup"><span data-stu-id="b2ac8-109">Some of the features provided by Neighbor Discovery are:</span></span>  
  
-   <span data-ttu-id="b2ac8-110">Zjišťování směrovačů.</span><span class="sxs-lookup"><span data-stu-id="b2ac8-110">Router discovery.</span></span> <span data-ttu-id="b2ac8-111">To umožňuje hostitelům identifikovat místního směrovače.</span><span class="sxs-lookup"><span data-stu-id="b2ac8-111">This allows hosts to identify local routers.</span></span>  
  
-   <span data-ttu-id="b2ac8-112">Adresa řešení.</span><span class="sxs-lookup"><span data-stu-id="b2ac8-112">Address resolution.</span></span> <span data-ttu-id="b2ac8-113">To umožňuje uzly přeložit adresu linkové vrstvě pro příslušnou adresou dalšího směrování (náhrada za Address Resolution Protocol [ARP]).</span><span class="sxs-lookup"><span data-stu-id="b2ac8-113">This allows nodes to resolve a link-layer address for a corresponding next-hop address (a replacement for Address Resolution Protocol [ARP]).</span></span>  
  
-   <span data-ttu-id="b2ac8-114">Automatické konfigurace adresy.</span><span class="sxs-lookup"><span data-stu-id="b2ac8-114">Address auto-configuration.</span></span> <span data-ttu-id="b2ac8-115">To umožňuje hostitelům pro automatickou konfiguraci místní a globální adresy.</span><span class="sxs-lookup"><span data-stu-id="b2ac8-115">This allows hosts to automatically configure site-local and global addresses.</span></span>  
  
 <span data-ttu-id="b2ac8-116">ND používá Internet Control Message Protocol pro protokol IPv6 (ICMPv6) zpráv, které zahrnují:</span><span class="sxs-lookup"><span data-stu-id="b2ac8-116">Neighbor Discovery uses Internet Control Message Protocol for IPv6 (ICMPv6) messages that include:</span></span>  
  
-   <span data-ttu-id="b2ac8-117">Inzerování směrovače.</span><span class="sxs-lookup"><span data-stu-id="b2ac8-117">Router advertisement.</span></span> <span data-ttu-id="b2ac8-118">Odeslaný směrovač částečně pravidelně nebo v reakci na oslovení směrovače.</span><span class="sxs-lookup"><span data-stu-id="b2ac8-118">Sent by a router on a pseudo-periodic basis or in response to a router solicitation.</span></span> <span data-ttu-id="b2ac8-119">Směrovače IPv6 pomocí inzerování směrovače inzerovat jejich dostupnost, předpony a další parametry.</span><span class="sxs-lookup"><span data-stu-id="b2ac8-119">IPv6 routers use router advertisements to advertise their availability, address prefixes, and other parameters.</span></span>  
  
-   <span data-ttu-id="b2ac8-120">Oslovení směrovače.</span><span class="sxs-lookup"><span data-stu-id="b2ac8-120">Router solicitation.</span></span> <span data-ttu-id="b2ac8-121">Odeslaný požádat o směrovače na odkaz okamžitě poslat inzerování směrovače.</span><span class="sxs-lookup"><span data-stu-id="b2ac8-121">Sent by a host to request that routers on the link send a router advertisement immediately.</span></span>  
  
-   <span data-ttu-id="b2ac8-122">Sousední žádostí.</span><span class="sxs-lookup"><span data-stu-id="b2ac8-122">Neighbor solicitation.</span></span> <span data-ttu-id="b2ac8-123">Odeslaný uzly pro rozpoznání adresy, detekce duplicitních adres, nebo chcete-li ověřit, že souseda je stále dostupný.</span><span class="sxs-lookup"><span data-stu-id="b2ac8-123">Sent by nodes for address resolution, duplicate address detection, or to verify that a neighbor is still reachable.</span></span>  
  
-   <span data-ttu-id="b2ac8-124">Sousední oznámení o inzerovaném programu.</span><span class="sxs-lookup"><span data-stu-id="b2ac8-124">Neighbor advertisement.</span></span> <span data-ttu-id="b2ac8-125">Odesílá se uzly reagovat na sousední oslovení nebo oznámit okolí změnu adresy na linkové vrstvě.</span><span class="sxs-lookup"><span data-stu-id="b2ac8-125">Sent by nodes to respond to a neighbor solicitation or to notify neighbors of a change in link-layer address.</span></span>  
  
-   <span data-ttu-id="b2ac8-126">Přesměrování.</span><span class="sxs-lookup"><span data-stu-id="b2ac8-126">Redirect.</span></span> <span data-ttu-id="b2ac8-127">Odesílá udávajících lepší adresa dalšího směrování do určitého cíle pro odesílání uzel.</span><span class="sxs-lookup"><span data-stu-id="b2ac8-127">Sent by routers to indicate a better next-hop address to a particular destination for a sending node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2ac8-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2ac8-128">See Also</span></span>  
 [<span data-ttu-id="b2ac8-129">Protokol IP (Internet Protocol) verze 6</span><span class="sxs-lookup"><span data-stu-id="b2ac8-129">Internet Protocol Version 6</span></span>](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [<span data-ttu-id="b2ac8-130">Sokety</span><span class="sxs-lookup"><span data-stu-id="b2ac8-130">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
