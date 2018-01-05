---
title: Cloudy PNRP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a82e2bf1-62ab-4c2d-83f3-3217a6aead2e
caps.latest.revision: "4"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f142c7aaa71ab2dbee1d2955f2c235a65e6c8bfa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="pnrp-clouds"></a><span data-ttu-id="f88e6-102">Cloudy PNRP</span><span class="sxs-lookup"><span data-stu-id="f88e6-102">PNRP Clouds</span></span>
<span data-ttu-id="f88e6-103">PNRP "cloud" představuje sadu uzlů, které lze vzájemně komunikovat přes síť.</span><span class="sxs-lookup"><span data-stu-id="f88e6-103">A PNRP "cloud" represents a set of nodes that can communicate with each other through the network.</span></span> <span data-ttu-id="f88e6-104">Termín "cloud" je totožná s "peer-to-peer graf" a "sdílené OK".</span><span class="sxs-lookup"><span data-stu-id="f88e6-104">The term "cloud" is synonymous with "peer mesh" and "peer-to-peer graph".</span></span>  
  
 <span data-ttu-id="f88e6-105">Komunikace mezi uzly by nikdy křížová z jednoho cloudu do jiného.</span><span class="sxs-lookup"><span data-stu-id="f88e6-105">Communication between nodes should never cross from one cloud to another.</span></span> <span data-ttu-id="f88e6-106">A <xref:System.Net.PeerToPeer.Cloud> instance je jedinečně identifikovaný jeho název, který je malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="f88e6-106">A <xref:System.Net.PeerToPeer.Cloud> instance is uniquely identified by its name, which is case-sensitive.</span></span> <span data-ttu-id="f88e6-107">Jedinou druhou stranu nebo uzel může být připojen k více než jeden cloud.</span><span class="sxs-lookup"><span data-stu-id="f88e6-107">A single peer or node may be connected to more than one cloud.</span></span>  
  
 <span data-ttu-id="f88e6-108">Cloudy jsou velmi úzce svázané s síťových rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f88e6-108">Clouds are tied very closely to network interfaces.</span></span>  <span data-ttu-id="f88e6-109">Na počítači více adresami se dvěma síťovými kartami připojené k různým podsítím bude vrácen tři cloudů: jeden pro každou z místní adresy odkaz na rozhraní a jeden globální obor cloudu.</span><span class="sxs-lookup"><span data-stu-id="f88e6-109">On a multi-homed machine with two network cards attached to different subnets, three clouds will be returned: one for each of the link local addresses per interface, and a single global scope cloud.</span></span>  
  
 <span data-ttu-id="f88e6-110">PNRP používá tři cloudu "obory", ve kterých je obor seskupení počítačů, které se nepodařilo najít vzájemně:</span><span class="sxs-lookup"><span data-stu-id="f88e6-110">PNRP uses three cloud "scopes", in which a scope is a grouping of computers that are able to find each other:</span></span>  
  
-   <span data-ttu-id="f88e6-111">Globální cloudu odpovídá globální rozsah IPv6 adres a globální adresy a představuje všechny počítače v celé Internet s protokolem IPv6.</span><span class="sxs-lookup"><span data-stu-id="f88e6-111">The global cloud corresponds to the global IPv6 address scope and global addresses and represents all the computers on the entire IPv6 Internet.</span></span> <span data-ttu-id="f88e6-112">Není k dispozici pouze jeden globální cloud.</span><span class="sxs-lookup"><span data-stu-id="f88e6-112">There is only a single global cloud.</span></span>  
  
