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
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698154"
---
# <a name="network-settings-schema"></a><span data-ttu-id="b2188-102">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="b2188-102">Network Settings Schema</span></span>
<span data-ttu-id="b2188-103">Nastavení sítě určují, jak se .NET Framework připojí k Internetu.</span><span class="sxs-lookup"><span data-stu-id="b2188-103">Network settings specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="b2188-104">Nastavení \<System. NET > určují, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="b2188-104">The \<system.net> settings specify how the .NET Framework connects to the network.</span></span> <span data-ttu-id="b2188-105">Následující tabulka popisuje funkci každého podřízeného prvku konfigurace pod [prvkem\<System .net > elementu (nastavení sítě)](system-net-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="b2188-105">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="b2188-106">Prvek</span><span class="sxs-lookup"><span data-stu-id="b2188-106">Element</span></span>|<span data-ttu-id="b2188-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b2188-107">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b2188-108">\<element > authenticationModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="b2188-108">\<authenticationModules> Element (Network Settings)</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="b2188-109">Určuje moduly používané pro ověřování internetových požadavků.</span><span class="sxs-lookup"><span data-stu-id="b2188-109">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="b2188-110">\<element > connectionManagement (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="b2188-110">\<connectionManagement> Element (Network Settings)</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="b2188-111">Určuje maximální počet připojení k hostitelům v Internetu.</span><span class="sxs-lookup"><span data-stu-id="b2188-111">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="b2188-112">\<element > defaultProxy (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="b2188-112">\<defaultProxy> Element (Network Settings)</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="b2188-113">Určuje proxy server, který se používá pro požadavky HTTP na Internet.</span><span class="sxs-lookup"><span data-stu-id="b2188-113">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="b2188-114">\<element > mailSettings (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="b2188-114">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="b2188-115">Obsahuje nastavení pro možnosti odesílání pošty.</span><span class="sxs-lookup"><span data-stu-id="b2188-115">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="b2188-116">\<element > requestCaching (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="b2188-116">\<requestCaching> Element (Network Settings)</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="b2188-117">Řídí mechanismus ukládání do mezipaměti pro síťové požadavky.</span><span class="sxs-lookup"><span data-stu-id="b2188-117">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="b2188-118">\<element > webRequestModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="b2188-118">\<webRequestModules> Element (Network Settings)</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="b2188-119">Určuje moduly, které se používají k vyžádání informací od hostitelů v Internetu.</span><span class="sxs-lookup"><span data-stu-id="b2188-119">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
<span data-ttu-id="b2188-120">Nastavení > identifikátoru URI \<určují, jak .NET Framework zpracovává webové adresy vyjádřené pomocí identifikátorů URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="b2188-120">The \<uri> settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="b2188-121">Následující tabulka popisuje funkci každého podřízeného prvku konfigurace pod [\<identifikátor uri > elementu (nastavení URI)](uri-element-uri-settings.md).</span><span class="sxs-lookup"><span data-stu-id="b2188-121">The following table describes the function of each child configuration element under the [\<uri> Element (Uri Settings)](uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="b2188-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="b2188-122">Element</span></span>|<span data-ttu-id="b2188-123">Popis</span><span class="sxs-lookup"><span data-stu-id="b2188-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b2188-124">\<element IDN > (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="b2188-124">\<idn> Element (Uri Settings)</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="b2188-125">Určuje, jestli se pro názvy domén použije analýza v mezinárodním názvu domény (IDN).</span><span class="sxs-lookup"><span data-stu-id="b2188-125">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="b2188-126">\<element > iriParsing (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="b2188-126">\<iriParsing> Element (Uri Settings)</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="b2188-127">Určuje, jestli se má u <xref:System.Uri> použít analýza mezinárodního identifikátoru prostředků (IRI) a jestli se mají použít pravidla analýzy IRI.</span><span class="sxs-lookup"><span data-stu-id="b2188-127">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="b2188-128">\<element > schemeSettings (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="b2188-128">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="b2188-129">Určuje, jak se bude <xref:System.Uri> analyzovat pro konkrétní schémata.</span><span class="sxs-lookup"><span data-stu-id="b2188-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b2188-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b2188-130">See also</span></span>

- [<span data-ttu-id="b2188-131">Konfigurace internetových aplikací</span><span class="sxs-lookup"><span data-stu-id="b2188-131">Configuring Internet Applications</span></span>](../../../network-programming/configuring-internet-applications.md)
- [<span data-ttu-id="b2188-132">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="b2188-132">Configuration File Schema</span></span>](../index.md)
