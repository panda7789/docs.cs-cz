---
title: "Názvy partnerů a ID PNRP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: afa538e8-948f-4a98-aa9f-305134004115
caps.latest.revision: "5"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 02f3f7585babd54c9d807afb308bccb7d67e2f88
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="peer-names-and-pnrp-ids"></a><span data-ttu-id="abb5b-102">Názvy partnerů a ID PNRP</span><span class="sxs-lookup"><span data-stu-id="abb5b-102">Peer Names and PNRP IDs</span></span>
<span data-ttu-id="abb5b-103">Název partnerského zařízení představuje koncový bod pro komunikaci, což může být do počítače, uživatele, skupiny, službou nebo nic přidružené partnerského uzlu, který lze přeložit na adresu IPv6.</span><span class="sxs-lookup"><span data-stu-id="abb5b-103">A Peer Name represents an endpoint for communication, which can be a computer, a user, a group, a service, or anything associated with a Peer that can be resolved to an IPv6 address.</span></span> <span data-ttu-id="abb5b-104">Řešení protokolu PNRP (Peer Name) trvá statisticky jedinečný název partnerského zařízení pro vytvoření PNRP ID, které slouží k identifikaci členů cloudu.</span><span class="sxs-lookup"><span data-stu-id="abb5b-104">The Peer Name Resolution Protocol (PNRP) takes the statistically unique Peer Name for the creation of a PNRP ID, which is used to identify cloud members.</span></span>  
  
## <a name="peer-names"></a><span data-ttu-id="abb5b-105">Názvy partnerů</span><span class="sxs-lookup"><span data-stu-id="abb5b-105">Peer Names</span></span>  
 <span data-ttu-id="abb5b-106">Názvy partnerů může být registrován jako nezabezpečená nebo zabezpečené.</span><span class="sxs-lookup"><span data-stu-id="abb5b-106">Peer names can be registered as unsecured or secured.</span></span> <span data-ttu-id="abb5b-107">Zabezpečená názvy jsou pouze textové řetězce, které se vztahují falšování identity, každý, kdo může registraci duplicitní název zabezpečená.</span><span class="sxs-lookup"><span data-stu-id="abb5b-107">Unsecured names are just text strings that are subject to spoofing, as anyone can register a duplicate unsecured name.</span></span> <span data-ttu-id="abb5b-108">Zabezpečená názvy jsou nejvhodnější v privátní nebo jinak chráněné sítě.</span><span class="sxs-lookup"><span data-stu-id="abb5b-108">Unsecured names are best used in private or otherwise protected networks.</span></span> <span data-ttu-id="abb5b-109">Zabezpečené názvy jsou chráněny certifikát a digitální podpis.</span><span class="sxs-lookup"><span data-stu-id="abb5b-109">Secured names are protected with a certificate and a digital signature.</span></span> <span data-ttu-id="abb5b-110">Původní vydavatel bude schopni prokázat vlastnictví zabezpečený název.</span><span class="sxs-lookup"><span data-stu-id="abb5b-110">Only the original publisher will be able to prove ownership of a secured name.</span></span>  
  
 <span data-ttu-id="abb5b-111">Kombinace cloudu a oboru poskytuje přiměřené zabezpečeném prostředí pro partnerské uzly, které jsou součástí PNRP aktivity.</span><span class="sxs-lookup"><span data-stu-id="abb5b-111">The combination of cloud and scope provides a reasonably secure environment for peers that participate in PNRP activity.</span></span> <span data-ttu-id="abb5b-112">Pomocí názvu zabezpečené sdílené ale nezajišťuje celkového zabezpečení síťových aplikací.</span><span class="sxs-lookup"><span data-stu-id="abb5b-112">However, using a secured peer name does not ensure the overall security of the networking application.</span></span> <span data-ttu-id="abb5b-113">Zabezpečení aplikace je závislá na implementaci.</span><span class="sxs-lookup"><span data-stu-id="abb5b-113">Security of the application is implementation-dependent.</span></span>  
  
 <span data-ttu-id="abb5b-114">Zabezpečené sdílené názvy jsou registrovat jenom podle jejich vlastníka a jsou chráněné službou kryptografie využívající veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="abb5b-114">Secured peer names are only registered by their owner and are protected with public key cryptography.</span></span> <span data-ttu-id="abb5b-115">Název zabezpečené partnera považuje za vlastní sdílené entita má odpovídající soukromý klíč.</span><span class="sxs-lookup"><span data-stu-id="abb5b-115">A secured peer name is considered owned by the peer entity having the corresponding private key.</span></span> <span data-ttu-id="abb5b-116">Vlastnictví lze prokázat přes adresu certifikovaných sdílené (CPA), která je podepsaná pomocí soukromého klíče.</span><span class="sxs-lookup"><span data-stu-id="abb5b-116">Ownership can be proved via the certified peer address (CPA), which is signed using the private key.</span></span> <span data-ttu-id="abb5b-117">Uživatel se zlými úmysly nelze forge vlastnictví název partnerského zařízení bez odpovídajícího privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="abb5b-117">A malicious user cannot forge ownership of a peer name without the corresponding private key.</span></span>  
  
