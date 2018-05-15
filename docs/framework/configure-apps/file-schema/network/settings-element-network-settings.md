---
title: '&lt;nastavení&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3f717705a6cd4cc29fe333f5012c7fec466d350b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltsettingsgt-element-network-settings"></a><span data-ttu-id="541cf-102">&lt;nastavení&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="541cf-102">&lt;settings&gt; Element (Network Settings)</span></span>
<span data-ttu-id="541cf-103">Nakonfiguruje možnosti základní sítě <xref:System.Net?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="541cf-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="541cf-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="541cf-104">\<configuration></span></span>  
<span data-ttu-id="541cf-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="541cf-105">\<system.net></span></span>  
<span data-ttu-id="541cf-106">\<Nastavení ></span><span class="sxs-lookup"><span data-stu-id="541cf-106">\<settings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="541cf-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="541cf-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="541cf-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="541cf-108">Attributes and Elements</span></span>  
 <span data-ttu-id="541cf-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="541cf-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="541cf-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="541cf-110">Attributes</span></span>  
 <span data-ttu-id="541cf-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="541cf-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="541cf-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="541cf-112">Child Elements</span></span>  
  
|<span data-ttu-id="541cf-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="541cf-113">Element</span></span>|<span data-ttu-id="541cf-114">Popis</span><span class="sxs-lookup"><span data-stu-id="541cf-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="541cf-115">HttpListener</span><span class="sxs-lookup"><span data-stu-id="541cf-115">httpListener</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/httplistener-element-network-settings.md)|<span data-ttu-id="541cf-116">Přizpůsobí parametrů používaných <xref:System.Net.HttpListener> třídy.</span><span class="sxs-lookup"><span data-stu-id="541cf-116">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="541cf-117">HttpWebRequest –</span><span class="sxs-lookup"><span data-stu-id="541cf-117">httpWebRequest</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md)|<span data-ttu-id="541cf-118">Přizpůsobí parametry webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="541cf-118">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="541cf-119">IPv6</span><span class="sxs-lookup"><span data-stu-id="541cf-119">ipv6</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)|<span data-ttu-id="541cf-120">Umožňuje Internet Protocol version 6 (IPv6) podporují.</span><span class="sxs-lookup"><span data-stu-id="541cf-120">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="541cf-121">\<performanceCounter > elementu (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="541cf-121">\<performanceCounter> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md)|<span data-ttu-id="541cf-122">Umožňuje síťovým čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="541cf-122">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="541cf-123">ServicePointManager –</span><span class="sxs-lookup"><span data-stu-id="541cf-123">servicePointManager</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/servicepointmanager-element-network-settings.md)|<span data-ttu-id="541cf-124">Nakonfiguruje připojení k síťovým prostředkům.</span><span class="sxs-lookup"><span data-stu-id="541cf-124">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="541cf-125">Soket</span><span class="sxs-lookup"><span data-stu-id="541cf-125">socket</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/socket-element-network-settings.md)|<span data-ttu-id="541cf-126">Určuje, zda operace soketu používat porty dokončení.</span><span class="sxs-lookup"><span data-stu-id="541cf-126">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="541cf-127">\<webproxyscript – > elementu (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="541cf-127">\<webProxyScript> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webproxyscript-element-network-settings.md)|<span data-ttu-id="541cf-128">Nakonfiguruje charakteristiky skript používá ke zjišťování webové proxy servery.</span><span class="sxs-lookup"><span data-stu-id="541cf-128">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="541cf-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="541cf-129">Parent Elements</span></span>  
  
|<span data-ttu-id="541cf-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="541cf-130">Element</span></span>|<span data-ttu-id="541cf-131">Popis</span><span class="sxs-lookup"><span data-stu-id="541cf-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="541cf-132">System.NET</span><span class="sxs-lookup"><span data-stu-id="541cf-132">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="541cf-133">Obsahuje nastavení, které určují, jak rozhraní .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="541cf-133">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="541cf-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="541cf-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="541cf-135">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="541cf-135">Configuration Files</span></span>  
 <span data-ttu-id="541cf-136">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="541cf-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="541cf-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="541cf-137">See Also</span></span>  
 <xref:System.Net?displayProperty=nameWithType>  
 [<span data-ttu-id="541cf-138">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="541cf-138">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
