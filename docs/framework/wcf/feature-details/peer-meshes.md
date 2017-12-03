---
title: "Skupiny partnerských uzlů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d93e312e-ac04-40f8-baea-5da1cacb546e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d747b2916f544294bb69f01aadc1321370878689
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="peer-meshes"></a><span data-ttu-id="3dc79-102">Skupiny partnerských uzlů</span><span class="sxs-lookup"><span data-stu-id="3dc79-102">Peer Meshes</span></span>
<span data-ttu-id="3dc79-103">A *OK sítě* je pojmenovaná kolekce partnerské uzly, který dokáže komunikovat mezi sebou a které jsou určeny OK jedinečné ID (vzájemně propojena graf)</span><span class="sxs-lookup"><span data-stu-id="3dc79-103">A *mesh* is a named collection (an interconnected graph) of peer nodes that can communicate among themselves and that are identified by a unique mesh ID.</span></span> <span data-ttu-id="3dc79-104">Každý uzel je připojen k více dalších uzlů.</span><span class="sxs-lookup"><span data-stu-id="3dc79-104">Each node is connected to multiple other nodes.</span></span> <span data-ttu-id="3dc79-105">V dobře propojené mřížku je mezi dvěma uzly, s relativně malý počet směrování mezi uzly ve nejvzdálenější okrajů oka, cestu a OK zůstanou připojené i v případě, že některé uzly nebo připojení vyřadit. Aktivní uzly v mřížce publikovaly své informace o koncový bod s odpovídajícím ID mřížky, aby ostatní partnerské uzly najít.</span><span class="sxs-lookup"><span data-stu-id="3dc79-105">In a well-connected mesh, there is a path between any two nodes, with relatively few hops between the nodes on the furthest edges of the mesh, and the mesh will remain connected even if some nodes or connections drop out. Active nodes in the mesh publish their endpoint information with a corresponding mesh ID so that other peers can find them.</span></span>  
  
## <a name="characteristics-of-a-mesh-created-using-peer-channel"></a><span data-ttu-id="3dc79-106">Vlastnosti vytvořený rovnocenného kanálu oka sítě</span><span class="sxs-lookup"><span data-stu-id="3dc79-106">Characteristics of a Mesh Created Using Peer Channel</span></span>  
  
#### <a name="uniquely-identified"></a><span data-ttu-id="3dc79-107">Jednoznačně identifikuje</span><span class="sxs-lookup"><span data-stu-id="3dc79-107">Uniquely Identified</span></span>  
  
-   <span data-ttu-id="3dc79-108">Jedinečné ID identifikuje každého OK.</span><span class="sxs-lookup"><span data-stu-id="3dc79-108">A unique ID identifies each mesh.</span></span> <span data-ttu-id="3dc79-109">Název OK (nebo OK ID) je ve stejném formátu jako název hostitele systému DNS (Domain Name).</span><span class="sxs-lookup"><span data-stu-id="3dc79-109">The name of the mesh (or mesh ID) is in the same format as a Domain Name System (DNS) host name.</span></span> <span data-ttu-id="3dc79-110">Toto ID OK jako takový musí být jedinečný pro určený klientský aplikace v rámci oboru překladač používá.</span><span class="sxs-lookup"><span data-stu-id="3dc79-110">As such, this mesh ID must be unique for the intended client of the application within the scope of the resolver being used.</span></span> <span data-ttu-id="3dc79-111">Běžný název, například "MyFamilysPeers" nebo "KevinsPokerTable", může snadno dojít ke konfliktu s další uživatelská jména a může vracet neúmyslným sdílené informace koncového bodu, což může způsobit problémy ochrany osobních údajů nebo zvýšení latence připojení.</span><span class="sxs-lookup"><span data-stu-id="3dc79-111">A common name such as "MyFamilysPeers" or "KevinsPokerTable," may easily collide with other user names and may return unintended peer endpoint information, which could result in privacy issues or increase connection latency.</span></span> <span data-ttu-id="3dc79-112">Jedním ze způsobů, abyste se těmto problémům může být k přidání jedinečné ID jako operátory Přezdívka pro síť (například "KevinsPokerTable90210").</span><span class="sxs-lookup"><span data-stu-id="3dc79-112">One way to avoid these issues may be to add a unique ID as a postfix to the nickname for the mesh (for example, "KevinsPokerTable90210").</span></span>  
  
#### <a name="message-flooding"></a><span data-ttu-id="3dc79-113">Zpráva zahlcení</span><span class="sxs-lookup"><span data-stu-id="3dc79-113">Message Flooding</span></span>  
  
