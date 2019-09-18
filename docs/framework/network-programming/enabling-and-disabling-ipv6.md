---
title: Povolení a zákaz IPv6
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
ms.openlocfilehash: 66c802dd5feb865faf7469cb7da04fbffcb4a2d6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048566"
---
# <a name="enabling-and-disabling-ipv6"></a><span data-ttu-id="fdaee-102">Povolení a zákaz IPv6</span><span class="sxs-lookup"><span data-stu-id="fdaee-102">Enabling and Disabling IPv6</span></span>
<span data-ttu-id="fdaee-103">Chcete-li použít protokol IPv6, ujistěte se, že používáte verzi operačního systému, která podporuje protokol IPv6, a ujistěte se, že jsou správně nakonfigurovány operační systém a síťové třídy.</span><span class="sxs-lookup"><span data-stu-id="fdaee-103">To use the IPv6 protocol, ensure that you are running a version of the operating system that supports IPv6 and ensure that the operating system and the networking classes are configured properly.</span></span>  
  
## <a name="configuration-steps"></a><span data-ttu-id="fdaee-104">Kroky konfigurace</span><span class="sxs-lookup"><span data-stu-id="fdaee-104">Configuration Steps</span></span>  
 <span data-ttu-id="fdaee-105">V následující tabulce jsou uvedeny různé konfigurace</span><span class="sxs-lookup"><span data-stu-id="fdaee-105">The following table lists various configurations</span></span>  
  
