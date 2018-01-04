---
title: "Schéma nastavení sítě"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d8f13b75d0558c002fd29938ce98d85f358acc9a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="network-settings-schema"></a><span data-ttu-id="c2e10-102">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="c2e10-102">Network Settings Schema</span></span>
<span data-ttu-id="c2e10-103">Nastavení sítě určete, jak rozhraní .NET Framework připojuje k Internetu.</span><span class="sxs-lookup"><span data-stu-id="c2e10-103">Network settings specify how the .NET Framework connects to the Internet.</span></span> <span data-ttu-id="c2e10-104">Následující tabulka popisuje funkci jednotlivých podřízených prvků konfigurace v části [ \<system.Net > elementu (nastavení sítě)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="c2e10-104">The following table describes the function of each child configuration element under the [\<system.Net> Element (Network Settings)](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md).</span></span>  
  
|<span data-ttu-id="c2e10-105">Prvek</span><span class="sxs-lookup"><span data-stu-id="c2e10-105">Element</span></span>|<span data-ttu-id="c2e10-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c2e10-106">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c2e10-107">\<authenticationModules – > elementu (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="c2e10-107">\<authenticationModules> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/authenticationmodules-element-network-settings.md)|<span data-ttu-id="c2e10-108">Určuje moduly používané k ověřování žádostí o Internetu.</span><span class="sxs-lookup"><span data-stu-id="c2e10-108">Specifies the modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="c2e10-109">\<connectionManagement – > elementu (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="c2e10-109">\<connectionManagement> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="c2e10-110">Určuje maximální počet připojení k hostiteli v síti Internet.</span><span class="sxs-lookup"><span data-stu-id="c2e10-110">Specifies the maximum number of connections to Internet hosts.</span></span>|  
|[<span data-ttu-id="c2e10-111">\<defaultProxy – > elementu (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="c2e10-111">\<defaultProxy> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="c2e10-112">Určuje proxy server používá pro požadavky HTTP na Internetu.</span><span class="sxs-lookup"><span data-stu-id="c2e10-112">Specifies the proxy server used for HTTP requests to the Internet.</span></span>|  
|[<span data-ttu-id="c2e10-113">\<mailSettings – > elementu (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="c2e10-113">\<mailSettings> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="c2e10-114">Obsahuje nastavení pro e-mailu odesílání možnosti.</span><span class="sxs-lookup"><span data-stu-id="c2e10-114">Contains settings for mail sending options.</span></span>|  
|[<span data-ttu-id="c2e10-115">\<requestCaching – > elementu (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="c2e10-115">\<requestCaching> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="c2e10-116">Určuje moduly používané pro vyžádání informací z Internetu hostitelů.</span><span class="sxs-lookup"><span data-stu-id="c2e10-116">Specifies the modules used to request information from Internet hosts.</span></span>|  
|[<span data-ttu-id="c2e10-117">\<requestCaching – > elementu (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="c2e10-117">\<requestCaching> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="c2e10-118">Nakonfiguruje možnosti základní sítě <xref:System.Net?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c2e10-118">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>|  
|[<span data-ttu-id="c2e10-119">\<webRequestModules – > elementu (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="c2e10-119">\<webRequestModules> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="c2e10-120">Určuje moduly používané pro vyžádání informací z Internetu hostitelů.</span><span class="sxs-lookup"><span data-stu-id="c2e10-120">Specifies the modules used to request information from Internet hosts.</span></span>|  
  
 <span data-ttu-id="c2e10-121">Identifikátor URI nastavení určují, jak rozhraní .NET Framework zpracovává webové adresy vyjádřit pomocí identifikátorů URI (URI).</span><span class="sxs-lookup"><span data-stu-id="c2e10-121">Uri settings specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span> <span data-ttu-id="c2e10-122">Následující tabulka popisuje funkci jednotlivých podřízených prvků konfigurace v části [ \<Uri > elementu (nastavení Uri)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md).</span><span class="sxs-lookup"><span data-stu-id="c2e10-122">The following table describes the function of each child configuration element under the [\<Uri> Element (Uri Settings)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md).</span></span>  
  
|<span data-ttu-id="c2e10-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="c2e10-123">Element</span></span>|<span data-ttu-id="c2e10-124">Popis</span><span class="sxs-lookup"><span data-stu-id="c2e10-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c2e10-125">\<IDN > elementu (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="c2e10-125">\<idn> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|<span data-ttu-id="c2e10-126">Určuje, pokud analýza mezinárodní název domény (IDN) se použijí pro názvy domén.</span><span class="sxs-lookup"><span data-stu-id="c2e10-126">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="c2e10-127">\<iriParsing > – Element (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="c2e10-127">\<iriParsing> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|<span data-ttu-id="c2e10-128">Určuje, zda analýza mezinárodní prostředků identifikátor (IRI) je použita k <xref:System.Uri> a zda má být použita IRI Analýza pravidla.</span><span class="sxs-lookup"><span data-stu-id="c2e10-128">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="c2e10-129">\<schemeSettings > – Element (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="c2e10-129">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="c2e10-130">Určuje, jak <xref:System.Uri> bude analyzovat pro konkrétní schémat.</span><span class="sxs-lookup"><span data-stu-id="c2e10-130">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c2e10-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2e10-131">See Also</span></span>  
 [<span data-ttu-id="c2e10-132">Konfigurace internetových aplikací</span><span class="sxs-lookup"><span data-stu-id="c2e10-132">Configuring Internet Applications</span></span>](../../../../../docs/framework/network-programming/configuring-internet-applications.md)  
 [<span data-ttu-id="c2e10-133">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="c2e10-133">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
