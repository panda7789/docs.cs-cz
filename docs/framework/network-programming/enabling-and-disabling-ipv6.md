---
title: Povolení a zákaz IPv6
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
ms.openlocfilehash: 9dbbbbb522628de81be3d3d1382867de99c570d0
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183084"
---
# <a name="enabling-and-disabling-ipv6"></a><span data-ttu-id="7b1bd-102">Povolení a zákaz IPv6</span><span class="sxs-lookup"><span data-stu-id="7b1bd-102">Enabling and Disabling IPv6</span></span>
<span data-ttu-id="7b1bd-103">Pokud chcete použít protokol IPv6, ujistěte se, že používáte verzi operačního systému, který podporuje protokol IPv6 a zajistit správnou konfiguraci operačního systému a síťové třídy.</span><span class="sxs-lookup"><span data-stu-id="7b1bd-103">To use the IPv6 protocol, ensure that you are running a version of the operating system that supports IPv6 and ensure that the operating system and the networking classes are configured properly.</span></span>  
  
## <a name="configuration-steps"></a><span data-ttu-id="7b1bd-104">Postup konfigurace</span><span class="sxs-lookup"><span data-stu-id="7b1bd-104">Configuration Steps</span></span>  
 <span data-ttu-id="7b1bd-105">V následující tabulce jsou uvedeny různé konfigurace</span><span class="sxs-lookup"><span data-stu-id="7b1bd-105">The following table lists various configurations</span></span>  
  