## <a name="pnrp-ids"></a><span data-ttu-id="abb5b-118">ID PNRP</span><span class="sxs-lookup"><span data-stu-id="abb5b-118">PNRP IDs</span></span>  
 <span data-ttu-id="abb5b-119">![PNRP ID](../../../docs/framework/network-programming/media/fdc9e8a0-4a1c-488d-a019-bc3a1973220c.gif "fdc9e8a0-4a1c-488d-a019-bc3a1973220c")</span><span class="sxs-lookup"><span data-stu-id="abb5b-119">![PNRP ID](../../../docs/framework/network-programming/media/fdc9e8a0-4a1c-488d-a019-bc3a1973220c.gif "fdc9e8a0-4a1c-488d-a019-bc3a1973220c")</span></span>  
  
 <span data-ttu-id="abb5b-120">ID PNRP se skládají z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="abb5b-120">PNRP IDs are composed of the following:</span></span>  
  
-   <span data-ttu-id="abb5b-121">Nejvyšších 128 bitů, označované jako ID peer-to-peer (P2P), je hodnota hash název partnera přiřazené ke koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="abb5b-121">The high-order 128 bits, known as the peer-to-peer (P2P) ID, are a hash of a peer name assigned to the endpoint.</span></span> <span data-ttu-id="abb5b-122">Název partnerského zařízení má následující formát: *Authority.Classifier*.</span><span class="sxs-lookup"><span data-stu-id="abb5b-122">The peer name has the following format: *Authority.Classifier*.</span></span> <span data-ttu-id="abb5b-123">Pro zabezpečené názvy *autority* je Secure Hash Algorithm 1 (SHA1) hodnota hash veřejného klíče pro název partnerského zařízení v hexadecimálních znaků.</span><span class="sxs-lookup"><span data-stu-id="abb5b-123">For secured names, *Authority* is the Secure Hash Algorithm 1 (SHA1) hash of the public key of the peer name in hexadecimal characters.</span></span> <span data-ttu-id="abb5b-124">Pro zabezpečená názvy *autority* je jeden znak "0".</span><span class="sxs-lookup"><span data-stu-id="abb5b-124">For unsecured names, the *Authority* is the single character "0".</span></span> <span data-ttu-id="abb5b-125">*Klasifikátor* je řetězec, který identifikuje aplikaci.</span><span class="sxs-lookup"><span data-stu-id="abb5b-125">*Classifier* is a string that identifies the application.</span></span> <span data-ttu-id="abb5b-126">Žádné sdílené název třídění může být větší než 149 znaků včetně `null` ukončovací znak.</span><span class="sxs-lookup"><span data-stu-id="abb5b-126">No peer name classifier can be greater than 149 characters long, including the `null` terminator.</span></span>  
  
-   <span data-ttu-id="abb5b-127">Nejnižší 128 bitů se používá pro umístění služby, což je generovaným číslem, který identifikuje různé instance stejné ID P2P ve stejném cloudu.</span><span class="sxs-lookup"><span data-stu-id="abb5b-127">The low-order 128 bits are used for the Service Location, which is a generated number that identifies different instances of the same P2P ID in the same cloud.</span></span>  
  
 <span data-ttu-id="abb5b-128">Tato kombinace P2P ID a umístění služby umožňuje více ID PNRP registraci z jednoho počítače.</span><span class="sxs-lookup"><span data-stu-id="abb5b-128">This combination of P2P ID and Service Location allows multiple PNRP IDs to be registered from a single computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abb5b-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="abb5b-129">See Also</span></span>  
 <xref:System.Net.PeerToPeer.PeerName>  
 <xref:System.Net.PeerToPeer>
