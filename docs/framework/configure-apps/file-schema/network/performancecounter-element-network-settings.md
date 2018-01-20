---
title: "&lt;performanceCounter&gt; – Element (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounter element
- <performanceCounter> element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: c50bf9e882ade86e70db217a75fef2a893c45572
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="ltperformancecountergt-element-network-settings"></a>&lt;performanceCounter&gt; – Element (nastavení sítě)
Povolí nebo zakáže sítě čítače výkonu.  
  
 \<Konfigurace >  
\<system.net>  
\<Nastavení >  
\<čítače výkonu >  
  
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
|[nastavení](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Nakonfiguruje možnosti základní sítě <xref:System.Net> oboru názvů.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).  
  
 Čítače výkonu sítě je nutné povolit v konfiguračním souboru má být použit. Všechny síťové čítače výkonu jsou zapnutá nebo vypnutá s jedním nastavením v konfiguračním souboru. Nelze povolit nebo zakázat jednotlivé čítače výkonu sítě. Další informace o konkrétní síťové čítače výkonu, najdete v části [sítě čítače výkonu](http://msdn.microsoft.com/library/d1860235-f643-46ae-846c-ff0ed8b0e3cd).  
  
 Výchozí hodnota je tento výkon sítě, které čítače jsou zakázány.  
  
 <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> Vlastnost lze použít k získání aktuální hodnota **povoleno** atribut z příslušných konfiguračních souborů.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nakonfigurovat <xref:System.Net> a související obory názvů povolit sítě čítače výkonu.  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>  
 [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [Čítače výkonu sítě](http://msdn.microsoft.com/library/d1860235-f643-46ae-846c-ff0ed8b0e3cd)
