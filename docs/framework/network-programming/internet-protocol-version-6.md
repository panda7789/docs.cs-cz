---
title: Protokol IP (Internet Protocol) verze 6
description: Přečtěte si o protokolu IPv6 a o tom, jak se liší od protokolu IPv4. .NET Framework aplikace podporují protokol IPv6, ale můžou vyžadovat konfiguraci.
ms.date: 03/30/2017
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
ms.openlocfilehash: dd8b0b26e449fba7479d2678aff25ed49e721a90
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502389"
---
# <a name="internet-protocol-version-6"></a><span data-ttu-id="65976-104">Protokol IP (Internet Protocol) verze 6</span><span class="sxs-lookup"><span data-stu-id="65976-104">Internet Protocol Version 6</span></span>
<span data-ttu-id="65976-105">Internet Protocol verze 6 (IPv6) je nová sada standardních protokolů pro síťovou vrstvu Internetu.</span><span class="sxs-lookup"><span data-stu-id="65976-105">The Internet Protocol version 6 (IPv6) is a new suite of standard protocols for the network layer of the Internet.</span></span> <span data-ttu-id="65976-106">Protokol IPv6 je navržený tak, aby vyřešil mnohé z problémů aktuální verze Internet Protocol sady (označované jako IPv4) s ohledem na vyčerpání adres, zabezpečení, automatickou konfiguraci, rozšiřitelnost atd.</span><span class="sxs-lookup"><span data-stu-id="65976-106">IPv6 is designed to solve many of the problems of the current version of the Internet Protocol suite (known as IPv4) with regard to address depletion, security, auto-configuration, extensibility, and so on.</span></span> <span data-ttu-id="65976-107">Protokol IPv6 rozšiřuje možnosti Internetu, aby umožňoval nové typy aplikací, včetně peer-to-peer a mobilní aplikace.</span><span class="sxs-lookup"><span data-stu-id="65976-107">IPv6 expands the capabilities of the Internet to enable new kinds of applications, including peer-to-peer and mobile applications.</span></span> <span data-ttu-id="65976-108">V následujícím seznamu jsou uvedené hlavní problémy s aktuálním protokolem IPv4:</span><span class="sxs-lookup"><span data-stu-id="65976-108">The following are the main issues of the current IPv4 protocol:</span></span>  
  
- <span data-ttu-id="65976-109">Rychlá vyčerpání adresního prostoru.</span><span class="sxs-lookup"><span data-stu-id="65976-109">Rapid depletion of the address space.</span></span>  
  
     <span data-ttu-id="65976-110">To vedlo k použití překladatelů síťových adres (NAT), které mapují několik privátních adres na jednu veřejnou IP adresu.</span><span class="sxs-lookup"><span data-stu-id="65976-110">This has led to the use of Network Address Translators (NATs) that map multiple private addresses to a single public IP address.</span></span> <span data-ttu-id="65976-111">Hlavními problémy vytvořenými tímto mechanismem jsou režie zpracování a neexistují kompletní připojení.</span><span class="sxs-lookup"><span data-stu-id="65976-111">The main problems created by this mechanism are processing overhead and lack of end-to-end connectivity.</span></span>  
  
- <span data-ttu-id="65976-112">Nedostatečná podpora hierarchie.</span><span class="sxs-lookup"><span data-stu-id="65976-112">Lack of hierarchy support.</span></span>  
  
     <span data-ttu-id="65976-113">Vzhledem k předdefinované organizaci vaší organizace nemá protokol IPv4 true hierarchickou podporu.</span><span class="sxs-lookup"><span data-stu-id="65976-113">Because of its inherent predefined class organization, IPv4 lacks true hierarchical support.</span></span> <span data-ttu-id="65976-114">Není možné strukturovat IP adresy způsobem, který skutečně mapuje topologii sítě.</span><span class="sxs-lookup"><span data-stu-id="65976-114">It is impossible to structure the IP addresses in a way that truly maps the network topology.</span></span> <span data-ttu-id="65976-115">Tato zásadní návrhová chyba vytvoří potřebu rozsáhlých směrovacích tabulek pro doručování paketů IPv4 do libovolného umístění v Internetu.</span><span class="sxs-lookup"><span data-stu-id="65976-115">This crucial design flaw creates the need for large routing tables to deliver IPv4 packets to any location on the Internet.</span></span>  
  
- <span data-ttu-id="65976-116">Složitá konfigurace sítě.</span><span class="sxs-lookup"><span data-stu-id="65976-116">Complex network configuration.</span></span>  
  
     <span data-ttu-id="65976-117">S protokolem IPv4 musí být adresy přiřazeny staticky nebo pomocí konfiguračního protokolu, jako je například DHCP.</span><span class="sxs-lookup"><span data-stu-id="65976-117">With IPv4, addresses must be assigned statically or using a configuration protocol such as DHCP.</span></span> <span data-ttu-id="65976-118">V ideálním případě by se hostitelé neměli spoléhat na správu infrastruktury DHCP.</span><span class="sxs-lookup"><span data-stu-id="65976-118">In an ideal situation, hosts would not have to rely on the administration of a DHCP infrastructure.</span></span> <span data-ttu-id="65976-119">Místo toho by se daly nakonfigurovat na základě segmentu sítě, ve kterém se nacházejí.</span><span class="sxs-lookup"><span data-stu-id="65976-119">Instead, they would be able to configure themselves based on the network segment in which they are located.</span></span>  
  
