---
title: <requestCaching> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
ms.openlocfilehash: afee69eb894518b1c88483e34a1d64d452019244
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74802125"
---
# <a name="requestcaching-element-network-settings"></a><span data-ttu-id="f3373-102">\<requestCaching> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="f3373-102">\<requestCaching> Element (Network Settings)</span></span>
<span data-ttu-id="f3373-103">Řídí mechanismus ukládání do mezipaměti pro síťové požadavky.</span><span class="sxs-lookup"><span data-stu-id="f3373-103">Controls the caching mechanism for network requests.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<requestCaching>**  
  
## <a name="syntax"></a><span data-ttu-id="f3373-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3373-104">Syntax</span></span>  
  
```xml  
<requestCaching  
  isPrivateCache ="true|false"  
  disableAllCaching="true|false"  
  defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
  unspecifiedMaximumAge= "d.hh:mm:ss">  
    <defaultHttpCachePolicy>...</defaultHttpCachePolicy>  
    <defaultFtpCachePolicy>...</defaultFtpCachePolicy>  
</requestCaching>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3373-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f3373-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f3373-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f3373-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3373-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="f3373-107">Attributes</span></span>  
  
|<span data-ttu-id="f3373-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="f3373-108">Attribute</span></span>|<span data-ttu-id="f3373-109">Popis</span><span class="sxs-lookup"><span data-stu-id="f3373-109">Description</span></span>|  
|---------------|-----------------|  
|`isPrivateCache`|<span data-ttu-id="f3373-110">Určuje, jestli mezipaměť poskytuje izolaci mezi informacemi různých uživatelů.</span><span class="sxs-lookup"><span data-stu-id="f3373-110">Specifies whether the cache provides isolation between the information of different users.</span></span> <span data-ttu-id="f3373-111">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="f3373-111">The default value is `true`.</span></span> <span data-ttu-id="f3373-112">Tato hodnota by měla být `false` pro aplikace střední vrstvy.</span><span class="sxs-lookup"><span data-stu-id="f3373-112">This value should be `false` for middle tier applications.</span></span>|  
|`disableAllCaching`|<span data-ttu-id="f3373-113">Určuje, že ukládání do mezipaměti je pro všechny webové odpovědi zakázané, a nedá se přepsat programově.</span><span class="sxs-lookup"><span data-stu-id="f3373-113">Specifies that caching is disabled for all Web responses, and cannot be overridden programmatically.</span></span>|  
|`defaultPolicyLevel`|<span data-ttu-id="f3373-114">Jedna z hodnot ve <xref:System.Net.Cache.RequestCacheLevel> výčtu.</span><span class="sxs-lookup"><span data-stu-id="f3373-114">One of the values in the <xref:System.Net.Cache.RequestCacheLevel> enumeration.</span></span> <span data-ttu-id="f3373-115">Výchozí hodnota je `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="f3373-115">The default value is `BypassCache`.</span></span>|  
|`unspecifiedMaximumAge`|<span data-ttu-id="f3373-116">Určuje výchozí čas, po kterém je obsah označen jako konec platnosti.</span><span class="sxs-lookup"><span data-stu-id="f3373-116">Specifies the default time after which content is marked as expired.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="f3373-117">policyLevel – atribut</span><span class="sxs-lookup"><span data-stu-id="f3373-117">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="f3373-118">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f3373-118">Value</span></span>|<span data-ttu-id="f3373-119">Description</span><span class="sxs-lookup"><span data-stu-id="f3373-119">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="f3373-120">Vrátí prostředek uložený v mezipaměti, pokud je prostředek v čerstvém stavu, že velikost obsahu je přesná a že jsou k dispozici atributy vypršení platnosti, změna a délka obsahu.</span><span class="sxs-lookup"><span data-stu-id="f3373-120">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="f3373-121">Vrátí prostředek ze serveru.</span><span class="sxs-lookup"><span data-stu-id="f3373-121">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="f3373-122">Vrátí prostředek uložený v mezipaměti, pokud je k dispozici délka obsahu a odpovídá velikosti položky.</span><span class="sxs-lookup"><span data-stu-id="f3373-122">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="f3373-123">Vrátí prostředek uložený v mezipaměti, pokud je zadaná délka obsahu a odpovídá velikosti položky. v opačném případě se prostředek stáhne ze serveru a vrátí se volajícímu.</span><span class="sxs-lookup"><span data-stu-id="f3373-123">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="f3373-124">Vrátí prostředek uložený v mezipaměti, pokud je časové razítko prostředku v mezipaměti stejné jako časové razítko prostředku na serveru. v opačném případě se prostředek stáhne ze serveru, uloží se do mezipaměti a vrátí se volajícímu.</span><span class="sxs-lookup"><span data-stu-id="f3373-124">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and is returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="f3373-125">Stáhne prostředek ze serveru, uloží ho do mezipaměti a vrátí prostředek volajícímu.</span><span class="sxs-lookup"><span data-stu-id="f3373-125">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="f3373-126">Pokud prostředek uložený v mezipaměti existuje, odstraní se.</span><span class="sxs-lookup"><span data-stu-id="f3373-126">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="f3373-127">Prostředek se stáhne ze serveru a vrátí se volajícímu.</span><span class="sxs-lookup"><span data-stu-id="f3373-127">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="f3373-128">Splňuje požadavky pomocí kopie prostředku uložené v mezipaměti, pokud je časové razítko stejné jako časové razítko prostředku na serveru. v opačném případě se prostředek stáhne ze serveru, zobrazí se volajícímu a uloží se do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="f3373-128">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and is stored in the cache,</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3373-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f3373-129">Child Elements</span></span>  
  
