---
title: <defaultHttpCachePolicy> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultHttpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultHttpCachePolicy
helpviewer_keywords:
- defaultHttpCachePolicy element
- <defaultHttpCachePolicy> element
ms.assetid: 2c1247d0-39b0-4c12-919a-a925ce075c79
ms.openlocfilehash: 1dd31884a072d16ed004c0b49be61e8cee399787
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664155"
---
# <a name="defaulthttpcachepolicy-element-network-settings"></a><span data-ttu-id="25647-102">\<defaultHttpCachePolicy – element > (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="25647-102">\<defaultHttpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="25647-103">Popisuje, zda je ukládání do mezipaměti protokolu HTTP aktivní a popisuje výchozí zásady ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="25647-103">Describes whether HTTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="25647-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="25647-104">\<configuration></span></span>  
<span data-ttu-id="25647-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="25647-105">\<system.net></span></span>  
<span data-ttu-id="25647-106">\<requestCaching></span><span class="sxs-lookup"><span data-stu-id="25647-106">\<requestCaching></span></span>  
<span data-ttu-id="25647-107">\<defaultHttpCachePolicy></span><span class="sxs-lookup"><span data-stu-id="25647-107">\<defaultHttpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25647-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25647-108">Syntax</span></span>  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25647-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="25647-109">Attributes and Elements</span></span>  
 <span data-ttu-id="25647-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="25647-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25647-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="25647-111">Attributes</span></span>  
  
|<span data-ttu-id="25647-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="25647-112">Attribute</span></span>|<span data-ttu-id="25647-113">Popis</span><span class="sxs-lookup"><span data-stu-id="25647-113">Description</span></span>|  
|---------------|-----------------|  
|`maximumAge`|<span data-ttu-id="25647-114">Určuje maximální časový interval, po jehož uplynutí je objekt uložený v mezipaměti označený jako neplatný.</span><span class="sxs-lookup"><span data-stu-id="25647-114">Specifies the maximum time interval before a cached object is marked as expired.</span></span>|  
|`maximumStale`|<span data-ttu-id="25647-115">Určuje maximální dobu, po jejímž uplynutí je vypočítaná doba aktuálnosti, než je objekt uložený v mezipaměti označený jako neplatný.</span><span class="sxs-lookup"><span data-stu-id="25647-115">Specifies the maximum time past the computed freshness time before a cached object is marked as expired.</span></span>|  
|`minimumFresh`|<span data-ttu-id="25647-116">Určuje minimální dobu, po kterou bude objekt v mezipaměti považován za čerstvý.</span><span class="sxs-lookup"><span data-stu-id="25647-116">Specifies the minimum time for a cached object to be considered fresh.</span></span>|  
|`policyLevel`|<span data-ttu-id="25647-117">Určuje, jestli jsou zásady ukládání do mezipaměti automatické, nebo jestli se mezipaměť nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="25647-117">Specifies whether the caching policy is automatic, or whether the cache is bypassed.</span></span> <span data-ttu-id="25647-118">Výchozí hodnota je `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="25647-118">The default value is `BypassCache`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="25647-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="25647-119">Child Elements</span></span>  
 <span data-ttu-id="25647-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="25647-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="25647-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="25647-121">Parent Elements</span></span>  
  
|<span data-ttu-id="25647-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="25647-122">Element</span></span>|<span data-ttu-id="25647-123">Popis</span><span class="sxs-lookup"><span data-stu-id="25647-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25647-124">requestCaching</span><span class="sxs-lookup"><span data-stu-id="25647-124">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="25647-125">Řídí mechanismus ukládání do mezipaměti pro síťové požadavky.</span><span class="sxs-lookup"><span data-stu-id="25647-125">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25647-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25647-126">Remarks</span></span>  
 <span data-ttu-id="25647-127">Hodnota `policyLevel` atributu je buď `BypassCache` nebo `Default`.</span><span class="sxs-lookup"><span data-stu-id="25647-127">The value for the `policyLevel` attribute is either `BypassCache` or `Default`.</span></span>  
  
 <span data-ttu-id="25647-128">Hodnoty pro `maximumAge`prvky, `maximumStale`a `minimumFresh` jsou buď explicitním časovým intervalem formátu *d*. *HH*:*mm*:*SS* (dny, hodiny, minuty a sekundy) nebo konstanty `minValue` nebo `maxValue`, podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="25647-128">Values for the `maximumAge`, `maximumStale`, and `minimumFresh` elements are either an explicit time interval with a format of *d*.*hh*:*mm*:*ss* (days, hours, minutes, and seconds), or the constants `minValue` or `maxValue`, as appropriate.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="25647-129">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="25647-129">Configuration Files</span></span>  
 <span data-ttu-id="25647-130">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="25647-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="25647-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="25647-131">Example</span></span>  
 <span data-ttu-id="25647-132">Následující příklad ukazuje, jak zadat minimální dobu v čase 6 hodin, maximální dobu stáří dvou dnů a maximální zastaralou dobu čtyř hodin.</span><span class="sxs-lookup"><span data-stu-id="25647-132">The following example shows how to specify a minimum fresh time of six hours, a maximum age time of two days, and a maximum stale time of four hours.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultHttpCachePolicy  
        minimumFresh="0.06:00:00"  
        maximumAge="2.00:00:00"  
        maximumStale="0.04:00:00"
      />  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="25647-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25647-133">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="25647-134">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="25647-134">Network Settings Schema</span></span>](index.md)
