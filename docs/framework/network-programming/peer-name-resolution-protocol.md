---
title: Protokol PNRP (Peer Name Resolution Protocol)
ms.date: 03/30/2017
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
ms.openlocfilehash: c8b7b2190349323bf212d816a77f5f7810f6ca2c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428220"
---
# <a name="peer-name-resolution-protocol"></a><span data-ttu-id="96252-102">Protokol PNRP (Peer Name Resolution Protocol)</span><span class="sxs-lookup"><span data-stu-id="96252-102">Peer Name Resolution Protocol</span></span>
<span data-ttu-id="96252-103">V prostředích peer-to-peer používají partneři konkrétní systémy překladu názvů k řešení různých síťových umístění (adres, protokolů a portů) v názvech nebo jiných typech identifikátorů.</span><span class="sxs-lookup"><span data-stu-id="96252-103">In peer-to-peer environments, peers use specific name resolution systems to resolve each other's network locations (addresses, protocols, and ports) from names or other types of identifiers.</span></span> <span data-ttu-id="96252-104">V minulosti bylo překlad IP adres komplikovanější díky složitě přechodným připojením a dalším nedostatkům v systému DNS (Domain Name System).</span><span class="sxs-lookup"><span data-stu-id="96252-104">In the past, peer name resolution has been complicated by the inherently transient connectivity as well as other shortcomings within the Domain Name System (DNS).</span></span>  
  
 <span data-ttu-id="96252-105">Síťové platformy Microsoft® Windows® peer-to-peer řeší tento problém pomocí protokolu PNRP (Peer Name Resolution Protocol), bezpečné, škálovatelné a dynamické registrace názvů a protokolu překladu IP adres, který se poprvé vyvinul pro systém Windows XP a následně upgradován v Systém Windows Vista™.</span><span class="sxs-lookup"><span data-stu-id="96252-105">The Microsoft® Windows® Peer-to-Peer Networking platform solves this problem with the Peer Name Resolution Protocol (PNRP), a secure, scalable, and dynamic name registration and name resolution protocol first developed for Windows XP and then upgraded in Windows Vista™.</span></span> <span data-ttu-id="96252-106">PNRP funguje velmi jinak než tradiční systémy pro překlad názvů a otevírá Skvělé nové možnosti pro vývojáře aplikací.</span><span class="sxs-lookup"><span data-stu-id="96252-106">PNRP works very differently from traditional name resolution systems, opening up exciting new possibilities for application developers.</span></span>  
  
 <span data-ttu-id="96252-107">S protokolem PNRP lze pro počítač nebo jednotlivé aplikace nebo služby na počítači použít rovnocenné názvy.</span><span class="sxs-lookup"><span data-stu-id="96252-107">With PNRP, peer names can be applied to the machine, or individual applications or services on the machine.</span></span> <span data-ttu-id="96252-108">Překlad názvů partnerů zahrnuje adresu, port a případně rozšířenou datovou část.</span><span class="sxs-lookup"><span data-stu-id="96252-108">A peer name resolution includes an address, port, and possibly an extended payload.</span></span> <span data-ttu-id="96252-109">Mezi výhody tohoto systému patří odolnost proti chybám, žádné kritické body a překlad názvů, které nikdy nevrátí zastaralé adresy. Díky tomuto protokolu máte vynikající řešení pro hledání mobilních uživatelů.</span><span class="sxs-lookup"><span data-stu-id="96252-109">Benefits of this system include fault tolerance, no bottlenecks, and name resolutions that will never return stale addresses; making the protocol an excellent solution for locating mobile users.</span></span>  
  
 <span data-ttu-id="96252-110">Z hlediska zabezpečení je možné názvy partnerských uzlů publikovat jako zabezpečené (chráněné) nebo nezabezpečené (bez ochrany).</span><span class="sxs-lookup"><span data-stu-id="96252-110">In terms of security, peer names can be published as secured (protected) or unsecured (unprotected).</span></span> <span data-ttu-id="96252-111">Protokol PNRP používá kryptografii s veřejným klíčem k ochraně názvů bezpečných partnerských uzlů proti falšování identity; oba počítače i služby můžou mít název s protokolem PNRP.</span><span class="sxs-lookup"><span data-stu-id="96252-111">PNRP uses public key cryptography to protect secure peer names against spoofing; both computers and services can be named with PNRP.</span></span>  
  
<span data-ttu-id="96252-112">Protokol PNRP (Peer Name Resolution Protocol) ukazuje následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="96252-112">The Peer Name Resolution Protocol demonstrates the following properties:</span></span>  
  
- <span data-ttu-id="96252-113">Distribuováno a skoro zcela bez serveru.</span><span class="sxs-lookup"><span data-stu-id="96252-113">Distributed and almost entirely serverless.</span></span> <span data-ttu-id="96252-114">Servery jsou vyžadovány pouze pro zaváděcí proces.</span><span class="sxs-lookup"><span data-stu-id="96252-114">Servers are only required for the bootstrapping process.</span></span>  
  
- <span data-ttu-id="96252-115">Zabezpečené publikování názvu bez účasti třetích stran.</span><span class="sxs-lookup"><span data-stu-id="96252-115">Secure name publication without the involvement of third parties.</span></span> <span data-ttu-id="96252-116">Na rozdíl od publikování názvu DNS je publikace názvu PNRP okamžitá a bez finančních nákladů.</span><span class="sxs-lookup"><span data-stu-id="96252-116">Unlike DNS name publication, PNRP name publication is instantaneous and without financial cost.</span></span>  
  