|<span data-ttu-id="7b1bd-106">Operační systém podporující protokol IPv6?</span><span class="sxs-lookup"><span data-stu-id="7b1bd-106">Operating system IPv6-enabled?</span></span>|<span data-ttu-id="7b1bd-107">Síťové třídy povolen protokol IPv6?</span><span class="sxs-lookup"><span data-stu-id="7b1bd-107">Networking classes IPv6-enabled?</span></span>|<span data-ttu-id="7b1bd-108">Popis</span><span class="sxs-lookup"><span data-stu-id="7b1bd-108">Description</span></span>|  
|-------------------------------------|---------------------------------------|-----------------|  
|<span data-ttu-id="7b1bd-109">Ne</span><span class="sxs-lookup"><span data-stu-id="7b1bd-109">No</span></span>|<span data-ttu-id="7b1bd-110">Ne</span><span class="sxs-lookup"><span data-stu-id="7b1bd-110">No</span></span>|<span data-ttu-id="7b1bd-111">Můžete analyzovat adresy IPv6.</span><span class="sxs-lookup"><span data-stu-id="7b1bd-111">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="7b1bd-112">Ne</span><span class="sxs-lookup"><span data-stu-id="7b1bd-112">No</span></span>|<span data-ttu-id="7b1bd-113">Ano</span><span class="sxs-lookup"><span data-stu-id="7b1bd-113">Yes</span></span>|<span data-ttu-id="7b1bd-114">Můžete analyzovat adresy IPv6.</span><span class="sxs-lookup"><span data-stu-id="7b1bd-114">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="7b1bd-115">Ano</span><span class="sxs-lookup"><span data-stu-id="7b1bd-115">Yes</span></span>|<span data-ttu-id="7b1bd-116">Ne</span><span class="sxs-lookup"><span data-stu-id="7b1bd-116">No</span></span>|<span data-ttu-id="7b1bd-117">Můžete analyzovat adresy IPv6 a překládat adresy IPv6 pomocí metody rozlišování názvů není označená jako zastaralá.</span><span class="sxs-lookup"><span data-stu-id="7b1bd-117">Can parse IPv6 addresses and resolve IPv6 addresses using name resolution methods not marked obsolete.</span></span>|  
|<span data-ttu-id="7b1bd-118">Ano</span><span class="sxs-lookup"><span data-stu-id="7b1bd-118">Yes</span></span>|<span data-ttu-id="7b1bd-119">Ano</span><span class="sxs-lookup"><span data-stu-id="7b1bd-119">Yes</span></span>|<span data-ttu-id="7b1bd-120">Můžete analyzovat a řešit adres IPv6 pomocí všech metod, včetně těch, které označená jako zastaralá.</span><span class="sxs-lookup"><span data-stu-id="7b1bd-120">Can parse and resolve IPv6 addresses using all methods including those marked obsolete.</span></span>|  
  
 <span data-ttu-id="7b1bd-121">Mějte na paměti, že pokud chcete povolit podporu protokolu IPv6 pro všechny třídy v oboru názvů System.Net, je třeba upravit konfigurační soubor počítače nebo konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="7b1bd-121">Be aware that to enable the IPv6 support for all classes in the System.Net namespace, you must modify the computer configuration file or the configuration file for the application.</span></span> <span data-ttu-id="7b1bd-122">Konfigurační soubor aplikace má vyšší prioritu než konfigurační soubor počítače.</span><span class="sxs-lookup"><span data-stu-id="7b1bd-122">The configuration file for an application has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="7b1bd-123">Příklad toho, jak upravit konfigurační soubor počítače *machine.config*k povolení podpory naleznete v protokolu Ipv6, [postupy: Úprava konfiguračního souboru počítače na povolení podpory Ipv6](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span><span class="sxs-lookup"><span data-stu-id="7b1bd-123">For an example of how to modify the computer configuration file, *machine.config*, to enable Ipv6 support see, [How to: Modify the Computer Configuration File to Enable Ipv6 Support](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span> <span data-ttu-id="7b1bd-124">Také se ujistěte, že je povolena podpora protokolu IPv6 pro operační systém.</span><span class="sxs-lookup"><span data-stu-id="7b1bd-124">Also, ensure that the IPv6 support is enabled for the operating system.</span></span>  
  
 <span data-ttu-id="7b1bd-125">Rozhraní .NET Framework obsahuje konfigurační přepínač, nastavte v konfiguračním souboru následujícím způsobem</span><span class="sxs-lookup"><span data-stu-id="7b1bd-125">The .NET Framework has a configuration switch set in a configuration file as follows</span></span>  
  
```xml  
<system.net>…  
    <settings>…  
        <ipv6 enabled="true"/>…  
    </settings>…  
</system.net>  
```  
  
 <span data-ttu-id="7b1bd-126">Pro rozhraní .NET Framework verze 1.1 nebo starší, hodnota **podporuje protokol ipv6** konfigurační přepínač určuje, zda členové <xref:System.Net.Dns?displayProperty=nameWithType> třídy zpáteční adresu IPv6.</span><span class="sxs-lookup"><span data-stu-id="7b1bd-126">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="7b1bd-127">Pro rozhraní .NET Framework verze 2.0 nebo novější, pokud Windows podporuje protokol IPv6 a členy <xref:System.Net.Dns?displayProperty=nameWithType> třídy, (například <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> metoda), vrátí adresy IPv6 s jediným omezením.</span><span class="sxs-lookup"><span data-stu-id="7b1bd-127">For .NET Framework version 2.0 and later, if Windows supports IPv6, then members of the <xref:System.Net.Dns?displayProperty=nameWithType> class, (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="7b1bd-128">Zastaralé členy DNS <xref:System.Net.Dns?displayProperty=nameWithType> (například <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> metoda) přečte a rozpoznat hodnotu v konfiguračním souboru pro nastavení podporuje protokol ipv6.</span><span class="sxs-lookup"><span data-stu-id="7b1bd-128">Obsolete members of the DNS <xref:System.Net.Dns?displayProperty=nameWithType> (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file for the ipv6 enabled setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b1bd-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b1bd-129">See Also</span></span>  
 [<span data-ttu-id="7b1bd-130">Protokol IP (Internet Protocol) verze 6</span><span class="sxs-lookup"><span data-stu-id="7b1bd-130">Internet Protocol Version 6</span></span>](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [<span data-ttu-id="7b1bd-131">Sokety</span><span class="sxs-lookup"><span data-stu-id="7b1bd-131">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)  
 [<span data-ttu-id="7b1bd-132">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="7b1bd-132">Network Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [<span data-ttu-id="7b1bd-133">\<IPv6 > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="7b1bd-133">\<ipv6> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
