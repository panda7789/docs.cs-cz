---
title: Směrování IPv6
ms.date: 03/30/2017
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
ms.openlocfilehash: 93300107710164d755d578633b7fa6651f984987
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047790"
---
# <a name="ipv6-routing"></a><span data-ttu-id="61bef-102">Směrování IPv6</span><span class="sxs-lookup"><span data-stu-id="61bef-102">IPv6 Routing</span></span>
<span data-ttu-id="61bef-103">Flexibilní mechanismus směrování je výhodou protokolu IPv6.</span><span class="sxs-lookup"><span data-stu-id="61bef-103">A flexible routing mechanism is a benefit of IPv6.</span></span> <span data-ttu-id="61bef-104">Vzhledem ke způsobu, jakým byla a přidělována ID sítě IPv4, musí být velké směrovací tabulky udržovány směrovači, které jsou v páteřních sítích.</span><span class="sxs-lookup"><span data-stu-id="61bef-104">Due to the way in which IPv4 network IDs were and are allocated, large routing tables need to be maintained by the routers that are on the Internet backbones.</span></span> <span data-ttu-id="61bef-105">Tyto směrovače musí znát všechny trasy, aby bylo možné předávat pakety, které jsou potenciálně směrovány do libovolného uzlu v Síti Internet.</span><span class="sxs-lookup"><span data-stu-id="61bef-105">These routers must know all the routes in order to forward packets that are potentially directed to any node on the Internet.</span></span> <span data-ttu-id="61bef-106">Díky schopnosti agregovat adresy umožňuje protokol IPv6 flexibilní adresování a výrazně zmenšuje velikost směrovacích tabulek.</span><span class="sxs-lookup"><span data-stu-id="61bef-106">With its ability to aggregate addresses, IPv6 allows flexible addressing and drastically reduces the size of routing tables.</span></span> <span data-ttu-id="61bef-107">V této nové architektuře adresování musí zprostředkující směrovače sledovat pouze místní část své sítě, aby mohly zprávy odpovídajícím způsobem předat dál.</span><span class="sxs-lookup"><span data-stu-id="61bef-107">In this new addressing architecture, intermediate routers must keep track only of the local portion of their network in order to forward the messages appropriately.</span></span>  
  
## <a name="neighbor-discovery"></a><span data-ttu-id="61bef-108">Zjišťování souseda</span><span class="sxs-lookup"><span data-stu-id="61bef-108">Neighbor Discovery</span></span>  
 <span data-ttu-id="61bef-109">Některé z funkcí poskytovaných Neighbor Discovery jsou:</span><span class="sxs-lookup"><span data-stu-id="61bef-109">Some of the features provided by Neighbor Discovery are:</span></span>  
  
- <span data-ttu-id="61bef-110">Zjišťování směrovače.</span><span class="sxs-lookup"><span data-stu-id="61bef-110">Router discovery.</span></span> <span data-ttu-id="61bef-111">To umožňuje hostitelům identifikovat místní směrovače.</span><span class="sxs-lookup"><span data-stu-id="61bef-111">This allows hosts to identify local routers.</span></span>  
  
- <span data-ttu-id="61bef-112">Rozlišení adresy.</span><span class="sxs-lookup"><span data-stu-id="61bef-112">Address resolution.</span></span> <span data-ttu-id="61bef-113">To umožňuje uzlům vyřešit adresu linkové vrstvy pro odpovídající adresu dalšího směrování (náhrada za protokol Http Resolution Protocol [ARP]).</span><span class="sxs-lookup"><span data-stu-id="61bef-113">This allows nodes to resolve a link-layer address for a corresponding next-hop address (a replacement for Address Resolution Protocol [ARP]).</span></span>  
  
- <span data-ttu-id="61bef-114">Automatická konfigurace adresy.</span><span class="sxs-lookup"><span data-stu-id="61bef-114">Address auto-configuration.</span></span> <span data-ttu-id="61bef-115">To umožňuje hostitelům automaticky konfigurovat místní a globální adresy lokality.</span><span class="sxs-lookup"><span data-stu-id="61bef-115">This allows hosts to automatically configure site-local and global addresses.</span></span>  
  
 <span data-ttu-id="61bef-116">Zjišťování souseda používá pro zprávy IPv6 (ICMPv6) protokol IPV6 (ICMPv6), které zahrnují:</span><span class="sxs-lookup"><span data-stu-id="61bef-116">Neighbor Discovery uses Internet Control Message Protocol for IPv6 (ICMPv6) messages that include:</span></span>  
  
- <span data-ttu-id="61bef-117">Router reklama.</span><span class="sxs-lookup"><span data-stu-id="61bef-117">Router advertisement.</span></span> <span data-ttu-id="61bef-118">Odesláno směrovačem pseudopravidelně nebo v reakci na oslovení směrovače.</span><span class="sxs-lookup"><span data-stu-id="61bef-118">Sent by a router on a pseudo-periodic basis or in response to a router solicitation.</span></span> <span data-ttu-id="61bef-119">Směrovače IPv6 používají inzerování směrovačů k propagaci své dostupnosti, předpon adres a dalších parametrů.</span><span class="sxs-lookup"><span data-stu-id="61bef-119">IPv6 routers use router advertisements to advertise their availability, address prefixes, and other parameters.</span></span>  
  
- <span data-ttu-id="61bef-120">Oslovení směrovače.</span><span class="sxs-lookup"><span data-stu-id="61bef-120">Router solicitation.</span></span> <span data-ttu-id="61bef-121">Odesláno hostitelem s požadavkem, aby směrovače na propojení okamžitě odeslali reklamu směrovače.</span><span class="sxs-lookup"><span data-stu-id="61bef-121">Sent by a host to request that routers on the link send a router advertisement immediately.</span></span>  
  
- <span data-ttu-id="61bef-122">Sousedské obtěžování.</span><span class="sxs-lookup"><span data-stu-id="61bef-122">Neighbor solicitation.</span></span> <span data-ttu-id="61bef-123">Odesláno uzly pro překlad adres, vyhledávání duplicitních adres nebo ověření, zda je soused stále dostupný.</span><span class="sxs-lookup"><span data-stu-id="61bef-123">Sent by nodes for address resolution, duplicate address detection, or to verify that a neighbor is still reachable.</span></span>  
  
- <span data-ttu-id="61bef-124">Sousedská reklama.</span><span class="sxs-lookup"><span data-stu-id="61bef-124">Neighbor advertisement.</span></span> <span data-ttu-id="61bef-125">Odesláno uzly reagovat na souseda oslovení nebo upozornit sousedy na změnu adresy linkové vrstvy.</span><span class="sxs-lookup"><span data-stu-id="61bef-125">Sent by nodes to respond to a neighbor solicitation or to notify neighbors of a change in link-layer address.</span></span>  
  
- <span data-ttu-id="61bef-126">Přesměrování.</span><span class="sxs-lookup"><span data-stu-id="61bef-126">Redirect.</span></span> <span data-ttu-id="61bef-127">Odeslané směrovači k označení lepší adresy dalšího směrování do určitého cíle pro odesílající uzel.</span><span class="sxs-lookup"><span data-stu-id="61bef-127">Sent by routers to indicate a better next-hop address to a particular destination for a sending node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61bef-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="61bef-128">See also</span></span>

- [<span data-ttu-id="61bef-129">Protokol IP (Internet Protocol) verze 6</span><span class="sxs-lookup"><span data-stu-id="61bef-129">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)
- [<span data-ttu-id="61bef-130">Sokety</span><span class="sxs-lookup"><span data-stu-id="61bef-130">Sockets</span></span>](sockets.md)
