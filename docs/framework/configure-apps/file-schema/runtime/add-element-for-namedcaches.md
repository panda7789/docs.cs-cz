---
title: Element <add> pro <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: c1345022b79df371ad9c89a39a0a8b625e26608c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154502"
---
# <a name="add-element-for-namedcaches"></a>\<přidání prvku \<> pro> namedCaches
Přidá `namedCache` položku `namedCaches` do kolekce pro mezipaměti paměti.  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<pojmenováno Caches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<přidat>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<namedCaches>  
    <add name="Default" />  
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
|`CacheMemoryLimitMegabytes`|Celá hodnota, která určuje maximální povolenou velikost (v megabajtech), <xref:System.Runtime.Caching.MemoryCache> na kterou může instanci instanci zvětšit. Výchozí hodnota je 0, což <xref:System.Runtime.Caching.MemoryCache> znamená, že ve výchozím nastavení se používají autosizing heuristiky třídy.|  
|`Name`|Název mezipaměti.|  
|`PhysicalMemoryLimitPercentage`|Celá hodnota mezi 0 a 100, která určuje maximální procento fyzicky nainstalované paměti počítače, které mohou být spotřebovány mezipamětí. Výchozí hodnota je 0, což <xref:System.Runtime.Caching.MemoryCache> znamená, že ve výchozím nastavení se používají autosizing heuristiky třídy.|  
|`PollingInterval`|Hodnota, která označuje časový interval, po kterém implementace mezipaměti porovnává aktuální zatížení paměti s absolutní a procentuální limity paměti, které jsou nastaveny pro instanci mezipaměti. Tato hodnota je zadána ve formátu HH:MM:SS.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 `None`  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<pojmenováno Caches>](namedcaches-element-cache-settings.md)|Obsahuje kolekci nastavení konfigurace <xref:System.Runtime.Caching.MemoryCache> pro pojmenované instance.|  
  
## <a name="remarks"></a>Poznámky  
 Prvek `add` přidá položku `namedCaches` do kolekce pro mezipaměti paměti. Před použitím `add` prvku můžete použít prvek [clear,](clear-element-for-namedcaches.md) abyste si byli jisti, že v kolekci nejsou žádné jiné pojmenované mezipaměti. Tento prvek lze použít v souboru machine.config a v souboru Web.config.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak definovat `namedCache` nastavení pro `namedCaches` výchozí položku do kolekce pro mezipaměti paměti.  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"
               cacheMemoryLimitMegabytes="0"
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- [\<namedCaches> Element (Nastavení mezipaměti)](namedcaches-element-cache-settings.md)
