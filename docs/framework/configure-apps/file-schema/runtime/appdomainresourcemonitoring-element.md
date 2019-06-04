---
title: Element <appDomainResourceMonitoring>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad0ae023215eeb1f42f9351369ee77d41d537b88
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487725"
---
# <a name="appdomainresourcemonitoring-element"></a>\<appDomainResourceMonitoring> Element
Dá pokyn modulu runtime ke shromažďování statistik na všech doménách aplikace v procesu po dobu trvání procesu.  
  
 \<Konfigurace >  
\<modul runtime >  
\<appDomainResourceMonitoring>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda modul runtime shromažďuje statistiky pro sledování prostředků domény aplikace.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Value|Popis|  
|-----------|-----------------|  
|`true`|Statistika Sledování prostředků domény aplikace se shromažďují.|  
|`false`|Statistika Sledování prostředků domény aplikace se neshromažďují.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Sledování prostředků aplikační domény nabízíme v rámci doménové třídy spravované aplikace, který je hostitelem [iclrappdomainresourcemonitor –](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) rozhraní a trasování událostí pro Windows (ETW). Pokud je zapnuto monitorování, statistiky se shromažďují pro všechny domény aplikace v procesu po dobu trvání procesu.  
  
 Chcete-li povolit monitorování ze spravovaného kódu, použijte <xref:System.AppDomain.MonitoringIsEnabled%2A> vlastnost.  
  
 Tento prvek konfigurace je k dispozici pouze v rozhraní .NET Framework 4 a novější.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak povolit sledování prostředků domény aplikace.  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
