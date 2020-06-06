---
title: <system.runtime.caching> – element (nastavení mezipaměti)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: df4887c8801dcf8af06b3826673a03cbc7dbc9b5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153851"
---
# <a name="systemruntimecaching-element-cache-settings"></a>\<system.runtime.caching> – element (nastavení mezipaměti)

Poskytuje konfiguraci pro výchozí implementaci v paměti <xref:System.Runtime.Caching.ObjectCache> prostřednictvím `memoryCache` záznamu v konfiguračním souboru.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.runtime.caching>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy

`None`  

### <a name="child-elements"></a>Podřízené elementy

|Prvek|Description|  
|-------------|-----------------|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|Definuje prvek, který se používá ke konfiguraci mezipaměti založené na <xref:System.Runtime.Caching.MemoryCache> třídě.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|Určuje kořenový element v každém konfiguračním souboru, který je používán modulem CLR (Common Language Runtime) a .NET Framework aplikacemi.|  
  
## <a name="remarks"></a>Poznámky

Třídy v tomto oboru názvů poskytují způsob, jak používat ukládání do mezipaměti, jako jsou ty v ASP.NET, ale bez závislosti na `System.Web` sestavení. Další informace najdete v tématu [ukládání do mezipaměti v .NET Frameworkch aplikacích](../../../performance/caching-in-net-framework-applications.md).  
  
> [!NOTE]
> Funkce ukládání výstupu do mezipaměti a typy v <xref:System.Runtime.Caching> oboru názvů jsou v .NET Framework 4 nové.  
  
## <a name="example"></a>Příklad

Následující příklad ukazuje, jak nakonfigurovat mezipaměť, která je založena na <xref:System.Runtime.Caching.MemoryCache> třídě. V tomto příkladu se dozvíte, jak nakonfigurovat instanci `namedCaches` položky pro paměťovou mezipaměť. Název mezipaměti je nastaven na výchozí název položky mezipaměti nastavením `name` atributu na výchozí.  
  
`cacheMemoryLimitMegabytes`Atribut a `physicalMemoryPercentage` atribut jsou nastaveny na hodnotu nula. Nastavení těchto atributů na hodnotu nula znamená, že <xref:System.Runtime.Caching.MemoryCache> výchozí hodnoty pro automatické změny velikosti jsou používány ve výchozím nastavení. Implementace mezipaměti by měla porovnat aktuální zatížení paměti s absolutními a procentuálními hodnotami paměti založenými na procentech každé dvě minuty.  
  
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

- [\<memoryCache>– Element (nastavení mezipaměti)](memorycache-element-cache-settings.md)
