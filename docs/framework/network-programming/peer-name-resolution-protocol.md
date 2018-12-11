---
title: Protokol PNRP
ms.date: 03/30/2017
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
ms.openlocfilehash: f04b0b2e27c03ed477c6ceb10a5cbe41e1c7ce7c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129154"
---
# <a name="peer-name-resolution-protocol"></a><span data-ttu-id="04802-102">Protokol PNRP</span><span class="sxs-lookup"><span data-stu-id="04802-102">Peer Name Resolution Protocol</span></span>
<span data-ttu-id="04802-103">V prostředích peer-to-peer partnerské uzly použít konkrétní název řešení systémy druhé strany umístění v síti (adresy, protokoly a porty) z názvů nebo jiných typů identifikátorů.</span><span class="sxs-lookup"><span data-stu-id="04802-103">In peer-to-peer environments, peers use specific name resolution systems to resolve each other's network locations (addresses, protocols, and ports) from names or other types of identifiers.</span></span> <span data-ttu-id="04802-104">V minulosti má bylo složité peer name resolution Protocol ze své podstaty přechodné připojení, stejně jako ostatní nedostatky v v systému DNS (Domain Name).</span><span class="sxs-lookup"><span data-stu-id="04802-104">In the past, peer name resolution has been complicated by the inherently transient connectivity as well as other shortcomings within the Domain Name System (DNS).</span></span>  
  
 <span data-ttu-id="04802-105">Microsoft® Windows® sítě Peer-to-Peer platforma řeší tento problém se řešení protokolu PNRP (Peer Name), zabezpečené, škálovatelné a dynamické registraci a protokol nejdřív vyvinutý pro systém Windows XP a pak upgradovat v Windows Vista™.</span><span class="sxs-lookup"><span data-stu-id="04802-105">The Microsoft® Windows® Peer-to-Peer Networking platform solves this problem with the Peer Name Resolution Protocol (PNRP), a secure, scalable, and dynamic name registration and name resolution protocol first developed for Windows XP and then upgraded in Windows Vista™.</span></span> <span data-ttu-id="04802-106">PNRP funguje nějak významně odlišně, než tradiční název řešení systémy, otevírá zajímavé nové možnosti pro vývojáře aplikací.</span><span class="sxs-lookup"><span data-stu-id="04802-106">PNRP works very differently from traditional name resolution systems, opening up exciting new possibilities for application developers.</span></span>  
  
 <span data-ttu-id="04802-107">S protokolem PNRP můžete použít názvy partnerských uzlů do počítače, nebo jednotlivých aplikací nebo služeb v počítači.</span><span class="sxs-lookup"><span data-stu-id="04802-107">With PNRP, peer names can be applied to the machine, or individual applications or services on the machine.</span></span> <span data-ttu-id="04802-108">Peer name resolution Protocol obsahuje adresu, port a případně rozšířené datové části.</span><span class="sxs-lookup"><span data-stu-id="04802-108">A peer name resolution includes an address, port, and possibly an extended payload.</span></span> <span data-ttu-id="04802-109">Mezi výhody tohoto systému patří odolnost proti chybám, žádné kritické body a název řešení, které nikdy vrátí zastaralé adresy; provádění protokolu vynikající řešení pro hledání mobilních uživatelů.</span><span class="sxs-lookup"><span data-stu-id="04802-109">Benefits of this system include fault tolerance, no bottlenecks, and name resolutions that will never return stale addresses; making the protocol an excellent solution for locating mobile users.</span></span>  
  
 <span data-ttu-id="04802-110">Z hlediska zabezpečení, názvy partnerských uzlů může být publikován jako zabezpečené (chráněný) nebo nezabezpečené (bez ochrany).</span><span class="sxs-lookup"><span data-stu-id="04802-110">In terms of security, peer names can be published as secured (protected) or unsecured (unprotected).</span></span> <span data-ttu-id="04802-111">Protokol PNRP používá kryptografii využívající veřejného klíče k ochraně názvy partnerských uzlů zabezpečené proti falšování identity; s protokolem PNRP může mít název počítače a služby.</span><span class="sxs-lookup"><span data-stu-id="04802-111">PNRP uses public key cryptography to protect secure peer names against spoofing; both computers and services can be named with PNRP.</span></span>  
  
<span data-ttu-id="04802-112">Protokol Peer Name Resolution demonstruje následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="04802-112">The Peer Name Resolution Protocol demonstrates the following properties:</span></span>  
  
-   <span data-ttu-id="04802-113">Distribuované a téměř zcela bez serveru.</span><span class="sxs-lookup"><span data-stu-id="04802-113">Distributed and almost entirely serverless.</span></span> <span data-ttu-id="04802-114">Servery jsou pouze potřeba samozaváděcí procesu.</span><span class="sxs-lookup"><span data-stu-id="04802-114">Servers are only required for the bootstrapping process.</span></span>  
  
-   <span data-ttu-id="04802-115">Zabezpečené publikování názvů bez zapojení třetím stranám.</span><span class="sxs-lookup"><span data-stu-id="04802-115">Secure name publication without the involvement of third parties.</span></span> <span data-ttu-id="04802-116">Na rozdíl od publikace název DNS je název publikace PNRP okamžité a bez finančních nákladů.</span><span class="sxs-lookup"><span data-stu-id="04802-116">Unlike DNS name publication, PNRP name publication is instantaneous and without financial cost.</span></span>  
  
