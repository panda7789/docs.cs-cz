---
title: <namedCaches> – element (nastavení mezipaměti)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: 9cedd462aa539745ddab844dff158912914cb024
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663584"
---
# <a name="namedcaches-element-cache-settings"></a>\<namedCaches – element > (nastavení mezipaměti)
Určuje kolekci konfiguračních nastavení pro pojmenované <xref:System.Runtime.Caching.MemoryCache> instance. Vlastnost odkazuje na kolekci konfiguračních nastavení z jednoho nebo více `namedCaches` prvků konfiguračního souboru. <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A>  
  
 \<> Konfigurace  
\<System. Runtime. Caching >  
\<memoryCache>  
\<namedCaches>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<namedCaches>  
  <add name="default"/>   
</namedCaches>  
```  
  
## <a name="type"></a>type  
 `None`  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|Celočíselná hodnota, která určuje maximální povolenou velikost v megabajtech, kterou může instance a <xref:System.Runtime.Caching.MemoryCache> růst. Výchozí hodnota je 0, což znamená, že ve výchozím nastavení jsou používány heuristiky <xref:System.Runtime.Caching.MemoryCache> autovelikosti třídy.|  
|`name`|Název mezipaměti.|  
|`physicalMemoryLimitPercentage`|Celočíselná hodnota mezi 0 a 100, která určuje maximální procento fyzicky instalované paměti počítače, kterou může mezipaměť spotřebovat. Výchozí hodnota je 0, což znamená, že ve výchozím nastavení jsou používány heuristiky <xref:System.Runtime.Caching.MemoryCache> autovelikosti třídy.|  
|`pollingInterval`|Hodnota, která označuje časový interval, po kterém implementace mezipaměti porovnává aktuální zatížení paměti s omezeními na základě absolutního a procenta velikosti paměti, které jsou nastaveny pro instanci mezipaměti. Tato hodnota je zadaná ve formátu "HH: MM: SS".|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<add>](add-element-for-namedcaches.md)|Přidá pojmenovanou mezipaměť do `namedCaches` kolekce mezipaměti paměti.|  
|[\<clear>](clear-element-for-namedcaches.md)|`namedCaches` Vymaže kolekci mezipaměti paměti.|  
|[\<remove>](remove-element-for-namedcaches.md)|Odebere pojmenovanou položku mezipaměti z `namedCaches` kolekce pro mezipaměť paměti.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|Definuje prvek, který se používá ke konfiguraci mezipaměti založené na <xref:System.Runtime.Caching.MemoryCache> třídě.|  
  
## <a name="remarks"></a>Poznámky  
 Oddíl konfigurace mezipaměti paměti v souboru Web. `add`config může obsahovat atributy, `remove`a `clear` pro `namedCaches` kolekci. Každá `namedCaches` položka je jednoznačně identifikována `name` atributem.  
  
 Můžete načíst instance položek mezipaměti paměti odkazem na informace v konfiguračních souborech aplikace. Ve výchozím nastavení obsahuje pouze výchozí instance mezipaměti záznam v konfiguračním souboru. Výchozí instance mezipaměti je instance, která je vrácena z <xref:System.Runtime.Caching.MemoryCache.Default%2A> vlastnosti.  
  
 Pokud nastavíte atribut Name na výchozí, bude element používat výchozí instanci mezipaměti paměti.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nastavit název mezipaměti na výchozí název položky mezipaměti nastavením `name` atributu na "default".  
  
 `cacheMemoryLimitMegabytes` Atribut`physicalMemoryPercentage` a atribut jsou nastaveny na hodnotu nula. Nastavení těchto atributů na hodnotu nula znamená, že se používají heuristické <xref:System.Runtime.Caching.MemoryCache> automatické změny velikosti třídy. Implementace mezipaměti porovnává aktuální zatížení paměti s použitím absolutních a procentuálních limitů paměti založených na procentech každé dvě minuty.  
  
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

- [\<memoryCache – Element > (nastavení mezipaměti)](memorycache-element-cache-settings.md)
