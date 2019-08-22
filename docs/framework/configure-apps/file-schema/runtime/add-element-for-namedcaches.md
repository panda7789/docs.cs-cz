---
title: <add> – element pro <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: fd6668a551663470a97b07ff131710dbe92a91f5
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659029"
---
# <a name="add-element-for-namedcaches"></a>\<Přidat > element pro \<> namedCaches
`namedCache` Přidá položku`namedCaches` do kolekce mezipaměti paměti.  
  
 \<system.runtime.caching>  
\<memoryCache>  
\<namedCaches>  
\<add>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>type  
 `None`  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|-|-|  
|`CacheMemoryLimitMegabytes`|Celočíselná hodnota, která určuje maximální povolenou velikost (v megabajtech), kterou může <xref:System.Runtime.Caching.MemoryCache> instance a růst. Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> ve výchozím nastavení jsou používány heuristické automatické změny velikosti třídy.|  
|`Name`|Název mezipaměti.|  
|`PhysicalMemoryLimitPercentage`|Celočíselná hodnota mezi 0 a 100, která určuje maximální procento fyzicky instalované paměti počítače, kterou může mezipaměť spotřebovat. Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> ve výchozím nastavení jsou používány heuristické automatické změny velikosti třídy.|  
|`PollingInterval`|Hodnota, která označuje časový interval, po kterém implementace mezipaměti porovnává aktuální zatížení paměti s omezeními na základě absolutního a procenta velikosti paměti, které jsou nastaveny pro instanci mezipaměti. Tato hodnota je zadaná ve formátu "HH: MM: SS".|  
  
### <a name="child-elements"></a>Podřízené elementy  
 `None`  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|Obsahuje kolekci konfiguračních nastavení pro pojmenované <xref:System.Runtime.Caching.MemoryCache> instance.|  
  
## <a name="remarks"></a>Poznámky  
 Element přidá položku `namedCaches` do kolekce mezipaměti paměti. `add` Element [clear](clear-element-for-namedcaches.md) lze použít před použitím `add` elementu, aby bylo jisté, že v kolekci nejsou žádné další pojmenované mezipaměti. Tento element lze použít v souboru Machine. config a v souboru Web. config.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak definovat nastavení pro výchozí `namedCache` položku `namedCaches` do kolekce mezipaměti paměti.  
  
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
  
## <a name="see-also"></a>Viz také:

- [\<namedCaches – element > (nastavení mezipaměti)](namedcaches-element-cache-settings.md)
