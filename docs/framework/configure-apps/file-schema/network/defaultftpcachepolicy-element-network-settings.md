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
ms.openlocfilehash: 9261a430642cb4d5ac4507835bd0fd3561bd8c02
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088431"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a><span data-ttu-id="e64cf-102">\<defaultFtpCachePolicy> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="e64cf-102">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="e64cf-103">Popisuje, zda je ukládání do mezipaměti FTP aktivní a popisuje výchozí zásady ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="e64cf-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultFtpCachePolicy>**

## <a name="syntax"></a><span data-ttu-id="e64cf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e64cf-104">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e64cf-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e64cf-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e64cf-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e64cf-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e64cf-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="e64cf-107">Attributes</span></span>  
  
|<span data-ttu-id="e64cf-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="e64cf-108">Attribute</span></span>|<span data-ttu-id="e64cf-109">Popis</span><span class="sxs-lookup"><span data-stu-id="e64cf-109">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="e64cf-110">Určuje zásady ukládání do mezipaměti FTP.</span><span class="sxs-lookup"><span data-stu-id="e64cf-110">Specifies the FTP caching policy.</span></span> <span data-ttu-id="e64cf-111">Výchozí hodnota je `Default`.</span><span class="sxs-lookup"><span data-stu-id="e64cf-111">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="e64cf-112">policyLevel – atribut</span><span class="sxs-lookup"><span data-stu-id="e64cf-112">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="e64cf-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e64cf-113">Value</span></span>|<span data-ttu-id="e64cf-114">Description</span><span class="sxs-lookup"><span data-stu-id="e64cf-114">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="e64cf-115">Vrátí prostředek uložený v mezipaměti, pokud je prostředek v čerstvém stavu, že velikost obsahu je přesná a že jsou k dispozici atributy vypršení platnosti, změna a délka obsahu.</span><span class="sxs-lookup"><span data-stu-id="e64cf-115">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="e64cf-116">Vrátí prostředek ze serveru.</span><span class="sxs-lookup"><span data-stu-id="e64cf-116">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="e64cf-117">Vrátí prostředek uložený v mezipaměti, pokud je k dispozici délka obsahu a odpovídá velikosti položky.</span><span class="sxs-lookup"><span data-stu-id="e64cf-117">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="e64cf-118">Vrátí prostředek uložený v mezipaměti, pokud je zadaná délka obsahu a odpovídá velikosti položky. v opačném případě se prostředek stáhne ze serveru a vrátí se volajícímu.</span><span class="sxs-lookup"><span data-stu-id="e64cf-118">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="e64cf-119">Vrátí prostředek uložený v mezipaměti, pokud je časové razítko prostředku v mezipaměti stejné jako časové razítko prostředku na serveru. v opačném případě se prostředek stáhne ze serveru, uloží se do mezipaměti a vrátí volajícímu.</span><span class="sxs-lookup"><span data-stu-id="e64cf-119">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="e64cf-120">Stáhne prostředek ze serveru, uloží ho do mezipaměti a vrátí prostředek volajícímu.</span><span class="sxs-lookup"><span data-stu-id="e64cf-120">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="e64cf-121">Pokud prostředek uložený v mezipaměti existuje, odstraní se.</span><span class="sxs-lookup"><span data-stu-id="e64cf-121">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="e64cf-122">Prostředek se stáhne ze serveru a vrátí se volajícímu.</span><span class="sxs-lookup"><span data-stu-id="e64cf-122">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="e64cf-123">Splňuje požadavky pomocí kopie prostředku uložené v mezipaměti, pokud je časové razítko stejné jako časové razítko prostředku na serveru. v opačném případě se prostředek stáhne ze serveru, zobrazí se volajícímu a uloží se do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="e64cf-123">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e64cf-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e64cf-124">Child Elements</span></span>  
 <span data-ttu-id="e64cf-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="e64cf-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e64cf-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e64cf-126">Parent Elements</span></span>  
  
|<span data-ttu-id="e64cf-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="e64cf-127">Element</span></span>|<span data-ttu-id="e64cf-128">Description</span><span class="sxs-lookup"><span data-stu-id="e64cf-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e64cf-129">requestCaching</span><span class="sxs-lookup"><span data-stu-id="e64cf-129">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="e64cf-130">Řídí mechanismus ukládání do mezipaměti pro síťové požadavky.</span><span class="sxs-lookup"><span data-stu-id="e64cf-130">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e64cf-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e64cf-131">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="e64cf-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="e64cf-132">Example</span></span>  
 <span data-ttu-id="e64cf-133">Následující příklad ukazuje, jak určit zásady ukládání do mezipaměti FTP pro `NoCacheNoStore` .</span><span class="sxs-lookup"><span data-stu-id="e64cf-133">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e64cf-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="e64cf-134">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="e64cf-135">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="e64cf-135">Network Settings Schema</span></span>](index.md)
