---
title: Povolení a zakázání IPv6
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b018d646816bda96945a440a890da20b81b1cbbc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393929"
---
# <a name="enabling-and-disabling-ipv6"></a><span data-ttu-id="3f29f-102">Povolení a zakázání IPv6</span><span class="sxs-lookup"><span data-stu-id="3f29f-102">Enabling and Disabling IPv6</span></span>
<span data-ttu-id="3f29f-103">Chcete-li používat protokol IPv6, ujistěte se, že používáte verzi operačního systému, který podporuje protokol IPv6 a ujistěte se, že operační systém a síťové třídy jsou konfigurována správně.</span><span class="sxs-lookup"><span data-stu-id="3f29f-103">To use the IPv6 protocol, ensure that you are running a version of the operating system that supports IPv6 and ensure that the operating system and the networking classes are configured properly.</span></span>  
  
## <a name="configuration-steps"></a><span data-ttu-id="3f29f-104">Kroky konfigurace</span><span class="sxs-lookup"><span data-stu-id="3f29f-104">Configuration Steps</span></span>  
 <span data-ttu-id="3f29f-105">Následující tabulka uvádí různé konfigurace</span><span class="sxs-lookup"><span data-stu-id="3f29f-105">The following table lists various configurations</span></span>  
  
|<span data-ttu-id="3f29f-106">Operační systém podporující protokol IPv6?</span><span class="sxs-lookup"><span data-stu-id="3f29f-106">Operating system IPv6-enabled?</span></span>|<span data-ttu-id="3f29f-107">Sítě třídy povolen protokol IPv6?</span><span class="sxs-lookup"><span data-stu-id="3f29f-107">Networking classes IPv6-enabled?</span></span>|<span data-ttu-id="3f29f-108">Popis</span><span class="sxs-lookup"><span data-stu-id="3f29f-108">Description</span></span>|  
|-------------------------------------|---------------------------------------|-----------------|  
|<span data-ttu-id="3f29f-109">Ne</span><span class="sxs-lookup"><span data-stu-id="3f29f-109">No</span></span>|<span data-ttu-id="3f29f-110">Ne</span><span class="sxs-lookup"><span data-stu-id="3f29f-110">No</span></span>|<span data-ttu-id="3f29f-111">Můžete analyzovat adresy IPv6.</span><span class="sxs-lookup"><span data-stu-id="3f29f-111">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="3f29f-112">Ne</span><span class="sxs-lookup"><span data-stu-id="3f29f-112">No</span></span>|<span data-ttu-id="3f29f-113">Ano</span><span class="sxs-lookup"><span data-stu-id="3f29f-113">Yes</span></span>|<span data-ttu-id="3f29f-114">Můžete analyzovat adresy IPv6.</span><span class="sxs-lookup"><span data-stu-id="3f29f-114">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="3f29f-115">Ano</span><span class="sxs-lookup"><span data-stu-id="3f29f-115">Yes</span></span>|<span data-ttu-id="3f29f-116">Ne</span><span class="sxs-lookup"><span data-stu-id="3f29f-116">No</span></span>|<span data-ttu-id="3f29f-117">Můžete analyzovat adresy IPv6 a překládat adresy IPv6 pomocí metody rozlišování názvů není označena jako zastaralá.</span><span class="sxs-lookup"><span data-stu-id="3f29f-117">Can parse IPv6 addresses and resolve IPv6 addresses using name resolution methods not marked obsolete.</span></span>|  
|<span data-ttu-id="3f29f-118">Ano</span><span class="sxs-lookup"><span data-stu-id="3f29f-118">Yes</span></span>|<span data-ttu-id="3f29f-119">Ano</span><span class="sxs-lookup"><span data-stu-id="3f29f-119">Yes</span></span>|<span data-ttu-id="3f29f-120">Můžete analyzovat a řešit pomocí všech metod, včetně těch, které označeny jako zastaralé adresy IPv6.</span><span class="sxs-lookup"><span data-stu-id="3f29f-120">Can parse and resolve IPv6 addresses using all methods including those marked obsolete.</span></span>|  
  
 <span data-ttu-id="3f29f-121">Upozorňujeme, že pokud chcete povolit podporu IPv6 pro všechny třídy v oboru názvů System.Net, je třeba upravit konfiguračního souboru počítače nebo konfiguračního souboru pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3f29f-121">Be aware that to enable the IPv6 support for all classes in the System.Net namespace, you must modify the computer configuration file or the configuration file for the application.</span></span> <span data-ttu-id="3f29f-122">Konfigurační soubor pro aplikaci, má přednost před konfiguračního souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="3f29f-122">The configuration file for an application has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="3f29f-123">Příklad toho, jak upravit konfigurační soubor na počítači *machine.config*, aby Ipv6 podpory najdete [postup: Upravte konfigurační soubor počítače. Chcete-li povolit podporu Ipv6](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span><span class="sxs-lookup"><span data-stu-id="3f29f-123">For an example of how to modify the computer configuration file, *machine.config*, to enable Ipv6 support see, [How to: Modify the Computer Configuration File to Enable Ipv6 Support](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span> <span data-ttu-id="3f29f-124">Ujistěte se také, že je povolena podpora protokolu IPv6 pro operační systém.</span><span class="sxs-lookup"><span data-stu-id="3f29f-124">Also, ensure that the IPv6 support is enabled for the operating system.</span></span>  
  
 <span data-ttu-id="3f29f-125">Rozhraní .NET Framework má přepínač konfigurace následujícím způsobem nastavit v konfiguračním souboru</span><span class="sxs-lookup"><span data-stu-id="3f29f-125">The .NET Framework has a configuration switch set in a configuration file as follows</span></span>  
  
