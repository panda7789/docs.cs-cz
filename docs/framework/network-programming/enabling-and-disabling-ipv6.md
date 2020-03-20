---
title: Povolení a zákaz IPv6
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
ms.openlocfilehash: 66c802dd5feb865faf7469cb7da04fbffcb4a2d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048566"
---
# <a name="enabling-and-disabling-ipv6"></a><span data-ttu-id="580f3-102">Povolení a zákaz IPv6</span><span class="sxs-lookup"><span data-stu-id="580f3-102">Enabling and Disabling IPv6</span></span>
<span data-ttu-id="580f3-103">Chcete-li použít protokol IPv6, ujistěte se, že používáte verzi operačního systému, která podporuje protokol IPv6, a ujistěte se, že jsou správně nakonfigurovány třídy operačního systému a sítě.</span><span class="sxs-lookup"><span data-stu-id="580f3-103">To use the IPv6 protocol, ensure that you are running a version of the operating system that supports IPv6 and ensure that the operating system and the networking classes are configured properly.</span></span>  
  
## <a name="configuration-steps"></a><span data-ttu-id="580f3-104">Kroky konfigurace</span><span class="sxs-lookup"><span data-stu-id="580f3-104">Configuration Steps</span></span>  
 <span data-ttu-id="580f3-105">V následující tabulce jsou uvedeny různé konfigurace</span><span class="sxs-lookup"><span data-stu-id="580f3-105">The following table lists various configurations</span></span>  
  
