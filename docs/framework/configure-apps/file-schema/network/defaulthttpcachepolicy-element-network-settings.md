---
title: '&lt;defaulthttpcachepolicy –&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultHttpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultHttpCachePolicy
helpviewer_keywords:
- defaultHttpCachePolicy element
- <defaultHttpCachePolicy> element
ms.assetid: 2c1247d0-39b0-4c12-919a-a925ce075c79
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 1e1b27cb8c0df4450c1a08151af19913b65fc2b3
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028102"
---
# <a name="ltdefaulthttpcachepolicygt-element-network-settings"></a><span data-ttu-id="90e38-102">&lt;defaulthttpcachepolicy –&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="90e38-102">&lt;defaultHttpCachePolicy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="90e38-103">Popisuje, zda HTTP, ukládání do mezipaměti je aktivní a popisuje výchozí zásady ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="90e38-103">Describes whether HTTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="90e38-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="90e38-104">\<configuration></span></span>  
<span data-ttu-id="90e38-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="90e38-105">\<system.net></span></span>  
<span data-ttu-id="90e38-106">\<requestCaching – ></span><span class="sxs-lookup"><span data-stu-id="90e38-106">\<requestCaching></span></span>  
<span data-ttu-id="90e38-107">\<defaulthttpcachepolicy – ></span><span class="sxs-lookup"><span data-stu-id="90e38-107">\<defaultHttpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90e38-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90e38-108">Syntax</span></span>  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90e38-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="90e38-109">Attributes and Elements</span></span>  
 <span data-ttu-id="90e38-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="90e38-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90e38-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="90e38-111">Attributes</span></span>  
  
|<span data-ttu-id="90e38-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="90e38-112">Attribute</span></span>|<span data-ttu-id="90e38-113">Popis</span><span class="sxs-lookup"><span data-stu-id="90e38-113">Description</span></span>|  
|---------------|-----------------|  
|`maximumAge`|<span data-ttu-id="90e38-114">Určuje maximální dobu, než objekt uložený v mezipaměti je označena jako neplatná.</span><span class="sxs-lookup"><span data-stu-id="90e38-114">Specifies the maximum time interval before a cached object is marked as expired.</span></span>|  
|`maximumStale`|<span data-ttu-id="90e38-115">Určuje maximální dobu, po čase vypočítané aktuálnosti před objekt uložený v mezipaměti je označena jako neplatná.</span><span class="sxs-lookup"><span data-stu-id="90e38-115">Specifies the maximum time past the computed freshness time before a cached object is marked as expired.</span></span>|  
|`minimumFresh`|<span data-ttu-id="90e38-116">Určuje minimální dobu pro objekt uložený v mezipaměti k považovat za čerstvý.</span><span class="sxs-lookup"><span data-stu-id="90e38-116">Specifies the minimum time for a cached object to be considered fresh.</span></span>|  
|`policyLevel`|<span data-ttu-id="90e38-117">Určuje, zda je automatické zásady ukládání do mezipaměti, nebo zda obejít mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="90e38-117">Specifies whether the caching policy is automatic, or whether the cache is bypassed.</span></span> <span data-ttu-id="90e38-118">Výchozí hodnota je `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="90e38-118">The default value is `BypassCache`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90e38-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="90e38-119">Child Elements</span></span>  
 <span data-ttu-id="90e38-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="90e38-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="90e38-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="90e38-121">Parent Elements</span></span>  
  
|<span data-ttu-id="90e38-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="90e38-122">Element</span></span>|<span data-ttu-id="90e38-123">Popis</span><span class="sxs-lookup"><span data-stu-id="90e38-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90e38-124">requestCaching –</span><span class="sxs-lookup"><span data-stu-id="90e38-124">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="90e38-125">Určuje mechanismus ukládání do mezipaměti pro síťové požadavky.</span><span class="sxs-lookup"><span data-stu-id="90e38-125">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90e38-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="90e38-126">Remarks</span></span>  
 <span data-ttu-id="90e38-127">Hodnota `policyLevel` atribut je buď `BypassCache` nebo `Default`.</span><span class="sxs-lookup"><span data-stu-id="90e38-127">The value for the `policyLevel` attribute is either `BypassCache` or `Default`.</span></span>  
  
 <span data-ttu-id="90e38-128">Hodnoty `maximumAge`, `maximumStale`, a `minimumFresh` prvky jsou buď explicitní čas intervalu ve formátu *d*. *hh*:*mm*:*ss* (dny, hodiny, minuty a sekundy), nebo konstanty `minValue` nebo `maxValue`podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="90e38-128">Values for the `maximumAge`, `maximumStale`, and `minimumFresh` elements are either an explicit time interval with a format of *d*.*hh*:*mm*:*ss* (days, hours, minutes, and seconds), or the constants `minValue` or `maxValue`, as appropriate.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="90e38-129">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="90e38-129">Configuration Files</span></span>  
 <span data-ttu-id="90e38-130">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="90e38-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="90e38-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="90e38-131">Example</span></span>  
 <span data-ttu-id="90e38-132">Následující příklad ukazuje, jak zadat minimální aktuální čas šest hodin, maximální stáří času o dva dny a maximální zastaralé dobu čtyř hodin.</span><span class="sxs-lookup"><span data-stu-id="90e38-132">The following example shows how to specify a minimum fresh time of six hours, a maximum age time of two days, and a maximum stale time of four hours.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="90e38-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="90e38-133">See Also</span></span>  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.Cache.RequestCacheLevel>  
 [<span data-ttu-id="90e38-134">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="90e38-134">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
