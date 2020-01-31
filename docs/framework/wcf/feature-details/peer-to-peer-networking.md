---
title: Síť rovnocenných počítačů
ms.date: 03/30/2017
ms.assetid: ad6cb67b-fd1c-4ca1-a767-b410da2e16ca
ms.openlocfilehash: 2905a429e907f7e97c482c22229a6bc928c52243
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744671"
---
# <a name="peer-to-peer-networking"></a><span data-ttu-id="6baac-102">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="6baac-102">Peer-to-Peer Networking</span></span>
<span data-ttu-id="6baac-103">Rovnocenný kanál je v Windows Communication Foundation (WCF) s více částmi komunikační technologie peer-to-peer (P2P).</span><span class="sxs-lookup"><span data-stu-id="6baac-103">Peer Channel is a multiparty, peer-to-peer (P2P) communication technology in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="6baac-104">Pro vývojáře aplikací poskytuje zabezpečený a škálovatelný komunikační kanál P2P založený na zprávách.</span><span class="sxs-lookup"><span data-stu-id="6baac-104">It provides a secure and scalable message-based P2P communication channel for application developers.</span></span> <span data-ttu-id="6baac-105">Jeden běžný příklad aplikace s více částmi, která může využívat rovnocenným kanálem, je aplikace pro spolupráci, jako je například chat, kde skupina osob v rámci peer-to-peer bez serverů navzájem spolupracuje.</span><span class="sxs-lookup"><span data-stu-id="6baac-105">One common example of a multiparty application that can benefit from Peer Channel is a collaborative application, such as chat, where a group of people chat with one another in a peer-to-peer manner without servers.</span></span> <span data-ttu-id="6baac-106">Partnerský kanál umožňuje spolupráci v P2P, distribuci obsahu, Vyrovnávání zatížení a distribuované zpracování pro scénáře uživatelů i podnikových scénářů.</span><span class="sxs-lookup"><span data-stu-id="6baac-106">Peer Channel enables P2P collaboration, content distribution, load balancing, and distributed processing for both consumer and enterprise scenarios.</span></span>  
  
 <span data-ttu-id="6baac-107">Partnerský kanál je ve výchozím nastavení povolený v systému Windows Vista, stejně jako všechny služby WCF.</span><span class="sxs-lookup"><span data-stu-id="6baac-107">Peer Channel is enabled by default on Windows Vista, as is all of WCF.</span></span> <span data-ttu-id="6baac-108">Chcete-li získat přístup ke třídám rovnocenného kanálu, přidejte do projektu odkazy na System. ServiceModel. dll.</span><span class="sxs-lookup"><span data-stu-id="6baac-108">To access Peer Channel classes, add references to System.ServiceModel.dll to your project.</span></span>  
  
 <span data-ttu-id="6baac-109">Následující části obsahují informace o sítích peer-to-peer a použití tříd rovnocenného kanálu k vytváření síťových aplikací s povoleným partnerským vztahem.</span><span class="sxs-lookup"><span data-stu-id="6baac-109">The following sections contain information about peer-to-peer networking and the use of Peer Channel classes to create peer-enabled network applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6baac-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6baac-110">In This Section</span></span>  
 <span data-ttu-id="6baac-111">[Scénáře rovnocenného kanálu](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md): popisuje vývojové scénáře podporované rozhraními API pro rovnocenné kanály, jako je zasílání zpráv o publikování a předplatném, spolupráce, distribuované zpracování a hraní her.</span><span class="sxs-lookup"><span data-stu-id="6baac-111">[Peer Channel Scenarios](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md):  Describes development scenarios supported by the Peer Channel APIs, such as publication/subscription messaging, collaboration, distributed processing, and gaming.</span></span>  
  
 <span data-ttu-id="6baac-112">[Koncepty rovnocenného kanálu](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md): popisuje partnerské sítě, rovnocenné uzly, zabezpečení rovnocenného kanálu a překladače rovnocenných zařízení.</span><span class="sxs-lookup"><span data-stu-id="6baac-112">[Peer Channel Concepts](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md):  Describes Peer Meshes, Peer Nodes, Peer Channel security, and Peer Resolvers.</span></span>  
  
 <span data-ttu-id="6baac-113">[Sestavování aplikace rovnocenného kanálu](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md): poskytuje pokyny k vývoji aplikací rovnocenného kanálu.</span><span class="sxs-lookup"><span data-stu-id="6baac-113">[Building a Peer Channel Application](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md):  Provides guidance on developing Peer Channel applications.</span></span>  
  
## <a name="peer-channel-code-examples"></a><span data-ttu-id="6baac-114">Příklady kódu rovnocenného kanálu</span><span class="sxs-lookup"><span data-stu-id="6baac-114">Peer Channel Code Examples</span></span>  
 <span data-ttu-id="6baac-115">[Vlastní překladač rovnocenných kanálů](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751466(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="6baac-115">[Peer Channel Custom Peer Resolver](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751466(v=vs.90))</span></span>  
  
## <a name="peer-channel-team-blog"></a><span data-ttu-id="6baac-116">Blog týmu partnerského kanálu</span><span class="sxs-lookup"><span data-stu-id="6baac-116">Peer Channel Team blog</span></span>  
 [<span data-ttu-id="6baac-117">Blog týmu partnerského kanálu</span><span class="sxs-lookup"><span data-stu-id="6baac-117">Peer Channel Team Blog</span></span>](https://docs.microsoft.com/archive/blogs/peerchan/)
