---
title: <settings> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
ms.openlocfilehash: 839907d9339d459070fff12dbca22d3c2df5b020
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260616"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="fab3b-102">\<Nastavení > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="fab3b-102">\<settings> Element (Network Settings)</span></span>
<span data-ttu-id="fab3b-103">Nakonfiguruje možnosti základní sítě pro <xref:System.Net?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="fab3b-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="fab3b-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="fab3b-104">\<configuration></span></span>  
<span data-ttu-id="fab3b-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="fab3b-105">\<system.net></span></span>  
<span data-ttu-id="fab3b-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="fab3b-106">\<settings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fab3b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fab3b-107">Syntax</span></span>  
  
```xml  
<settings>  
  <httpListener>...</httpListener>  
  <httpWebRequest>...</httpWebRequest>  
  <ipv6>...</ipv6>  
  <performanceCounters>...</performanceCounters>  
  <servicePointManager>...</servicePointManager>  
  <socket>...</socket>  
  <webProxyScript>...</webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fab3b-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fab3b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fab3b-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fab3b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fab3b-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="fab3b-110">Attributes</span></span>  
 <span data-ttu-id="fab3b-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="fab3b-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fab3b-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fab3b-112">Child Elements</span></span>  
  
|<span data-ttu-id="fab3b-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="fab3b-113">Element</span></span>|<span data-ttu-id="fab3b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="fab3b-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fab3b-115">httpListener</span><span class="sxs-lookup"><span data-stu-id="fab3b-115">httpListener</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/httplistener-element-network-settings.md)|<span data-ttu-id="fab3b-116">Přizpůsobí parametrů používaných <xref:System.Net.HttpListener> třídy.</span><span class="sxs-lookup"><span data-stu-id="fab3b-116">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="fab3b-117">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="fab3b-117">httpWebRequest</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md)|<span data-ttu-id="fab3b-118">Přizpůsobí parametrů webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="fab3b-118">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="fab3b-119">ipv6</span><span class="sxs-lookup"><span data-stu-id="fab3b-119">ipv6</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)|<span data-ttu-id="fab3b-120">Umožňuje Internet Protocol verze 6 (IPv6) podporují.</span><span class="sxs-lookup"><span data-stu-id="fab3b-120">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="fab3b-121">\<performanceCounter > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="fab3b-121">\<performanceCounter> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md)|<span data-ttu-id="fab3b-122">Umožňuje síťovým čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="fab3b-122">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="fab3b-123">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="fab3b-123">servicePointManager</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/servicepointmanager-element-network-settings.md)|<span data-ttu-id="fab3b-124">Nakonfiguruje připojení k síťovým prostředkům.</span><span class="sxs-lookup"><span data-stu-id="fab3b-124">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="fab3b-125">Soketu</span><span class="sxs-lookup"><span data-stu-id="fab3b-125">socket</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/socket-element-network-settings.md)|<span data-ttu-id="fab3b-126">Určuje, zda operace soketu používat porty dokončení.</span><span class="sxs-lookup"><span data-stu-id="fab3b-126">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="fab3b-127">\<webproxyscript – > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="fab3b-127">\<webProxyScript> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webproxyscript-element-network-settings.md)|<span data-ttu-id="fab3b-128">Konfiguruje vlastnosti souboru, který používá ke zjišťování webové proxy servery.</span><span class="sxs-lookup"><span data-stu-id="fab3b-128">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fab3b-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fab3b-129">Parent Elements</span></span>  
  
|<span data-ttu-id="fab3b-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="fab3b-130">Element</span></span>|<span data-ttu-id="fab3b-131">Popis</span><span class="sxs-lookup"><span data-stu-id="fab3b-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fab3b-132">system.net</span><span class="sxs-lookup"><span data-stu-id="fab3b-132">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="fab3b-133">Obsahuje nastavení, která určují, jak rozhraní .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="fab3b-133">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fab3b-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fab3b-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="fab3b-135">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="fab3b-135">Configuration Files</span></span>  
 <span data-ttu-id="fab3b-136">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="fab3b-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fab3b-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fab3b-137">See also</span></span>
- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="fab3b-138">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="fab3b-138">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