-   <span data-ttu-id="3dc79-114">OK umožňuje zprávy, které mají být předány z jednoho nebo více odesílatelů všechny ostatní partnerské uzly stejné v mřížce.</span><span class="sxs-lookup"><span data-stu-id="3dc79-114">The mesh allows messages to be propagated from one or more senders to all other peer nodes in the same mesh.</span></span> <span data-ttu-id="3dc79-115">Zprávy zaplněn partnerské uzly použít záhlaví zadaná v oboru názvů v `http://schemas.microsoft.com/net/2006/05/peer`.</span><span class="sxs-lookup"><span data-stu-id="3dc79-115">Messages flooded by peer nodes use headers specified in the namespace at `http://schemas.microsoft.com/net/2006/05/peer`.</span></span>  
  
#### <a name="optimized-connections"></a><span data-ttu-id="3dc79-116">Optimalizované připojení</span><span class="sxs-lookup"><span data-stu-id="3dc79-116">Optimized Connections</span></span>  
  
-   <span data-ttu-id="3dc79-117">Pokud uzly připojení nebo odpojení, zajistíte, že všechny uzly mají dobré připojení s menší riziko vytváření oddílů (skupiny uzly navzájem izolované) automaticky upraví rovnocenného kanálu oka.</span><span class="sxs-lookup"><span data-stu-id="3dc79-117">A Peer Channel mesh automatically adjusts when nodes join and leave, ensuring that all nodes have good connectivity with little chance of creating partitions (groups of nodes isolated from each other).</span></span> <span data-ttu-id="3dc79-118">Připojení v mřížce jsou také dynamicky optimalizované podle aktuální vzory přenosů dat tak, aby latence zprávu od odesílatele k příjemce je co nejmenší.</span><span class="sxs-lookup"><span data-stu-id="3dc79-118">Connections in the mesh are also dynamically optimized based on current traffic patterns so that message latency from sender to receiver is as small as possible.</span></span>  
  
#### <a name="popular-network-features-that-peer-channel-does-not-provide"></a><span data-ttu-id="3dc79-119">Oblíbené síťové funkce, které neposkytuje rovnocenného kanálu</span><span class="sxs-lookup"><span data-stu-id="3dc79-119">Popular Network Features That Peer Channel Does Not Provide</span></span>  
 <span data-ttu-id="3dc79-120">Je důležité si uvědomit oblíbených síťové funkce, které neposkytuje rovnocenného kanálu.</span><span class="sxs-lookup"><span data-stu-id="3dc79-120">It is important to be aware of popular network features that Peer Channel does not provide.</span></span> <span data-ttu-id="3dc79-121">Tyto funkce, které může všechny být postavená na rovnocenného kanálu, patří:</span><span class="sxs-lookup"><span data-stu-id="3dc79-121">These features, which may all be built on top of Peer Channel, include the following:</span></span>  
  
-   <span data-ttu-id="3dc79-122">**Řazení zpráv:** zprávy pocházející z jednoho zdroje nemusí dorazí na všech jiných stran ve stejném pořadí, nebo v pořadí, odeslaný zdroji.</span><span class="sxs-lookup"><span data-stu-id="3dc79-122">**Message ordering:** Messages originating from a single source may not arrive at all other parties in the same order or in the order that the source sent.</span></span> <span data-ttu-id="3dc79-123">Aplikace, které vyžadují zprávy být dodávány v určitém pořadí musí vytvořit ji do svých aplikací (například zahrnutím monotónně se zvyšující ID s všechny zprávy).</span><span class="sxs-lookup"><span data-stu-id="3dc79-123">Applications that require messages be delivered in a certain order must build it into their applications (for example, by including a monotonically increasing ID with all messages).</span></span>  
  
-   <span data-ttu-id="3dc79-124">**Spolehlivé zasílání zpráv:** rovnocenného kanálu nezahrnuje mechanismus zajistit příjem zpráv ve všech partnerských uzlů.</span><span class="sxs-lookup"><span data-stu-id="3dc79-124">**Reliable messaging:** Peer Channel does not include a mechanism to ensure message reception by all peers.</span></span> <span data-ttu-id="3dc79-125">Pokud chcete zajistit doručení zpráv, musíte napsat spolehlivost vrstvu nad rovnocenného kanálu.</span><span class="sxs-lookup"><span data-stu-id="3dc79-125">To guarantee message delivery, you must write a reliability layer on top of Peer Channel.</span></span>
