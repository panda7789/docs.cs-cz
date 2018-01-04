---
title: Protokol PNRP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: ba38c7e42126bb70161dcb72ffdd6965e8def044
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="peer-name-resolution-protocol"></a><span data-ttu-id="0d93b-102">Protokol PNRP</span><span class="sxs-lookup"><span data-stu-id="0d93b-102">Peer Name Resolution Protocol</span></span>
<span data-ttu-id="0d93b-103">V prostředích peer-to-peer partnerské uzly používají určitý název řešení systémy přeložit vzájemně umístění v síti (adresy, protokoly a porty) z názvů nebo jiné typy identifikátorů.</span><span class="sxs-lookup"><span data-stu-id="0d93b-103">In peer-to-peer environments, peers use specific name resolution systems to resolve each other's network locations (addresses, protocols, and ports) from names or other types of identifiers.</span></span> <span data-ttu-id="0d93b-104">V minulosti má byla peer name resolution Protocol ztěžuje ze své podstaty přechodný připojení a také další nedostatků v v systému DNS (Domain Name).</span><span class="sxs-lookup"><span data-stu-id="0d93b-104">In the past, peer name resolution has been complicated by the inherently transient connectivity as well as other shortcomings within the Domain Name System (DNS).</span></span>  
  
 <span data-ttu-id="0d93b-105">Microsoft® Windows® Peer-to-Peer sítě platforma řeší tento problém s řešení protokolu PNRP (Peer Name), zabezpečená, škálovatelná a dynamické registraci a protokolu name resolution protocol nejprve vyvinuté pro systém Windows XP a pak upgradovat na Vista™ systému Windows.</span><span class="sxs-lookup"><span data-stu-id="0d93b-105">The Microsoft® Windows® Peer-to-Peer Networking platform solves this problem with the Peer Name Resolution Protocol (PNRP), a secure, scalable, and dynamic name registration and name resolution protocol first developed for Windows XP and then upgraded in Windows Vista™.</span></span> <span data-ttu-id="0d93b-106">PNRP funguje velmi jinak, než tradiční název řešení systémy, otevírá zajímavé nové možnosti pro vývojáře aplikací.</span><span class="sxs-lookup"><span data-stu-id="0d93b-106">PNRP works very differently from traditional name resolution systems, opening up exciting new possibilities for application developers.</span></span>  
  
 <span data-ttu-id="0d93b-107">S PNRP můžete použít sdílené názvy do počítače, nebo jednotlivých aplikací nebo služeb v počítači.</span><span class="sxs-lookup"><span data-stu-id="0d93b-107">With PNRP, peer names can be applied to the machine, or individual applications or services on the machine.</span></span> <span data-ttu-id="0d93b-108">Peer name resolution Protocol zahrnuje adresu, port a které by mohly mít rozšířené datové části.</span><span class="sxs-lookup"><span data-stu-id="0d93b-108">A peer name resolution includes an address, port, and possibly an extended payload.</span></span> <span data-ttu-id="0d93b-109">Příklady výhod tohoto systému odolnost proti chybám, žádné kritická místa a název řešení, které nikdy vrátí zastaralé adresy; provedení protokol vynikající řešení pro hledání mobilních uživatelů.</span><span class="sxs-lookup"><span data-stu-id="0d93b-109">Benefits of this system include fault tolerance, no bottlenecks, and name resolutions that will never return stale addresses; making the protocol an excellent solution for locating mobile users.</span></span>  
  
 <span data-ttu-id="0d93b-110">Z hlediska zabezpečení, může být názvy partnerů publikován jako zabezpečené (chráněné) nebo zabezpečená (nechráněné).</span><span class="sxs-lookup"><span data-stu-id="0d93b-110">In terms of security, peer names can be published as secured (protected) or unsecured (unprotected).</span></span> <span data-ttu-id="0d93b-111">PNRP používá kryptografie využívající veřejného klíče k ochraně zabezpečené sdílené názvy proti falšování identity; počítače a služby mohou být pojmenovány PNRP.</span><span class="sxs-lookup"><span data-stu-id="0d93b-111">PNRP uses public key cryptography to protect secure peer names against spoofing; both computers and services can be named with PNRP.</span></span>  
  
-   <span data-ttu-id="0d93b-112">Protokol Peer Name Resolution ukazuje následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="0d93b-112">The Peer Name Resolution Protocol demonstrates the following properties:</span></span>  
  
-   <span data-ttu-id="0d93b-113">Distribuované a téměř úplně bez serveru.</span><span class="sxs-lookup"><span data-stu-id="0d93b-113">Distributed and almost entirely serverless.</span></span> <span data-ttu-id="0d93b-114">Servery jsou pouze požadované pro samozaváděcí proces.</span><span class="sxs-lookup"><span data-stu-id="0d93b-114">Servers are only required for the bootstrapping process.</span></span>  
  
-   <span data-ttu-id="0d93b-115">Zabezpečte název publikace bez zapojení třetích stran.</span><span class="sxs-lookup"><span data-stu-id="0d93b-115">Secure name publication without the involvement of third parties.</span></span> <span data-ttu-id="0d93b-116">Na rozdíl od publikaci název DNS je název publikace PNRP okamžitou a bez finanční náklady.</span><span class="sxs-lookup"><span data-stu-id="0d93b-116">Unlike DNS name publication, PNRP name publication is instantaneous and without financial cost.</span></span>  
  
