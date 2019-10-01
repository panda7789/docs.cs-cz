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
# <a name="network-settings-schema"></a><span data-ttu-id="74a8e-102">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="74a8e-102">Network Settings Schema</span></span>
<span data-ttu-id="74a8e-103">Nastavení sítě určují, jak se .NET Framework připojí k Internetu.</span><span class="sxs-lookup"><span data-stu-id="74a8e-103">Network settings specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="74a8e-104">Nastavení @no__t -0system. NET > určují, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="74a8e-104">The \<system.net> settings specify how the .NET Framework connects to the network.</span></span> <span data-ttu-id="74a8e-105">Následující tabulka popisuje funkci každého podřízeného prvku konfigurace pod [prvkem \<System .net > elementu (nastavení sítě)](system-net-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="74a8e-105">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="74a8e-106">Prvek</span><span class="sxs-lookup"><span data-stu-id="74a8e-106">Element</span></span>|<span data-ttu-id="74a8e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="74a8e-107">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74a8e-108">@no__t – element > 1authenticationModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="74a8e-108">\<authenticationModules> Element (Network Settings)</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="74a8e-109">Určuje moduly používané pro ověřování internetových požadavků.</span><span class="sxs-lookup"><span data-stu-id="74a8e-109">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="74a8e-110">@no__t – element > 1connectionManagement (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="74a8e-110">\<connectionManagement> Element (Network Settings)</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="74a8e-111">Určuje maximální počet připojení k hostitelům v Internetu.</span><span class="sxs-lookup"><span data-stu-id="74a8e-111">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="74a8e-112">@no__t – element > 1defaultProxy (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="74a8e-112">\<defaultProxy> Element (Network Settings)</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="74a8e-113">Určuje proxy server, který se používá pro požadavky HTTP na Internet.</span><span class="sxs-lookup"><span data-stu-id="74a8e-113">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="74a8e-114">@no__t – element > 1mailSettings (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="74a8e-114">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="74a8e-115">Obsahuje nastavení pro možnosti odesílání pošty.</span><span class="sxs-lookup"><span data-stu-id="74a8e-115">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="74a8e-116">@no__t – element > 1requestCaching (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="74a8e-116">\<requestCaching> Element (Network Settings)</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="74a8e-117">Řídí mechanismus ukládání do mezipaměti pro síťové požadavky.</span><span class="sxs-lookup"><span data-stu-id="74a8e-117">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="74a8e-118">@no__t – element > 1webRequestModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="74a8e-118">\<webRequestModules> Element (Network Settings)</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="74a8e-119">Určuje moduly, které se používají k vyžádání informací od hostitelů v Internetu.</span><span class="sxs-lookup"><span data-stu-id="74a8e-119">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
<span data-ttu-id="74a8e-120">Nastavení > \<uri určují, jak .NET Framework zpracovává webové adresy vyjádřené pomocí identifikátorů URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="74a8e-120">The \<uri> settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="74a8e-121">Následující tabulka popisuje funkci každého podřízeného prvku konfigurace pod [elementem \<uri > (nastavení identifikátoru URI)](uri-element-uri-settings.md).</span><span class="sxs-lookup"><span data-stu-id="74a8e-121">The following table describes the function of each child configuration element under the [\<uri> Element (Uri Settings)](uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="74a8e-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="74a8e-122">Element</span></span>|<span data-ttu-id="74a8e-123">Popis</span><span class="sxs-lookup"><span data-stu-id="74a8e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74a8e-124">@no__t – element > 1idn (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="74a8e-124">\<idn> Element (Uri Settings)</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="74a8e-125">Určuje, jestli se pro názvy domén použije analýza v mezinárodním názvu domény (IDN).</span><span class="sxs-lookup"><span data-stu-id="74a8e-125">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="74a8e-126">@no__t – element > 1iriParsing (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="74a8e-126">\<iriParsing> Element (Uri Settings)</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="74a8e-127">Určuje, jestli se má použít analýza mezinárodní identifikátoru prostředků (IRI) pro <xref:System.Uri> a jestli se mají použít pravidla analýzy IRI.</span><span class="sxs-lookup"><span data-stu-id="74a8e-127">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="74a8e-128">@no__t – element > 1schemeSettings (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="74a8e-128">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="74a8e-129">Určuje, jak se bude pro konkrétní schémata analyzovat <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="74a8e-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="74a8e-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74a8e-130">See also</span></span>

- [<span data-ttu-id="74a8e-131">Konfigurace internetových aplikací</span><span class="sxs-lookup"><span data-stu-id="74a8e-131">Configuring Internet Applications</span></span>](../../../network-programming/configuring-internet-applications.md)
- [<span data-ttu-id="74a8e-132">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="74a8e-132">Configuration File Schema</span></span>](../index.md)