```xml  
<system.net>…  
    <settings>…  
        <ipv6 enabled="true"/>…  
    </settings>…  
</system.net>  
```  
  
 <span data-ttu-id="3f29f-126">Pro rozhraní .NET Framework verze 1.1 a starší se hodnota **pro protokol ipv6** konfigurace přepínače určuje zda členy <xref:System.Net.Dns?displayProperty=nameWithType> třída vrátit adresy IPv6.</span><span class="sxs-lookup"><span data-stu-id="3f29f-126">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="3f29f-127">Pro rozhraní .NET Framework verze 2.0 nebo novější, pokud systém Windows podporuje protokol IPv6 a potom členy <xref:System.Net.Dns?displayProperty=nameWithType> třídy (například <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> metoda), vrátí adresy IPv6 s jedním z omezení.</span><span class="sxs-lookup"><span data-stu-id="3f29f-127">For .NET Framework version 2.0 and later, if Windows supports IPv6, then members of the <xref:System.Net.Dns?displayProperty=nameWithType> class, (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="3f29f-128">Zastaralé členy DNS <xref:System.Net.Dns?displayProperty=nameWithType> (například <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> metoda) bude číst a rozpoznat hodnota v konfiguračním souboru pro nastavení pro protokol ipv6.</span><span class="sxs-lookup"><span data-stu-id="3f29f-128">Obsolete members of the DNS <xref:System.Net.Dns?displayProperty=nameWithType> (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file for the ipv6 enabled setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f29f-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f29f-129">See Also</span></span>  
 [<span data-ttu-id="3f29f-130">Protokol IP (Internet Protocol) verze 6</span><span class="sxs-lookup"><span data-stu-id="3f29f-130">Internet Protocol Version 6</span></span>](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [<span data-ttu-id="3f29f-131">Sokety</span><span class="sxs-lookup"><span data-stu-id="3f29f-131">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)  
 [<span data-ttu-id="3f29f-132">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="3f29f-132">Network Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [<span data-ttu-id="3f29f-133">\<IPv6 > elementu (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="3f29f-133">\<ipv6> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
