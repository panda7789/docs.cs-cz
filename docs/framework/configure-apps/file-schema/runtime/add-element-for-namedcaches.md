---
title: '&lt;Přidat&gt; – Element pro &lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 695ee744bdf2226f0647c4cdf142a2dca4e97a4a
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2018
ms.locfileid: "47863322"
---
# <a name="ltaddgt-element-for-ltnamedcachesgt"></a>&lt;Přidat&gt; – Element pro &lt;namedCaches&gt;
Přidá `namedCache` položku a `namedCaches` kolekce pro mezipaměť.  
  
 \<system.runtime.caching>  
\<memoryCache >  
\<namedcaches – >  
\<add>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<namedCaches>  
    <add name="default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>Typ  
 `None`  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|-|-|  
|`CacheMemoryLimitMegabytes`|Celočíselná hodnota, která určuje maximální povolenou velikost (v megabajtech), která instance <xref:System.Runtime.Caching.MemoryCache> růst, aby. Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> heuristiky automatické přizpůsobení velikosti třídy se používají ve výchozím nastavení.|  
|`Name`|Název mezipaměti.|  
|`PhysicalMemoryLimitPercentage`|Celočíselná hodnota mezi 0 a 100 určující maximální procento paměti fyzicky nainstalované počítače, které mohou být spotřebovány mezipaměti. Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> heuristiky automatické přizpůsobení velikosti třídy se používají ve výchozím nastavení.|  
|`PollingInterval`|Hodnota, která určuje časový interval, po jejímž uplynutí implementaci mezipaměti porovná aktuální zatížení paměti do paměti absolutní a založený na procentech omezení, které jsou nastavené pro instanci mezipaměti. Tato hodnota se zadává ve formátu "hh: mm:".|  
  
### <a name="child-elements"></a>Podřízené elementy  
 `None`  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|Obsahuje kolekci prvků konfigurace nastavení pro pojmenované <xref:System.Runtime.Caching.MemoryCache> instancí.|  
  
## <a name="remarks"></a>Poznámky  
 `add` Element přidá záznam, tím `namedCaches` kolekce pro mezipaměť. Můžete použít [vymazat](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) prvek před použitím `add` element je potřeba mít jistotu, že neexistují žádné jiné s názvem mezipaměti v kolekci. Tento element lze použít v souboru machine.config a v souboru Web.config.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak definovat nastavení pro výchozí `namedCache` položku a `namedCaches` kolekce pro mezipaměť.  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [\<namedcaches – > – Element (nastavení mezipaměti)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
