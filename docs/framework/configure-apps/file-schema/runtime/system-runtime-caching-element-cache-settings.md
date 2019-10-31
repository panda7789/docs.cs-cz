---
title: <system.runtime.caching> – element (nastavení mezipaměti)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: 70573f92f1799a54116bc91f7a39d157a7ae5b36
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115507"
---
# <a name="systemruntimecaching-element-cache-settings"></a>\<element System. Runtime. Caching > elementu (nastavení mezipaměti)

Poskytuje konfiguraci pro výchozí implementaci <xref:System.Runtime.Caching.ObjectCache> v paměti prostřednictvím položky `memoryCache` v konfiguračním souboru.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp; **\<System. Runtime. caching >**  
  
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

|Prvek|Popis|  
|-------------|-----------------|  
|[\<memoryCache >](memorycache-element-cache-settings.md)|Definuje prvek, který se používá ke konfiguraci mezipaměti, která je založena na třídě <xref:System.Runtime.Caching.MemoryCache>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Konfigurace \<](../configuration-element.md)|Určuje kořenový element v každém konfiguračním souboru, který je používán modulem CLR (Common Language Runtime) a .NET Framework aplikacemi.|  
  
## <a name="remarks"></a>Poznámky

Třídy v tomto oboru názvů poskytují způsob, jak používat ukládání do mezipaměti jako v ASP.NET, ale bez závislosti na sestavení `System.Web`. Další informace najdete v tématu [ukládání do mezipaměti v .NET Frameworkch aplikacích](../../../performance/caching-in-net-framework-applications.md).  
  
> [!NOTE]
> Funkce ukládání výstupu do mezipaměti a typy v oboru názvů <xref:System.Runtime.Caching> jsou v .NET Framework 4 nové.  
  
## <a name="example"></a>Příklad

Následující příklad ukazuje, jak nakonfigurovat mezipaměť, která je založena na třídě <xref:System.Runtime.Caching.MemoryCache>. Příklad ukazuje, jak nakonfigurovat instanci položky `namedCaches` pro paměťovou mezipaměť. Název mezipaměti je nastaven na výchozí název položky mezipaměti nastavením atributu `name` na výchozí.  
  
Atribut `cacheMemoryLimitMegabytes` a atribut `physicalMemoryPercentage` jsou nastaveny na hodnotu nula. Nastavení těchto atributů na hodnotu nula znamená, že ve výchozím nastavení se používají heuristiky <xref:System.Runtime.Caching.MemoryCache> automatické velikosti. Implementace mezipaměti by měla porovnat aktuální zatížení paměti s absolutními a procentuálními hodnotami paměti založenými na procentech každé dvě minuty.  
  
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

- [\<element > memoryCache (nastavení mezipaměti)](memorycache-element-cache-settings.md)
