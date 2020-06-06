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
ms.openlocfilehash: d510c445c585a36005ed415b14188efc4be03984
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089107"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="10482-102">\<settings> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="10482-102">\<settings> Element (Network Settings)</span></span>
<span data-ttu-id="10482-103">Nakonfiguruje základní možnosti sítě pro <xref:System.Net?displayProperty=nameWithType> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="10482-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<settings>**

## <a name="syntax"></a><span data-ttu-id="10482-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10482-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10482-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="10482-105">Attributes and Elements</span></span>  
 <span data-ttu-id="10482-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="10482-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10482-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="10482-107">Attributes</span></span>  
 <span data-ttu-id="10482-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="10482-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="10482-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="10482-109">Child Elements</span></span>  
  
|<span data-ttu-id="10482-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="10482-110">Element</span></span>|<span data-ttu-id="10482-111">Description</span><span class="sxs-lookup"><span data-stu-id="10482-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10482-112">httpListener</span><span class="sxs-lookup"><span data-stu-id="10482-112">httpListener</span></span>](httplistener-element-network-settings.md)|<span data-ttu-id="10482-113">Přizpůsobuje parametry používané <xref:System.Net.HttpListener> třídou.</span><span class="sxs-lookup"><span data-stu-id="10482-113">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="10482-114">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="10482-114">httpWebRequest</span></span>](httpwebrequest-element-network-settings.md)|<span data-ttu-id="10482-115">Přizpůsobuje parametry webového požadavku.</span><span class="sxs-lookup"><span data-stu-id="10482-115">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="10482-116">protokolů</span><span class="sxs-lookup"><span data-stu-id="10482-116">ipv6</span></span>](ipv6-element-network-settings.md)|<span data-ttu-id="10482-117">Povolí podporu Internet Protocol verze 6 (IPv6).</span><span class="sxs-lookup"><span data-stu-id="10482-117">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="10482-118">\<performanceCounter>– Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="10482-118">\<performanceCounter> Element (Network Settings)</span></span>](performancecounter-element-network-settings.md)|<span data-ttu-id="10482-119">Povolí čítače výkonu sítě.</span><span class="sxs-lookup"><span data-stu-id="10482-119">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="10482-120">Třída ServicePointManager</span><span class="sxs-lookup"><span data-stu-id="10482-120">servicePointManager</span></span>](servicepointmanager-element-network-settings.md)|<span data-ttu-id="10482-121">Nakonfiguruje připojení k síťovým prostředkům.</span><span class="sxs-lookup"><span data-stu-id="10482-121">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="10482-122">zásuvky</span><span class="sxs-lookup"><span data-stu-id="10482-122">socket</span></span>](socket-element-network-settings.md)|<span data-ttu-id="10482-123">Určuje, jestli operace soketu používají porty dokončení.</span><span class="sxs-lookup"><span data-stu-id="10482-123">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="10482-124">\<webProxyScript>– Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="10482-124">\<webProxyScript> Element (Network Settings)</span></span>](webproxyscript-element-network-settings.md)|<span data-ttu-id="10482-125">Konfiguruje charakteristiky skriptu používaného pro zjišťování webových proxy serverů.</span><span class="sxs-lookup"><span data-stu-id="10482-125">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="10482-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="10482-126">Parent Elements</span></span>  
  
|<span data-ttu-id="10482-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="10482-127">Element</span></span>|<span data-ttu-id="10482-128">Description</span><span class="sxs-lookup"><span data-stu-id="10482-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10482-129">system.net</span><span class="sxs-lookup"><span data-stu-id="10482-129">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="10482-130">Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="10482-130">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10482-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="10482-131">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="10482-132">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="10482-132">Configuration Files</span></span>  
 <span data-ttu-id="10482-133">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="10482-133">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10482-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="10482-134">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="10482-135">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="10482-135">Network Settings Schema</span></span>](index.md)
