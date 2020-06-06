---
title: <memoryCache> – element (nastavení mezipaměti)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 94c21e0408b7616bf0c8a24267b72bfa7cc3aaa0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153981"
---
# <a name="memorycache-element-cache-settings"></a>\<memoryCache> – element (nastavení mezipaměti)
Definuje prvek, který se používá ke konfiguraci mezipaměti založené na <xref:System.Runtime.Caching.MemoryCache> třídě. <xref:System.Runtime.Caching.Configuration.MemoryCacheElement>Třída definuje element [MemoryCache](memorycache-element-cache-settings.md) , který můžete použít ke konfiguraci mezipaměti. <xref:System.Runtime.Caching.MemoryCache>V jedné aplikaci lze použít více instancí třídy. Každý `memoryCache` prvek v konfiguračním souboru může obsahovat nastavení pro pojmenovanou <xref:System.Runtime.Caching.MemoryCache> instanci.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<memoryCache>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<memoryCache>
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>
</memoryCache>  
```  
  
## <a name="type"></a>Typ  
 <xref:System.Runtime.Caching.MemoryCache>Deník.  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|Maximální velikost paměti v megabajtech, kterou <xref:System.Runtime.Caching.MemoryCache> může instance objektu růst. Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> ve výchozím nastavení jsou použity heuristické hodnoty třídy AutoSize.|  
|`Name`|Název konfigurace mezipaměti.|  
|`PhysicalMemoryLimitPercentage`|Procento fyzické paměti, které může mezipaměť použít. Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> ve výchozím nastavení jsou použity heuristické hodnoty třídy AutoSize.|  
|`PollingInterval`|Hodnota, která označuje časový interval, po kterém implementace mezipaměti porovnává aktuální zatížení paměti s omezeními na základě absolutního a procenta velikosti paměti, které jsou nastaveny pro instanci mezipaměti. Hodnota je zadána ve formátu "HH: MM: SS".|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|Obsahuje kolekci konfiguračních nastavení `namedCache` instance.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|Určuje kořenový element v každém konfiguračním souboru, který je používán modulem CLR (Common Language Runtime) a .NET Framework aplikacemi.|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|Obsahuje typy, které umožňují implementovat ukládání výstupu do mezipaměti v aplikacích, které jsou integrovány do .NET Framework.|  
  
## <a name="remarks"></a>Poznámky  
 <xref:System.Runtime.Caching.MemoryCache>Třída je konkrétní implementace abstraktní <xref:System.Runtime.Caching.ObjectCache> třídy. Instance <xref:System.Runtime.Caching.MemoryCache> třídy mohou být dodány s informacemi o konfiguraci z konfiguračních souborů aplikace. Konfigurační oddíl [MemoryCache](memorycache-element-cache-settings.md) obsahuje `namedCaches` kolekci konfigurací.  
  
 Při inicializaci objektu mezipaměti založeného na paměti se nejprve pokusí najít `namedCaches` položku, která odpovídá názvu v parametru, který je předán konstruktoru mezipaměti paměti. Pokud `namedCaches` je položka nalezena, informace o pro dotazování a správu paměti se načítají z konfiguračního souboru.  
  
 Proces inicializace pak určí, zda byly všechny položky konfigurace přepsány, pomocí volitelné kolekce párů název/hodnota v informacích o konfiguraci v konstruktoru. Pokud předáte jednu z následujících hodnot v kolekci dvojice název/hodnota, přepíší tyto hodnoty informace získané z konfiguračního souboru:  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nastavit název <xref:System.Runtime.Caching.MemoryCache> objektu na výchozí název objektu mezipaměti nastavením `name` atributu na hodnotu "default".  
  
 `cacheMemoryLimitMegabytes`Atribut a `physicalMemoryLimitPercentage` atribut jsou nastaveny na hodnotu nula. Nastavení těchto atributů na hodnotu nula znamená, že <xref:System.Runtime.Caching.MemoryCache> výchozí hodnoty pro automatické změny velikosti jsou používány ve výchozím nastavení. Implementace mezipaměti by měla porovnat aktuální zatížení paměti s absolutními a procentuálními hodnotami paměti založenými na procentech každé dvě minuty.  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Caching.MemoryCache>
- [\<system.runtime.caching>– Element (nastavení mezipaměti)](system-runtime-caching-element-cache-settings.md)
- [\<namedCaches>– Element (nastavení mezipaměti)](namedcaches-element-cache-settings.md)
