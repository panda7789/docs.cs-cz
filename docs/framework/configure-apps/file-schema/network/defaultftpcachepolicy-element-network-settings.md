---
title: <defaultFtpCachePolicy> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
ms.openlocfilehash: 7ff44f0251936d51b4e396c37c53322efa110227
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659412"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a><span data-ttu-id="36494-102">\<defaultFtpCachePolicy – element > (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="36494-102">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="36494-103">Popisuje, zda je ukládání do mezipaměti FTP aktivní a popisuje výchozí zásady ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="36494-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="36494-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="36494-104">\<configuration></span></span>  
<span data-ttu-id="36494-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="36494-105">\<system.net></span></span>  
<span data-ttu-id="36494-106">\<requestCaching></span><span class="sxs-lookup"><span data-stu-id="36494-106">\<requestCaching></span></span>  
<span data-ttu-id="36494-107">\<defaultFtpCachePolicy></span><span class="sxs-lookup"><span data-stu-id="36494-107">\<defaultFtpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36494-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36494-108">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36494-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="36494-109">Attributes and Elements</span></span>  
 <span data-ttu-id="36494-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="36494-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36494-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="36494-111">Attributes</span></span>  
  
|<span data-ttu-id="36494-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="36494-112">Attribute</span></span>|<span data-ttu-id="36494-113">Popis</span><span class="sxs-lookup"><span data-stu-id="36494-113">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="36494-114">Určuje zásady ukládání do mezipaměti FTP.</span><span class="sxs-lookup"><span data-stu-id="36494-114">Specifies the FTP caching policy.</span></span> <span data-ttu-id="36494-115">Výchozí hodnota je `Default`.</span><span class="sxs-lookup"><span data-stu-id="36494-115">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="36494-116">policyLevel – atribut</span><span class="sxs-lookup"><span data-stu-id="36494-116">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="36494-117">Value</span><span class="sxs-lookup"><span data-stu-id="36494-117">Value</span></span>|<span data-ttu-id="36494-118">Popis</span><span class="sxs-lookup"><span data-stu-id="36494-118">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="36494-119">Vrátí prostředek uložený v mezipaměti, pokud je prostředek v čerstvém stavu, že velikost obsahu je přesná a že jsou k dispozici atributy vypršení platnosti, změna a délka obsahu.</span><span class="sxs-lookup"><span data-stu-id="36494-119">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="36494-120">Vrátí prostředek ze serveru.</span><span class="sxs-lookup"><span data-stu-id="36494-120">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="36494-121">Vrátí prostředek uložený v mezipaměti, pokud je k dispozici délka obsahu a odpovídá velikosti položky.</span><span class="sxs-lookup"><span data-stu-id="36494-121">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="36494-122">Vrátí prostředek uložený v mezipaměti, pokud je zadaná délka obsahu a odpovídá velikosti položky. v opačném případě se prostředek stáhne ze serveru a vrátí se volajícímu.</span><span class="sxs-lookup"><span data-stu-id="36494-122">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="36494-123">Vrátí prostředek uložený v mezipaměti, pokud je časové razítko prostředku v mezipaměti stejné jako časové razítko prostředku na serveru. v opačném případě se prostředek stáhne ze serveru, uloží se do mezipaměti a vrátí volajícímu.</span><span class="sxs-lookup"><span data-stu-id="36494-123">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="36494-124">Stáhne prostředek ze serveru, uloží ho do mezipaměti a vrátí prostředek volajícímu.</span><span class="sxs-lookup"><span data-stu-id="36494-124">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="36494-125">Pokud prostředek uložený v mezipaměti existuje, odstraní se.</span><span class="sxs-lookup"><span data-stu-id="36494-125">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="36494-126">Prostředek se stáhne ze serveru a vrátí se volajícímu.</span><span class="sxs-lookup"><span data-stu-id="36494-126">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="36494-127">Splňuje požadavky pomocí kopie prostředku uložené v mezipaměti, pokud je časové razítko stejné jako časové razítko prostředku na serveru. v opačném případě se prostředek stáhne ze serveru, zobrazí se volajícímu a uloží se do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="36494-127">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="36494-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="36494-128">Child Elements</span></span>  
 <span data-ttu-id="36494-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="36494-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="36494-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="36494-130">Parent Elements</span></span>  
  
|<span data-ttu-id="36494-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="36494-131">Element</span></span>|<span data-ttu-id="36494-132">Popis</span><span class="sxs-lookup"><span data-stu-id="36494-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36494-133">requestCaching</span><span class="sxs-lookup"><span data-stu-id="36494-133">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="36494-134">Řídí mechanismus ukládání do mezipaměti pro síťové požadavky.</span><span class="sxs-lookup"><span data-stu-id="36494-134">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36494-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="36494-135">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="36494-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="36494-136">Example</span></span>  
 <span data-ttu-id="36494-137">Následující příklad ukazuje, jak určit zásady ukládání do mezipaměti FTP pro `NoCacheNoStore`.</span><span class="sxs-lookup"><span data-stu-id="36494-137">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultFtpCachePolicy  
        policyLevel="NoCacheNoStore">  
      </defaultFtpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="36494-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="36494-138">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="36494-139">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="36494-139">Network Settings Schema</span></span>](index.md)
