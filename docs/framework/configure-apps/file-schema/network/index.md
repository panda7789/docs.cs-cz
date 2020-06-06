---
title: Schéma nastavení sítě
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
ms.openlocfilehash: 5e3bd1b1734fc7fba50b72785531a8b001d6d741
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "71698154"
---
# <a name="network-settings-schema"></a><span data-ttu-id="aa259-102">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="aa259-102">Network Settings Schema</span></span>
<span data-ttu-id="aa259-103">Nastavení sítě určují, jak se .NET Framework připojí k Internetu.</span><span class="sxs-lookup"><span data-stu-id="aa259-103">Network settings specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="aa259-104">\<system.net>Nastavení určuje, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="aa259-104">The \<system.net> settings specify how the .NET Framework connects to the network.</span></span> <span data-ttu-id="aa259-105">Následující tabulka popisuje funkci každého podřízeného elementu konfigurace pod [ \<system.Net> elementem (nastavení sítě)](system-net-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="aa259-105">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="aa259-106">Prvek</span><span class="sxs-lookup"><span data-stu-id="aa259-106">Element</span></span>|<span data-ttu-id="aa259-107">Description</span><span class="sxs-lookup"><span data-stu-id="aa259-107">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aa259-108">\<authenticationModules>– Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="aa259-108">\<authenticationModules> Element (Network Settings)</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="aa259-109">Určuje moduly používané pro ověřování internetových požadavků.</span><span class="sxs-lookup"><span data-stu-id="aa259-109">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="aa259-110">\<connectionManagement>– Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="aa259-110">\<connectionManagement> Element (Network Settings)</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="aa259-111">Určuje maximální počet připojení k hostitelům v Internetu.</span><span class="sxs-lookup"><span data-stu-id="aa259-111">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="aa259-112">\<defaultProxy>– Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="aa259-112">\<defaultProxy> Element (Network Settings)</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="aa259-113">Určuje proxy server, který se používá pro požadavky HTTP na Internet.</span><span class="sxs-lookup"><span data-stu-id="aa259-113">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="aa259-114">\<mailSettings>– Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="aa259-114">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="aa259-115">Obsahuje nastavení pro možnosti odesílání pošty.</span><span class="sxs-lookup"><span data-stu-id="aa259-115">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="aa259-116">\<requestCaching>– Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="aa259-116">\<requestCaching> Element (Network Settings)</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="aa259-117">Řídí mechanismus ukládání do mezipaměti pro síťové požadavky.</span><span class="sxs-lookup"><span data-stu-id="aa259-117">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="aa259-118">\<webRequestModules>– Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="aa259-118">\<webRequestModules> Element (Network Settings)</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="aa259-119">Určuje moduly, které se používají k vyžádání informací od hostitelů v Internetu.</span><span class="sxs-lookup"><span data-stu-id="aa259-119">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
<span data-ttu-id="aa259-120">\<uri>Nastavení určuje způsob, jakým .NET Framework zpracovává webové adresy vyjádřené pomocí identifikátorů URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="aa259-120">The \<uri> settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="aa259-121">Následující tabulka popisuje funkci každého podřízeného elementu konfigurace pod [ \<uri> elementem (nastavení URI)](uri-element-uri-settings.md).</span><span class="sxs-lookup"><span data-stu-id="aa259-121">The following table describes the function of each child configuration element under the [\<uri> Element (Uri Settings)](uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="aa259-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="aa259-122">Element</span></span>|<span data-ttu-id="aa259-123">Description</span><span class="sxs-lookup"><span data-stu-id="aa259-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aa259-124">\<idn>– Element (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="aa259-124">\<idn> Element (Uri Settings)</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="aa259-125">Určuje, jestli se pro názvy domén použije analýza v mezinárodním názvu domény (IDN).</span><span class="sxs-lookup"><span data-stu-id="aa259-125">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="aa259-126">\<iriParsing>– Element (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="aa259-126">\<iriParsing> Element (Uri Settings)</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="aa259-127">Určuje, jestli se má použít analýza mezinárodní identifikátoru prostředků (IRI) <xref:System.Uri> a jestli se mají použít pravidla analýzy IRI.</span><span class="sxs-lookup"><span data-stu-id="aa259-127">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="aa259-128">\<schemeSettings>– Element (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="aa259-128">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="aa259-129">Určuje, jak se <xref:System.Uri> bude analyzovat pro konkrétní schémata.</span><span class="sxs-lookup"><span data-stu-id="aa259-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aa259-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="aa259-130">See also</span></span>

- [<span data-ttu-id="aa259-131">Konfigurace internetových aplikací</span><span class="sxs-lookup"><span data-stu-id="aa259-131">Configuring Internet Applications</span></span>](../../../network-programming/configuring-internet-applications.md)
- [<span data-ttu-id="aa259-132">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="aa259-132">Configuration File Schema</span></span>](../index.md)
