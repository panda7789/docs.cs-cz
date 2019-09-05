---
title: <memoryCache> – element (nastavení mezipaměti)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 25467fc751ad772e74ca714e6059bc5134300ed6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252488"
---
# <a name="memorycache-element-cache-settings"></a>\<memoryCache – Element > (nastavení mezipaměti)
Definuje prvek, který se používá ke konfiguraci mezipaměti založené na <xref:System.Runtime.Caching.MemoryCache> třídě. Třída definuje element MemoryCache, který můžete použít ke konfiguraci mezipaměti. [](memorycache-element-cache-settings.md) <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> V jedné aplikaci lze <xref:System.Runtime.Caching.MemoryCache> použít více instancí třídy. Každý `memoryCache` prvek v konfiguračním souboru může obsahovat nastavení pro pojmenovanou <xref:System.Runtime.Caching.MemoryCache> instanci.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. Runtime. Caching >** ](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<memoryCache >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<memoryCache>   
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>   
</memoryCache>  
```  
  
## <a name="type"></a>type  
 <xref:System.Runtime.Caching.MemoryCache>Deník.  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|Maximální velikost paměti v megabajtech, kterou může instance <xref:System.Runtime.Caching.MemoryCache> objektu růst. Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> ve výchozím nastavení jsou použity heuristické hodnoty třídy AutoSize.|  
|`Name`|Název konfigurace mezipaměti.|  
|`PhysicalMemoryLimitPercentage`|Procento fyzické paměti, které může mezipaměť použít. Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> ve výchozím nastavení jsou použity heuristické hodnoty třídy AutoSize.|  
|`PollingInterval`|Hodnota, která označuje časový interval, po kterém implementace mezipaměti porovnává aktuální zatížení paměti s omezeními na základě absolutního a procenta velikosti paměti, které jsou nastaveny pro instanci mezipaměti. Hodnota je zadána ve formátu "HH: MM: SS".|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|Obsahuje kolekci konfiguračních nastavení `namedCache` instance.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> Konfigurace](../configuration-element.md)|Určuje kořenový element v každém konfiguračním souboru, který je používán modulem CLR (Common Language Runtime) a .NET Framework aplikacemi.|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|Obsahuje typy, které umožňují implementovat ukládání výstupu do mezipaměti v aplikacích, které jsou integrovány do .NET Framework.|  
  
## <a name="remarks"></a>Poznámky  
 Třída je konkrétní implementace abstraktní <xref:System.Runtime.Caching.ObjectCache> třídy. <xref:System.Runtime.Caching.MemoryCache> <xref:System.Runtime.Caching.MemoryCache> Instance třídy mohou být dodány s informacemi o konfiguraci z konfiguračních souborů aplikace. Konfigurační oddíl [MemoryCache](memorycache-element-cache-settings.md) obsahuje `namedCaches` kolekci konfigurací.  
  
 Při inicializaci objektu mezipaměti založeného na paměti se nejprve pokusí najít `namedCaches` položku, která odpovídá názvu v parametru, který je předán konstruktoru mezipaměti paměti. Pokud je `namedCaches` položka nalezena, informace o pro dotazování a správu paměti se načítají z konfiguračního souboru.  
  
 Proces inicializace pak určí, zda byly všechny položky konfigurace přepsány, pomocí volitelné kolekce párů název/hodnota v informacích o konfiguraci v konstruktoru. Pokud předáte jednu z následujících hodnot v kolekci dvojice název/hodnota, přepíší tyto hodnoty informace získané z konfiguračního souboru:  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nastavit název <xref:System.Runtime.Caching.MemoryCache> objektu na výchozí název objektu mezipaměti `name` nastavením atributu na hodnotu "default".  
  
 `cacheMemoryLimitMegabytes` Atribut`physicalMemoryLimitPercentage` a atribut jsou nastaveny na hodnotu nula. Nastavení těchto atributů na hodnotu nula znamená, <xref:System.Runtime.Caching.MemoryCache> že výchozí hodnoty pro automatické změny velikosti jsou používány ve výchozím nastavení. Implementace mezipaměti by měla porovnat aktuální zatížení paměti s absolutními a procentuálními hodnotami paměti založenými na procentech každé dvě minuty.  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"   
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
- [\<System. Runtime. Caching > element (nastavení mezipaměti)](system-runtime-caching-element-cache-settings.md)
- [\<namedCaches – element > (nastavení mezipaměti)](namedcaches-element-cache-settings.md)
