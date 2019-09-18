---
title: Protokol IP (Internet Protocol) verze 6
ms.date: 03/30/2017
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
ms.openlocfilehash: 367db4fa4e585d6066009dbd1afacb154829319a
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047881"
---
# <a name="internet-protocol-version-6"></a><span data-ttu-id="4f57a-102">Protokol IP (Internet Protocol) verze 6</span><span class="sxs-lookup"><span data-stu-id="4f57a-102">Internet Protocol Version 6</span></span>
<span data-ttu-id="4f57a-103">Internet Protocol verze 6 (IPv6) je nová sada standardních protokolů pro síťovou vrstvu Internetu.</span><span class="sxs-lookup"><span data-stu-id="4f57a-103">The Internet Protocol version 6 (IPv6) is a new suite of standard protocols for the network layer of the Internet.</span></span> <span data-ttu-id="4f57a-104">Protokol IPv6 je navržený tak, aby vyřešil mnohé z problémů aktuální verze Internet Protocol sady (označované jako IPv4) s ohledem na vyčerpání adres, zabezpečení, automatickou konfiguraci, rozšiřitelnost atd.</span><span class="sxs-lookup"><span data-stu-id="4f57a-104">IPv6 is designed to solve many of the problems of the current version of the Internet Protocol suite (known as IPv4) with regard to address depletion, security, auto-configuration, extensibility, and so on.</span></span> <span data-ttu-id="4f57a-105">Protokol IPv6 rozšiřuje možnosti Internetu, aby umožňoval nové typy aplikací, včetně peer-to-peer a mobilní aplikace.</span><span class="sxs-lookup"><span data-stu-id="4f57a-105">IPv6 expands the capabilities of the Internet to enable new kinds of applications, including peer-to-peer and mobile applications.</span></span> <span data-ttu-id="4f57a-106">V následujícím seznamu jsou uvedené hlavní problémy s aktuálním protokolem IPv4:</span><span class="sxs-lookup"><span data-stu-id="4f57a-106">The following are the main issues of the current IPv4 protocol:</span></span>  
  
- <span data-ttu-id="4f57a-107">Rychlá vyčerpání adresního prostoru.</span><span class="sxs-lookup"><span data-stu-id="4f57a-107">Rapid depletion of the address space.</span></span>  
  
     <span data-ttu-id="4f57a-108">To vedlo k použití překladatelů síťových adres (NAT), které mapují několik privátních adres na jednu veřejnou IP adresu.</span><span class="sxs-lookup"><span data-stu-id="4f57a-108">This has led to the use of Network Address Translators (NATs) that map multiple private addresses to a single public IP address.</span></span> <span data-ttu-id="4f57a-109">Hlavními problémy vytvořenými tímto mechanismem jsou režie zpracování a neexistují kompletní připojení.</span><span class="sxs-lookup"><span data-stu-id="4f57a-109">The main problems created by this mechanism are processing overhead and lack of end-to-end connectivity.</span></span>  
  
- <span data-ttu-id="4f57a-110">Nedostatečná podpora hierarchie.</span><span class="sxs-lookup"><span data-stu-id="4f57a-110">Lack of hierarchy support.</span></span>  
  
     <span data-ttu-id="4f57a-111">Vzhledem k předdefinované organizaci vaší organizace nemá protokol IPv4 true hierarchickou podporu.</span><span class="sxs-lookup"><span data-stu-id="4f57a-111">Because of its inherent predefined class organization, IPv4 lacks true hierarchical support.</span></span> <span data-ttu-id="4f57a-112">Není možné strukturovat IP adresy způsobem, který skutečně mapuje topologii sítě.</span><span class="sxs-lookup"><span data-stu-id="4f57a-112">It is impossible to structure the IP addresses in a way that truly maps the network topology.</span></span> <span data-ttu-id="4f57a-113">Tato zásadní návrhová chyba vytvoří potřebu rozsáhlých směrovacích tabulek pro doručování paketů IPv4 do libovolného umístění v Internetu.</span><span class="sxs-lookup"><span data-stu-id="4f57a-113">This crucial design flaw creates the need for large routing tables to deliver IPv4 packets to any location on the Internet.</span></span>  
  
- <span data-ttu-id="4f57a-114">Složitá konfigurace sítě.</span><span class="sxs-lookup"><span data-stu-id="4f57a-114">Complex network configuration.</span></span>  
  
     <span data-ttu-id="4f57a-115">S protokolem IPv4 musí být adresy přiřazeny staticky nebo pomocí konfiguračního protokolu, jako je například DHCP.</span><span class="sxs-lookup"><span data-stu-id="4f57a-115">With IPv4, addresses must be assigned statically or using a configuration protocol such as DHCP.</span></span> <span data-ttu-id="4f57a-116">V ideálním případě by se hostitelé neměli spoléhat na správu infrastruktury DHCP.</span><span class="sxs-lookup"><span data-stu-id="4f57a-116">In an ideal situation, hosts would not have to rely on the administration of a DHCP infrastructure.</span></span> <span data-ttu-id="4f57a-117">Místo toho by se daly nakonfigurovat na základě segmentu sítě, ve kterém se nacházejí.</span><span class="sxs-lookup"><span data-stu-id="4f57a-117">Instead, they would be able to configure themselves based on the network segment in which they are located.</span></span>  
  
