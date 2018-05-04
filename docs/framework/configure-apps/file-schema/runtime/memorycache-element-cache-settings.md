---
title: '&lt;memoryCache&gt; – Element (nastavení mezipaměti)'
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3d0d741fd8193c7d874d70248cbd149f11163ed0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltmemorycachegt-element-cache-settings"></a>&lt;memoryCache&gt; – Element (nastavení mezipaměti)
Definuje element, který slouží ke konfiguraci mezipaměti, který je založen na <xref:System.Runtime.Caching.MemoryCache> třídy. <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> Třída definuje [memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) element, který můžete použít ke konfiguraci mezipaměti. Více instancí <xref:System.Runtime.Caching.MemoryCache> třídy lze v jedné aplikaci. Každý `memoryCache` element v konfiguračním souboru může obsahovat nastavení pro pojmenovaná <xref:System.Runtime.Caching.MemoryCache> instance.  
  
 \<Konfigurace >  
\<system.runtime.caching>  
\<memoryCache >  
  
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
|`CacheMemoryLimitMegabytes`|Velikost maximální velikost paměti v megabajtech, která instance <xref:System.Runtime.Caching.MemoryCache> objekt můžete dosáhnout. Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> heuristiky autosize třídy se používají ve výchozím nastavení.|  
|`Name`|Název konfigurace mezipaměti.|  
|`PhysicalMemoryLimitPercentage`|Procento fyzické paměti, které je možné pomocí mezipaměti. Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> heuristiky autosize třídy se používají ve výchozím nastavení.|  
|`PollingInterval`|Hodnota, která určuje časový interval, po jejímž uplynutí implementace mezipaměti porovná aktuální zatížení paměti do paměti absolutní a na základě procenta omezení, které jsou nastavené pro instanci mezipaměti. Hodnota je zadáno ve formátu hh: mm".|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|Obsahuje kolekci nastavení konfigurace `namedCache` instance.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<system.runtime.caching>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|Obsahuje typy, které umožňují implementovat ukládání výstupu do mezipaměti v aplikacích, které jsou součástí [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].|  
  
## <a name="remarks"></a>Poznámky  
 <xref:System.Runtime.Caching.MemoryCache> Třída je konkrétní implementaci abstraktní <xref:System.Runtime.Caching.ObjectCache> třídy. Instance <xref:System.Runtime.Caching.MemoryCache> třídy můžete zadat s informace o konfiguraci z konfigurační soubory aplikace. [MemoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) obsahuje oddíl konfigurace `namedCaches` kolekce konfigurace.  
  
 Při inicializaci objektu mezipaměti nejprve se pokusí najít `namedCaches` položku, která odpovídá názvu v parametr, který je předaný konstruktoru mezipaměti paměti. Pokud `namedCaches` není nalezena položka, dotazování a správu paměti informace se načítají z konfiguračního souboru.  
  
 Proces inicializace pak určuje, zda byly přepsána žádné položky konfigurace, pomocí volitelné kolekce dvojic název/hodnota informací o konfiguraci v konstruktoru. Pokud předáte některého z následujících hodnot v kolekci dvojice název hodnota, tyto hodnoty přepsat informacemi získanými z konfiguračního souboru:  
  
-   <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
-   <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
-   <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nastavit název <xref:System.Runtime.Caching.MemoryCache> objekt, který má výchozí název objektu mezipaměti nastavením `name` atribut "Výchozí".  
  
 `cacheMemoryLimitMegabytes` Atribut a `physicalMemoryLimitPercentage` atribut nastaveny na nulu. Nastavení těchto atributů na nulu, znamená to, který <xref:System.Runtime.Caching.MemoryCache> Automatická změna velikosti heuristiky se používají ve výchozím nastavení. Implementace mezipaměti musí porovnat aktuálního zatížení paměti do paměti absolutní a na základě procenta omezení každé dvě minuty.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Caching.MemoryCache>  
 [\<System.Runtime.Caching – > elementu (nastavení mezipaměti)](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)  
 [\<namedCaches > – Element (nastavení mezipaměti)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
