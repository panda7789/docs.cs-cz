---
title: '&lt;alwaysflowimpersonationpolicy –&gt; – Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/alwaysFlowImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#alwaysFlowImpersonationPolicy
helpviewer_keywords:
- alwaysFlowImpersonationPolicy element
- <alwaysFlowImpersonationPolicy> element
ms.assetid: ee622801-9e46-470b-85ab-88c4b1dd2ee1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfdc2d434b61d1c1e16ebfdcc2ea423f96254be5
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187829"
---
# <a name="ltalwaysflowimpersonationpolicygt-element"></a>&lt;alwaysflowimpersonationpolicy –&gt; – Element
Určuje, že identita Windows vždy toky přes asynchronní body, bez ohledu na to, jak se provádí zosobnění.  
  
 \<Konfigurace >  
\<modul runtime >  
\<alwaysFlowImpersonationPolicy>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<alwaysFlowImpersonationPolicy    
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda Windows identity toky přes asynchronní body.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Windows identity není téct přes asynchronní body, pokud se pomocí provádí zosobnění spravovaného metody, například <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>. Toto nastavení je výchozí.|  
|`true`|Identita Windows vždy toky přes asynchronní body, bez ohledu na to, jak se provádí zosobnění.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 V rozhraní .NET Framework verze 1.0 a 1.1 identita Windows není téct přes asynchronní body. V rozhraní .NET Framework verze 2.0 je <xref:System.Threading.ExecutionContext> objekt, který obsahuje informace o aktuálně spuštěné vlákno a toky přes asynchronní body v rámci domény aplikace. <xref:System.Security.Principal.WindowsIdentity> Také toků, která prochází přes asynchronní body, pokud zosobnění bylo dosaženo pomocí informací v rámci spravovaného metody, například <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> a ne prostřednictvím jiným způsobem, jako je například platforma vyvolání pro nativní metody. Tento element slouží k určení, že identita Windows téct přes asynchronní body, bez ohledu na to, jak bylo dosaženo zosobnění.  
  
 Je-li změnit toto výchozí chování dvěma dalšími způsoby:  
  
1.  Ve spravovaném kódu na základě vlákno.  
  
     Tok na základě vlákna můžete potlačit pomocí úpravy <xref:System.Threading.ExecutionContext> a <xref:System.Security.SecurityContext> nastavení pomocí <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, nebo <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> metody.  
  
2.  Ve volání nespravovaných hostitelských rozhraní načíst modul CLR (CLR).  
  
     Pokud nespravovaných hostitelských rozhraní (místo jednoduchých spustitelný soubor spravovaný) slouží k načtení modulu CLR, můžete zadat speciální příznak ve volání [CorBindToRuntimeEx – funkce](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funkce. Chcete-li povolit režim kompatibility pro celý proces, nastavte `flags` parametr pro [CorBindToRuntimeEx – funkce](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) k `STARTUP_ALWAYSFLOW_IMPERSONATION`.  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 V aplikaci .NET Framework Tento element lze použít pouze v konfiguračním souboru aplikace.  
  
 Pro aplikace ASP.NET se dá nakonfigurovat tok zosobnění v soubor aspnet.config součástí \<složky Windows > \Microsoft.NET\Framework\vx.x.xxxx adresáře.  
  
 Technologie ASP.NET ve výchozím nastavení zakáže zosobnění tok v soubor aspnet.config pomocí následujících nastavení:  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 V technologii ASP.NET Pokud chcete místo toho povolit tok zosobnění je nutné explicitně zadat následující nastavení:  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit, že identita Windows toky přes asynchronní body, i v případě, že zosobnění se dosahuje prostřednictvím znamená, že než spravovaných metod.  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [\<legacyimpersonationpolicy – > – Element](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)