-   <span data-ttu-id="04802-117">PNRP aktualizace v reálném čase, se zabránilo zastaralé adres.</span><span class="sxs-lookup"><span data-stu-id="04802-117">PNRP updates in real-time, which prevents the resolution of stale addresses.</span></span>  
  
-   <span data-ttu-id="04802-118">Řešení názvů pomocí protokolu PNRP se rozpíná za počítače tím, že také překlad názvů pro služby.</span><span class="sxs-lookup"><span data-stu-id="04802-118">The resolution of names via PNRP extends beyond computers by also allowing name resolution for services.</span></span>  
  
## <a name="the-systemnetpeertopeer-namespace"></a><span data-ttu-id="04802-119">Obor názvů System.Net.PeerToPeer</span><span class="sxs-lookup"><span data-stu-id="04802-119">The System.Net.PeerToPeer namespace</span></span>  
  
-   <span data-ttu-id="04802-120">Je definována funkce PNRP <xref:System.Net.PeerToPeer> oboru názvů v rámci rozhraní .NET Framework verze 3.5.</span><span class="sxs-lookup"><span data-stu-id="04802-120">PNRP functionality is defined by the <xref:System.Net.PeerToPeer> namespace within the .NET Framework version 3.5.</span></span> <span data-ttu-id="04802-121">Poskytuje sadu typů, které je možné registrovat a překládat názvy partnerských uzlů dostupné službou PNRP.</span><span class="sxs-lookup"><span data-stu-id="04802-121">It provides a set of types that can be used to register and resolve peer names with an available PNRP service.</span></span>  
  
-   <span data-ttu-id="04802-122">(PNRP a překladače vlastní partnerských uzlů může být vytvořen a instance pomocí typů součástí <xref:System.ServiceModel.PeerResolvers> oboru názvů.)</span><span class="sxs-lookup"><span data-stu-id="04802-122">(PNRP and custom peer resolvers can be created and instantiated using the types provided in the <xref:System.ServiceModel.PeerResolvers> namespace.)</span></span>  
  
-   <span data-ttu-id="04802-123">Základní typy, které slouží k registraci a řešení názvů pomocí protokolu PNRP služby k dispozici jsou následující:</span><span class="sxs-lookup"><span data-stu-id="04802-123">The basic types used to register and resolve names with an available PNRP service are as follows:</span></span>  
  
-   <span data-ttu-id="04802-124"><xref:System.Net.PeerToPeer.Cloud>: Definuje informace, které popisují dostupné cloudu PNRP, včetně jeho rozsahu.</span><span class="sxs-lookup"><span data-stu-id="04802-124"><xref:System.Net.PeerToPeer.Cloud>: Defines the information describing an available PNRP cloud, including its scope.</span></span>  
  
-   <span data-ttu-id="04802-125"><xref:System.Net.PeerToPeer.PeerName>: Definuje název partnera, který slouží k registraci a následně vyřešit sdílené v rámci cloudu.</span><span class="sxs-lookup"><span data-stu-id="04802-125"><xref:System.Net.PeerToPeer.PeerName>: Defines a peer name that can be used to register and subsequently resolve a peer within a cloud.</span></span>  
  
-   <span data-ttu-id="04802-126"><xref:System.Net.PeerToPeer.PeerNameRecord>: Definuje záznamu v cloudu PNRP, který obsahuje informace o registraci pro partnerský uzel, který obsahuje koncové body sítě, na kterých mohou kontaktovat partnerský uzel.</span><span class="sxs-lookup"><span data-stu-id="04802-126"><xref:System.Net.PeerToPeer.PeerNameRecord>: Defines the record in PNRP cloud that contains the registration information for a peer, which includes the network endpoints at which the peer can be contacted.</span></span>  
  
-   <span data-ttu-id="04802-127"><xref:System.Net.PeerToPeer.PeerNameRegistration>: Definuje proces registrace pro název partnerského zařízení, včetně metod ke spuštění a zastavení registrace názvu partnera.</span><span class="sxs-lookup"><span data-stu-id="04802-127"><xref:System.Net.PeerToPeer.PeerNameRegistration>: Defines the registration process for a peer name, including methods to start and stop peer name registration.</span></span>  
  
-   <span data-ttu-id="04802-128"><xref:System.Net.PeerToPeer.PeerNameResolver>: Definuje proces pro vyřešení název partnerského zařízení do jeho koncových bodů sítě, včetně synchronní a asynchronní metody pro překlad.</span><span class="sxs-lookup"><span data-stu-id="04802-128"><xref:System.Net.PeerToPeer.PeerNameResolver>: Defines the process for resolving a peer name to its network endpoint(s), including both synchronous and asynchronous methods for resolution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04802-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04802-129">See also</span></span>  
- <xref:System.ServiceModel.PeerResolvers>  
- <xref:System.Net.PeerToPeer>  
- [<span data-ttu-id="04802-130">Ukázky programování sítě</span><span class="sxs-lookup"><span data-stu-id="04802-130">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)
- [<span data-ttu-id="04802-131">Ukázka technologie PeerToPeer</span><span class="sxs-lookup"><span data-stu-id="04802-131">PeerToPeer Technology Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179571)
