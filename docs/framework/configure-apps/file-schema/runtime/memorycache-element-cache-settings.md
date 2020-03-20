---
title: <memoryCache> – element (nastavení mezipaměti)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 94c21e0408b7616bf0c8a24267b72bfa7cc3aaa0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153981"
---
# <a name="memorycache-element-cache-settings"></a>\<memoryCache> Element (Nastavení mezipaměti)
Definuje prvek, který se používá ke konfiguraci <xref:System.Runtime.Caching.MemoryCache> mezipaměti, která je založena na třídě. Třída <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> definuje element [memoryCache,](memorycache-element-cache-settings.md) který můžete použít ke konfiguraci mezipaměti. Více instancí <xref:System.Runtime.Caching.MemoryCache> třídy lze použít v jedné aplikaci. Každý `memoryCache` prvek v konfiguračním <xref:System.Runtime.Caching.MemoryCache> souboru může obsahovat nastavení pojmenované instance.  
  
[**\<>konfigurace**](../configuration-element.md)\
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
 <xref:System.Runtime.Caching.MemoryCache>Třída.  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|Maximální velikost paměti v megabajtech, do které <xref:System.Runtime.Caching.MemoryCache> může být instance objektu narůstat. Výchozí hodnota je 0, což <xref:System.Runtime.Caching.MemoryCache> znamená, že ve výchozím nastavení se používají heuristiky automatické velikosti třídy.|  
|`Name`|Název konfigurace mezipaměti.|  
|`PhysicalMemoryLimitPercentage`|Procento fyzické paměti, které lze použít v mezipaměti. Výchozí hodnota je 0, což <xref:System.Runtime.Caching.MemoryCache> znamená, že ve výchozím nastavení se používají heuristiky automatické velikosti třídy.|  
|`PollingInterval`|Hodnota, která označuje časový interval, po kterém implementace mezipaměti porovnává aktuální zatížení paměti s absolutní a procentuální limity paměti, které jsou nastaveny pro instanci mezipaměti. Hodnota je zadána ve formátu HH:MM:SS.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<pojmenováno Caches>](namedcaches-element-cache-settings.md)|Obsahuje kolekci nastavení konfigurace `namedCache` pro instanci.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<>konfigurace](../configuration-element.md)|Určuje kořenový prvek v každém konfiguračním souboru, který používá aplikace COMMON Language runtime a .NET Framework.|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|Obsahuje typy, které umožňují implementovat ukládání výstupu do mezipaměti v aplikacích, které jsou integrovány do rozhraní .NET Framework.|  
  
## <a name="remarks"></a>Poznámky  
 Třída <xref:System.Runtime.Caching.MemoryCache> je konkrétní implementace abstraktní <xref:System.Runtime.Caching.ObjectCache> třídy. Instance <xref:System.Runtime.Caching.MemoryCache> třídy mohou být dodávány s informacemi o konfiguraci z konfiguračních souborů aplikace. Oddíl konfigurace [memoryCache](memorycache-element-cache-settings.md) `namedCaches` obsahuje kolekci konfigurace.  
  
 Při inicializování objektu mezipaměti založeného `namedCaches` na paměti se nejprve pokusí najít položku, která odpovídá názvu v parametru, který je předán konstruktoru mezipaměti. Pokud `namedCaches` je nalezena položka, jsou z konfiguračního souboru načteny informace o dotazování a správě paměti.  
  
 Proces inicializace pak určuje, zda byly všechny položky konfigurace přepsány pomocí volitelné kolekce dvojic názvů a hodnot informací o konfiguraci v konstruktoru. Pokud v kolekci dvojice název/hodnota předáte některou z následujících hodnot, tyto hodnoty přepíší informace získané z konfiguračního souboru:  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nastavit <xref:System.Runtime.Caching.MemoryCache> název objektu na výchozí název `name` objektu mezipaměti nastavením atributu "Výchozí".  
  
 Atribut `cacheMemoryLimitMegabytes` a `physicalMemoryLimitPercentage` atribut jsou nastaveny na nulu. Nastavení těchto atributů na <xref:System.Runtime.Caching.MemoryCache> nulu znamená, že autosizing heuristiky jsou používány ve výchozím nastavení. Implementace mezipaměti by měla porovnávat aktuální zatížení paměti s absolutními a procentuálními limity paměti každé dvě minuty.  
  
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
- [\<system.runtime.caching> Element (Nastavení mezipaměti)](system-runtime-caching-element-cache-settings.md)
- [\<namedCaches> Element (Nastavení mezipaměti)](namedcaches-element-cache-settings.md)
