---
title: Povolení a zákaz IPv6
description: Pomocí těchto kroků konfigurace povolte použití protokolu IPv6, včetně úprav konfiguračního souboru pro počítač nebo aplikaci.
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
ms.openlocfilehash: 7729647b09df20a98d5d639a641cb0a31f557330
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502610"
---
# <a name="enabling-and-disabling-ipv6"></a><span data-ttu-id="7b972-103">Povolení a zákaz IPv6</span><span class="sxs-lookup"><span data-stu-id="7b972-103">Enabling and Disabling IPv6</span></span>
<span data-ttu-id="7b972-104">Chcete-li použít protokol IPv6, ujistěte se, že používáte verzi operačního systému, která podporuje protokol IPv6, a ujistěte se, že jsou správně nakonfigurovány operační systém a síťové třídy.</span><span class="sxs-lookup"><span data-stu-id="7b972-104">To use the IPv6 protocol, ensure that you are running a version of the operating system that supports IPv6 and ensure that the operating system and the networking classes are configured properly.</span></span>  
  
## <a name="configuration-steps"></a><span data-ttu-id="7b972-105">Kroky konfigurace</span><span class="sxs-lookup"><span data-stu-id="7b972-105">Configuration Steps</span></span>  
 <span data-ttu-id="7b972-106">V následující tabulce jsou uvedeny různé konfigurace</span><span class="sxs-lookup"><span data-stu-id="7b972-106">The following table lists various configurations</span></span>  
  
|<span data-ttu-id="7b972-107">Je povolený protokol IPv6 operačního systému?</span><span class="sxs-lookup"><span data-stu-id="7b972-107">Operating system IPv6-enabled?</span></span>|<span data-ttu-id="7b972-108">Síťové třídy podporující protokol IPv6?</span><span class="sxs-lookup"><span data-stu-id="7b972-108">Networking classes IPv6-enabled?</span></span>|<span data-ttu-id="7b972-109">Description</span><span class="sxs-lookup"><span data-stu-id="7b972-109">Description</span></span>|  
|-------------------------------------|---------------------------------------|-----------------|  
|<span data-ttu-id="7b972-110">Ne</span><span class="sxs-lookup"><span data-stu-id="7b972-110">No</span></span>|<span data-ttu-id="7b972-111">Ne</span><span class="sxs-lookup"><span data-stu-id="7b972-111">No</span></span>|<span data-ttu-id="7b972-112">Může analyzovat adresy IPv6.</span><span class="sxs-lookup"><span data-stu-id="7b972-112">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="7b972-113">No</span><span class="sxs-lookup"><span data-stu-id="7b972-113">No</span></span>|<span data-ttu-id="7b972-114">Ano</span><span class="sxs-lookup"><span data-stu-id="7b972-114">Yes</span></span>|<span data-ttu-id="7b972-115">Může analyzovat adresy IPv6.</span><span class="sxs-lookup"><span data-stu-id="7b972-115">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="7b972-116">Ano</span><span class="sxs-lookup"><span data-stu-id="7b972-116">Yes</span></span>|<span data-ttu-id="7b972-117">Ne</span><span class="sxs-lookup"><span data-stu-id="7b972-117">No</span></span>|<span data-ttu-id="7b972-118">Dokáže analyzovat adresy IPv6 a překládat adresy IPv6 pomocí metod překladu názvů, které nejsou označené jako zastaralé.</span><span class="sxs-lookup"><span data-stu-id="7b972-118">Can parse IPv6 addresses and resolve IPv6 addresses using name resolution methods not marked obsolete.</span></span>|  
|<span data-ttu-id="7b972-119">Ano</span><span class="sxs-lookup"><span data-stu-id="7b972-119">Yes</span></span>|<span data-ttu-id="7b972-120">Ano</span><span class="sxs-lookup"><span data-stu-id="7b972-120">Yes</span></span>|<span data-ttu-id="7b972-121">Může analyzovat a řešit adresy IPv6 pomocí všech metod, včetně těch, které jsou označené jako zastaralé.</span><span class="sxs-lookup"><span data-stu-id="7b972-121">Can parse and resolve IPv6 addresses using all methods including those marked obsolete.</span></span>|  
  
 <span data-ttu-id="7b972-122">Uvědomte si, že pokud chcete povolit podporu IPv6 pro všechny třídy v oboru názvů System.Net, musíte upravit konfigurační soubor počítače nebo konfigurační soubor pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7b972-122">Be aware that to enable the IPv6 support for all classes in the System.Net namespace, you must modify the computer configuration file or the configuration file for the application.</span></span> <span data-ttu-id="7b972-123">Konfigurační soubor aplikace má přednost před konfiguračním souborem počítače.</span><span class="sxs-lookup"><span data-stu-id="7b972-123">The configuration file for an application has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="7b972-124">Příklad úprav konfiguračního souboru počítače *Machine. config*, který umožňuje podporu protokolu IPv6, najdete v tématu [Postupy: Změna konfiguračního souboru počítače pro povolení podpory protokolu IPv6](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span><span class="sxs-lookup"><span data-stu-id="7b972-124">For an example of how to modify the computer configuration file, *machine.config*, to enable Ipv6 support see, [How to: Modify the Computer Configuration File to Enable Ipv6 Support](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span> <span data-ttu-id="7b972-125">Také se ujistěte, že je pro operační systém povolena podpora protokolu IPv6.</span><span class="sxs-lookup"><span data-stu-id="7b972-125">Also, ensure that the IPv6 support is enabled for the operating system.</span></span>  
  
 <span data-ttu-id="7b972-126">.NET Framework má konfigurační přepínač nastavený v konfiguračním souboru následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="7b972-126">The .NET Framework has a configuration switch set in a configuration file as follows</span></span>  
  
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
  
 <span data-ttu-id="7b972-127">U .NET Framework verze 1,1 a starší určuje hodnota přepínače konfigurace s **povoleným protokolem IPv6** , zda členové <xref:System.Net.Dns?displayProperty=nameWithType> třídy vrací IPv6 adresy.</span><span class="sxs-lookup"><span data-stu-id="7b972-127">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="7b972-128">Pro .NET Framework verze 2,0 a novější, pokud systém Windows podporuje protokol IPv6, pak členové <xref:System.Net.Dns?displayProperty=nameWithType> třídy (například <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> Metoda) vrátí adresy IPv6 s jedním omezením.</span><span class="sxs-lookup"><span data-stu-id="7b972-128">For .NET Framework version 2.0 and later, if Windows supports IPv6, then members of the <xref:System.Net.Dns?displayProperty=nameWithType> class, (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="7b972-129">Zastaralí členové DNS <xref:System.Net.Dns?displayProperty=nameWithType> (například <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> Metoda) přečtou a rozpoznají hodnotu v konfiguračním souboru pro nastavení s povoleným protokolem IPv6.</span><span class="sxs-lookup"><span data-stu-id="7b972-129">Obsolete members of the DNS <xref:System.Net.Dns?displayProperty=nameWithType> (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file for the ipv6 enabled setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b972-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b972-130">See also</span></span>

- [<span data-ttu-id="7b972-131">Protokol IP (Internet Protocol) verze 6</span><span class="sxs-lookup"><span data-stu-id="7b972-131">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)
- [<span data-ttu-id="7b972-132">Sokety</span><span class="sxs-lookup"><span data-stu-id="7b972-132">Sockets</span></span>](sockets.md)
- [<span data-ttu-id="7b972-133">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="7b972-133">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="7b972-134">\<ipv6>– Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="7b972-134">\<ipv6> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