- <span data-ttu-id="65976-120">Chybí integrované ověřování a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="65976-120">Lack of built-in authentication and confidentiality.</span></span>  
  
     <span data-ttu-id="65976-121">Protokol IPv4 nevyžaduje podporu žádného mechanismu, který poskytuje ověřování nebo šifrování vyměňovaných dat.</span><span class="sxs-lookup"><span data-stu-id="65976-121">IPv4 does not require the support for any mechanism that provides authentication or encryption of the exchanged data.</span></span> <span data-ttu-id="65976-122">Tato změna se projeví v protokolu IPv6.</span><span class="sxs-lookup"><span data-stu-id="65976-122">This changes with IPv6.</span></span> <span data-ttu-id="65976-123">Protokol IPSec (Internet Protocol Security) je požadavek na podporu IPv6.</span><span class="sxs-lookup"><span data-stu-id="65976-123">Internet Protocol security (IPSec) is an IPv6 support requirement.</span></span>  
  
 <span data-ttu-id="65976-124">Nová sada protokolů musí splňovat následující základní požadavky:</span><span class="sxs-lookup"><span data-stu-id="65976-124">A new protocol suite must satisfy the following basic requirements:</span></span>  
  
- <span data-ttu-id="65976-125">Velký rozsah směrování a adresování s nízkou režií.</span><span class="sxs-lookup"><span data-stu-id="65976-125">Large-scale routing and addressing with low overhead.</span></span>  
  
- <span data-ttu-id="65976-126">Automatická konfigurace v různých situacích připojení.</span><span class="sxs-lookup"><span data-stu-id="65976-126">Auto-configuration for various connecting situations.</span></span>  
  
- <span data-ttu-id="65976-127">Integrované ověřování a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="65976-127">Built-in authentication and confidentiality.</span></span>  
  
 <span data-ttu-id="65976-128">Další informace najdete v tématech [adresování IPv6](ipv6-addressing.md), [směrování IPv6](ipv6-routing.md), [Automatická konfigurace protokolu IPv6](ipv6-auto-configuration.md), [povolení a zakázání protokolu IPv6](enabling-and-disabling-ipv6.md)a [Postupy: Změna konfiguračního souboru počítače na povolení podpory protokolu IPv6](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span><span class="sxs-lookup"><span data-stu-id="65976-128">For more information, see [IPv6 Addressing](ipv6-addressing.md), [IPv6 Routing](ipv6-routing.md), [IPv6 Auto-Configuration](ipv6-auto-configuration.md), [Enabling and Disabling IPv6](enabling-and-disabling-ipv6.md), and [How to: Modify the Computer Configuration File to Enable IPv6 Support](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="65976-129">Odkazy</span><span class="sxs-lookup"><span data-stu-id="65976-129">References</span></span>  
 <span data-ttu-id="65976-130">V následující části jsou vybrané dokumenty RFC, které najdete na webu [IETF (Internet Engineering Task Force)](https://www.ietf.org/) :</span><span class="sxs-lookup"><span data-stu-id="65976-130">The following are selected RFC documents that you can find at the [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website:</span></span>  
  
- <span data-ttu-id="65976-131">RFC 1287, směrem k budoucí internetové architektuře.</span><span class="sxs-lookup"><span data-stu-id="65976-131">RFC 1287, Towards the Future Internet Architecture.</span></span>  
  
- <span data-ttu-id="65976-132">RFC 1454, porovnání návrhů pro další verzi protokolu IP.</span><span class="sxs-lookup"><span data-stu-id="65976-132">RFC 1454, Comparison of Proposals for Next Version of IP.</span></span>  
  
- <span data-ttu-id="65976-133">RFC 2373, Architektura adresování IP verze 6.</span><span class="sxs-lookup"><span data-stu-id="65976-133">RFC 2373, IP Version 6 Addressing Architecture.</span></span>  
  
- <span data-ttu-id="65976-134">RFC 2374: globální formát adresy jednosměrového vysílání IPv6, který je agregován.</span><span class="sxs-lookup"><span data-stu-id="65976-134">RFC 2374, An IPv6 Aggregatable Global Unicast Address Format.</span></span>  
  
 <span data-ttu-id="65976-135">Informace související s protokolem IPv6 najdete také v protokolu [IP verze 6 (IPv6)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29).</span><span class="sxs-lookup"><span data-stu-id="65976-135">You can also find IPv6-related information on the [IP Version 6 (IPv6)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65976-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65976-136">See also</span></span>

- [<span data-ttu-id="65976-137">Ukázka soketů IPv6</span><span class="sxs-lookup"><span data-stu-id="65976-137">IPv6 Sockets Sample</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms180981%28v=vs.85%29)
- [<span data-ttu-id="65976-138">Ukázky programování sítě</span><span class="sxs-lookup"><span data-stu-id="65976-138">Network Programming Samples</span></span>](network-programming-samples.md)
- [<span data-ttu-id="65976-139">Sokety</span><span class="sxs-lookup"><span data-stu-id="65976-139">Sockets</span></span>](sockets.md)
