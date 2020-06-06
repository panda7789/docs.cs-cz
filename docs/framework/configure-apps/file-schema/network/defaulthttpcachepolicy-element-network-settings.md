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
ms.openlocfilehash: c5029a7d1e53c28d0abb232efdc3e0bd2c9658d4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088421"
---
# <a name="defaulthttpcachepolicy-element-network-settings"></a><span data-ttu-id="55a48-102">\<defaultHttpCachePolicy> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="55a48-102">\<defaultHttpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="55a48-103">Popisuje, zda je ukládání do mezipaměti protokolu HTTP aktivní a popisuje výchozí zásady ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="55a48-103">Describes whether HTTP caching is active and describes the default caching policy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultHttpCachePolicy>**

## <a name="syntax"></a><span data-ttu-id="55a48-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55a48-104">Syntax</span></span>  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55a48-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="55a48-105">Attributes and Elements</span></span>  
 <span data-ttu-id="55a48-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="55a48-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55a48-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="55a48-107">Attributes</span></span>  
  
|<span data-ttu-id="55a48-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="55a48-108">Attribute</span></span>|<span data-ttu-id="55a48-109">Popis</span><span class="sxs-lookup"><span data-stu-id="55a48-109">Description</span></span>|  
|---------------|-----------------|  
|`maximumAge`|<span data-ttu-id="55a48-110">Určuje maximální časový interval, po jehož uplynutí je objekt uložený v mezipaměti označený jako neplatný.</span><span class="sxs-lookup"><span data-stu-id="55a48-110">Specifies the maximum time interval before a cached object is marked as expired.</span></span>|  
|`maximumStale`|<span data-ttu-id="55a48-111">Určuje maximální dobu, po jejímž uplynutí je vypočítaná doba aktuálnosti, než je objekt uložený v mezipaměti označený jako neplatný.</span><span class="sxs-lookup"><span data-stu-id="55a48-111">Specifies the maximum time past the computed freshness time before a cached object is marked as expired.</span></span>|  
|`minimumFresh`|<span data-ttu-id="55a48-112">Určuje minimální dobu, po kterou bude objekt v mezipaměti považován za čerstvý.</span><span class="sxs-lookup"><span data-stu-id="55a48-112">Specifies the minimum time for a cached object to be considered fresh.</span></span>|  
|`policyLevel`|<span data-ttu-id="55a48-113">Určuje, jestli jsou zásady ukládání do mezipaměti automatické, nebo jestli se mezipaměť nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="55a48-113">Specifies whether the caching policy is automatic, or whether the cache is bypassed.</span></span> <span data-ttu-id="55a48-114">Výchozí hodnota je `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="55a48-114">The default value is `BypassCache`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55a48-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="55a48-115">Child Elements</span></span>  
 <span data-ttu-id="55a48-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="55a48-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55a48-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="55a48-117">Parent Elements</span></span>  
  
|<span data-ttu-id="55a48-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="55a48-118">Element</span></span>|<span data-ttu-id="55a48-119">Description</span><span class="sxs-lookup"><span data-stu-id="55a48-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55a48-120">requestCaching</span><span class="sxs-lookup"><span data-stu-id="55a48-120">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="55a48-121">Řídí mechanismus ukládání do mezipaměti pro síťové požadavky.</span><span class="sxs-lookup"><span data-stu-id="55a48-121">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55a48-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="55a48-122">Remarks</span></span>  
 <span data-ttu-id="55a48-123">Hodnota `policyLevel` atributu je buď `BypassCache` nebo `Default` .</span><span class="sxs-lookup"><span data-stu-id="55a48-123">The value for the `policyLevel` attribute is either `BypassCache` or `Default`.</span></span>  
  
 <span data-ttu-id="55a48-124">Hodnoty pro `maximumAge` prvky, `maximumStale` a `minimumFresh` jsou buď explicitním časovým intervalem formátu *d*.\* HH*:*mm*:*SS\* (dny, hodiny, minuty a sekundy) nebo konstanty `minValue` nebo `maxValue` , podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="55a48-124">Values for the `maximumAge`, `maximumStale`, and `minimumFresh` elements are either an explicit time interval with a format of *d*.*hh*:*mm*:*ss* (days, hours, minutes, and seconds), or the constants `minValue` or `maxValue`, as appropriate.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="55a48-125">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="55a48-125">Configuration Files</span></span>  
 <span data-ttu-id="55a48-126">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="55a48-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="55a48-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="55a48-127">Example</span></span>  
 <span data-ttu-id="55a48-128">Následující příklad ukazuje, jak zadat minimální dobu v čase 6 hodin, maximální dobu stáří dvou dnů a maximální zastaralou dobu čtyř hodin.</span><span class="sxs-lookup"><span data-stu-id="55a48-128">The following example shows how to specify a minimum fresh time of six hours, a maximum age time of two days, and a maximum stale time of four hours.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="55a48-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="55a48-129">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="55a48-130">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="55a48-130">Network Settings Schema</span></span>](index.md)
