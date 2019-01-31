---
title: <memoryCache> – element (nastavení vyrovnávací paměti)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 25e87aa9fa4e56c5042eb25c41f6cfe1b65aea24
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266374"
---
# <a name="memorycache-element-cache-settings"></a>\<memoryCache > – Element (nastavení mezipaměti)
Definuje element, který se používá ke konfiguraci, která je založená na mezipaměti <xref:System.Runtime.Caching.MemoryCache> třídy. <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> Definuje třídu [memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) element, který můžete použít ke konfiguraci mezipaměti. Více instancí <xref:System.Runtime.Caching.MemoryCache> třídy lze v jedné aplikaci. Každý `memoryCache` element v konfiguračním souboru může obsahovat nastavení pro pojmenovaná <xref:System.Runtime.Caching.MemoryCache> instance.  
  
 \<Konfigurace >  
\<system.runtime.caching>  
\<memoryCache>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<memoryCache>   
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>   
</memoryCache>  
```  
  
## <a name="type"></a>Typ  
 <xref:System.Runtime.Caching.MemoryCache> Třída.  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|Do maximální velikosti paměti, v megabajtech, který instance <xref:System.Runtime.Caching.MemoryCache> objekt růst, aby. Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> heuristické metody automaticky přizpůsobit velikost třídy se používají ve výchozím nastavení.|  
|`Name`|Název konfigurace mezipaměti.|  
|`PhysicalMemoryLimitPercentage`|Procento fyzické paměti, je možné do mezipaměti. Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> heuristické metody automaticky přizpůsobit velikost třídy se používají ve výchozím nastavení.|  
|`PollingInterval`|Hodnota, která určuje časový interval, po jejímž uplynutí implementaci mezipaměti porovná aktuální zatížení paměti do paměti absolutní a založený na procentech omezení, které jsou nastavené pro instanci mezipaměti. Hodnota je zadáno ve formátu "hh: mm:".|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|Obsahuje kolekci prvků konfigurace nastavení `namedCache` instance.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<system.runtime.caching>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|Obsahuje typy, které umožňují v aplikacích, které jsou součástí implementace ukládání výstupu do mezipaměti [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].|  
  
## <a name="remarks"></a>Poznámky  
 <xref:System.Runtime.Caching.MemoryCache> Je konkrétní implementaci abstraktní třída <xref:System.Runtime.Caching.ObjectCache> třídy. Instance <xref:System.Runtime.Caching.MemoryCache> třídy může být zadán s informace o konfiguraci z konfiguračních souborů aplikace. [MemoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) oddíl konfigurace obsahuje `namedCaches` kolekce konfigurací.  
  
 Při inicializaci mezipaměti na základě paměti objektu, nejprve se pokusí najít `namedCaches` položku, která odpovídá názvu parametru, který je předán konstruktoru mezipaměti paměti. Pokud `namedCaches` položka nenajde, dotazování a správu paměti informace se načítají z konfiguračního souboru.  
  
 Proces inicializace pak určuje, zda byly přepsat všechny položky konfigurace, pomocí volitelné kolekci dvojic název/hodnota informací o konfiguraci v konstruktoru. Pokud předáte některou z následujících hodnot v kolekci dvojice název/hodnota, tyto hodnoty přepsání informacemi získanými z konfiguračního souboru:  
  
-   <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
-   <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
-   <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nastavit název <xref:System.Runtime.Caching.MemoryCache> objekt má výchozí název objektu mezipaměti tak, že nastavíte `name` atribut "Výchozí".  
  
 `cacheMemoryLimitMegabytes` Atribut a `physicalMemoryLimitPercentage` je atribut nastaven na hodnotu nula. Nastavení těchto atributů 0 znamená, <xref:System.Runtime.Caching.MemoryCache> heuristiky automatické přizpůsobení velikosti se používají ve výchozím nastavení. Implementace mezipaměti by měla porovnání aktuálního zatížení paměti proti absolutní a založený na procentech paměťová omezení každé dvě minuty.  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Runtime.Caching.MemoryCache>
- [\<System.Runtime.Caching > – Element (nastavení mezipaměti)](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)
- [\<namedcaches – > – Element (nastavení mezipaměti)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
