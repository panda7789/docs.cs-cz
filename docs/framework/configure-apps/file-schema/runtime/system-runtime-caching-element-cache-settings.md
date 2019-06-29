---
title: <system.runtime.caching> – element (nastavení mezipaměti)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbb977e05fa54b726b0cd584d287dc00c8ced995
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423257"
---
# <a name="systemruntimecaching-element-cache-settings"></a>\<System.Runtime.Caching > – Element (nastavení mezipaměti)

Poskytuje konfiguraci pro výchozí v paměťově <xref:System.Runtime.Caching.ObjectCache> implementaci prostřednictvím `memoryCache` záznam v konfiguračním souboru.  
  
 \<Konfigurace >  
\<system.runtime.caching>  
  
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
|[\<memoryCache>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|Definuje element, který se používá ke konfiguraci, která je založená na mezipaměti <xref:System.Runtime.Caching.MemoryCache> třídy.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Určuje kořenový element v každém konfiguračním souboru, který je používán common language runtime a aplikace rozhraní .NET Framework.|  
  
## <a name="remarks"></a>Poznámky

Třídy v tomto oboru názvů poskytují způsob, jak používat ukládání do mezipaměti zařízení podobné těm v technologii ASP.NET, ale bez závislosti na `System.Web` sestavení. Další informace najdete v tématu [ukládání do mezipaměti v aplikacích .NET Framework](../../../../../docs/framework/performance/caching-in-net-framework-applications.md).  
  
> [!NOTE]
>  Výstupu do mezipaměti, funkce a typy v <xref:System.Runtime.Caching> obor názvů jsou nové v rozhraní .NET Framework 4.  
  
## <a name="example"></a>Příklad

Následující příklad ukazuje postup při konfiguraci mezipaměti, který je založen na <xref:System.Runtime.Caching.MemoryCache> třídy. Tento příklad ukazuje, jak nakonfigurovat instanci `namedCaches` zadání mezipaměti. Název mezipaměti, je nastavena na výchozí název položky mezipaměti tak, že nastavíte `name` atribut "Výchozí".  
  
`cacheMemoryLimitMegabytes` Atribut a `physicalMemoryPercentage` je atribut nastaven na hodnotu nula. Nastavení těchto atributů 0 znamená, <xref:System.Runtime.Caching.MemoryCache> heuristiky automatické přizpůsobení velikosti se používají ve výchozím nastavení. Implementace mezipaměti by měla porovnání aktuálního zatížení paměti proti absolutní a založený na procentech paměťová omezení každé dvě minuty.  
  
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

- [\<memoryCache > – Element (nastavení mezipaměti)](memorycache-element-cache-settings.md)
