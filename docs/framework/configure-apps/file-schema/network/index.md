---
title: Schéma nastavení sítě
description: Přečtěte si o schématu nastavení sítě, které určuje, jak se .NET Framework připojuje k Internetu a zpracovává identifikátory URI.
ms.date: 03/30/2017
helpviewer_keywords:
- elements [.NET Framework], network configuration elements
- sending data, network configuration elements
- receiving data, network configuration elements
- configuration settings [.NET Framework], networks
- Internet, network configuration elements
- network configuration elements
- network settings
- connections [.NET Framework], network configuration elements
- network resources, network configuration elements
ms.assetid: f1de5a0f-76c5-4833-819f-5222b8146340
ms.openlocfilehash: 6a22d7f1608db2e8909d0ead11e9110ec8a8a2c5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504573"
---
# <a name="network-settings-schema"></a><span data-ttu-id="35500-103">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="35500-103">Network Settings Schema</span></span>
<span data-ttu-id="35500-104">Nastavení sítě určují, jak se .NET Framework připojí k Internetu.</span><span class="sxs-lookup"><span data-stu-id="35500-104">Network settings specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="35500-105">\<system.net>Nastavení určuje, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="35500-105">The \<system.net> settings specify how the .NET Framework connects to the network.</span></span> <span data-ttu-id="35500-106">Následující tabulka popisuje funkci každého podřízeného elementu konfigurace pod [ \<system.Net> elementem (nastavení sítě)](system-net-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="35500-106">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="35500-107">Prvek</span><span class="sxs-lookup"><span data-stu-id="35500-107">Element</span></span>|<span data-ttu-id="35500-108">Description</span><span class="sxs-lookup"><span data-stu-id="35500-108">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35500-109">\<authenticationModules>– Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="35500-109">\<authenticationModules> Element (Network Settings)</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="35500-110">Určuje moduly používané pro ověřování internetových požadavků.</span><span class="sxs-lookup"><span data-stu-id="35500-110">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="35500-111">\<connectionManagement>– Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="35500-111">\<connectionManagement> Element (Network Settings)</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="35500-112">Určuje maximální počet připojení k hostitelům v Internetu.</span><span class="sxs-lookup"><span data-stu-id="35500-112">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="35500-113">\<defaultProxy>– Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="35500-113">\<defaultProxy> Element (Network Settings)</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="35500-114">Určuje proxy server, který se používá pro požadavky HTTP na Internet.</span><span class="sxs-lookup"><span data-stu-id="35500-114">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="35500-115">\<mailSettings>– Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="35500-115">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="35500-116">Obsahuje nastavení pro možnosti odesílání pošty.</span><span class="sxs-lookup"><span data-stu-id="35500-116">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="35500-117">\<requestCaching>– Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="35500-117">\<requestCaching> Element (Network Settings)</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="35500-118">Řídí mechanismus ukládání do mezipaměti pro síťové požadavky.</span><span class="sxs-lookup"><span data-stu-id="35500-118">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="35500-119">\<webRequestModules>– Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="35500-119">\<webRequestModules> Element (Network Settings)</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="35500-120">Určuje moduly, které se používají k vyžádání informací od hostitelů v Internetu.</span><span class="sxs-lookup"><span data-stu-id="35500-120">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
<span data-ttu-id="35500-121">\<uri>Nastavení určuje způsob, jakým .NET Framework zpracovává webové adresy vyjádřené pomocí identifikátorů URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="35500-121">The \<uri> settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="35500-122">Následující tabulka popisuje funkci každého podřízeného elementu konfigurace pod [ \<uri> elementem (nastavení URI)](uri-element-uri-settings.md).</span><span class="sxs-lookup"><span data-stu-id="35500-122">The following table describes the function of each child configuration element under the [\<uri> Element (Uri Settings)](uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="35500-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="35500-123">Element</span></span>|<span data-ttu-id="35500-124">Description</span><span class="sxs-lookup"><span data-stu-id="35500-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35500-125">\<idn>– Element (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="35500-125">\<idn> Element (Uri Settings)</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="35500-126">Určuje, jestli se pro názvy domén použije analýza v mezinárodním názvu domény (IDN).</span><span class="sxs-lookup"><span data-stu-id="35500-126">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="35500-127">\<iriParsing>– Element (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="35500-127">\<iriParsing> Element (Uri Settings)</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="35500-128">Určuje, jestli se má použít analýza mezinárodní identifikátoru prostředků (IRI) <xref:System.Uri> a jestli se mají použít pravidla analýzy IRI.</span><span class="sxs-lookup"><span data-stu-id="35500-128">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="35500-129">\<schemeSettings>– Element (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="35500-129">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="35500-130">Určuje, jak se <xref:System.Uri> bude analyzovat pro konkrétní schémata.</span><span class="sxs-lookup"><span data-stu-id="35500-130">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="35500-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="35500-131">See also</span></span>

- [<span data-ttu-id="35500-132">Konfigurace internetových aplikací</span><span class="sxs-lookup"><span data-stu-id="35500-132">Configuring Internet Applications</span></span>](../../../network-programming/configuring-internet-applications.md)
- [<span data-ttu-id="35500-133">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="35500-133">Configuration File Schema</span></span>](../index.md)
