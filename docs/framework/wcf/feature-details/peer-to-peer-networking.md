---
title: Síť rovnocenných počítačů
ms.date: 03/30/2017
ms.assetid: ad6cb67b-fd1c-4ca1-a767-b410da2e16ca
ms.openlocfilehash: 16416ec467caa10216930ae3c961869cbfcd59d8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43456982"
---
# <a name="peer-to-peer-networking"></a><span data-ttu-id="c4f21-102">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="c4f21-102">Peer-to-Peer Networking</span></span>
<span data-ttu-id="c4f21-103">Rovnocenný kanál je éře, peer-to-peer (P2P) komunikaci technologie Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c4f21-103">Peer Channel is a multiparty, peer-to-peer (P2P) communication technology in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="c4f21-104">Poskytuje zabezpečené a škálovatelné založenou na zprávách P2P komunikační kanál pro vývojáře aplikací.</span><span class="sxs-lookup"><span data-stu-id="c4f21-104">It provides a secure and scalable message-based P2P communication channel for application developers.</span></span> <span data-ttu-id="c4f21-105">Jedním z běžných příkladů éře aplikace, které mohou těžit z rovnocenného kanálu je spolupráci aplikací, jako je například konverzace, kde je skupina lidí konverzace mezi sebou způsobem peer-to-peer bez serverů.</span><span class="sxs-lookup"><span data-stu-id="c4f21-105">One common example of a multiparty application that can benefit from Peer Channel is a collaborative application, such as chat, where a group of people chat with one another in a peer-to-peer manner without servers.</span></span> <span data-ttu-id="c4f21-106">Rovnocenný kanál umožňuje spolupráci P2P, distribuci obsahu, Vyrovnávání zatížení a distribuované zpracování pro zákaznické a podnikové scénáře.</span><span class="sxs-lookup"><span data-stu-id="c4f21-106">Peer Channel enables P2P collaboration, content distribution, load balancing, and distributed processing for both consumer and enterprise scenarios.</span></span>  
  
 <span data-ttu-id="c4f21-107">Rovnocenný kanál je povolené ve výchozím nastavení na [!INCLUDE[wv](../../../../includes/wv-md.md)], protože všechny služby WCF.</span><span class="sxs-lookup"><span data-stu-id="c4f21-107">Peer Channel is enabled by default on [!INCLUDE[wv](../../../../includes/wv-md.md)], as is all of WCF.</span></span> <span data-ttu-id="c4f21-108">Pro přístup k protokolu Peer Channel třídy, do projektu přidají odkazy System.ServiceModel.dll.</span><span class="sxs-lookup"><span data-stu-id="c4f21-108">To access Peer Channel classes, add references to System.ServiceModel.dll to your project.</span></span>  
  
 <span data-ttu-id="c4f21-109">Následující části obsahují informace o sítích peer-to-peer a používání tříd protokolu Peer Channel k vytváření aplikací pro sítě peer povoleno.</span><span class="sxs-lookup"><span data-stu-id="c4f21-109">The following sections contain information about peer-to-peer networking and the use of Peer Channel classes to create peer-enabled network applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c4f21-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c4f21-110">In This Section</span></span>  
 <span data-ttu-id="c4f21-111">[Vytvoření partnerského vztahu scénáře kanálu](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md): Popisuje podporována rozhraní API kanálu Peer vývojové scénáře, jako je zasílání zpráv, spolupráci, publikování nebo odběru distribuované zpracování a hraní her.</span><span class="sxs-lookup"><span data-stu-id="c4f21-111">[Peer Channel Scenarios](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md):  Describes development scenarios supported by the Peer Channel APIs, such as publication/subscription messaging, collaboration, distributed processing, and gaming.</span></span>  
  
 <span data-ttu-id="c4f21-112">[Vytvoření partnerského vztahu kanál koncepty](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md): Popisuje sdílené mřížky, partnerské uzly, zabezpečení rovnocenného kanálu a překladače partnerských uzlů.</span><span class="sxs-lookup"><span data-stu-id="c4f21-112">[Peer Channel Concepts](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md):  Describes Peer Meshes, Peer Nodes, Peer Channel security, and Peer Resolvers.</span></span>  
  
 <span data-ttu-id="c4f21-113">[Sestavení aplikace Peer Channel](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md): obsahuje pokyny k vývoji aplikací protokolu Peer Channel.</span><span class="sxs-lookup"><span data-stu-id="c4f21-113">[Building a Peer Channel Application](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md):  Provides guidance on developing Peer Channel applications.</span></span>  
  
## <a name="peer-channel-code-examples"></a><span data-ttu-id="c4f21-114">Příklady kódu pro protokolu peer Channel</span><span class="sxs-lookup"><span data-stu-id="c4f21-114">Peer Channel Code Examples</span></span>  
 [<span data-ttu-id="c4f21-115">Rozpoznávání partnera vlastního protokolu peer Channel</span><span class="sxs-lookup"><span data-stu-id="c4f21-115">Peer Channel Custom Peer Resolver</span></span>](https://msdn.microsoft.com/library/5b75a2bb-7ff1-4a14-abe7-3debf0537d23)  
  
## <a name="peer-channel-team-blog"></a><span data-ttu-id="c4f21-116">Blog týmu protokolu peer Channel</span><span class="sxs-lookup"><span data-stu-id="c4f21-116">Peer Channel Team blog</span></span>  
 [<span data-ttu-id="c4f21-117">Blog týmu protokolu peer Channel</span><span class="sxs-lookup"><span data-stu-id="c4f21-117">Peer Channel Team Blog</span></span>](https://go.microsoft.com/fwlink/?LinkID=114530)
