---
title: Protokol IPv6
ms.date: 03/30/2017
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
ms.openlocfilehash: 6f956a8dc3e899012144ccf266a7cbe1c5f9dab4
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200004"
---
# <a name="internet-protocol-version-6"></a><span data-ttu-id="6745b-102">Protokol IPv6</span><span class="sxs-lookup"><span data-stu-id="6745b-102">Internet Protocol Version 6</span></span>
<span data-ttu-id="6745b-103">Internet Protocol verze 6 (IPv6) je nová sada standardních protokolů pro síťové vrstvy z Internetu.</span><span class="sxs-lookup"><span data-stu-id="6745b-103">The Internet Protocol version 6 (IPv6) is a new suite of standard protocols for the network layer of the Internet.</span></span> <span data-ttu-id="6745b-104">Protokol IPv6 je navržená k řešení mnoha problémů je aktuální verze sady Internet Protocol (označují se termínem IPv4) s ohledem na plnění vyčerpávání, zabezpečení, automatickou konfiguraci, rozšíření a tak dále.</span><span class="sxs-lookup"><span data-stu-id="6745b-104">IPv6 is designed to solve many of the problems of the current version of the Internet Protocol suite (known as IPv4) with regard to address depletion, security, auto-configuration, extensibility, and so on.</span></span> <span data-ttu-id="6745b-105">Protokol IPv6 se rozšiřují možnosti Internetu povolit nové typy aplikací, jako jsou třeba aplikace peer-to-peer a mobilní.</span><span class="sxs-lookup"><span data-stu-id="6745b-105">IPv6 expands the capabilities of the Internet to enable new kinds of applications, including peer-to-peer and mobile applications.</span></span> <span data-ttu-id="6745b-106">Toto jsou hlavní problémy aktuální protokolu IPv4:</span><span class="sxs-lookup"><span data-stu-id="6745b-106">The following are the main issues of the current IPv4 protocol:</span></span>  
  
-   <span data-ttu-id="6745b-107">Rychlé vyčerpání adresního prostoru.</span><span class="sxs-lookup"><span data-stu-id="6745b-107">Rapid depletion of the address space.</span></span>  
  
     <span data-ttu-id="6745b-108">To vedlo k využívání síťových adres (NAT), které mapují více privátních adres na jednu veřejnou IP adresu.</span><span class="sxs-lookup"><span data-stu-id="6745b-108">This has led to the use of Network Address Translators (NATs) that map multiple private addresses to a single public IP address.</span></span> <span data-ttu-id="6745b-109">Hlavní problémy, které vytvořil tento mechanismus zpracování režijní náklady a nedostupnosti začátku do konce.</span><span class="sxs-lookup"><span data-stu-id="6745b-109">The main problems created by this mechanism are processing overhead and lack of end-to-end connectivity.</span></span>  
  
-   <span data-ttu-id="6745b-110">Chybějící podpora hierarchie.</span><span class="sxs-lookup"><span data-stu-id="6745b-110">Lack of hierarchy support.</span></span>  
  
     <span data-ttu-id="6745b-111">Z důvodu jeho vlastní třídy předdefinovaného organizace nemá IPv4 true hierarchické podpory.</span><span class="sxs-lookup"><span data-stu-id="6745b-111">Because of its inherent predefined class organization, IPv4 lacks true hierarchical support.</span></span> <span data-ttu-id="6745b-112">Není možné strukturovat IP adres tak, aby skutečně mapy topologie sítě.</span><span class="sxs-lookup"><span data-stu-id="6745b-112">It is impossible to structure the IP addresses in a way that truly maps the network topology.</span></span> <span data-ttu-id="6745b-113">Tato chyba zásadní návrh vytvoří potřebné pro velké tabulky směrování k poskytování IPv4 paketů do jakéhokoli umístění na Internetu.</span><span class="sxs-lookup"><span data-stu-id="6745b-113">This crucial design flaw creates the need for large routing tables to deliver IPv4 packets to any location on the Internet.</span></span>  
  
-   <span data-ttu-id="6745b-114">Konfigurace složité sítě.</span><span class="sxs-lookup"><span data-stu-id="6745b-114">Complex network configuration.</span></span>  
  
     <span data-ttu-id="6745b-115">S podporou protokolu IPv4, musí být adresy staticky přiřadit nebo pomocí protokolu konfigurace, jako je DHCP.</span><span class="sxs-lookup"><span data-stu-id="6745b-115">With IPv4, addresses must be assigned statically or using a configuration protocol such as DHCP.</span></span> <span data-ttu-id="6745b-116">V ideálním případě by hostitelé nemusíte spoléhat na správu infrastruktury DHCP.</span><span class="sxs-lookup"><span data-stu-id="6745b-116">In an ideal situation, hosts would not have to rely on the administration of a DHCP infrastructure.</span></span> <span data-ttu-id="6745b-117">Místo toho by moct konfigurovat sami podle segmentu sítě, ve které se nacházejí.</span><span class="sxs-lookup"><span data-stu-id="6745b-117">Instead, they would be able to configure themselves based on the network segment in which they are located.</span></span>  
  