-   <span data-ttu-id="0d93b-117">PNRP aktualizace v v reálném čase, která brání zastaralé adres.</span><span class="sxs-lookup"><span data-stu-id="0d93b-117">PNRP updates in real-time, which prevents the resolution of stale addresses.</span></span>  
  
-   <span data-ttu-id="0d93b-118">Řešení názvů pomocí protokolu PNRP přesahuje počítače tím, že se také překlad názvů pro služby.</span><span class="sxs-lookup"><span data-stu-id="0d93b-118">The resolution of names via PNRP extends beyond computers by also allowing name resolution for services.</span></span>  
  
-  
  
## <a name="the-systemnetpeertopeer-namespace"></a><span data-ttu-id="0d93b-119">Namespace System.Net.PeerToPeer</span><span class="sxs-lookup"><span data-stu-id="0d93b-119">The System.Net.PeerToPeer Namespace</span></span>  
  
-   <span data-ttu-id="0d93b-120">Funkce PNRP je definována <xref:System.Net.PeerToPeer> oboru názvů v rozhraní .NET Framework verze 3.5.</span><span class="sxs-lookup"><span data-stu-id="0d93b-120">PNRP functionality is defined by the <xref:System.Net.PeerToPeer> namespace within the .NET Framework version 3.5.</span></span> <span data-ttu-id="0d93b-121">Poskytuje sadu typů, které lze použít k registraci a překladu názvů partnerů s služby k dispozici PNRP.</span><span class="sxs-lookup"><span data-stu-id="0d93b-121">It provides a set of types that can be used to register and resolve peer names with an available PNRP service.</span></span>  
  
-  
  
-   <span data-ttu-id="0d93b-122">(PNRP a překladače vlastní partnerských uzlů může být vytvořen a instancí pomocí typy součástí <xref:System.ServiceModel.PeerResolvers> oboru názvů.)</span><span class="sxs-lookup"><span data-stu-id="0d93b-122">(PNRP and custom peer resolvers can be created and instantiated using the types provided in the <xref:System.ServiceModel.PeerResolvers> namespace.)</span></span>  
  
-  
  
-   <span data-ttu-id="0d93b-123">Základní typy používá k registraci a překlad názvů s PNRP služby k dispozici jsou následující:</span><span class="sxs-lookup"><span data-stu-id="0d93b-123">The basic types used to register and resolve names with an available PNRP service are as follows:</span></span>  
  
-  
  
-   <span data-ttu-id="0d93b-124"><xref:System.Net.PeerToPeer.Cloud>: Definuje informace, které popisují dostupné PNRP cloudu, včetně jeho oboru.</span><span class="sxs-lookup"><span data-stu-id="0d93b-124"><xref:System.Net.PeerToPeer.Cloud>: Defines the information describing an available PNRP cloud, including its scope.</span></span>  
  
-   <span data-ttu-id="0d93b-125"><xref:System.Net.PeerToPeer.PeerName>: Definuje název partnerského zařízení, která slouží k registraci a následně vyřešit partnerského uzlu v cloudu.</span><span class="sxs-lookup"><span data-stu-id="0d93b-125"><xref:System.Net.PeerToPeer.PeerName>: Defines a peer name that can be used to register and subsequently resolve a peer within a cloud.</span></span>  
  
-   <span data-ttu-id="0d93b-126"><xref:System.Net.PeerToPeer.PeerNameRecord>: Definuje záznam PNRP cloudu, který obsahuje informace o registraci pro partnerský uzel, včetně koncových bodů sítě, na kterých mohou kontaktovat partnerský uzel.</span><span class="sxs-lookup"><span data-stu-id="0d93b-126"><xref:System.Net.PeerToPeer.PeerNameRecord>: Defines the record in PNRP cloud that contains the registration information for a peer, which includes the network endpoints at which the peer can be contacted.</span></span>  
  
-   <span data-ttu-id="0d93b-127"><xref:System.Net.PeerToPeer.PeerNameRegistration>: Definuje proces registrace pro název partnerského zařízení, včetně metody pro spuštění a zastavení registrace názvu partnera.</span><span class="sxs-lookup"><span data-stu-id="0d93b-127"><xref:System.Net.PeerToPeer.PeerNameRegistration>: Defines the registration process for a peer name, including methods to start and stop peer name registration.</span></span>  
  
-   <span data-ttu-id="0d93b-128"><xref:System.Net.PeerToPeer.PeerNameResolver>: Definuje proces překladu název partnerského zařízení na jeho koncové sítě, včetně synchronní a asynchronní metody pro řešení.</span><span class="sxs-lookup"><span data-stu-id="0d93b-128"><xref:System.Net.PeerToPeer.PeerNameResolver>: Defines the process for resolving a peer name to its network endpoint(s), including both synchronous and asynchronous methods for resolution.</span></span>  
  
-  
  
-  
  
## <a name="see-also"></a><span data-ttu-id="0d93b-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d93b-129">See Also</span></span>  
 <xref:System.ServiceModel.PeerResolvers>  
 <xref:System.Net.PeerToPeer>  
 [<span data-ttu-id="0d93b-130">Ukázky programování sítě</span><span class="sxs-lookup"><span data-stu-id="0d93b-130">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)  
 [<span data-ttu-id="0d93b-131">Ukázka PeerToPeer technologie</span><span class="sxs-lookup"><span data-stu-id="0d93b-131">PeerToPeer Technology Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179571)
