---
title: Protokol PNRP (Peer Name Resolution Protocol)
ms.date: 03/30/2017
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
ms.openlocfilehash: c8b7b2190349323bf212d816a77f5f7810f6ca2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74428220"
---
# <a name="peer-name-resolution-protocol"></a><span data-ttu-id="aad7c-102">Protokol PNRP (Peer Name Resolution Protocol)</span><span class="sxs-lookup"><span data-stu-id="aad7c-102">Peer Name Resolution Protocol</span></span>
<span data-ttu-id="aad7c-103">V prostředích typu peer-to-peer používají partneři specifické systémy pro překlad názvů k vzájemnému překladu síťových umístění (adres, protokolů a portů) z názvů nebo jiných typů identifikátorů.</span><span class="sxs-lookup"><span data-stu-id="aad7c-103">In peer-to-peer environments, peers use specific name resolution systems to resolve each other's network locations (addresses, protocols, and ports) from names or other types of identifiers.</span></span> <span data-ttu-id="aad7c-104">V minulosti bylo překlad názvů rovnocenných stran komplikováno neodmyslitelně přechodným připojením a dalšími nedostatky v systému DNS (Domain Name System).</span><span class="sxs-lookup"><span data-stu-id="aad7c-104">In the past, peer name resolution has been complicated by the inherently transient connectivity as well as other shortcomings within the Domain Name System (DNS).</span></span>  
  
 <span data-ttu-id="aad7c-105">Microsoft® Windows® Peer-to-Peer síťová platforma řeší tento problém s Peer Name Resolution Protocol (PNRP), zabezpečené, škálovatelné a dynamické registrace názvů a překlad názvů protokol nejprve vyvinut pro Windows XP a poté inovované v Windows Vista™.</span><span class="sxs-lookup"><span data-stu-id="aad7c-105">The Microsoft® Windows® Peer-to-Peer Networking platform solves this problem with the Peer Name Resolution Protocol (PNRP), a secure, scalable, and dynamic name registration and name resolution protocol first developed for Windows XP and then upgraded in Windows Vista™.</span></span> <span data-ttu-id="aad7c-106">PNRP funguje velmi odlišně od tradičních systémů pro rozlišení názvů a otevírá vzrušující nové možnosti pro vývojáře aplikací.</span><span class="sxs-lookup"><span data-stu-id="aad7c-106">PNRP works very differently from traditional name resolution systems, opening up exciting new possibilities for application developers.</span></span>  
  
 <span data-ttu-id="aad7c-107">S PNRP, peer jména lze použít na počítači nebo jednotlivé aplikace nebo služby v počítači.</span><span class="sxs-lookup"><span data-stu-id="aad7c-107">With PNRP, peer names can be applied to the machine, or individual applications or services on the machine.</span></span> <span data-ttu-id="aad7c-108">Překlad názvů partnera obsahuje adresu, port a případně rozšířenou datovou část.</span><span class="sxs-lookup"><span data-stu-id="aad7c-108">A peer name resolution includes an address, port, and possibly an extended payload.</span></span> <span data-ttu-id="aad7c-109">Mezi výhody tohoto systému patří odolnost proti chybám, žádná kritická místa a překlady názvů, které nikdy nevrátí zastaralé adresy; čímž se protokol dělá vynikajícím řešením pro vyhledávání mobilních uživatelů.</span><span class="sxs-lookup"><span data-stu-id="aad7c-109">Benefits of this system include fault tolerance, no bottlenecks, and name resolutions that will never return stale addresses; making the protocol an excellent solution for locating mobile users.</span></span>  
  
 <span data-ttu-id="aad7c-110">Z hlediska zabezpečení mohou být názvy rovnocenných počítačů publikovány jako zabezpečené (chráněné) nebo nezabezpečené (nechráněné).</span><span class="sxs-lookup"><span data-stu-id="aad7c-110">In terms of security, peer names can be published as secured (protected) or unsecured (unprotected).</span></span> <span data-ttu-id="aad7c-111">PNRP používá kryptografii s veřejným klíčem k ochraně zabezpečených názvů rovnocenných počítačů před falšováním z falšování; počítače i služby lze pojmenovat pomocí PNRP.</span><span class="sxs-lookup"><span data-stu-id="aad7c-111">PNRP uses public key cryptography to protect secure peer names against spoofing; both computers and services can be named with PNRP.</span></span>  
  
<span data-ttu-id="aad7c-112">Protokol Peer Name Resolution Protocol demonstruje následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="aad7c-112">The Peer Name Resolution Protocol demonstrates the following properties:</span></span>  
  
- <span data-ttu-id="aad7c-113">Distribuováno a téměř výhradně bez serveru.</span><span class="sxs-lookup"><span data-stu-id="aad7c-113">Distributed and almost entirely serverless.</span></span> <span data-ttu-id="aad7c-114">Servery jsou vyžadovány pouze pro zaváděcí proces.</span><span class="sxs-lookup"><span data-stu-id="aad7c-114">Servers are only required for the bootstrapping process.</span></span>  
  
- <span data-ttu-id="aad7c-115">Bezpečné zveřejnění názvu bez účasti třetích stran.</span><span class="sxs-lookup"><span data-stu-id="aad7c-115">Secure name publication without the involvement of third parties.</span></span> <span data-ttu-id="aad7c-116">Na rozdíl od publikace názvu DNS je publikace názvu PNRP okamžitá a bez finančních nákladů.</span><span class="sxs-lookup"><span data-stu-id="aad7c-116">Unlike DNS name publication, PNRP name publication is instantaneous and without financial cost.</span></span>  
  