-   <span data-ttu-id="f88e6-113">Místní cloudu odpovídá místní rozsah adres protokolu IPv6 a místní adresy.</span><span class="sxs-lookup"><span data-stu-id="f88e6-113">The link-local cloud corresponds to the link-local IPv6 address scope and link-local addresses.</span></span> <span data-ttu-id="f88e6-114">Místní cloudu je pro konkrétní připojení, což je většinou stejný jako místně připojené podsítě.</span><span class="sxs-lookup"><span data-stu-id="f88e6-114">A link-local cloud is for a specific link, which is typically the same as the locally attached subnet.</span></span> <span data-ttu-id="f88e6-115">Může existovat více cloudů specifická pro připojení.</span><span class="sxs-lookup"><span data-stu-id="f88e6-115">There can be multiple link-local clouds.</span></span>  
  
 <span data-ttu-id="f88e6-116">Třetí cloudu, jednotlivých lokalit cloudu, odpovídá rozsah adres IPv6 lokality a místní adresy.</span><span class="sxs-lookup"><span data-stu-id="f88e6-116">A third cloud, the site-specific cloud, corresponds to the site IPv6 address scope and site-local addresses.</span></span> <span data-ttu-id="f88e6-117">Tento cloud se už nepoužívá, i když se pořád podporuje v PNRP.</span><span class="sxs-lookup"><span data-stu-id="f88e6-117">This cloud has been deprecated, although it is still supported in PNRP.</span></span>  
  
## <a name="clouds"></a><span data-ttu-id="f88e6-118">Cloudy</span><span class="sxs-lookup"><span data-stu-id="f88e6-118">Clouds</span></span>  
 <span data-ttu-id="f88e6-119">PNRP cloudy jsou reprezentované pomocí instance <xref:System.Net.PeerToPeer.Cloud> třídy.</span><span class="sxs-lookup"><span data-stu-id="f88e6-119">PNRP clouds are represented by instances of the <xref:System.Net.PeerToPeer.Cloud> class.</span></span> <span data-ttu-id="f88e6-120">Skupiny cloudů používat sdílené jsou reprezentované pomocí instance Výčtový typ <xref:System.Net.PeerToPeer.CloudCollection> třídy.</span><span class="sxs-lookup"><span data-stu-id="f88e6-120">Groups of clouds used a peer are represented by instances of the enumerable <xref:System.Net.PeerToPeer.CloudCollection> class.</span></span> <span data-ttu-id="f88e6-121">Je možné získat kolekce PNRP cloudů ví, že aktuální sdílené volání statických <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="f88e6-121">Collections of PNRP clouds known to the current peer can be obtained by calling the static <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> method.</span></span>  
  
 <span data-ttu-id="f88e6-122">Jednotlivé cloudy mít jedinečné názvy, vyjádřené řetězec 256 znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="f88e6-122">Individual clouds have unique names, represented as a 256 character Unicode string.</span></span> <span data-ttu-id="f88e6-123">Názvy těchto spolu s výše uvedené oboru, se používají k vytvoření jedinečné instancí třídy cloudu.</span><span class="sxs-lookup"><span data-stu-id="f88e6-123">These names, along with the above-mentioned scope, are used to construct unique instances of the Cloud class.</span></span> <span data-ttu-id="f88e6-124">Tato instance může serializovat a znovu vytvořena pro trvalé používání.</span><span class="sxs-lookup"><span data-stu-id="f88e6-124">These instances can be serialized and reconstructed for persistent usage.</span></span>  
  
 <span data-ttu-id="f88e6-125">Po vytvoření nebo získat instanci cloudu, můžete se s ním vytvořit mřížku známé partnerské uzly zaregistrovat sdílené názvy.</span><span class="sxs-lookup"><span data-stu-id="f88e6-125">Once a Cloud instance is created or obtained, peer names can be registered with it to create a mesh of known peers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f88e6-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="f88e6-126">See Also</span></span>  
 <xref:System.Net.PeerToPeer.Cloud>  
 [<span data-ttu-id="f88e6-127">Protokol PNRP</span><span class="sxs-lookup"><span data-stu-id="f88e6-127">Peer Name Resolution Protocol</span></span>](../../../docs/framework/network-programming/peer-name-resolution-protocol.md)
