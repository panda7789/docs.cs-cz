---
title: "Směrování IPv6"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
caps.latest.revision: "4"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 21edbfee91a759b0b48f9dd6c0c9e900cdff93f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ipv6-routing"></a><span data-ttu-id="1333f-102">Směrování IPv6</span><span class="sxs-lookup"><span data-stu-id="1333f-102">IPv6 Routing</span></span>
<span data-ttu-id="1333f-103">Flexibilní mechanismus směrování je výhodou IPv6.</span><span class="sxs-lookup"><span data-stu-id="1333f-103">A flexible routing mechanism is a benefit of IPv6.</span></span> <span data-ttu-id="1333f-104">Vzhledem ke způsobu, ve které IPv4 ID sítě byly a jsou přidělené, velké směrovacích tabulek třeba udržovat směrovače, které jsou na Internetu páteřním.</span><span class="sxs-lookup"><span data-stu-id="1333f-104">Due to the way in which IPv4 network IDs were and are allocated, large routing tables need to be maintained by the routers that are on the Internet backbones.</span></span> <span data-ttu-id="1333f-105">Tyto směrovače musí znát všechny trasy k předávání paketů, které jsou potenciálně směrované do kteréhokoli uzlu na Internetu.</span><span class="sxs-lookup"><span data-stu-id="1333f-105">These routers must know all the routes in order to forward packets that are potentially directed to any node on the Internet.</span></span> <span data-ttu-id="1333f-106">S jeho schopnost agregační adresy IPv6 umožňuje flexibilní adresování a výrazně snižuje velikost směrovacích tabulek.</span><span class="sxs-lookup"><span data-stu-id="1333f-106">With its ability to aggregate addresses, IPv6 allows flexible addressing and drastically reduces the size of routing tables.</span></span> <span data-ttu-id="1333f-107">V této nové adresování architektuře zprostředkující směrovače musí sledovat pouze místní část svoji síť k předávání zpráv správně.</span><span class="sxs-lookup"><span data-stu-id="1333f-107">In this new addressing architecture, intermediate routers must keep track only of the local portion of their network in order to forward the messages appropriately.</span></span>  
  
## <a name="neighbor-discovery"></a><span data-ttu-id="1333f-108">ND</span><span class="sxs-lookup"><span data-stu-id="1333f-108">Neighbor Discovery</span></span>  
 <span data-ttu-id="1333f-109">Některé funkce poskytované službou ND jsou:</span><span class="sxs-lookup"><span data-stu-id="1333f-109">Some of the features provided by Neighbor Discovery are:</span></span>  
  
-   <span data-ttu-id="1333f-110">Zjišťování směrovače.</span><span class="sxs-lookup"><span data-stu-id="1333f-110">Router discovery.</span></span> <span data-ttu-id="1333f-111">To umožňuje hostitelům identifikovat místního směrovače.</span><span class="sxs-lookup"><span data-stu-id="1333f-111">This allows hosts to identify local routers.</span></span>  
  
-   <span data-ttu-id="1333f-112">Překlad adres.</span><span class="sxs-lookup"><span data-stu-id="1333f-112">Address resolution.</span></span> <span data-ttu-id="1333f-113">To umožňuje uzly k překladu adresy linkové vrstvě pro odpovídající adresa dalšího směrování (náhrada za Address Resolution Protocol [ARP]).</span><span class="sxs-lookup"><span data-stu-id="1333f-113">This allows nodes to resolve a link-layer address for a corresponding next-hop address (a replacement for Address Resolution Protocol [ARP]).</span></span>  
  
-   <span data-ttu-id="1333f-114">Adres automatické konfigurace.</span><span class="sxs-lookup"><span data-stu-id="1333f-114">Address auto-configuration.</span></span> <span data-ttu-id="1333f-115">To umožňuje hostitelům pro automatickou konfiguraci místní a globální adresy.</span><span class="sxs-lookup"><span data-stu-id="1333f-115">This allows hosts to automatically configure site-local and global addresses.</span></span>  
  
 <span data-ttu-id="1333f-116">ND používá Internet Control Message Protocol pro protokol IPv6 (ICMPv6) zprávy, které zahrnují:</span><span class="sxs-lookup"><span data-stu-id="1333f-116">Neighbor Discovery uses Internet Control Message Protocol for IPv6 (ICMPv6) messages that include:</span></span>  
  
-   <span data-ttu-id="1333f-117">Inzerování směrovače.</span><span class="sxs-lookup"><span data-stu-id="1333f-117">Router advertisement.</span></span> <span data-ttu-id="1333f-118">Jsou odesílány směrovačem částečně pravidelně nebo v reakci na vyhledávací.</span><span class="sxs-lookup"><span data-stu-id="1333f-118">Sent by a router on a pseudo-periodic basis or in response to a router solicitation.</span></span> <span data-ttu-id="1333f-119">Směrovače IPv6 pomocí inzerování směrovače inzerovat jejich dostupnost, předpony a dalších parametrů.</span><span class="sxs-lookup"><span data-stu-id="1333f-119">IPv6 routers use router advertisements to advertise their availability, address prefixes, and other parameters.</span></span>  
  
-   <span data-ttu-id="1333f-120">Oslovení směrovače.</span><span class="sxs-lookup"><span data-stu-id="1333f-120">Router solicitation.</span></span> <span data-ttu-id="1333f-121">Odešle hostitele požadavku, že směrovače na tento odkaz Odeslat inzerování směrovače okamžitě.</span><span class="sxs-lookup"><span data-stu-id="1333f-121">Sent by a host to request that routers on the link send a router advertisement immediately.</span></span>  
  
-   <span data-ttu-id="1333f-122">Oslovení sousedním.</span><span class="sxs-lookup"><span data-stu-id="1333f-122">Neighbor solicitation.</span></span> <span data-ttu-id="1333f-123">Odesílány uzly pro rozpoznání adresy, detekce duplicitních adres, a ověřte, zda je sousedním stále dostupný.</span><span class="sxs-lookup"><span data-stu-id="1333f-123">Sent by nodes for address resolution, duplicate address detection, or to verify that a neighbor is still reachable.</span></span>  
  
-   <span data-ttu-id="1333f-124">Sousedním oznámení o inzerovaném programu.</span><span class="sxs-lookup"><span data-stu-id="1333f-124">Neighbor advertisement.</span></span> <span data-ttu-id="1333f-125">Odesílány uzly reagovat na sousedním oslovení nebo oznámení okolí změny v adrese linkové vrstvě.</span><span class="sxs-lookup"><span data-stu-id="1333f-125">Sent by nodes to respond to a neighbor solicitation or to notify neighbors of a change in link-layer address.</span></span>  
  
-   <span data-ttu-id="1333f-126">Přesměrování.</span><span class="sxs-lookup"><span data-stu-id="1333f-126">Redirect.</span></span> <span data-ttu-id="1333f-127">Odesílá udávajících lepší adresa dalšího směrování na určité cílové místo pro odesílání uzel.</span><span class="sxs-lookup"><span data-stu-id="1333f-127">Sent by routers to indicate a better next-hop address to a particular destination for a sending node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1333f-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="1333f-128">See Also</span></span>  
 [<span data-ttu-id="1333f-129">Protokol IP verze 6</span><span class="sxs-lookup"><span data-stu-id="1333f-129">Internet Protocol Version 6</span></span>](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [<span data-ttu-id="1333f-130">Sokety</span><span class="sxs-lookup"><span data-stu-id="1333f-130">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
