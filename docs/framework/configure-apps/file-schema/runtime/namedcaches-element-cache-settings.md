---
title: <namedCaches> – element (nastavení mezipaměti)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: e0640ca18d386141f3c03135019eb4fe959b5bf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153955"
---
# <a name="namedcaches-element-cache-settings"></a>\<namedCaches> Element (Nastavení mezipaměti)
Určuje kolekci nastavení konfigurace pro <xref:System.Runtime.Caching.MemoryCache> pojmenované instance. Vlastnost <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> odkazuje na kolekci nastavení konfigurace `namedCaches` z jednoho nebo více prvků konfiguračního souboru.  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<pojmenováno Caches>**  
  
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
|`cacheMemoryLimitMegabytes`|Celá hodnota, která určuje maximální přípustnou velikost v megabajtech, na <xref:System.Runtime.Caching.MemoryCache> kterou může instanci instanci zvětšit. Výchozí hodnota je 0, což znamená, že autosizing <xref:System.Runtime.Caching.MemoryCache> heuristiky třídy se používají ve výchozím nastavení.|  
|`name`|Název mezipaměti.|  
|`physicalMemoryLimitPercentage`|Celá hodnota mezi 0 a 100, která určuje maximální procento fyzicky nainstalované paměti počítače, které mohou být spotřebovány mezipamětí. Výchozí hodnota je 0, což znamená, že autosizing <xref:System.Runtime.Caching.MemoryCache> heuristiky třídy se používají ve výchozím nastavení.|  
|`pollingInterval`|Hodnota, která označuje časový interval, po kterém implementace mezipaměti porovnává aktuální zatížení paměti s absolutní a procentuální limity paměti, které jsou nastaveny pro instanci mezipaměti. Tato hodnota je zadána ve formátu HH:MM:SS.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<přidat>](add-element-for-namedcaches.md)|Přidá pojmenovanou `namedCaches` mezipaměť do kolekce mezipaměti.|  
|[\<jasné>](clear-element-for-namedcaches.md)|Vymaže kolekci `namedCaches` mezipaměti mezipaměti.|  
|[\<odebrat>](remove-element-for-namedcaches.md)|Odebere pojmenovanou položku mezipaměti `namedCaches` z kolekce mezipaměti.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<>konfigurace](../configuration-element.md)|Určuje kořenový prvek v každém konfiguračním souboru, který používá aplikace COMMON Language runtime a .NET Framework.|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|Definuje prvek, který se používá ke konfiguraci <xref:System.Runtime.Caching.MemoryCache> mezipaměti, která je založena na třídě.|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|Obsahuje typy, které umožňují implementovat ukládání výstupu do mezipaměti v aplikacích, které jsou integrovány do rozhraní .NET Framework.|  
  
## <a name="remarks"></a>Poznámky  
 Oddíl konfigurace mezipaměti souboru Web.config `add` `remove`může `clear` obsahovat , `namedCaches` a atributy kolekce. Každá `namedCaches` položka je jednoznačně `name` identifikována atributem.  
  
 Instance položek mezipaměti mezipaměti můžete načíst odkazováním na informace v konfiguračních souborech aplikace. Ve výchozím nastavení má v konfiguračním souboru položku pouze výchozí instance mezipaměti. Výchozí instance mezipaměti je instance, <xref:System.Runtime.Caching.MemoryCache.Default%2A> která je vrácena z vlastnosti.  
  
 Pokud nastavíte atribut name na "default", prvek použije výchozí instanci mezipaměti paměti.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nastavit název mezipaměti na výchozí název `name` položky mezipaměti nastavením atributu na "výchozí".  
  
 Atribut `cacheMemoryLimitMegabytes` a `physicalMemoryPercentage` atribut jsou nastaveny na nulu. Nastavení těchto atributů na nulu znamená, že se <xref:System.Runtime.Caching.MemoryCache> používají autosizing heuristiky třídy. Implementace mezipaměti porovnává aktuální zatížení paměti s absolutní a procentuální limity paměti každé dvě minuty.  
  
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

- [\<memoryCache> Element (Nastavení mezipaměti)](memorycache-element-cache-settings.md)
