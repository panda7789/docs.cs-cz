---
title: Protokol IP verze 6
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 333fbb452cb1f24b5e62d1106eff4560b26267b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="internet-protocol-version-6"></a><span data-ttu-id="cefb0-102">Protokol IP verze 6</span><span class="sxs-lookup"><span data-stu-id="cefb0-102">Internet Protocol Version 6</span></span>
<span data-ttu-id="cefb0-103">Internet Protocol version 6 (IPv6) je nová sada standardních protokolů pro síťovou vrstvou sítě Internet.</span><span class="sxs-lookup"><span data-stu-id="cefb0-103">The Internet Protocol version 6 (IPv6) is a new suite of standard protocols for the network layer of the Internet.</span></span> <span data-ttu-id="cefb0-104">Protokol IPv6 je proto, aby vyřešila mnohé z problémů aktuální verze sady Internet Protocol (známé jako IPv4) s ohledem na adrese spotřebovávat, zabezpečení, automatická konfigurace, rozšíření a tak dále.</span><span class="sxs-lookup"><span data-stu-id="cefb0-104">IPv6 is designed to solve many of the problems of the current version of the Internet Protocol suite (known as IPv4) with regard to address depletion, security, auto-configuration, extensibility, and so on.</span></span> <span data-ttu-id="cefb0-105">IPv6 rozšíří možnosti Internetu povolit nové typy aplikací, včetně peer-to-peer a mobilních aplikací.</span><span class="sxs-lookup"><span data-stu-id="cefb0-105">IPv6 expands the capabilities of the Internet to enable new kinds of applications, including peer-to-peer and mobile applications.</span></span> <span data-ttu-id="cefb0-106">Tady jsou hlavní problémy aktuální protokolu IPv4:</span><span class="sxs-lookup"><span data-stu-id="cefb0-106">The following are the main issues of the current IPv4 protocol:</span></span>  
  
-   <span data-ttu-id="cefb0-107">Rychlé spotřebovávat adresního prostoru.</span><span class="sxs-lookup"><span data-stu-id="cefb0-107">Rapid depletion of the address space.</span></span>  
  
     <span data-ttu-id="cefb0-108">To vedlo k použití síťových adres (NAT), mapovat více soukromých adres na jednu veřejnou IP adresu.</span><span class="sxs-lookup"><span data-stu-id="cefb0-108">This has led to the use of Network Address Translators (NATs) that map multiple private addresses to a single public IP address.</span></span> <span data-ttu-id="cefb0-109">Hlavní problémy, které tento mechanismus jsou zpracování režii a nedostatku možností připojení klient server.</span><span class="sxs-lookup"><span data-stu-id="cefb0-109">The main problems created by this mechanism are processing overhead and lack of end-to-end connectivity.</span></span>  
  
-   <span data-ttu-id="cefb0-110">Nedostatečná podpora hierarchie.</span><span class="sxs-lookup"><span data-stu-id="cefb0-110">Lack of hierarchy support.</span></span>  
  
     <span data-ttu-id="cefb0-111">Z důvodu jeho organizaci vyplývajících předdefinované třída chybí IPv4 true hierarchické podpory.</span><span class="sxs-lookup"><span data-stu-id="cefb0-111">Because of its inherent predefined class organization, IPv4 lacks true hierarchical support.</span></span> <span data-ttu-id="cefb0-112">Není možné struktury IP adresy způsobem, který skutečně mapuje síťové topologie.</span><span class="sxs-lookup"><span data-stu-id="cefb0-112">It is impossible to structure the IP addresses in a way that truly maps the network topology.</span></span> <span data-ttu-id="cefb0-113">Tato chyba zásadní návrh vytvoří potřebu rozsáhlé směrovací tabulky pro doručování paketů IPv4 do libovolného umístění na Internetu.</span><span class="sxs-lookup"><span data-stu-id="cefb0-113">This crucial design flaw creates the need for large routing tables to deliver IPv4 packets to any location on the Internet.</span></span>  
  
-   <span data-ttu-id="cefb0-114">Konfigurace nejsložitějších sítí.</span><span class="sxs-lookup"><span data-stu-id="cefb0-114">Complex network configuration.</span></span>  
  
     <span data-ttu-id="cefb0-115">S IPv4, musí staticky přiřazené adresy nebo protokol konfigurace například DHCP.</span><span class="sxs-lookup"><span data-stu-id="cefb0-115">With IPv4, addresses must be assigned statically or using a configuration protocol such as DHCP.</span></span> <span data-ttu-id="cefb0-116">V ideálním případě hostitelů neměli spoléhat na správu infrastruktury DHCP.</span><span class="sxs-lookup"><span data-stu-id="cefb0-116">In an ideal situation, hosts would not have to rely on the administration of a DHCP infrastructure.</span></span> <span data-ttu-id="cefb0-117">Místo toho se bude moct konfigurovat sami podle segmentu sítě, ve které se nacházejí.</span><span class="sxs-lookup"><span data-stu-id="cefb0-117">Instead, they would be able to configure themselves based on the network segment in which they are located.</span></span>  
  
