---
title: Směrování IPv6
ms.date: 03/30/2017
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
ms.openlocfilehash: 93300107710164d755d578633b7fa6651f984987
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047790"
---
# <a name="ipv6-routing"></a><span data-ttu-id="1898b-102">Směrování IPv6</span><span class="sxs-lookup"><span data-stu-id="1898b-102">IPv6 Routing</span></span>
<span data-ttu-id="1898b-103">Flexibilní mechanizmus směrování je výhodou protokolu IPv6.</span><span class="sxs-lookup"><span data-stu-id="1898b-103">A flexible routing mechanism is a benefit of IPv6.</span></span> <span data-ttu-id="1898b-104">Vzhledem k tomu, jak se přidělují identifikátory sítě IPv4 a jsou přidělené, musí být velké směrovací tabulky udržované směrovači, které se nacházejí v Internetu.</span><span class="sxs-lookup"><span data-stu-id="1898b-104">Due to the way in which IPv4 network IDs were and are allocated, large routing tables need to be maintained by the routers that are on the Internet backbones.</span></span> <span data-ttu-id="1898b-105">Aby bylo možné přesměrování paketů, které jsou potenciálně směrovány na libovolný uzel na internetu, musí tyto směrovače znát všechny trasy.</span><span class="sxs-lookup"><span data-stu-id="1898b-105">These routers must know all the routes in order to forward packets that are potentially directed to any node on the Internet.</span></span> <span data-ttu-id="1898b-106">Díky schopnosti agregovat adresy podporuje IPv6 flexibilní adresování a významně snižuje velikost směrovacích tabulek.</span><span class="sxs-lookup"><span data-stu-id="1898b-106">With its ability to aggregate addresses, IPv6 allows flexible addressing and drastically reduces the size of routing tables.</span></span> <span data-ttu-id="1898b-107">V této nové architektuře adres musí zprostředkující směrovače sledovat pouze místní část své sítě, aby bylo možné zprávy přeposílat správně.</span><span class="sxs-lookup"><span data-stu-id="1898b-107">In this new addressing architecture, intermediate routers must keep track only of the local portion of their network in order to forward the messages appropriately.</span></span>  
  
## <a name="neighbor-discovery"></a><span data-ttu-id="1898b-108">Sousední zjišťování</span><span class="sxs-lookup"><span data-stu-id="1898b-108">Neighbor Discovery</span></span>  
 <span data-ttu-id="1898b-109">Mezi funkce poskytované sousedním zjišťováním patří:</span><span class="sxs-lookup"><span data-stu-id="1898b-109">Some of the features provided by Neighbor Discovery are:</span></span>  
  
- <span data-ttu-id="1898b-110">Zjišťování směrovače.</span><span class="sxs-lookup"><span data-stu-id="1898b-110">Router discovery.</span></span> <span data-ttu-id="1898b-111">To umožňuje hostitelům identifikovat místní směrovače.</span><span class="sxs-lookup"><span data-stu-id="1898b-111">This allows hosts to identify local routers.</span></span>  
  
- <span data-ttu-id="1898b-112">Překlad adres.</span><span class="sxs-lookup"><span data-stu-id="1898b-112">Address resolution.</span></span> <span data-ttu-id="1898b-113">To umožňuje uzlům přeložit adresu linkové vrstvy pro odpovídající adresu dalšího směrování (náhradu za protokol ARP (Address Resolution Protocol)).</span><span class="sxs-lookup"><span data-stu-id="1898b-113">This allows nodes to resolve a link-layer address for a corresponding next-hop address (a replacement for Address Resolution Protocol [ARP]).</span></span>  
  
- <span data-ttu-id="1898b-114">Automatická konfigurace adres.</span><span class="sxs-lookup"><span data-stu-id="1898b-114">Address auto-configuration.</span></span> <span data-ttu-id="1898b-115">To umožňuje hostitelům automaticky konfigurovat místní a globální adresy lokality.</span><span class="sxs-lookup"><span data-stu-id="1898b-115">This allows hosts to automatically configure site-local and global addresses.</span></span>  
  
 <span data-ttu-id="1898b-116">Sousední zjišťování používá protokol zpráv protokolu IPv6 (ICMPv6), který zahrnuje:</span><span class="sxs-lookup"><span data-stu-id="1898b-116">Neighbor Discovery uses Internet Control Message Protocol for IPv6 (ICMPv6) messages that include:</span></span>  
  
- <span data-ttu-id="1898b-117">Inzerování směrovače.</span><span class="sxs-lookup"><span data-stu-id="1898b-117">Router advertisement.</span></span> <span data-ttu-id="1898b-118">Odesílá se směrovačem na základě pseudo-periody nebo v reakci na oslovování směrovače.</span><span class="sxs-lookup"><span data-stu-id="1898b-118">Sent by a router on a pseudo-periodic basis or in response to a router solicitation.</span></span> <span data-ttu-id="1898b-119">Směrovače IPv6 používají inzerování směrovače k inzerování jejich dostupnosti, předpon adres a dalších parametrů.</span><span class="sxs-lookup"><span data-stu-id="1898b-119">IPv6 routers use router advertisements to advertise their availability, address prefixes, and other parameters.</span></span>  
  
- <span data-ttu-id="1898b-120">Oslovování směrovače.</span><span class="sxs-lookup"><span data-stu-id="1898b-120">Router solicitation.</span></span> <span data-ttu-id="1898b-121">Odesílá se hostitelem, aby požádal o to, aby směrovače v odkazu odeslaly oznámení směrovače okamžitě.</span><span class="sxs-lookup"><span data-stu-id="1898b-121">Sent by a host to request that routers on the link send a router advertisement immediately.</span></span>  
  
- <span data-ttu-id="1898b-122">Oslovování sousedů.</span><span class="sxs-lookup"><span data-stu-id="1898b-122">Neighbor solicitation.</span></span> <span data-ttu-id="1898b-123">Odesílá se uzly kvůli překladu adres, duplicitě zjišťování adres nebo k ověření, že je sousední uzel stále dosažitelný.</span><span class="sxs-lookup"><span data-stu-id="1898b-123">Sent by nodes for address resolution, duplicate address detection, or to verify that a neighbor is still reachable.</span></span>  
  
- <span data-ttu-id="1898b-124">Inzerování sousedů.</span><span class="sxs-lookup"><span data-stu-id="1898b-124">Neighbor advertisement.</span></span> <span data-ttu-id="1898b-125">Odesílá se uzly, aby reagovaly na oslovování sousedů nebo upozornily sousedním uzlům na změnu v adrese linkové vrstvy.</span><span class="sxs-lookup"><span data-stu-id="1898b-125">Sent by nodes to respond to a neighbor solicitation or to notify neighbors of a change in link-layer address.</span></span>  
  
- <span data-ttu-id="1898b-126">Požadavek.</span><span class="sxs-lookup"><span data-stu-id="1898b-126">Redirect.</span></span> <span data-ttu-id="1898b-127">Odesílá se směrovači k označení lepší adresy dalšího směrování na konkrétní cíl pro odesílající uzel.</span><span class="sxs-lookup"><span data-stu-id="1898b-127">Sent by routers to indicate a better next-hop address to a particular destination for a sending node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1898b-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1898b-128">See also</span></span>

- [<span data-ttu-id="1898b-129">Protokol IP (Internet Protocol) verze 6</span><span class="sxs-lookup"><span data-stu-id="1898b-129">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)
- [<span data-ttu-id="1898b-130">Sokety</span><span class="sxs-lookup"><span data-stu-id="1898b-130">Sockets</span></span>](sockets.md)