- <span data-ttu-id="96252-117">Aktualizace PNRP v reálném čase, což brání vyřešení zastaralých adres.</span><span class="sxs-lookup"><span data-stu-id="96252-117">PNRP updates in real-time, which prevents the resolution of stale addresses.</span></span>  
  
- <span data-ttu-id="96252-118">Překlad názvů prostřednictvím protokolu PNRP překračuje počítače tím, že umožňuje překlad názvů služeb.</span><span class="sxs-lookup"><span data-stu-id="96252-118">The resolution of names via PNRP extends beyond computers by also allowing name resolution for services.</span></span>  
  
## <a name="the-systemnetpeertopeer-namespace"></a><span data-ttu-id="96252-119">Obor názvů System .NET. PeerToPeer</span><span class="sxs-lookup"><span data-stu-id="96252-119">The System.Net.PeerToPeer namespace</span></span>  
  
- <span data-ttu-id="96252-120">Funkce PNRP je definována oborem názvů <xref:System.Net.PeerToPeer> v rámci .NET Framework verze 3,5.</span><span class="sxs-lookup"><span data-stu-id="96252-120">PNRP functionality is defined by the <xref:System.Net.PeerToPeer> namespace within the .NET Framework version 3.5.</span></span> <span data-ttu-id="96252-121">Poskytuje sadu typů, které se dají použít k registraci a překladu názvů partnerských uzlů pomocí dostupné služby PNRP.</span><span class="sxs-lookup"><span data-stu-id="96252-121">It provides a set of types that can be used to register and resolve peer names with an available PNRP service.</span></span>  
  
- <span data-ttu-id="96252-122">(Protokol PNRP a vlastní překladače rovnocenných zařízení je možné vytvořit a vytvořit z něj typy poskytované v oboru názvů <xref:System.ServiceModel.PeerResolvers>.)</span><span class="sxs-lookup"><span data-stu-id="96252-122">(PNRP and custom peer resolvers can be created and instantiated using the types provided in the <xref:System.ServiceModel.PeerResolvers> namespace.)</span></span>  
  
- <span data-ttu-id="96252-123">Následující typy, které se používají k registraci a překladu názvů pomocí dostupné služby PNRP, jsou tyto:</span><span class="sxs-lookup"><span data-stu-id="96252-123">The basic types used to register and resolve names with an available PNRP service are as follows:</span></span>  
  
- <span data-ttu-id="96252-124"><xref:System.Net.PeerToPeer.Cloud>: definuje informace popisující dostupný Cloud PNRP, včetně jeho oboru.</span><span class="sxs-lookup"><span data-stu-id="96252-124"><xref:System.Net.PeerToPeer.Cloud>: Defines the information describing an available PNRP cloud, including its scope.</span></span>  
  
- <span data-ttu-id="96252-125"><xref:System.Net.PeerToPeer.PeerName>: definuje název partnerského zařízení, který se dá použít k registraci a následnému vyřešení partnerského vztahu v rámci cloudu.</span><span class="sxs-lookup"><span data-stu-id="96252-125"><xref:System.Net.PeerToPeer.PeerName>: Defines a peer name that can be used to register and subsequently resolve a peer within a cloud.</span></span>  
  
- <span data-ttu-id="96252-126"><xref:System.Net.PeerToPeer.PeerNameRecord>: definuje záznam v cloudu PNRP, který obsahuje informace o registraci pro partnera, který obsahuje koncové body sítě, na kterých se dá partnerský uzel kontaktovat.</span><span class="sxs-lookup"><span data-stu-id="96252-126"><xref:System.Net.PeerToPeer.PeerNameRecord>: Defines the record in PNRP cloud that contains the registration information for a peer, which includes the network endpoints at which the peer can be contacted.</span></span>  
  
- <span data-ttu-id="96252-127"><xref:System.Net.PeerToPeer.PeerNameRegistration>: definuje proces registrace pro název partnerského zařízení, včetně metod pro spuštění a zastavení registrace názvu partnera.</span><span class="sxs-lookup"><span data-stu-id="96252-127"><xref:System.Net.PeerToPeer.PeerNameRegistration>: Defines the registration process for a peer name, including methods to start and stop peer name registration.</span></span>  
  
- <span data-ttu-id="96252-128"><xref:System.Net.PeerToPeer.PeerNameResolver>: definuje proces pro překlad názvu partnerského vztahu na jeho koncové body sítě, včetně synchronních a asynchronních metod pro řešení.</span><span class="sxs-lookup"><span data-stu-id="96252-128"><xref:System.Net.PeerToPeer.PeerNameResolver>: Defines the process for resolving a peer name to its network endpoint(s), including both synchronous and asynchronous methods for resolution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96252-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96252-129">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers>
- <xref:System.Net.PeerToPeer>
- [<span data-ttu-id="96252-130">Ukázky programování sítě</span><span class="sxs-lookup"><span data-stu-id="96252-130">Network Programming Samples</span></span>](network-programming-samples.md)

<!-- to-do: review sample links
- [PeerToPeer Technology Sample](https://go.microsoft.com/fwlink/?LinkID=179571)
-->
