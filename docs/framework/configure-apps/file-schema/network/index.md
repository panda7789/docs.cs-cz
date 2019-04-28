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
ms.openlocfilehash: 71d945e6046a8648a812de939f197429bc695808
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674529"
---
# <a name="network-settings-schema"></a><span data-ttu-id="3035a-102">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="3035a-102">Network Settings Schema</span></span>
<span data-ttu-id="3035a-103">Nastavení sítě určete, jak rozhraní .NET Framework připojí k Internetu.</span><span class="sxs-lookup"><span data-stu-id="3035a-103">Network settings specify how the .NET Framework connects to the Internet.</span></span> <span data-ttu-id="3035a-104">Následující tabulka popisuje funkce každý podřízený element konfigurace v rámci [ \<system.Net > – Element (nastavení sítě)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="3035a-104">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="3035a-105">Prvek</span><span class="sxs-lookup"><span data-stu-id="3035a-105">Element</span></span>|<span data-ttu-id="3035a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="3035a-106">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3035a-107">\<authenticationModules – > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="3035a-107">\<authenticationModules> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="3035a-108">Určuje moduly používané k ověření požadavků na Internetu.</span><span class="sxs-lookup"><span data-stu-id="3035a-108">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="3035a-109">\<connectionManagement – > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="3035a-109">\<connectionManagement> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="3035a-110">Určuje maximální počet připojení k hostiteli v síti Internet.</span><span class="sxs-lookup"><span data-stu-id="3035a-110">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="3035a-111">\<defaultProxy > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="3035a-111">\<defaultProxy> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="3035a-112">Určuje proxy server používá pro požadavky HTTP na Internetu.</span><span class="sxs-lookup"><span data-stu-id="3035a-112">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="3035a-113">\<mailSettings – > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="3035a-113">\<mailSettings> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="3035a-114">Obsahuje nastavení pro možnosti pro odesílání pošty.</span><span class="sxs-lookup"><span data-stu-id="3035a-114">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="3035a-115">\<requestCaching – > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="3035a-115">\<requestCaching> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="3035a-116">Určuje mechanismus ukládání do mezipaměti pro síťové požadavky.</span><span class="sxs-lookup"><span data-stu-id="3035a-116">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="3035a-117">\<webRequestModules – > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="3035a-117">\<webRequestModules> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="3035a-118">Určuje moduly používaná pro požádání o informace z hostitelů v Internetu.</span><span class="sxs-lookup"><span data-stu-id="3035a-118">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
 <span data-ttu-id="3035a-119">Nastavení URI zadejte způsob, jakým rozhraní .NET Framework zpracovává webové adresy vyjádřena pomocí uniform resource Identifier (identifikátory URI).</span><span class="sxs-lookup"><span data-stu-id="3035a-119">Uri settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="3035a-120">Následující tabulka popisuje funkce každý podřízený element konfigurace v rámci [ \<Uri > – Element (nastavení Uri)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md).</span><span class="sxs-lookup"><span data-stu-id="3035a-120">The following table describes the function of each child configuration element under the [\<Uri> Element (Uri Settings)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="3035a-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="3035a-121">Element</span></span>|<span data-ttu-id="3035a-122">Popis</span><span class="sxs-lookup"><span data-stu-id="3035a-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3035a-123">\<IDN > – Element (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="3035a-123">\<idn> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|<span data-ttu-id="3035a-124">Určuje, pokud analýza mezinárodních názvů domén (IDN) platí pro názvy domén.</span><span class="sxs-lookup"><span data-stu-id="3035a-124">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="3035a-125">\<iriParsing > – Element (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="3035a-125">\<iriParsing> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|<span data-ttu-id="3035a-126">Určuje, pokud analýze International Resource Identifier (IRI) se použije k <xref:System.Uri> a určuje, zda by měl použít IRI pravidel pro analýzu.</span><span class="sxs-lookup"><span data-stu-id="3035a-126">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="3035a-127">\<schemeSettings > – Element (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="3035a-127">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="3035a-128">Určuje, jak <xref:System.Uri> pro konkrétní schémata, bude analyzována.</span><span class="sxs-lookup"><span data-stu-id="3035a-128">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3035a-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3035a-129">See also</span></span>

- [<span data-ttu-id="3035a-130">Konfigurace internetových aplikací</span><span class="sxs-lookup"><span data-stu-id="3035a-130">Configuring Internet Applications</span></span>](../../../../../docs/framework/network-programming/configuring-internet-applications.md)
- [<span data-ttu-id="3035a-131">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="3035a-131">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
