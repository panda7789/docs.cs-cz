---
title: '&lt;performanceCounter&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounter element
- <performanceCounter> element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
ms.openlocfilehash: ea0eba097505741aba31bce4f23e0cc9ca1d4608
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712480"
---
# <a name="ltperformancecountergt-element-network-settings"></a>&lt;performanceCounter&gt; – Element (nastavení sítě)
Povolí nebo zakáže čítače výkonu sítě.  
  
 \<Konfigurace >  
\<system.net>  
\<settings>  
\<performanceCounters>  
  
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
|[settings](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Nakonfiguruje možnosti základní sítě pro <xref:System.Net> oboru názvů.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).  
  
 Čítače výkonu sítě musí být povolené v konfiguračním souboru, který se má použít. Všechny čítače výkonu sítě jsou povolené nebo zakázané s jedno nastavení v konfiguračním souboru. Jednotlivé čítače výkonu sítě nemůže být povolena nebo zakázána. Další informace o konkrétní čítače výkonu sítě, naleznete v tématu [čítače výkonu sítě](../../../../../docs/framework/debug-trace-profile/performance-counters.md#networking).  
  
 Výchozí hodnota je tento výkon sítě za čítače jsou zakázané.  
  
 <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> Vlastnost lze použít k získání aktuální hodnoty **povolené** atribut z příslušných konfiguračních souborů.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nakonfigurovat <xref:System.Net> a souvisejících oborech názvů umožňuje čítače výkonu sítě.  
  
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
- [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
- [Čítače výkonu sítě](../../../../../docs/framework/debug-trace-profile/performance-counters.md#networking)
