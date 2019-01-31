---
title: <namedCaches> – element (nastavení vyrovnávací paměti)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: 1dedd3ca192b5fb0ee561ce138f0948c52581f89
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55287479"
---
# <a name="namedcaches-element-cache-settings"></a>\<namedcaches – > – Element (nastavení mezipaměti)
Určuje kolekci nastavení konfigurace pro pojmenované <xref:System.Runtime.Caching.MemoryCache> instancí. <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> Vlastnost odkazuje na soubor konfiguračních nastavení z jedné nebo více `namedCaches` prvky konfiguračního souboru.  
  
 \<Konfigurace >  
\< System.Runtime.Caching >  
\<memoryCache>  
\<namedCaches>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<namedCaches>  
  <add name="default"/>   
</namedCaches>  
```  
  
## <a name="type"></a>Typ  
 `None`  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|Celočíselná hodnota, která určuje maximální povolenou velikost v megabajtech, který instance <xref:System.Runtime.Caching.MemoryCache> růst, aby. Výchozí hodnota je 0, což znamená, že automatické přizpůsobení velikosti heuristiky z <xref:System.Runtime.Caching.MemoryCache> třída se používá ve výchozím nastavení.|  
|`name`|Název mezipaměti.|  
|`physicalMemoryLimitPercentage`|Celočíselná hodnota mezi 0 a 100 určující maximální procento paměti fyzicky nainstalované počítače, které mohou být spotřebovány mezipaměti. Výchozí hodnota je 0, což znamená, že automatické přizpůsobení velikosti heuristiky z <xref:System.Runtime.Caching.MemoryCache> třída se používá ve výchozím nastavení.|  
|`pollingInterval`|Hodnota, která určuje časový interval, po jejímž uplynutí implementaci mezipaměti porovná aktuální zatížení paměti do paměti absolutní a založený na procentech omezení, které jsou nastavené pro instanci mezipaměti. Tato hodnota se zadává ve formátu "hh: mm:".|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)|Přidá pojmenované mezipaměti, aby `namedCaches` kolekce pro mezipaměť.|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)|Vymaže `namedCaches` kolekce pro mezipaměť.|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)|Odebere položku pojmenovanou mezipaměť z `namedCaches` kolekce pro mezipaměť.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<memoryCache>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|Definuje element, který se používá ke konfiguraci, která je založená na mezipaměti <xref:System.Runtime.Caching.MemoryCache> třídy.|  
  
## <a name="remarks"></a>Poznámky  
 Konfigurační oddíl mezipaměti paměti souboru Web.config mohou obsahovat `add`, `remove`, a `clear` atributů pro `namedCaches` kolekce. Každý `namedCaches` položka je jedinečně identifikovaný `name` atribut.  
  
 Instance položky mezipaměti paměti můžete načíst pomocí odkazu na informace v konfiguračních souborech aplikace. Ve výchozím nastavení pouze výchozí instanci mezipaměti má záznam v konfiguračním souboru. Výchozí instance mezipaměti je instanci, která je vrácena z <xref:System.Runtime.Caching.MemoryCache.Default%2A> vlastnost.  
  
 Pokud nastavíte atribut name "Výchozí", element používá výchozí instanci mezipaměti paměti.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nastavit název mezipaměti, výchozí název položky mezipaměti tak, že nastavíte `name` atribut "Výchozí".  
  
 `cacheMemoryLimitMegabytes` Atribut a `physicalMemoryPercentage` je atribut nastaven na hodnotu nula. Nastavení těchto atributů na hodnotu nula znamená, že automatické přizpůsobení velikosti heuristiky z <xref:System.Runtime.Caching.MemoryCache> třída se používá. Implementace mezipaměti porovná aktuální zatížení paměti proti absolutní a založený na procentech paměťová omezení každé dvě minuty.  
  
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
- [\<memoryCache > – Element (nastavení mezipaměti)](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