|<span data-ttu-id="f3373-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="f3373-130">Element</span></span>|<span data-ttu-id="f3373-131">Description</span><span class="sxs-lookup"><span data-stu-id="f3373-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3373-132">defaultHttpCachePolicy</span><span class="sxs-lookup"><span data-stu-id="f3373-132">defaultHttpCachePolicy</span></span>](defaulthttpcachepolicy-element-network-settings.md)|<span data-ttu-id="f3373-133">Volitelný element.</span><span class="sxs-lookup"><span data-stu-id="f3373-133">Optional element.</span></span><br /><br /> <span data-ttu-id="f3373-134">Popisuje, zda je ukládání do mezipaměti protokolu HTTP aktivní a popisuje výchozí zásady ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="f3373-134">Describes whether HTTP caching is active and describes the default caching policy.</span></span>|  
|[<span data-ttu-id="f3373-135">\<defaultFtpCachePolicy>– Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="f3373-135">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>](defaultftpcachepolicy-element-network-settings.md)|<span data-ttu-id="f3373-136">Volitelný element.</span><span class="sxs-lookup"><span data-stu-id="f3373-136">Optional element.</span></span><br /><br /> <span data-ttu-id="f3373-137">Popisuje, zda je ukládání do mezipaměti FTP aktivní a popisuje výchozí zásady ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="f3373-137">Describes whether FTP caching is active and describes the default caching policy.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f3373-138">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f3373-138">Parent Elements</span></span>  
  
|<span data-ttu-id="f3373-139">Prvek</span><span class="sxs-lookup"><span data-stu-id="f3373-139">Element</span></span>|<span data-ttu-id="f3373-140">Description</span><span class="sxs-lookup"><span data-stu-id="f3373-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3373-141">system.net</span><span class="sxs-lookup"><span data-stu-id="f3373-141">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="f3373-142">Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="f3373-142">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f3373-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3373-143">Example</span></span>  
 <span data-ttu-id="f3373-144">Následující příklad ukazuje, jak zakázat ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="f3373-144">The following example shows how to disable all caching.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f3373-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3373-145">See also</span></span>

- <xref:System.Net.Cache?displayProperty=nameWithType>
- [<span data-ttu-id="f3373-146">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="f3373-146">Network Settings Schema</span></span>](index.md)