- <span data-ttu-id="4f57a-118">Chybí integrované ověřování a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="4f57a-118">Lack of built-in authentication and confidentiality.</span></span>  
  
     <span data-ttu-id="4f57a-119">Protokol IPv4 nevyžaduje podporu žádného mechanismu, který poskytuje ověřování nebo šifrování vyměňovaných dat.</span><span class="sxs-lookup"><span data-stu-id="4f57a-119">IPv4 does not require the support for any mechanism that provides authentication or encryption of the exchanged data.</span></span> <span data-ttu-id="4f57a-120">Tato změna se projeví v protokolu IPv6.</span><span class="sxs-lookup"><span data-stu-id="4f57a-120">This changes with IPv6.</span></span> <span data-ttu-id="4f57a-121">Protokol IPSec (Internet Protocol Security) je požadavek na podporu IPv6.</span><span class="sxs-lookup"><span data-stu-id="4f57a-121">Internet Protocol security (IPSec) is an IPv6 support requirement.</span></span>  
  
 <span data-ttu-id="4f57a-122">Nová sada protokolů musí splňovat následující základní požadavky:</span><span class="sxs-lookup"><span data-stu-id="4f57a-122">A new protocol suite must satisfy the following basic requirements:</span></span>  
  
- <span data-ttu-id="4f57a-123">Velký rozsah směrování a adresování s nízkou režií.</span><span class="sxs-lookup"><span data-stu-id="4f57a-123">Large-scale routing and addressing with low overhead.</span></span>  
  
- <span data-ttu-id="4f57a-124">Automatická konfigurace v různých situacích připojení.</span><span class="sxs-lookup"><span data-stu-id="4f57a-124">Auto-configuration for various connecting situations.</span></span>  
  
- <span data-ttu-id="4f57a-125">Integrované ověřování a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="4f57a-125">Built-in authentication and confidentiality.</span></span>  
  
 <span data-ttu-id="4f57a-126">Další informace najdete v tématech [adresování IPv6](ipv6-addressing.md), [směrování IPv6](ipv6-routing.md), [Automatická konfigurace protokolu IPv6](ipv6-auto-configuration.md), [povolení a zakázání protokolu IPv6](enabling-and-disabling-ipv6.md)a [postupy: Úpravou konfiguračního souboru počítače povolte podporu](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md)protokolu IPv6.</span><span class="sxs-lookup"><span data-stu-id="4f57a-126">For more information, see [IPv6 Addressing](ipv6-addressing.md), [IPv6 Routing](ipv6-routing.md), [IPv6 Auto-Configuration](ipv6-auto-configuration.md), [Enabling and Disabling IPv6](enabling-and-disabling-ipv6.md), and [How to: Modify the Computer Configuration File to Enable IPv6 Support](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="4f57a-127">Odkazy</span><span class="sxs-lookup"><span data-stu-id="4f57a-127">References</span></span>  
 <span data-ttu-id="4f57a-128">V následující části jsou vybrané dokumenty RFC, které najdete na webu [IETF (Internet Engineering Task Force)](https://www.ietf.org/) :</span><span class="sxs-lookup"><span data-stu-id="4f57a-128">The following are selected RFC documents that you can find at the [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website:</span></span>  
  
- <span data-ttu-id="4f57a-129">RFC 1287, směrem k budoucí internetové architektuře.</span><span class="sxs-lookup"><span data-stu-id="4f57a-129">RFC 1287, Towards the Future Internet Architecture.</span></span>  
  
- <span data-ttu-id="4f57a-130">RFC 1454, porovnání návrhů pro další verzi protokolu IP.</span><span class="sxs-lookup"><span data-stu-id="4f57a-130">RFC 1454, Comparison of Proposals for Next Version of IP.</span></span>  
  
- <span data-ttu-id="4f57a-131">RFC 2373, Architektura adresování IP verze 6.</span><span class="sxs-lookup"><span data-stu-id="4f57a-131">RFC 2373, IP Version 6 Addressing Architecture.</span></span>  
  
- <span data-ttu-id="4f57a-132">RFC 2374: globální formát adresy jednosměrového vysílání IPv6, který je agregován.</span><span class="sxs-lookup"><span data-stu-id="4f57a-132">RFC 2374, An IPv6 Aggregatable Global Unicast Address Format.</span></span>  
  
 <span data-ttu-id="4f57a-133">Informace související s protokolem IPv6 najdete také v protokolu [IP verze 6 (IPv6)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29).</span><span class="sxs-lookup"><span data-stu-id="4f57a-133">You can also find IPv6-related information on the [IP Version 6 (IPv6)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f57a-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f57a-134">See also</span></span>

- [<span data-ttu-id="4f57a-135">Ukázka soketů IPv6</span><span class="sxs-lookup"><span data-stu-id="4f57a-135">IPv6 Sockets Sample</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms180981%28v=vs.85%29)
- [<span data-ttu-id="4f57a-136">Ukázky programování sítě</span><span class="sxs-lookup"><span data-stu-id="4f57a-136">Network Programming Samples</span></span>](network-programming-samples.md)
- [<span data-ttu-id="4f57a-137">Sokety</span><span class="sxs-lookup"><span data-stu-id="4f57a-137">Sockets</span></span>](sockets.md)
