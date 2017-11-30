---
title: "&lt;namedCaches&gt; – Element (nastavení mezipaměti)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: bdafddcb05dd50f059c9f6804573beec085a4a2a
ms.sourcegitcommit: d0f7646d67db5809cf43ff1d27b399a4020e8ee2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2017
---
# <a name="ltnamedcachesgt-element-cache-settings"></a>&lt;namedCaches&gt; – Element (nastavení mezipaměti)
Určuje kolekci nastavení konfigurace pro pojmenované <xref:System.Runtime.Caching.MemoryCache> instance. <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> Odkazuje vlastnost kolekce nastavení konfigurace z jedné nebo více `namedCaches` elementy konfiguračního souboru.  
  
 \<Konfigurace >  
\<System.Runtime.Caching – >  
\<memoryCache >  
\<namedCaches >  
  
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
|`cacheMemoryLimitMegabytes`|Celočíselná hodnota, která určuje maximální povolenou velikost v megabajtech, která instance <xref:System.Runtime.Caching.MemoryCache> můžete dosáhnout. Výchozí hodnota je 0, což znamená, že heuristiky Automatická změna velikosti z <xref:System.Runtime.Caching.MemoryCache> třída se používá ve výchozím nastavení.|  
|`name`|Název mezipaměti.|  
|`physicalMemoryLimitPercentage`|Celočíselná hodnota mezi 0 a 100 určující maximální procento paměti fyzicky nainstalovaném počítači, která mohou být spotřebovávána mezipaměti. Výchozí hodnota je 0, což znamená, že heuristiky Automatická změna velikosti z <xref:System.Runtime.Caching.MemoryCache> třída se používá ve výchozím nastavení.|  
|`pollingInterval`|Hodnota, která určuje časový interval, po jejímž uplynutí implementace mezipaměti porovná aktuální zatížení paměti do paměti absolutní a na základě procenta omezení, které jsou nastavené pro instanci mezipaměti. Tato hodnota je uvedeno ve formátu hh: mm".|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Přidat >](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)|Přidá pojmenované mezipaměti, aby `namedCaches` kolekci pro mezipaměť.|  
|[\<Clear >](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)|Vymaže `namedCaches` kolekci pro mezipaměť.|  
|[\<Odebrat >](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)|Odebere položku s názvem mezipaměti z `namedCaches` kolekci pro mezipaměť.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<memoryCache >](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|Definuje element, který slouží ke konfiguraci mezipaměti, který je založen na <xref:System.Runtime.Caching.MemoryCache> třídy.|  
  
## <a name="remarks"></a>Poznámky  
 Oddíl konfigurace mezipaměti paměti souboru Web.config může obsahovat `add`, `remove`, a `clear` atributy pro `namedCaches` kolekce. Každý `namedCaches` položka je jedinečně identifikovaný `name` atribut.  
  
 Instance položky mezipaměti paměti můžete načíst tak, že odkazy na informace v konfigurační soubory aplikace. Ve výchozím nastavení pouze výchozí instance mezipaměti má záznam v konfiguračním souboru. Výchozí instance mezipaměti je instanci, která je vrácena z <xref:System.Runtime.Caching.MemoryCache.Default%2A> vlastnost.  
  
 Pokud jste nastavili atribut názvu "Výchozí", element používá výchozí instanci mezipaměti paměti.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nastavit název mezipaměti na výchozí název položky mezipaměti nastavením `name` atribut "Výchozí".  
  
 `cacheMemoryLimitMegabytes` Atribut a `physicalMemoryPercentage` atribut nastaveny na nulu. Nastavení těchto atributů na hodnotu nula znamená, že heuristiky Automatická změna velikosti z <xref:System.Runtime.Caching.MemoryCache> třída se používá. Implementace mezipaměti porovná aktuální zatížení paměti do paměti absolutní a na základě procenta omezení každé dvě minuty.  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [\<memoryCache > – Element (nastavení mezipaměti)](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
