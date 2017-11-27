---
title: "&lt;requestCaching –&gt; – Element (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f2737e67fe1fe1e33b2600f448b02321f6ce1888
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltrequestcachinggt-element-network-settings"></a><span data-ttu-id="fe8dc-102">&lt;requestCaching –&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="fe8dc-102">&lt;requestCaching&gt; Element (Network Settings)</span></span>
<span data-ttu-id="fe8dc-103">Ovládací prvky ukládání do mezipaměti mechanismus pro síťové požadavky.</span><span class="sxs-lookup"><span data-stu-id="fe8dc-103">Controls the caching mechanism for network requests.</span></span>  
  
 <span data-ttu-id="fe8dc-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="fe8dc-104">\<configuration></span></span>  
<span data-ttu-id="fe8dc-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="fe8dc-105">\<system.net></span></span>  
<span data-ttu-id="fe8dc-106">\<requestCaching – ></span><span class="sxs-lookup"><span data-stu-id="fe8dc-106">\<requestCaching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe8dc-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe8dc-107">Syntax</span></span>  
  
```xml  
      <requestCaching>  
        isPrivateCache ="true|false"  
        disableAllCaching="true|false"  
        defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
        unspecifiedMaximumAge= "d.hh.mm.ss">  
          <defaultHttpCachePolicy> … </defaultHttpCachePolicy>  
          <defaultFtpCachePolicy> … </defaultFtpCachePolicy>  
      </requestCaching>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe8dc-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fe8dc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fe8dc-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fe8dc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe8dc-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="fe8dc-110">Attributes</span></span>  
  
|<span data-ttu-id="fe8dc-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="fe8dc-111">Attribute</span></span>|<span data-ttu-id="fe8dc-112">Popis</span><span class="sxs-lookup"><span data-stu-id="fe8dc-112">Description</span></span>|  
|---------------|-----------------|  
|`isPrivateCache`|<span data-ttu-id="fe8dc-113">Určuje, zda mezipaměti zajišťuje izolaci mezi informace o různých uživatelů.</span><span class="sxs-lookup"><span data-stu-id="fe8dc-113">Specifies whether the cache provides isolation between the information of different users.</span></span> <span data-ttu-id="fe8dc-114">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="fe8dc-114">The default value is `true`.</span></span> <span data-ttu-id="fe8dc-115">Tato hodnota by měla být `false` pro aplikace střední vrstvy.</span><span class="sxs-lookup"><span data-stu-id="fe8dc-115">This value should be `false` for middle tier applications.</span></span>|  
|`disableAllCaching`|<span data-ttu-id="fe8dc-116">Určuje, že ukládání do mezipaměti je zakázán pro všechny webové odezvy a nebylo možné přepsat prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="fe8dc-116">Specifies that caching is disabled for all Web responses, and cannot be overridden programmatically.</span></span>|  
|`defaultPolicyLevel`|<span data-ttu-id="fe8dc-117">Jedna z hodnot v <xref:System.Net.Cache.RequestCacheLevel> výčtu.</span><span class="sxs-lookup"><span data-stu-id="fe8dc-117">One of the values in the <xref:System.Net.Cache.RequestCacheLevel> enumeration.</span></span> <span data-ttu-id="fe8dc-118">Výchozí hodnota je `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="fe8dc-118">The default value is `BypassCache`.</span></span>|  
|`unspecifiedMaximumAge`|<span data-ttu-id="fe8dc-119">Určuje výchozí dobu, po jejímž uplynutí obsah je označena jako neplatná.</span><span class="sxs-lookup"><span data-stu-id="fe8dc-119">Specifies the default time after which content is marked as expired.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="fe8dc-120">PolicyLevel atribut, který</span><span class="sxs-lookup"><span data-stu-id="fe8dc-120">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="fe8dc-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="fe8dc-121">Value</span></span>|<span data-ttu-id="fe8dc-122">Popis</span><span class="sxs-lookup"><span data-stu-id="fe8dc-122">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="fe8dc-123">Vrátí prostředků v mezipaměti, pokud je nový prostředek, délka obsahu je přesné a vypršení platnosti, úpravy a délka obsahu atributy jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="fe8dc-123">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="fe8dc-124">Vrátí prostředku ze serveru.</span><span class="sxs-lookup"><span data-stu-id="fe8dc-124">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="fe8dc-125">Vrátí prostředků v mezipaměti, pokud délka obsahu je k dispozici a odpovídá velikosti položky.</span><span class="sxs-lookup"><span data-stu-id="fe8dc-125">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="fe8dc-126">Vrátí prostředků v mezipaměti, pokud délka obsahu je k dispozici a odpovídá velikost položky; prostředek, jinak se stáhne ze serveru a je vrácen volajícímu.</span><span class="sxs-lookup"><span data-stu-id="fe8dc-126">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="fe8dc-127">Vrátí prostředků v mezipaměti, pokud časové razítko v mezipaměti prostředku je stejný jako časové razítko prostředků na serveru. prostředek, jinak se stáhne ze serveru, uložené v mezipaměti a je vrácen volajícímu.</span><span class="sxs-lookup"><span data-stu-id="fe8dc-127">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and is returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="fe8dc-128">Soubory ke stažení prostředku ze serveru, ukládá do mezipaměti a vrátí prostředek volajícímu.</span><span class="sxs-lookup"><span data-stu-id="fe8dc-128">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="fe8dc-129">Pokud existuje prostředek v mezipaměti, je odstraněn.</span><span class="sxs-lookup"><span data-stu-id="fe8dc-129">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="fe8dc-130">Prostředek se stáhne ze serveru a je vrácen volajícímu.</span><span class="sxs-lookup"><span data-stu-id="fe8dc-130">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="fe8dc-131">Splňuje požadavek pomocí kopii prostředku v mezipaměti, pokud časové razítko je stejný jako časové razítko prostředků na serveru. jinak prostředku se stáhne ze serveru, zobrazí volajícího a je uložen v mezipaměti,</span><span class="sxs-lookup"><span data-stu-id="fe8dc-131">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and is stored in the cache,</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fe8dc-132">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fe8dc-132">Child Elements</span></span>  
  
