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
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089107"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="34808-102">\<nastavení > elementu (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="34808-102">\<settings> Element (Network Settings)</span></span>
<span data-ttu-id="34808-103">Konfiguruje základní možnosti sítě pro obor názvů <xref:System.Net?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="34808-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  

<span data-ttu-id="34808-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="34808-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="34808-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="34808-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="34808-106">&nbsp;&nbsp;&nbsp;&nbsp;**nastavení\<**</span><span class="sxs-lookup"><span data-stu-id="34808-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<settings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="34808-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34808-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34808-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="34808-108">Attributes and Elements</span></span>  
 <span data-ttu-id="34808-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="34808-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34808-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="34808-110">Attributes</span></span>  
 <span data-ttu-id="34808-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="34808-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="34808-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="34808-112">Child Elements</span></span>  
  
|<span data-ttu-id="34808-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="34808-113">Element</span></span>|<span data-ttu-id="34808-114">Popis</span><span class="sxs-lookup"><span data-stu-id="34808-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34808-115">httpListener</span><span class="sxs-lookup"><span data-stu-id="34808-115">httpListener</span></span>](httplistener-element-network-settings.md)|<span data-ttu-id="34808-116">Přizpůsobuje parametry používané třídou <xref:System.Net.HttpListener>.</span><span class="sxs-lookup"><span data-stu-id="34808-116">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="34808-117">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="34808-117">httpWebRequest</span></span>](httpwebrequest-element-network-settings.md)|<span data-ttu-id="34808-118">Přizpůsobuje parametry webového požadavku.</span><span class="sxs-lookup"><span data-stu-id="34808-118">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="34808-119">protokolů</span><span class="sxs-lookup"><span data-stu-id="34808-119">ipv6</span></span>](ipv6-element-network-settings.md)|<span data-ttu-id="34808-120">Povolí podporu Internet Protocol verze 6 (IPv6).</span><span class="sxs-lookup"><span data-stu-id="34808-120">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="34808-121">\<element > performanceCounter (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="34808-121">\<performanceCounter> Element (Network Settings)</span></span>](performancecounter-element-network-settings.md)|<span data-ttu-id="34808-122">Povolí čítače výkonu sítě.</span><span class="sxs-lookup"><span data-stu-id="34808-122">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="34808-123">Třída ServicePointManager</span><span class="sxs-lookup"><span data-stu-id="34808-123">servicePointManager</span></span>](servicepointmanager-element-network-settings.md)|<span data-ttu-id="34808-124">Nakonfiguruje připojení k síťovým prostředkům.</span><span class="sxs-lookup"><span data-stu-id="34808-124">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="34808-125">zásuvky</span><span class="sxs-lookup"><span data-stu-id="34808-125">socket</span></span>](socket-element-network-settings.md)|<span data-ttu-id="34808-126">Určuje, jestli operace soketu používají porty dokončení.</span><span class="sxs-lookup"><span data-stu-id="34808-126">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="34808-127">\<element > webProxyScript (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="34808-127">\<webProxyScript> Element (Network Settings)</span></span>](webproxyscript-element-network-settings.md)|<span data-ttu-id="34808-128">Konfiguruje charakteristiky skriptu používaného pro zjišťování webových proxy serverů.</span><span class="sxs-lookup"><span data-stu-id="34808-128">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="34808-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="34808-129">Parent Elements</span></span>  
  
|<span data-ttu-id="34808-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="34808-130">Element</span></span>|<span data-ttu-id="34808-131">Popis</span><span class="sxs-lookup"><span data-stu-id="34808-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34808-132">system.net</span><span class="sxs-lookup"><span data-stu-id="34808-132">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="34808-133">Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="34808-133">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34808-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="34808-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="34808-135">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="34808-135">Configuration Files</span></span>  
 <span data-ttu-id="34808-136">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="34808-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34808-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="34808-137">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="34808-138">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="34808-138">Network Settings Schema</span></span>](index.md)