- <span data-ttu-id="aad7c-117">PNRP aktualizace v reálném čase, což zabraňuje řešení zastaralých adres.</span><span class="sxs-lookup"><span data-stu-id="aad7c-117">PNRP updates in real-time, which prevents the resolution of stale addresses.</span></span>  
  
- <span data-ttu-id="aad7c-118">Rozlišení názvů prostřednictvím PNRP přesahuje počítače tím, že také umožňuje překlad názvů pro služby.</span><span class="sxs-lookup"><span data-stu-id="aad7c-118">The resolution of names via PNRP extends beyond computers by also allowing name resolution for services.</span></span>  
  
## <a name="the-systemnetpeertopeer-namespace"></a><span data-ttu-id="aad7c-119">Obor názvů System.Net.PeerToPeer</span><span class="sxs-lookup"><span data-stu-id="aad7c-119">The System.Net.PeerToPeer namespace</span></span>  
  
- <span data-ttu-id="aad7c-120">Funkce PNRP je definována <xref:System.Net.PeerToPeer> oborem názvů v rámci rozhraní .NET Framework verze 3.5.</span><span class="sxs-lookup"><span data-stu-id="aad7c-120">PNRP functionality is defined by the <xref:System.Net.PeerToPeer> namespace within the .NET Framework version 3.5.</span></span> <span data-ttu-id="aad7c-121">Poskytuje sadu typů, které lze použít k registraci a překladu názvů rovnocenných počítačů s dostupnou službou PNRP.</span><span class="sxs-lookup"><span data-stu-id="aad7c-121">It provides a set of types that can be used to register and resolve peer names with an available PNRP service.</span></span>  
  
- <span data-ttu-id="aad7c-122">(PNRP a vlastní peer překladače lze vytvořit a vytvořit instance <xref:System.ServiceModel.PeerResolvers> pomocí typů uvedených v oboru názvů.)</span><span class="sxs-lookup"><span data-stu-id="aad7c-122">(PNRP and custom peer resolvers can be created and instantiated using the types provided in the <xref:System.ServiceModel.PeerResolvers> namespace.)</span></span>  
  
- <span data-ttu-id="aad7c-123">Základní typy používané k registraci a překladu názvů s dostupnou službou PNRP jsou následující:</span><span class="sxs-lookup"><span data-stu-id="aad7c-123">The basic types used to register and resolve names with an available PNRP service are as follows:</span></span>  
  
- <span data-ttu-id="aad7c-124"><xref:System.Net.PeerToPeer.Cloud>: Definuje informace popisující dostupný cloud PNRP, včetně jeho oboru.</span><span class="sxs-lookup"><span data-stu-id="aad7c-124"><xref:System.Net.PeerToPeer.Cloud>: Defines the information describing an available PNRP cloud, including its scope.</span></span>  
  
- <span data-ttu-id="aad7c-125"><xref:System.Net.PeerToPeer.PeerName>: Definuje název partnera, který lze použít k registraci a následně přeložit partnera v rámci cloudu.</span><span class="sxs-lookup"><span data-stu-id="aad7c-125"><xref:System.Net.PeerToPeer.PeerName>: Defines a peer name that can be used to register and subsequently resolve a peer within a cloud.</span></span>  
  
- <span data-ttu-id="aad7c-126"><xref:System.Net.PeerToPeer.PeerNameRecord>: Definuje záznam v cloudu PNRP, který obsahuje registrační informace pro partnera, který zahrnuje koncové body sítě, ve kterých lze kontaktovat partnera.</span><span class="sxs-lookup"><span data-stu-id="aad7c-126"><xref:System.Net.PeerToPeer.PeerNameRecord>: Defines the record in PNRP cloud that contains the registration information for a peer, which includes the network endpoints at which the peer can be contacted.</span></span>  
  
- <span data-ttu-id="aad7c-127"><xref:System.Net.PeerToPeer.PeerNameRegistration>: Definuje proces registrace pro název partnera, včetně metod pro spuštění a zastavení registrace názvu partnera.</span><span class="sxs-lookup"><span data-stu-id="aad7c-127"><xref:System.Net.PeerToPeer.PeerNameRegistration>: Defines the registration process for a peer name, including methods to start and stop peer name registration.</span></span>  
  
- <span data-ttu-id="aad7c-128"><xref:System.Net.PeerToPeer.PeerNameResolver>: Definuje proces pro překlad názvu partnera do koncového bodu (koncových bodů sítě), včetně synchronních i asynchronních metod řešení.</span><span class="sxs-lookup"><span data-stu-id="aad7c-128"><xref:System.Net.PeerToPeer.PeerNameResolver>: Defines the process for resolving a peer name to its network endpoint(s), including both synchronous and asynchronous methods for resolution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aad7c-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="aad7c-129">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers>
- <xref:System.Net.PeerToPeer>
- [<span data-ttu-id="aad7c-130">Ukázky programování sítě</span><span class="sxs-lookup"><span data-stu-id="aad7c-130">Network Programming Samples</span></span>](network-programming-samples.md)

<!-- to-do: review sample links
- [PeerToPeer Technology Sample](https://go.microsoft.com/fwlink/?LinkID=179571)
-->