|<span data-ttu-id="580f3-106">Operační systém s podporou IPv6?</span><span class="sxs-lookup"><span data-stu-id="580f3-106">Operating system IPv6-enabled?</span></span>|<span data-ttu-id="580f3-107">Síťové třídy s podporou IPv6?</span><span class="sxs-lookup"><span data-stu-id="580f3-107">Networking classes IPv6-enabled?</span></span>|<span data-ttu-id="580f3-108">Popis</span><span class="sxs-lookup"><span data-stu-id="580f3-108">Description</span></span>|  
|-------------------------------------|---------------------------------------|-----------------|  
|<span data-ttu-id="580f3-109">Ne</span><span class="sxs-lookup"><span data-stu-id="580f3-109">No</span></span>|<span data-ttu-id="580f3-110">Ne</span><span class="sxs-lookup"><span data-stu-id="580f3-110">No</span></span>|<span data-ttu-id="580f3-111">Může analyzovat adresy IPv6.</span><span class="sxs-lookup"><span data-stu-id="580f3-111">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="580f3-112">Ne</span><span class="sxs-lookup"><span data-stu-id="580f3-112">No</span></span>|<span data-ttu-id="580f3-113">Ano</span><span class="sxs-lookup"><span data-stu-id="580f3-113">Yes</span></span>|<span data-ttu-id="580f3-114">Může analyzovat adresy IPv6.</span><span class="sxs-lookup"><span data-stu-id="580f3-114">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="580f3-115">Ano</span><span class="sxs-lookup"><span data-stu-id="580f3-115">Yes</span></span>|<span data-ttu-id="580f3-116">Ne</span><span class="sxs-lookup"><span data-stu-id="580f3-116">No</span></span>|<span data-ttu-id="580f3-117">Může analyzovat adresy IPv6 a vyřešit adresy IPv6 pomocí metod překladu názvů, které nejsou označeny jako zastaralé.</span><span class="sxs-lookup"><span data-stu-id="580f3-117">Can parse IPv6 addresses and resolve IPv6 addresses using name resolution methods not marked obsolete.</span></span>|  
|<span data-ttu-id="580f3-118">Ano</span><span class="sxs-lookup"><span data-stu-id="580f3-118">Yes</span></span>|<span data-ttu-id="580f3-119">Ano</span><span class="sxs-lookup"><span data-stu-id="580f3-119">Yes</span></span>|<span data-ttu-id="580f3-120">Může analyzovat a vyřešit adresy IPv6 pomocí všech metod, včetně těch, které jsou označeny jako zastaralé.</span><span class="sxs-lookup"><span data-stu-id="580f3-120">Can parse and resolve IPv6 addresses using all methods including those marked obsolete.</span></span>|  
  
 <span data-ttu-id="580f3-121">Uvědomte si, že chcete-li povolit podporu Protokolu IPv6 pro všechny třídy v oboru názvů System.Net, je nutné upravit konfigurační soubor počítače nebo konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="580f3-121">Be aware that to enable the IPv6 support for all classes in the System.Net namespace, you must modify the computer configuration file or the configuration file for the application.</span></span> <span data-ttu-id="580f3-122">Konfigurační soubor aplikace má přednost před konfiguračním souborem počítače.</span><span class="sxs-lookup"><span data-stu-id="580f3-122">The configuration file for an application has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="580f3-123">Příklad úpravy konfiguračního souboru počítače *machine.config*, který umožňuje podporu protokolu Ipv6, naleznete v [tématu Jak: Úprava konfiguračního souboru počítače pro povolení podpory ipv6](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span><span class="sxs-lookup"><span data-stu-id="580f3-123">For an example of how to modify the computer configuration file, *machine.config*, to enable Ipv6 support see, [How to: Modify the Computer Configuration File to Enable Ipv6 Support](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span> <span data-ttu-id="580f3-124">Také se ujistěte, že je povolena podpora IPv6 pro operační systém.</span><span class="sxs-lookup"><span data-stu-id="580f3-124">Also, ensure that the IPv6 support is enabled for the operating system.</span></span>  
  
 <span data-ttu-id="580f3-125">Rozhraní .NET Framework má konfigurační přepínač nastavený v konfiguračním souboru následujícím způsobem</span><span class="sxs-lookup"><span data-stu-id="580f3-125">The .NET Framework has a configuration switch set in a configuration file as follows</span></span>  
  
```xml  
<system.net>  
  ...  
  <settings>  
    ...  
    <ipv6 enabled="true"/>  
    ...  
  </settings>  
  ...  
</system.net>  
```  
  
 <span data-ttu-id="580f3-126">Pro rozhraní .NET Framework verze 1.1 a starší hodnota konfiguračního <xref:System.Net.Dns?displayProperty=nameWithType> přepínače **s povolenou protokolem ipv6** určuje, zda členové třídy vrátí adresy IPv6.</span><span class="sxs-lookup"><span data-stu-id="580f3-126">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="580f3-127">Pro rozhraní .NET Framework verze 2.0 a novější, pokud systém <xref:System.Net.Dns?displayProperty=nameWithType> Windows podporuje Protokol <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> IPv6, vrátí členové třídy (například metoda) adresy IPv6 s jedním omezením.</span><span class="sxs-lookup"><span data-stu-id="580f3-127">For .NET Framework version 2.0 and later, if Windows supports IPv6, then members of the <xref:System.Net.Dns?displayProperty=nameWithType> class, (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="580f3-128">Zastaralé členy služby DNS <xref:System.Net.Dns?displayProperty=nameWithType> (například <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> metoda) přečtou a rozpozná hodnotu v konfiguračním souboru pro nastavení s povolenou službou ipv6.</span><span class="sxs-lookup"><span data-stu-id="580f3-128">Obsolete members of the DNS <xref:System.Net.Dns?displayProperty=nameWithType> (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file for the ipv6 enabled setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="580f3-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="580f3-129">See also</span></span>

- [<span data-ttu-id="580f3-130">Protokol IP (Internet Protocol) verze 6</span><span class="sxs-lookup"><span data-stu-id="580f3-130">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)
- [<span data-ttu-id="580f3-131">Sokety</span><span class="sxs-lookup"><span data-stu-id="580f3-131">Sockets</span></span>](sockets.md)
- [<span data-ttu-id="580f3-132">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="580f3-132">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="580f3-133">\<Ipv6> Element (Nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="580f3-133">\<ipv6> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