-   <span data-ttu-id="6745b-118">Chybějící integrované ověřování a zachováním důvěrnosti.</span><span class="sxs-lookup"><span data-stu-id="6745b-118">Lack of built-in authentication and confidentiality.</span></span>  
  
     <span data-ttu-id="6745b-119">IPv4 nevyžaduje podporu pro každý použitý mechanizmus, který poskytuje ověřování nebo výměnu dat šifrování.</span><span class="sxs-lookup"><span data-stu-id="6745b-119">IPv4 does not require the support for any mechanism that provides authentication or encryption of the exchanged data.</span></span> <span data-ttu-id="6745b-120">Tím se změní s protokolem IPv6.</span><span class="sxs-lookup"><span data-stu-id="6745b-120">This changes with IPv6.</span></span> <span data-ttu-id="6745b-121">Internet Protocol security (IPSec) je požadavek na podporu IPv6.</span><span class="sxs-lookup"><span data-stu-id="6745b-121">Internet Protocol security (IPSec) is an IPv6 support requirement.</span></span>  
  
 <span data-ttu-id="6745b-122">Nová sada protokolů musí splňovat základní požadavky na následující:</span><span class="sxs-lookup"><span data-stu-id="6745b-122">A new protocol suite must satisfy the following basic requirements:</span></span>  
  
-   <span data-ttu-id="6745b-123">Ve velkém měřítku směrování a adresování s nízkou režií.</span><span class="sxs-lookup"><span data-stu-id="6745b-123">Large-scale routing and addressing with low overhead.</span></span>  
  
-   <span data-ttu-id="6745b-124">Automatická konfigurace pro připojení různých situacích.</span><span class="sxs-lookup"><span data-stu-id="6745b-124">Auto-configuration for various connecting situations.</span></span>  
  
-   <span data-ttu-id="6745b-125">Integrované ověřování a zachováním důvěrnosti.</span><span class="sxs-lookup"><span data-stu-id="6745b-125">Built-in authentication and confidentiality.</span></span>  
  
 <span data-ttu-id="6745b-126">Další informace najdete v tématu [adresování IPv6](../../../docs/framework/network-programming/ipv6-addressing.md), [směrování IPv6](../../../docs/framework/network-programming/ipv6-routing.md), [automatickou konfiguraci protokolu IPv6](../../../docs/framework/network-programming/ipv6-auto-configuration.md), [povolení a zákaz IPv6](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md), a [Postupy: Úprava konfiguračního souboru počítače na povolení podpory IPv6](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span><span class="sxs-lookup"><span data-stu-id="6745b-126">For more information, see [IPv6 Addressing](../../../docs/framework/network-programming/ipv6-addressing.md), [IPv6 Routing](../../../docs/framework/network-programming/ipv6-routing.md), [IPv6 Auto-Configuration](../../../docs/framework/network-programming/ipv6-auto-configuration.md), [Enabling and Disabling IPv6](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md), and [How to: Modify the Computer Configuration File to Enable IPv6 Support](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="6745b-127">Odkazy</span><span class="sxs-lookup"><span data-stu-id="6745b-127">References</span></span>  
 <span data-ttu-id="6745b-128">Toto jsou vybrané dokumenty RFC, na které narazíte na [Engineering Task Force IETF (Internet)](https://www.ietf.org/) webu:</span><span class="sxs-lookup"><span data-stu-id="6745b-128">The following are selected RFC documents that you can find at the [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website:</span></span>  
  
-   <span data-ttu-id="6745b-129">RFC. 1287, směrem k architektuře budoucí Internet.</span><span class="sxs-lookup"><span data-stu-id="6745b-129">RFC 1287, Towards the Future Internet Architecture.</span></span>  
  
-   <span data-ttu-id="6745b-130">RFC 1454 porovnání návrhy na další verzi protokolu IP.</span><span class="sxs-lookup"><span data-stu-id="6745b-130">RFC 1454, Comparison of Proposals for Next Version of IP.</span></span>  
  
-   <span data-ttu-id="6745b-131">RFC 2373, Architektura adresování IP verze 6.</span><span class="sxs-lookup"><span data-stu-id="6745b-131">RFC 2373, IP Version 6 Addressing Architecture.</span></span>  
  
-   <span data-ttu-id="6745b-132">RFC 2374 formátu agregovatelné globální adresy jednosměrového vysílání IPv6.</span><span class="sxs-lookup"><span data-stu-id="6745b-132">RFC 2374, An IPv6 Aggregatable Global Unicast Address Format.</span></span>  
  
 <span data-ttu-id="6745b-133">Můžete také najít informace související s IPv6 na [IP verze 6 (IPv6)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29).</span><span class="sxs-lookup"><span data-stu-id="6745b-133">You can also find IPv6-related information on the [IP Version 6 (IPv6)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498%28v=ws.10%29).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6745b-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="6745b-134">See Also</span></span>  
 [<span data-ttu-id="6745b-135">Ukázka sokety IPv6</span><span class="sxs-lookup"><span data-stu-id="6745b-135">IPv6 Sockets Sample</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms180981%28v=vs.85%29)  
 [<span data-ttu-id="6745b-136">Ukázky programování sítě</span><span class="sxs-lookup"><span data-stu-id="6745b-136">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)  
 [<span data-ttu-id="6745b-137">Sokety</span><span class="sxs-lookup"><span data-stu-id="6745b-137">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
