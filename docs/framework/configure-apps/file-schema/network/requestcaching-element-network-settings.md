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
ms.openlocfilehash: af290e4b9258a08425a15e297ff538502edea916
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674425"
---
# <a name="requestcaching-element-network-settings"></a><span data-ttu-id="fb471-102">\<requestCaching – > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="fb471-102">\<requestCaching> Element (Network Settings)</span></span>
<span data-ttu-id="fb471-103">Určuje mechanismus ukládání do mezipaměti pro síťové požadavky.</span><span class="sxs-lookup"><span data-stu-id="fb471-103">Controls the caching mechanism for network requests.</span></span>  
  
 <span data-ttu-id="fb471-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="fb471-104">\<configuration></span></span>  
<span data-ttu-id="fb471-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="fb471-105">\<system.net></span></span>  
<span data-ttu-id="fb471-106">\<requestCaching></span><span class="sxs-lookup"><span data-stu-id="fb471-106">\<requestCaching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb471-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb471-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb471-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fb471-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fb471-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fb471-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb471-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="fb471-110">Attributes</span></span>  
  
|<span data-ttu-id="fb471-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="fb471-111">Attribute</span></span>|<span data-ttu-id="fb471-112">Popis</span><span class="sxs-lookup"><span data-stu-id="fb471-112">Description</span></span>|  
|---------------|-----------------|  
|`isPrivateCache`|<span data-ttu-id="fb471-113">Určuje, zda mezipaměti zajišťuje izolaci mezi informace o různé uživatele.</span><span class="sxs-lookup"><span data-stu-id="fb471-113">Specifies whether the cache provides isolation between the information of different users.</span></span> <span data-ttu-id="fb471-114">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="fb471-114">The default value is `true`.</span></span> <span data-ttu-id="fb471-115">Tato hodnota by měla být `false` pro aplikace střední vrstvy.</span><span class="sxs-lookup"><span data-stu-id="fb471-115">This value should be `false` for middle tier applications.</span></span>|  
|`disableAllCaching`|<span data-ttu-id="fb471-116">Určuje, že ukládání do mezipaměti je zakázaná pro všechny odpovědi na webu a nedají se přepsat prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="fb471-116">Specifies that caching is disabled for all Web responses, and cannot be overridden programmatically.</span></span>|  
|`defaultPolicyLevel`|<span data-ttu-id="fb471-117">Jedna z hodnot v <xref:System.Net.Cache.RequestCacheLevel> výčtu.</span><span class="sxs-lookup"><span data-stu-id="fb471-117">One of the values in the <xref:System.Net.Cache.RequestCacheLevel> enumeration.</span></span> <span data-ttu-id="fb471-118">Výchozí hodnota je `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="fb471-118">The default value is `BypassCache`.</span></span>|  
|`unspecifiedMaximumAge`|<span data-ttu-id="fb471-119">Určuje výchozí dobu, po jejímž uplynutí obsah označena jako neplatná.</span><span class="sxs-lookup"><span data-stu-id="fb471-119">Specifies the default time after which content is marked as expired.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="fb471-120">PolicyLevel, který atribut</span><span class="sxs-lookup"><span data-stu-id="fb471-120">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="fb471-121">Value</span><span class="sxs-lookup"><span data-stu-id="fb471-121">Value</span></span>|<span data-ttu-id="fb471-122">Popis</span><span class="sxs-lookup"><span data-stu-id="fb471-122">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="fb471-123">Vrátí uložený v mezipaměti prostředků, pokud je prostředek čerstvé, délka obsahu je správná, a vypršení platnosti, úpravu a délka obsahu atributy jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="fb471-123">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="fb471-124">Vrátí prostředek ze serveru.</span><span class="sxs-lookup"><span data-stu-id="fb471-124">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="fb471-125">Vrátí uložený v mezipaměti prostředků, pokud délka obsahu je k dispozici a odpovídá velikosti položky.</span><span class="sxs-lookup"><span data-stu-id="fb471-125">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="fb471-126">Vrátí uložený v mezipaměti prostředků, pokud délka obsahu je k dispozici a odpovídá velikost položky; v opačném případě zdroj se stáhne ze serveru a je vrátit zpět volajícímu.</span><span class="sxs-lookup"><span data-stu-id="fb471-126">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="fb471-127">Vrátí uložený v mezipaměti prostředků, pokud časové razítko v mezipaměti prostředku je stejný jako časové razítko prostředků na serveru. v opačném případě zdroj se stáhne ze serveru, uloží se do mezipaměti a je vrátit zpět volajícímu.</span><span class="sxs-lookup"><span data-stu-id="fb471-127">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and is returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="fb471-128">Soubory ke stažení prostředku ze serveru, ukládá do mezipaměti a vrátí řízení volajícímu prostředku.</span><span class="sxs-lookup"><span data-stu-id="fb471-128">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="fb471-129">Pokud existuje prostředek v mezipaměti, je odstranit.</span><span class="sxs-lookup"><span data-stu-id="fb471-129">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="fb471-130">Zdroj se stáhne ze serveru a je vrátit zpět volajícímu.</span><span class="sxs-lookup"><span data-stu-id="fb471-130">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="fb471-131">Splňuje požadavek s použitím uložené v mezipaměti kopie prostředku časové razítko je stejný jako časové razítko prostředků na serveru. v opačném případě zdroj se stáhne ze serveru, zobrazí volajícímu a je uložen v mezipaměti,</span><span class="sxs-lookup"><span data-stu-id="fb471-131">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and is stored in the cache,</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb471-132">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fb471-132">Child Elements</span></span>  
  
|<span data-ttu-id="fb471-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="fb471-133">Element</span></span>|<span data-ttu-id="fb471-134">Popis</span><span class="sxs-lookup"><span data-stu-id="fb471-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb471-135">defaultHttpCachePolicy</span><span class="sxs-lookup"><span data-stu-id="fb471-135">defaultHttpCachePolicy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaulthttpcachepolicy-element-network-settings.md)|<span data-ttu-id="fb471-136">Volitelný element.</span><span class="sxs-lookup"><span data-stu-id="fb471-136">Optional element.</span></span><br /><br /> <span data-ttu-id="fb471-137">Popisuje, zda HTTP, ukládání do mezipaměti je aktivní a popisuje výchozí zásady ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="fb471-137">Describes whether HTTP caching is active and describes the default caching policy.</span></span>|  
|[<span data-ttu-id="fb471-138">\<defaultFtpCachePolicy> Element (Network Settings)</span><span class="sxs-lookup"><span data-stu-id="fb471-138">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultftpcachepolicy-element-network-settings.md)|<span data-ttu-id="fb471-139">Volitelný element.</span><span class="sxs-lookup"><span data-stu-id="fb471-139">Optional element.</span></span><br /><br /> <span data-ttu-id="fb471-140">Popisuje, zda ukládání do mezipaměti serveru FTP je aktivní a popisuje výchozí zásady ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="fb471-140">Describes whether FTP caching is active and describes the default caching policy.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fb471-141">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fb471-141">Parent Elements</span></span>  
  
|<span data-ttu-id="fb471-142">Prvek</span><span class="sxs-lookup"><span data-stu-id="fb471-142">Element</span></span>|<span data-ttu-id="fb471-143">Popis</span><span class="sxs-lookup"><span data-stu-id="fb471-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb471-144">system.net</span><span class="sxs-lookup"><span data-stu-id="fb471-144">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="fb471-145">Obsahuje nastavení, která určují, jak rozhraní .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="fb471-145">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fb471-146">Příklad</span><span class="sxs-lookup"><span data-stu-id="fb471-146">Example</span></span>  
 <span data-ttu-id="fb471-147">Následující příklad ukazuje, jak zakázat ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="fb471-147">The following example shows how to disable all caching.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fb471-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb471-148">See also</span></span>

- <xref:System.Net.Cache?displayProperty=nameWithType>
- [<span data-ttu-id="fb471-149">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="fb471-149">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