|<span data-ttu-id="fdaee-106">Je povolený protokol IPv6 operačního systému?</span><span class="sxs-lookup"><span data-stu-id="fdaee-106">Operating system IPv6-enabled?</span></span>|<span data-ttu-id="fdaee-107">Síťové třídy podporující protokol IPv6?</span><span class="sxs-lookup"><span data-stu-id="fdaee-107">Networking classes IPv6-enabled?</span></span>|<span data-ttu-id="fdaee-108">Popis</span><span class="sxs-lookup"><span data-stu-id="fdaee-108">Description</span></span>|  
|-------------------------------------|---------------------------------------|-----------------|  
|<span data-ttu-id="fdaee-109">Ne</span><span class="sxs-lookup"><span data-stu-id="fdaee-109">No</span></span>|<span data-ttu-id="fdaee-110">Ne</span><span class="sxs-lookup"><span data-stu-id="fdaee-110">No</span></span>|<span data-ttu-id="fdaee-111">Může analyzovat adresy IPv6.</span><span class="sxs-lookup"><span data-stu-id="fdaee-111">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="fdaee-112">Ne</span><span class="sxs-lookup"><span data-stu-id="fdaee-112">No</span></span>|<span data-ttu-id="fdaee-113">Ano</span><span class="sxs-lookup"><span data-stu-id="fdaee-113">Yes</span></span>|<span data-ttu-id="fdaee-114">Může analyzovat adresy IPv6.</span><span class="sxs-lookup"><span data-stu-id="fdaee-114">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="fdaee-115">Ano</span><span class="sxs-lookup"><span data-stu-id="fdaee-115">Yes</span></span>|<span data-ttu-id="fdaee-116">Ne</span><span class="sxs-lookup"><span data-stu-id="fdaee-116">No</span></span>|<span data-ttu-id="fdaee-117">Dokáže analyzovat adresy IPv6 a překládat adresy IPv6 pomocí metod překladu názvů, které nejsou označené jako zastaralé.</span><span class="sxs-lookup"><span data-stu-id="fdaee-117">Can parse IPv6 addresses and resolve IPv6 addresses using name resolution methods not marked obsolete.</span></span>|  
|<span data-ttu-id="fdaee-118">Ano</span><span class="sxs-lookup"><span data-stu-id="fdaee-118">Yes</span></span>|<span data-ttu-id="fdaee-119">Ano</span><span class="sxs-lookup"><span data-stu-id="fdaee-119">Yes</span></span>|<span data-ttu-id="fdaee-120">Může analyzovat a řešit adresy IPv6 pomocí všech metod, včetně těch, které jsou označené jako zastaralé.</span><span class="sxs-lookup"><span data-stu-id="fdaee-120">Can parse and resolve IPv6 addresses using all methods including those marked obsolete.</span></span>|  
  
 <span data-ttu-id="fdaee-121">Uvědomte si, že pokud chcete povolit podporu IPv6 pro všechny třídy v oboru názvů System.Net, musíte upravit konfigurační soubor počítače nebo konfigurační soubor pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fdaee-121">Be aware that to enable the IPv6 support for all classes in the System.Net namespace, you must modify the computer configuration file or the configuration file for the application.</span></span> <span data-ttu-id="fdaee-122">Konfigurační soubor aplikace má přednost před konfiguračním souborem počítače.</span><span class="sxs-lookup"><span data-stu-id="fdaee-122">The configuration file for an application has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="fdaee-123">Příklad úprav konfiguračního souboru počítače *Machine. config*, který umožňuje podporu protokolu IPv6, najdete v tématu [postup: Úpravou konfiguračního souboru počítače povolte podporu](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md)protokolu IPv6.</span><span class="sxs-lookup"><span data-stu-id="fdaee-123">For an example of how to modify the computer configuration file, *machine.config*, to enable Ipv6 support see, [How to: Modify the Computer Configuration File to Enable Ipv6 Support](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span> <span data-ttu-id="fdaee-124">Také se ujistěte, že je pro operační systém povolena podpora protokolu IPv6.</span><span class="sxs-lookup"><span data-stu-id="fdaee-124">Also, ensure that the IPv6 support is enabled for the operating system.</span></span>  
  
 <span data-ttu-id="fdaee-125">.NET Framework má konfigurační přepínač nastavený v konfiguračním souboru následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="fdaee-125">The .NET Framework has a configuration switch set in a configuration file as follows</span></span>  
  
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
  
 <span data-ttu-id="fdaee-126">U .NET Framework verze 1,1 a starší určuje hodnota přepínače konfigurace s **povoleným protokolem IPv6** , zda členové <xref:System.Net.Dns?displayProperty=nameWithType> třídy vrací IPv6 adresy.</span><span class="sxs-lookup"><span data-stu-id="fdaee-126">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="fdaee-127">Pro .NET Framework verze 2,0 a novější, pokud systém Windows podporuje protokol IPv6, pak členové <xref:System.Net.Dns?displayProperty=nameWithType> třídy (například <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> Metoda) vrátí adresy IPv6 s jedním omezením.</span><span class="sxs-lookup"><span data-stu-id="fdaee-127">For .NET Framework version 2.0 and later, if Windows supports IPv6, then members of the <xref:System.Net.Dns?displayProperty=nameWithType> class, (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="fdaee-128">Zastaralí členové DNS <xref:System.Net.Dns?displayProperty=nameWithType> (například <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> Metoda) přečtou a rozpoznají hodnotu v konfiguračním souboru pro nastavení s povoleným protokolem IPv6.</span><span class="sxs-lookup"><span data-stu-id="fdaee-128">Obsolete members of the DNS <xref:System.Net.Dns?displayProperty=nameWithType> (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file for the ipv6 enabled setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdaee-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fdaee-129">See also</span></span>

- [<span data-ttu-id="fdaee-130">Protokol IP (Internet Protocol) verze 6</span><span class="sxs-lookup"><span data-stu-id="fdaee-130">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)
- [<span data-ttu-id="fdaee-131">Sokety</span><span class="sxs-lookup"><span data-stu-id="fdaee-131">Sockets</span></span>](sockets.md)
- [<span data-ttu-id="fdaee-132">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="fdaee-132">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="fdaee-133">\<> – element IPv6 (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="fdaee-133">\<ipv6> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
