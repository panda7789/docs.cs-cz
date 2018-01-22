---
title: "&lt;spuštění&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
caps.latest.revision: "19"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4299775cd23162839ab9846adc7d2c64cc18a404
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="ltstartupgt-element"></a>&lt;spuštění&gt; – Element
Určuje common language runtime spuštění informace.  
  
 \<Konfigurace >  
\<spuštění >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<startup useLegacyV2RuntimeActivationPolicy="true|false" >   
</startup>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`useLegacyV2RuntimeActivationPolicy`|Nepovinný atribut.<br /><br /> Určuje, jestli se má povolit [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] Zásady aktivace modulu runtime, nebo chcete použít [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] aktivace zásad.|  
  
## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a>useLegacyV2RuntimeActivationPolicy Attribute  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`true`|Povolit [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] Zásady aktivace modulu runtime pro vybraný modul runtime, který je pro vazbu techniky aktivace starší verze runtime (například [CorBindToRuntimeEx – funkce](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)) do výběru z konfiguračního souboru místo runtime omezení je na verze modulu CLR 2.0. Proto pokud CLR verze 4 nebo novější je zvoleno z konfiguračního souboru, ve smíšeném režimu sestavení vytvořených ve starších verzích rozhraní .NET Framework se načetly na zvolené verzi CLR. Nastavení této hodnoty zabraňuje CLR verze 1.1 nebo verze modulu CLR 2.0 načtení do stejně účinně zakázat funkci vedle sebe v procesu.|  
|`false`|Použít výchozí zásady aktivace pro [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] a novější, který je umožnit starší verze modulu runtime aktivace techniky načíst CLR verze 1.1 nebo 2.0 do procesu. Nastavení této hodnoty brání ve smíšeném režimu sestavení z načítání do rozhraní .NET Framework 4 nebo novější, pokud jejich byly vytvořené pomocí rozhraní .NET Framework 4 nebo novější. Tato hodnota je výchozí.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<requiredRuntime >](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|Určuje, jestli aplikace podporuje pouze verzi 1.0 modul common language runtime. Aplikace vytvořené s nástroji runtime verze 1.1 nebo novější by měly používat  **\<supportedRuntime >** element.|  
|[\<supportedRuntime>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|Určuje, kterou verzi modulu Common Language Runtime (CLR) aplikace podporuje.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
  
## <a name="remarks"></a>Poznámky  
 **\<SupportedRuntime >** element má být používána všechny aplikace vytvořené pomocí verze 1.1 nebo novější modulu runtime. Musíte použít aplikace založené na podporu pouze verze 1.0 modulu runtime  **\<requiredRuntime >** element.  
  
 Kód spuštění aplikace hostované v aplikaci Internet Explorer ignoruje  **\<spuštění >** elementu a jeho podřízené elementy.  
  
## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a>Atribut useLegacyV2RuntimeActivationPolicy  
 Tento atribut je užitečné, pokud vaše aplikace používá starší verze aktivace cesty, jako [CorBindToRuntimeEx – funkce](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), a chcete tyto cesty k aktivaci 4 verzi modulu CLR místo starší verze, nebo pokud je vaše aplikace vytvořené s nástroji [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] ale obsahuje závislost na ve smíšeném režimu sestavení vytvořené s dřívější verzi rozhraní .NET Framework. V těchto scénářích, nastavte atribut na `true`.  
  
> [!NOTE]
>  Nastavení atributu na `true` CLR verze 1.1 nebo verze modulu CLR 2.0 brání načtení do stejně účinně zakázat funkci vedle sebe v procesu (najdete v části [spuštění vedle sebe zprostředkovatel komunikace s objekty COM](http://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit verzi modulu runtime v konfiguračním souboru.  
  
```xml  
<!-- When used with version 1.0 of the .NET Framework runtime -->  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
<!-- When used with version 1.1 (or later) of the runtime -->  
<configuration>  
   <startup>  
      <supportedRuntime version="v1.1.4322"/>  
      <supportedRuntime version="v1.0.3705"/>  
   </startup>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení spouštění](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<PaveOver > Zadání kterou verzi modulu Runtime pro použití](http://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)  
 [Spuštění vedle sebe zprostředkovatel komunikace s objekty COM](http://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)  
 [Vnitroprocesové souběžné provádění](../../../../../docs/framework/deployment/in-process-side-by-side-execution.md)
