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
ms.openlocfilehash: 0f5d762a2b688bebcb7c027be6c639b6d64c069d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664108"
---
# <a name="network-settings-schema"></a><span data-ttu-id="31c18-102">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="31c18-102">Network Settings Schema</span></span>
<span data-ttu-id="31c18-103">Nastavení sítě určují, jak se .NET Framework připojí k Internetu.</span><span class="sxs-lookup"><span data-stu-id="31c18-103">Network settings specify how the .NET Framework connects to the Internet.</span></span> <span data-ttu-id="31c18-104">Následující tabulka popisuje funkci každého podřízeného prvku konfigurace pod [ \<prvkem System .NET > (nastavení sítě)](system-net-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="31c18-104">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="31c18-105">Prvek</span><span class="sxs-lookup"><span data-stu-id="31c18-105">Element</span></span>|<span data-ttu-id="31c18-106">Popis</span><span class="sxs-lookup"><span data-stu-id="31c18-106">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31c18-107">\<authenticationModules – element > (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="31c18-107">\<authenticationModules> Element (Network Settings)</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="31c18-108">Určuje moduly používané pro ověřování internetových požadavků.</span><span class="sxs-lookup"><span data-stu-id="31c18-108">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="31c18-109">\<connectionManagement – element > (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="31c18-109">\<connectionManagement> Element (Network Settings)</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="31c18-110">Určuje maximální počet připojení k hostitelům v Internetu.</span><span class="sxs-lookup"><span data-stu-id="31c18-110">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="31c18-111">\<defaultProxy – element > (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="31c18-111">\<defaultProxy> Element (Network Settings)</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="31c18-112">Určuje proxy server, který se používá pro požadavky HTTP na Internet.</span><span class="sxs-lookup"><span data-stu-id="31c18-112">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="31c18-113">\<mailSettings – element > (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="31c18-113">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="31c18-114">Obsahuje nastavení pro možnosti odesílání pošty.</span><span class="sxs-lookup"><span data-stu-id="31c18-114">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="31c18-115">\<requestCaching – element > (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="31c18-115">\<requestCaching> Element (Network Settings)</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="31c18-116">Řídí mechanismus ukládání do mezipaměti pro síťové požadavky.</span><span class="sxs-lookup"><span data-stu-id="31c18-116">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="31c18-117">\<webRequestModules – element > (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="31c18-117">\<webRequestModules> Element (Network Settings)</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="31c18-118">Určuje moduly, které se používají k vyžádání informací od hostitelů v Internetu.</span><span class="sxs-lookup"><span data-stu-id="31c18-118">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
 <span data-ttu-id="31c18-119">Nastavení identifikátoru URI určuje způsob, jakým .NET Framework zpracovává webové adresy vyjádřené pomocí identifikátorů URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="31c18-119">Uri settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="31c18-120">Následující tabulka popisuje funkci každého podřízeného prvku konfigurace pod [ \<identifikátorem URI > element (nastavení URI)](uri-element-uri-settings.md).</span><span class="sxs-lookup"><span data-stu-id="31c18-120">The following table describes the function of each child configuration element under the [\<Uri> Element (Uri Settings)](uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="31c18-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="31c18-121">Element</span></span>|<span data-ttu-id="31c18-122">Popis</span><span class="sxs-lookup"><span data-stu-id="31c18-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31c18-123">\<Element > IDN (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="31c18-123">\<idn> Element (Uri Settings)</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="31c18-124">Určuje, jestli se pro názvy domén použije analýza v mezinárodním názvu domény (IDN).</span><span class="sxs-lookup"><span data-stu-id="31c18-124">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="31c18-125">\<iriParsing – element > (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="31c18-125">\<iriParsing> Element (Uri Settings)</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="31c18-126">Určuje, jestli se <xref:System.Uri> má použít analýza mezinárodní identifikátoru prostředků (IRI) a jestli se mají použít pravidla analýzy IRI.</span><span class="sxs-lookup"><span data-stu-id="31c18-126">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="31c18-127">\<schemeSettings – element > (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="31c18-127">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="31c18-128">Určuje, jak <xref:System.Uri> se bude analyzovat pro konkrétní schémata.</span><span class="sxs-lookup"><span data-stu-id="31c18-128">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="31c18-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="31c18-129">See also</span></span>

- [<span data-ttu-id="31c18-130">Konfigurace internetových aplikací</span><span class="sxs-lookup"><span data-stu-id="31c18-130">Configuring Internet Applications</span></span>](../../../network-programming/configuring-internet-applications.md)
- [<span data-ttu-id="31c18-131">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="31c18-131">Configuration File Schema</span></span>](../index.md)
