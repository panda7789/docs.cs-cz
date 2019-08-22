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
ms.openlocfilehash: 12797e2f06d03aacd81700eae57d5776c1a6f354
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663998"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="47695-102">\<Nastavení > element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="47695-102">\<settings> Element (Network Settings)</span></span>
<span data-ttu-id="47695-103">Nakonfiguruje základní možnosti sítě pro <xref:System.Net?displayProperty=nameWithType> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="47695-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="47695-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="47695-104">\<configuration></span></span>  
<span data-ttu-id="47695-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="47695-105">\<system.net></span></span>  
<span data-ttu-id="47695-106">\<Nastavení ></span><span class="sxs-lookup"><span data-stu-id="47695-106">\<settings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47695-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47695-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47695-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="47695-108">Attributes and Elements</span></span>  
 <span data-ttu-id="47695-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="47695-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47695-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="47695-110">Attributes</span></span>  
 <span data-ttu-id="47695-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="47695-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="47695-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="47695-112">Child Elements</span></span>  
  
|<span data-ttu-id="47695-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="47695-113">Element</span></span>|<span data-ttu-id="47695-114">Popis</span><span class="sxs-lookup"><span data-stu-id="47695-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="47695-115">httpListener</span><span class="sxs-lookup"><span data-stu-id="47695-115">httpListener</span></span>](httplistener-element-network-settings.md)|<span data-ttu-id="47695-116">Přizpůsobuje parametry používané <xref:System.Net.HttpListener> třídou.</span><span class="sxs-lookup"><span data-stu-id="47695-116">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="47695-117">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="47695-117">httpWebRequest</span></span>](httpwebrequest-element-network-settings.md)|<span data-ttu-id="47695-118">Přizpůsobuje parametry webového požadavku.</span><span class="sxs-lookup"><span data-stu-id="47695-118">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="47695-119">ipv6</span><span class="sxs-lookup"><span data-stu-id="47695-119">ipv6</span></span>](ipv6-element-network-settings.md)|<span data-ttu-id="47695-120">Povolí podporu Internet Protocol verze 6 (IPv6).</span><span class="sxs-lookup"><span data-stu-id="47695-120">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="47695-121">\<performanceCounter – element > (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="47695-121">\<performanceCounter> Element (Network Settings)</span></span>](performancecounter-element-network-settings.md)|<span data-ttu-id="47695-122">Povolí čítače výkonu sítě.</span><span class="sxs-lookup"><span data-stu-id="47695-122">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="47695-123">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="47695-123">servicePointManager</span></span>](servicepointmanager-element-network-settings.md)|<span data-ttu-id="47695-124">Nakonfiguruje připojení k síťovým prostředkům.</span><span class="sxs-lookup"><span data-stu-id="47695-124">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="47695-125">zásuvky</span><span class="sxs-lookup"><span data-stu-id="47695-125">socket</span></span>](socket-element-network-settings.md)|<span data-ttu-id="47695-126">Určuje, jestli operace soketu používají porty dokončení.</span><span class="sxs-lookup"><span data-stu-id="47695-126">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="47695-127">\<webProxyScript – element > (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="47695-127">\<webProxyScript> Element (Network Settings)</span></span>](webproxyscript-element-network-settings.md)|<span data-ttu-id="47695-128">Konfiguruje charakteristiky skriptu používaného pro zjišťování webových proxy serverů.</span><span class="sxs-lookup"><span data-stu-id="47695-128">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="47695-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="47695-129">Parent Elements</span></span>  
  
|<span data-ttu-id="47695-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="47695-130">Element</span></span>|<span data-ttu-id="47695-131">Popis</span><span class="sxs-lookup"><span data-stu-id="47695-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="47695-132">system.net</span><span class="sxs-lookup"><span data-stu-id="47695-132">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="47695-133">Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="47695-133">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47695-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="47695-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="47695-135">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="47695-135">Configuration Files</span></span>  
 <span data-ttu-id="47695-136">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="47695-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47695-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="47695-137">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="47695-138">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="47695-138">Network Settings Schema</span></span>](index.md)
