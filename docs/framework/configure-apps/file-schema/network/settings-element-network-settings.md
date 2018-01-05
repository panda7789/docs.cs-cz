---
title: "&lt;nastavení&gt; – Element (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
caps.latest.revision: "21"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 6fd4b608964bca2e05424f2f76136fa69111adc4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltsettingsgt-element-network-settings"></a><span data-ttu-id="8e1c6-102">&lt;nastavení&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="8e1c6-102">&lt;settings&gt; Element (Network Settings)</span></span>
<span data-ttu-id="8e1c6-103">Nakonfiguruje možnosti základní sítě <xref:System.Net?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8e1c6-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="8e1c6-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="8e1c6-104">\<configuration></span></span>  
<span data-ttu-id="8e1c6-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="8e1c6-105">\<system.net></span></span>  
<span data-ttu-id="8e1c6-106">\<Nastavení ></span><span class="sxs-lookup"><span data-stu-id="8e1c6-106">\<settings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e1c6-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e1c6-107">Syntax</span></span>  
  
```xml  
<settings>  
  <httpListener> … </httpListener>  
  <httpWebRequest> … </httpWebRequest>  
  <ipv6> … </ipv6>  
  <performanceCounters> … </performanceCounters>  
  <servicePointManager> … </servicePointManager>  
  <socket> … </socket>  
  <webProxyScript> … </webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e1c6-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8e1c6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8e1c6-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8e1c6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e1c6-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="8e1c6-110">Attributes</span></span>  
 <span data-ttu-id="8e1c6-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="8e1c6-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8e1c6-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8e1c6-112">Child Elements</span></span>  
  
|<span data-ttu-id="8e1c6-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="8e1c6-113">Element</span></span>|<span data-ttu-id="8e1c6-114">Popis</span><span class="sxs-lookup"><span data-stu-id="8e1c6-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e1c6-115">httpListener</span><span class="sxs-lookup"><span data-stu-id="8e1c6-115">httpListener</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/httplistener-element-network-settings.md)|<span data-ttu-id="8e1c6-116">Přizpůsobí parametrů používaných <xref:System.Net.HttpListener> třídy.</span><span class="sxs-lookup"><span data-stu-id="8e1c6-116">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="8e1c6-117">HttpWebRequest –</span><span class="sxs-lookup"><span data-stu-id="8e1c6-117">httpWebRequest</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md)|<span data-ttu-id="8e1c6-118">Přizpůsobí parametry webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="8e1c6-118">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="8e1c6-119">IPv6</span><span class="sxs-lookup"><span data-stu-id="8e1c6-119">ipv6</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)|<span data-ttu-id="8e1c6-120">Umožňuje Internet Protocol version 6 (IPv6) podporují.</span><span class="sxs-lookup"><span data-stu-id="8e1c6-120">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="8e1c6-121">\<performanceCounter > elementu (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="8e1c6-121">\<performanceCounter> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md)|<span data-ttu-id="8e1c6-122">Umožňuje síťovým čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="8e1c6-122">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="8e1c6-123">ServicePointManager –</span><span class="sxs-lookup"><span data-stu-id="8e1c6-123">servicePointManager</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/servicepointmanager-element-network-settings.md)|<span data-ttu-id="8e1c6-124">Nakonfiguruje připojení k síťovým prostředkům.</span><span class="sxs-lookup"><span data-stu-id="8e1c6-124">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="8e1c6-125">soket</span><span class="sxs-lookup"><span data-stu-id="8e1c6-125">socket</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/socket-element-network-settings.md)|<span data-ttu-id="8e1c6-126">Určuje, zda operace soketu používat porty dokončení.</span><span class="sxs-lookup"><span data-stu-id="8e1c6-126">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="8e1c6-127">\<webproxyscript – > elementu (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="8e1c6-127">\<webProxyScript> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webproxyscript-element-network-settings.md)|<span data-ttu-id="8e1c6-128">Nakonfiguruje charakteristiky skript používá ke zjišťování webové proxy servery.</span><span class="sxs-lookup"><span data-stu-id="8e1c6-128">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8e1c6-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8e1c6-129">Parent Elements</span></span>  
  
|<span data-ttu-id="8e1c6-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="8e1c6-130">Element</span></span>|<span data-ttu-id="8e1c6-131">Popis</span><span class="sxs-lookup"><span data-stu-id="8e1c6-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e1c6-132">System.NET</span><span class="sxs-lookup"><span data-stu-id="8e1c6-132">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="8e1c6-133">Obsahuje nastavení, které určují, jak rozhraní .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="8e1c6-133">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e1c6-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8e1c6-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8e1c6-135">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="8e1c6-135">Configuration Files</span></span>  
 <span data-ttu-id="8e1c6-136">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="8e1c6-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e1c6-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e1c6-137">See Also</span></span>  
 <xref:System.Net?displayProperty=nameWithType>  
 [<span data-ttu-id="8e1c6-138">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="8e1c6-138">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