-   <span data-ttu-id="cefb0-118">Chybí integrované ověřování a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="cefb0-118">Lack of built-in authentication and confidentiality.</span></span>  
  
     <span data-ttu-id="cefb0-119">IPv4 nevyžaduje pro všechny mechanismus, který poskytuje ověřování nebo šifrování výměně dat na technickou podporu.</span><span class="sxs-lookup"><span data-stu-id="cefb0-119">IPv4 does not require the support for any mechanism that provides authentication or encryption of the exchanged data.</span></span> <span data-ttu-id="cefb0-120">Tato operace změní s IPv6.</span><span class="sxs-lookup"><span data-stu-id="cefb0-120">This changes with IPv6.</span></span> <span data-ttu-id="cefb0-121">Internet Protocol security (IPSec) je požadavek na podporu IPv6.</span><span class="sxs-lookup"><span data-stu-id="cefb0-121">Internet Protocol security (IPSec) is an IPv6 support requirement.</span></span>  
  
 <span data-ttu-id="cefb0-122">Nová sada protokolů musí splňovat základní požadavky na následující:</span><span class="sxs-lookup"><span data-stu-id="cefb0-122">A new protocol suite must satisfy the following basic requirements:</span></span>  
  
-   <span data-ttu-id="cefb0-123">Ve velkém měřítku směrování a adresování s nízkou režii.</span><span class="sxs-lookup"><span data-stu-id="cefb0-123">Large-scale routing and addressing with low overhead.</span></span>  
  
-   <span data-ttu-id="cefb0-124">Automatická konfigurace pro různé situace připojování.</span><span class="sxs-lookup"><span data-stu-id="cefb0-124">Auto-configuration for various connecting situations.</span></span>  
  
-   <span data-ttu-id="cefb0-125">Integrované ověřování a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="cefb0-125">Built-in authentication and confidentiality.</span></span>  
  
 <span data-ttu-id="cefb0-126">Další informace najdete v tématu [adresách IPv6](../../../docs/framework/network-programming/ipv6-addressing.md), [směrování IPv6](../../../docs/framework/network-programming/ipv6-routing.md), [automatické konfigurace protokolu IPv6](../../../docs/framework/network-programming/ipv6-auto-configuration.md), [povolení a zakázání IPv6](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md), a [Postup: Upravte konfigurační soubor počítače. Chcete-li povolit podporu IPv6](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span><span class="sxs-lookup"><span data-stu-id="cefb0-126">For more information, see [IPv6 Addressing](../../../docs/framework/network-programming/ipv6-addressing.md), [IPv6 Routing](../../../docs/framework/network-programming/ipv6-routing.md), [IPv6 Auto-Configuration](../../../docs/framework/network-programming/ipv6-auto-configuration.md), [Enabling and Disabling IPv6](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md), and [How to: Modify the Computer Configuration File to Enable IPv6 Support](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="cefb0-127">Odkazy</span><span class="sxs-lookup"><span data-stu-id="cefb0-127">References</span></span>  
 <span data-ttu-id="cefb0-128">Následují vybrané dokumenty RFC, které můžete najít na webu Internet Engineering Task Force ([http://www.ietf.org](http://www.ietf.org/)):</span><span class="sxs-lookup"><span data-stu-id="cefb0-128">The following are selected RFC documents that you can find at the Internet Engineering Task Force site ([http://www.ietf.org](http://www.ietf.org/)):</span></span>  
  
-   <span data-ttu-id="cefb0-129">RFC. 1287, směrem k architektuře budoucí Internetu.</span><span class="sxs-lookup"><span data-stu-id="cefb0-129">RFC 1287, Towards the Future Internet Architecture.</span></span>  
  
-   <span data-ttu-id="cefb0-130">RFC 1454 porovnání návrhy na další verzi protokolu IP.</span><span class="sxs-lookup"><span data-stu-id="cefb0-130">RFC 1454, Comparison of Proposals for Next Version of IP.</span></span>  
  
-   <span data-ttu-id="cefb0-131">RFC 2373, Architektura adresování IP verze 6.</span><span class="sxs-lookup"><span data-stu-id="cefb0-131">RFC 2373, IP Version 6 Addressing Architecture.</span></span>  
  
-   <span data-ttu-id="cefb0-132">RFC 2374, formátu agregovatelné globální adresy jednosměrového vysílání IPv6.</span><span class="sxs-lookup"><span data-stu-id="cefb0-132">RFC 2374, An IPv6 Aggregatable Global Unicast Address Format.</span></span>  
  
 <span data-ttu-id="cefb0-133">Můžete také najít informace týkající se IPv6 na [IPv6 oblast na webu Technet](http://go.microsoft.com/fwlink/?LinkID=179658).</span><span class="sxs-lookup"><span data-stu-id="cefb0-133">You can also find IPv6-related information on the [IPv6 area on Technet](http://go.microsoft.com/fwlink/?LinkID=179658).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cefb0-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="cefb0-134">See Also</span></span>  
 [<span data-ttu-id="cefb0-135">Ukázka Sockets IPv6</span><span class="sxs-lookup"><span data-stu-id="cefb0-135">IPv6 Sockets Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179568)  
 [<span data-ttu-id="cefb0-136">Ukázky programování sítě</span><span class="sxs-lookup"><span data-stu-id="cefb0-136">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)  
 [<span data-ttu-id="cefb0-137">Sokety</span><span class="sxs-lookup"><span data-stu-id="cefb0-137">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
