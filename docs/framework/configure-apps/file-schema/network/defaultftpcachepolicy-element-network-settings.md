---
title: '&lt;defaultftpcachepolicy –&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
author: mcleblanc
ms.author: markl
ms.openlocfilehash: e03fb02bd351058c1fcdedb8367d03318418a12c
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2018
ms.locfileid: "49316438"
---
# <a name="ltdefaultftpcachepolicygt-element-network-settings"></a><span data-ttu-id="2f523-102">&lt;defaultftpcachepolicy –&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="2f523-102">&lt;defaultFtpCachePolicy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="2f523-103">Popisuje, zda ukládání do mezipaměti serveru FTP je aktivní a popisuje výchozí zásady ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="2f523-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="2f523-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="2f523-104">\<configuration></span></span>  
<span data-ttu-id="2f523-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="2f523-105">\<system.net></span></span>  
<span data-ttu-id="2f523-106">\<requestCaching – ></span><span class="sxs-lookup"><span data-stu-id="2f523-106">\<requestCaching></span></span>  
<span data-ttu-id="2f523-107">\<defaultftpcachepolicy – ></span><span class="sxs-lookup"><span data-stu-id="2f523-107">\<defaultFtpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f523-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f523-108">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f523-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2f523-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2f523-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2f523-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f523-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="2f523-111">Attributes</span></span>  
  
|<span data-ttu-id="2f523-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="2f523-112">Attribute</span></span>|<span data-ttu-id="2f523-113">Popis</span><span class="sxs-lookup"><span data-stu-id="2f523-113">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="2f523-114">Určuje FTP zásady ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="2f523-114">Specifies the FTP caching policy.</span></span> <span data-ttu-id="2f523-115">Výchozí hodnota je `Default`.</span><span class="sxs-lookup"><span data-stu-id="2f523-115">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="2f523-116">PolicyLevel, který atribut</span><span class="sxs-lookup"><span data-stu-id="2f523-116">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="2f523-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2f523-117">Value</span></span>|<span data-ttu-id="2f523-118">Popis</span><span class="sxs-lookup"><span data-stu-id="2f523-118">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="2f523-119">Vrátí uložený v mezipaměti prostředků, pokud je prostředek čerstvé, délka obsahu je správná, a vypršení platnosti, úpravu a délka obsahu atributy jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="2f523-119">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="2f523-120">Vrátí prostředek ze serveru.</span><span class="sxs-lookup"><span data-stu-id="2f523-120">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="2f523-121">Vrátí uložený v mezipaměti prostředků, pokud délka obsahu je k dispozici a odpovídá velikosti položky.</span><span class="sxs-lookup"><span data-stu-id="2f523-121">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="2f523-122">Vrátí uložený v mezipaměti prostředků, pokud délka obsahu je k dispozici a odpovídá velikost položky; v opačném případě zdroj se stáhne ze serveru a je vrátit zpět volajícímu.</span><span class="sxs-lookup"><span data-stu-id="2f523-122">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="2f523-123">Vrátí uložený v mezipaměti prostředků, pokud časové razítko v mezipaměti prostředku je stejný jako časové razítko prostředků na serveru. v opačném případě zdroj staženy ze serveru, uložená v mezipaměti a vrátit zpět volajícímu.</span><span class="sxs-lookup"><span data-stu-id="2f523-123">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="2f523-124">Soubory ke stažení prostředku ze serveru, ukládá do mezipaměti a vrátí řízení volajícímu prostředku.</span><span class="sxs-lookup"><span data-stu-id="2f523-124">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="2f523-125">Pokud existuje prostředek v mezipaměti, je odstranit.</span><span class="sxs-lookup"><span data-stu-id="2f523-125">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="2f523-126">Zdroj se stáhne ze serveru a je vrátit zpět volajícímu.</span><span class="sxs-lookup"><span data-stu-id="2f523-126">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="2f523-127">Splňuje požadavek s použitím uložené v mezipaměti kopie prostředku časové razítko je stejný jako časové razítko prostředků na serveru. v opačném případě zdroj staženy ze serveru, zobrazí volajícímu a uložená v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="2f523-127">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2f523-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2f523-128">Child Elements</span></span>  
 <span data-ttu-id="2f523-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="2f523-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2f523-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2f523-130">Parent Elements</span></span>  
  
|<span data-ttu-id="2f523-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="2f523-131">Element</span></span>|<span data-ttu-id="2f523-132">Popis</span><span class="sxs-lookup"><span data-stu-id="2f523-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2f523-133">requestCaching –</span><span class="sxs-lookup"><span data-stu-id="2f523-133">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="2f523-134">Určuje mechanismus ukládání do mezipaměti pro síťové požadavky.</span><span class="sxs-lookup"><span data-stu-id="2f523-134">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f523-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2f523-135">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f523-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="2f523-136">Example</span></span>  
 <span data-ttu-id="2f523-137">Následující příklad ukazuje, jak určit zásady ukládání do mezipaměti FTP `NoCacheNoStore`.</span><span class="sxs-lookup"><span data-stu-id="2f523-137">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2f523-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="2f523-138">See Also</span></span>  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.Cache.RequestCacheLevel>  
 [<span data-ttu-id="2f523-139">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="2f523-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
