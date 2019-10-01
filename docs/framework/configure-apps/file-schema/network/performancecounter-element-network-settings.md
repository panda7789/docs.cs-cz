---
title: <performanceCounter> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounter element
- <performanceCounter> element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
ms.openlocfilehash: 3fe6b19d0055aafad859b55960800d9786d7fa08
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698003"
---
# <a name="performancecounter-element-network-settings"></a>@no__t – element > 0performanceCounter (nastavení sítě)
Povolí nebo zakáže čítače výkonu sítě.  
  
[ **@no__t – 2configuration >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **@no__t -4system. NET >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<settings >** ](settings-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<performanceCounters >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Určuje, zda jsou povoleny čítače výkonu sítě. Výchozí hodnota je `false`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[možnost](settings-element-network-settings.md)|Konfiguruje základní možnosti sítě pro obor názvů <xref:System.Net>.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).  
  
 V konfiguračním souboru musí být povolené čítače výkonu sítě, které se mají použít. Všechny čítače výkonu sítě jsou povoleny nebo zakázány v jednom nastavení konfiguračního souboru. Nelze povolit nebo zakázat jednotlivé čítače výkonu sítě. Další informace o konkrétních čítačích výkonu sítě najdete v tématu [čítače výkonu sítě](../../../debug-trace-profile/performance-counters.md#networking).  
  
 Výchozí hodnota je zakázané čítače výkonu sítě.  
  
 Vlastnost <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> lze použít k získání aktuální hodnoty atributu **Enabled** z příslušných konfiguračních souborů.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nakonfigurovat <xref:System.Net> a související obory názvů pro povolení čítačů výkonu sítě.  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <performanceCounters  
        enabled="true"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [Schéma nastavení sítě](index.md)
- [Čítače výkonu sítě](../../../debug-trace-profile/performance-counters.md#networking)