|<span data-ttu-id="fe8dc-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="fe8dc-133">Element</span></span>|<span data-ttu-id="fe8dc-134">Popis</span><span class="sxs-lookup"><span data-stu-id="fe8dc-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe8dc-135">defaulthttpcachepolicy –</span><span class="sxs-lookup"><span data-stu-id="fe8dc-135">defaultHttpCachePolicy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaulthttpcachepolicy-element-network-settings.md)|<span data-ttu-id="fe8dc-136">Volitelný element.</span><span class="sxs-lookup"><span data-stu-id="fe8dc-136">Optional element.</span></span><br /><br /> <span data-ttu-id="fe8dc-137">Popisuje, jestli ukládání do mezipaměti HTTP je aktivní a popisuje výchozí zásady ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="fe8dc-137">Describes whether HTTP caching is active and describes the default caching policy.</span></span>|  
|[<span data-ttu-id="fe8dc-138">\<defaultftpcachepolicy – > elementu (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="fe8dc-138">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultftpcachepolicy-element-network-settings.md)|<span data-ttu-id="fe8dc-139">Volitelný element.</span><span class="sxs-lookup"><span data-stu-id="fe8dc-139">Optional element.</span></span><br /><br /> <span data-ttu-id="fe8dc-140">Popisuje, jestli ukládání do mezipaměti FTP je aktivní a popisuje výchozí zásady ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="fe8dc-140">Describes whether FTP caching is active and describes the default caching policy.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fe8dc-141">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fe8dc-141">Parent Elements</span></span>  
  
|<span data-ttu-id="fe8dc-142">Prvek</span><span class="sxs-lookup"><span data-stu-id="fe8dc-142">Element</span></span>|<span data-ttu-id="fe8dc-143">Popis</span><span class="sxs-lookup"><span data-stu-id="fe8dc-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe8dc-144">System.NET</span><span class="sxs-lookup"><span data-stu-id="fe8dc-144">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="fe8dc-145">Obsahuje nastavení, které určují, jak rozhraní .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="fe8dc-145">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fe8dc-146">Příklad</span><span class="sxs-lookup"><span data-stu-id="fe8dc-146">Example</span></span>  
 <span data-ttu-id="fe8dc-147">Následující příklad ukazuje, jak zakázat ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="fe8dc-147">The following example shows how to disable all caching.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fe8dc-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="fe8dc-148">See Also</span></span>  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 [<span data-ttu-id="fe8dc-149">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="fe8dc-149">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
