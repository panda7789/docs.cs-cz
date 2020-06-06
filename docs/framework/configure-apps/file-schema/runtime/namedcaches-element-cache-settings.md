---
title: <namedCaches> – element (nastavení mezipaměti)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: e0640ca18d386141f3c03135019eb4fe959b5bf8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153955"
---
# <a name="namedcaches-element-cache-settings"></a>\<namedCaches> – element (nastavení mezipaměti)
Určuje kolekci konfiguračních nastavení pro pojmenované <xref:System.Runtime.Caching.MemoryCache> instance. <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A>Vlastnost odkazuje na kolekci konfiguračních nastavení z jednoho nebo více `namedCaches` prvků konfiguračního souboru.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**  
  
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
|`cacheMemoryLimitMegabytes`|Celočíselná hodnota, která určuje maximální povolenou velikost v megabajtech, kterou může instance a <xref:System.Runtime.Caching.MemoryCache> růst. Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> ve výchozím nastavení jsou používány heuristiky autovelikosti třídy.|  
|`name`|Název mezipaměti.|  
|`physicalMemoryLimitPercentage`|Celočíselná hodnota mezi 0 a 100, která určuje maximální procento fyzicky instalované paměti počítače, kterou může mezipaměť spotřebovat. Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> ve výchozím nastavení jsou používány heuristiky autovelikosti třídy.|  
|`pollingInterval`|Hodnota, která označuje časový interval, po kterém implementace mezipaměti porovnává aktuální zatížení paměti s omezeními na základě absolutního a procenta velikosti paměti, které jsou nastaveny pro instanci mezipaměti. Tato hodnota je zadaná ve formátu "HH: MM: SS".|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<add>](add-element-for-namedcaches.md)|Přidá pojmenovanou mezipaměť do `namedCaches` kolekce mezipaměti paměti.|  
|[\<clear>](clear-element-for-namedcaches.md)|Vymaže `namedCaches` kolekci mezipaměti paměti.|  
|[\<remove>](remove-element-for-namedcaches.md)|Odebere pojmenovanou položku mezipaměti z `namedCaches` kolekce pro mezipaměť paměti.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|Určuje kořenový element v každém konfiguračním souboru, který je používán modulem CLR (Common Language Runtime) a .NET Framework aplikacemi.|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|Definuje prvek, který se používá ke konfiguraci mezipaměti založené na <xref:System.Runtime.Caching.MemoryCache> třídě.|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|Obsahuje typy, které umožňují implementovat ukládání výstupu do mezipaměti v aplikacích, které jsou integrovány do .NET Framework.|  
  
## <a name="remarks"></a>Poznámky  
 Oddíl konfigurace mezipaměti paměti v souboru Web. config může obsahovat `add` `remove` atributy, a `clear` pro `namedCaches` kolekci. Každá `namedCaches` položka je jednoznačně identifikována `name` atributem.  
  
 Můžete načíst instance položek mezipaměti paměti odkazem na informace v konfiguračních souborech aplikace. Ve výchozím nastavení obsahuje pouze výchozí instance mezipaměti záznam v konfiguračním souboru. Výchozí instance mezipaměti je instance, která je vrácena z <xref:System.Runtime.Caching.MemoryCache.Default%2A> Vlastnosti.  
  
 Pokud nastavíte atribut Name na výchozí, bude element používat výchozí instanci mezipaměti paměti.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nastavit název mezipaměti na výchozí název položky mezipaměti nastavením `name` atributu na "default".  
  
 `cacheMemoryLimitMegabytes`Atribut a `physicalMemoryPercentage` atribut jsou nastaveny na hodnotu nula. Nastavení těchto atributů na hodnotu nula znamená, že se používají heuristické automatické změny velikosti <xref:System.Runtime.Caching.MemoryCache> třídy. Implementace mezipaměti porovnává aktuální zatížení paměti s použitím absolutních a procentuálních limitů paměti založených na procentech každé dvě minuty.  
  
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

- [\<memoryCache>– Element (nastavení mezipaměti)](memorycache-element-cache-settings.md)
