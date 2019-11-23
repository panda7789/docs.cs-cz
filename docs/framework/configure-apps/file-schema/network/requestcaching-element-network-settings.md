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
ms.openlocfilehash: f0979d2e0caeb0b22b90572aef0ad53235020f1d
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697830"
---
# <a name="requestcaching-element-network-settings"></a><span data-ttu-id="ebe56-102">\<element > requestCaching (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="ebe56-102">\<requestCaching> Element (Network Settings)</span></span>
<span data-ttu-id="ebe56-103">Řídí mechanismus ukládání do mezipaměti pro síťové požadavky.</span><span class="sxs-lookup"><span data-stu-id="ebe56-103">Controls the caching mechanism for network requests.</span></span>  
  
[<span data-ttu-id="ebe56-104">**Konfigurace \<>** </span><span class="sxs-lookup"><span data-stu-id="ebe56-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="ebe56-105">&nbsp;&nbsp;[ **\<System. NET >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="ebe56-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="ebe56-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<requestCaching >**</span><span class="sxs-lookup"><span data-stu-id="ebe56-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<requestCaching>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebe56-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ebe56-107">Syntax</span></span>  
  
```xml  
<requestCaching  
  isPrivateCache ="true|false"  
  disableAllCaching="true|false"  
  defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
  unspecifiedMaximumAge= "d.hh.mm.ss">  
    <defaultHttpCachePolicy>...</defaultHttpCachePolicy>  
    <defaultFtpCachePolicy>...</defaultFtpCachePolicy>  
</requestCaching>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ebe56-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ebe56-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ebe56-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ebe56-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ebe56-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="ebe56-110">Attributes</span></span>  
  
|<span data-ttu-id="ebe56-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="ebe56-111">Attribute</span></span>|<span data-ttu-id="ebe56-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ebe56-112">Description</span></span>|  
|---------------|-----------------|  
|`isPrivateCache`|<span data-ttu-id="ebe56-113">Určuje, jestli mezipaměť poskytuje izolaci mezi informacemi různých uživatelů.</span><span class="sxs-lookup"><span data-stu-id="ebe56-113">Specifies whether the cache provides isolation between the information of different users.</span></span> <span data-ttu-id="ebe56-114">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="ebe56-114">The default value is `true`.</span></span> <span data-ttu-id="ebe56-115">Tato hodnota by měla být `false` pro aplikace střední vrstvy.</span><span class="sxs-lookup"><span data-stu-id="ebe56-115">This value should be `false` for middle tier applications.</span></span>|  
|`disableAllCaching`|<span data-ttu-id="ebe56-116">Určuje, že ukládání do mezipaměti je pro všechny webové odpovědi zakázané, a nedá se přepsat programově.</span><span class="sxs-lookup"><span data-stu-id="ebe56-116">Specifies that caching is disabled for all Web responses, and cannot be overridden programmatically.</span></span>|  
|`defaultPolicyLevel`|<span data-ttu-id="ebe56-117">Jedna z hodnot ve výčtu <xref:System.Net.Cache.RequestCacheLevel>.</span><span class="sxs-lookup"><span data-stu-id="ebe56-117">One of the values in the <xref:System.Net.Cache.RequestCacheLevel> enumeration.</span></span> <span data-ttu-id="ebe56-118">Výchozí hodnota je `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="ebe56-118">The default value is `BypassCache`.</span></span>|  
|`unspecifiedMaximumAge`|<span data-ttu-id="ebe56-119">Určuje výchozí čas, po kterém je obsah označen jako konec platnosti.</span><span class="sxs-lookup"><span data-stu-id="ebe56-119">Specifies the default time after which content is marked as expired.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="ebe56-120">policyLevel – atribut</span><span class="sxs-lookup"><span data-stu-id="ebe56-120">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="ebe56-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ebe56-121">Value</span></span>|<span data-ttu-id="ebe56-122">Popis</span><span class="sxs-lookup"><span data-stu-id="ebe56-122">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="ebe56-123">Vrátí prostředek uložený v mezipaměti, pokud je prostředek v čerstvém stavu, že velikost obsahu je přesná a že jsou k dispozici atributy vypršení platnosti, změna a délka obsahu.</span><span class="sxs-lookup"><span data-stu-id="ebe56-123">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="ebe56-124">Vrátí prostředek ze serveru.</span><span class="sxs-lookup"><span data-stu-id="ebe56-124">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="ebe56-125">Vrátí prostředek uložený v mezipaměti, pokud je k dispozici délka obsahu a odpovídá velikosti položky.</span><span class="sxs-lookup"><span data-stu-id="ebe56-125">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="ebe56-126">Vrátí prostředek uložený v mezipaměti, pokud je zadaná délka obsahu a odpovídá velikosti položky. v opačném případě se prostředek stáhne ze serveru a vrátí se volajícímu.</span><span class="sxs-lookup"><span data-stu-id="ebe56-126">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="ebe56-127">Vrátí prostředek uložený v mezipaměti, pokud je časové razítko prostředku v mezipaměti stejné jako časové razítko prostředku na serveru. v opačném případě se prostředek stáhne ze serveru, uloží se do mezipaměti a vrátí se volajícímu.</span><span class="sxs-lookup"><span data-stu-id="ebe56-127">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and is returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="ebe56-128">Stáhne prostředek ze serveru, uloží ho do mezipaměti a vrátí prostředek volajícímu.</span><span class="sxs-lookup"><span data-stu-id="ebe56-128">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="ebe56-129">Pokud prostředek uložený v mezipaměti existuje, odstraní se.</span><span class="sxs-lookup"><span data-stu-id="ebe56-129">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="ebe56-130">Prostředek se stáhne ze serveru a vrátí se volajícímu.</span><span class="sxs-lookup"><span data-stu-id="ebe56-130">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="ebe56-131">Splňuje požadavky pomocí kopie prostředku uložené v mezipaměti, pokud je časové razítko stejné jako časové razítko prostředku na serveru. v opačném případě se prostředek stáhne ze serveru, zobrazí se volajícímu a uloží se do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="ebe56-131">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and is stored in the cache,</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ebe56-132">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ebe56-132">Child Elements</span></span>  
  
|<span data-ttu-id="ebe56-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="ebe56-133">Element</span></span>|<span data-ttu-id="ebe56-134">Popis</span><span class="sxs-lookup"><span data-stu-id="ebe56-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ebe56-135">defaultHttpCachePolicy</span><span class="sxs-lookup"><span data-stu-id="ebe56-135">defaultHttpCachePolicy</span></span>](defaulthttpcachepolicy-element-network-settings.md)|<span data-ttu-id="ebe56-136">Volitelný element.</span><span class="sxs-lookup"><span data-stu-id="ebe56-136">Optional element.</span></span><br /><br /> <span data-ttu-id="ebe56-137">Popisuje, zda je ukládání do mezipaměti protokolu HTTP aktivní a popisuje výchozí zásady ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="ebe56-137">Describes whether HTTP caching is active and describes the default caching policy.</span></span>|  
|[<span data-ttu-id="ebe56-138">\<element > defaultFtpCachePolicy (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="ebe56-138">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>](defaultftpcachepolicy-element-network-settings.md)|<span data-ttu-id="ebe56-139">Volitelný element.</span><span class="sxs-lookup"><span data-stu-id="ebe56-139">Optional element.</span></span><br /><br /> <span data-ttu-id="ebe56-140">Popisuje, zda je ukládání do mezipaměti FTP aktivní a popisuje výchozí zásady ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="ebe56-140">Describes whether FTP caching is active and describes the default caching policy.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ebe56-141">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ebe56-141">Parent Elements</span></span>  
  
|<span data-ttu-id="ebe56-142">Prvek</span><span class="sxs-lookup"><span data-stu-id="ebe56-142">Element</span></span>|<span data-ttu-id="ebe56-143">Popis</span><span class="sxs-lookup"><span data-stu-id="ebe56-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ebe56-144">system.net</span><span class="sxs-lookup"><span data-stu-id="ebe56-144">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="ebe56-145">Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="ebe56-145">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ebe56-146">Příklad</span><span class="sxs-lookup"><span data-stu-id="ebe56-146">Example</span></span>  
 <span data-ttu-id="ebe56-147">Následující příklad ukazuje, jak zakázat ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="ebe56-147">The following example shows how to disable all caching.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ebe56-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ebe56-148">See also</span></span>

- <xref:System.Net.Cache?displayProperty=nameWithType>
- [<span data-ttu-id="ebe56-149">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="ebe56-149">Network Settings Schema</span></span>](index.md)
