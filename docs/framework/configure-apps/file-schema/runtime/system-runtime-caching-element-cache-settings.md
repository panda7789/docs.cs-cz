---
title: <system.runtime.caching> – element (nastavení mezipaměti)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: df4887c8801dcf8af06b3826673a03cbc7dbc9b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153851"
---
# <a name="systemruntimecaching-element-cache-settings"></a>\<system.runtime.caching> Element (Nastavení mezipaměti)

Poskytuje konfiguraci pro výchozí <xref:System.Runtime.Caching.ObjectCache> implementaci `memoryCache` v paměti prostřednictvím položky v konfiguračním souboru.  
  
[**\<>konfigurace**](../configuration-element.md)\
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

|Element|Popis|  
|-------------|-----------------|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|Definuje prvek, který se používá ke konfiguraci <xref:System.Runtime.Caching.MemoryCache> mezipaměti, která je založena na třídě.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<>konfigurace](../configuration-element.md)|Určuje kořenový prvek v každém konfiguračním souboru, který používá aplikace COMMON Language runtime a .NET Framework.|  
  
## <a name="remarks"></a>Poznámky

Třídy v tomto oboru názvů poskytují způsob, jak používat ukládání do mezipaměti `System.Web` zařízení, jako jsou v ASP.NET, ale bez závislosti na sestavení. Další informace naleznete [v tématu Ukládání do mezipaměti v aplikacích rozhraní .NET Framework](../../../performance/caching-in-net-framework-applications.md).  
  
> [!NOTE]
> Funkce ukládání do mezipaměti výstupu <xref:System.Runtime.Caching> a typy v oboru názvů jsou nové v rozhraní .NET Framework 4.  
  
## <a name="example"></a>Příklad

Následující příklad ukazuje, jak nakonfigurovat mezipaměť, která je založena na <xref:System.Runtime.Caching.MemoryCache> třídě. Příklad ukazuje, jak nakonfigurovat `namedCaches` instanci položky pro mezipaměť. Název mezipaměti je nastaven na výchozí název položky mezipaměti nastavením atributu `name` "Výchozí".  
  
Atribut `cacheMemoryLimitMegabytes` a `physicalMemoryPercentage` atribut jsou nastaveny na nulu. Nastavení těchto atributů na <xref:System.Runtime.Caching.MemoryCache> nulu znamená, že autosizing heuristiky jsou používány ve výchozím nastavení. Implementace mezipaměti by měla porovnávat aktuální zatížení paměti s absolutními a procentuálními limity paměti každé dvě minuty.  
  
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

- [\<memoryCache> Element (Nastavení mezipaměti)](memorycache-element-cache-settings.md)
