---
title: Element <legacyImpersonationPolicy>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#legacyImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/legacyImpersonationPolicy
helpviewer_keywords:
- <legacyImpersonationPolicy> element
- legacyImpersonationPolicy element
ms.assetid: 6e00af10-42f3-4235-8415-1bb2db78394e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c39ee551dde19d87a75403f3db7433d1ef829f3b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704632"
---
# <a name="legacyimpersonationpolicy-element"></a>\<legacyImpersonationPolicy> Element
Určuje, že identita Windows není téct přes asynchronní body, bez ohledu na nastavení toku pro kontext spuštění pro aktuální vlákno.  
  
 \<Konfigurace >  
\<modul runtime >  
\<legacyImpersonationPolicy>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<legacyImpersonationPolicy    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, že <xref:System.Security.Principal.WindowsIdentity> není téct přes asynchronní body, bez ohledu na to <xref:System.Threading.ExecutionContext> tok nastavení pro aktuální vlákno.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|<xref:System.Security.Principal.WindowsIdentity> toky přes asynchronní body v závislosti na <xref:System.Threading.ExecutionContext> tok nastavení pro aktuální vlákno. Toto nastavení je výchozí.|  
|`true`|<xref:System.Security.Principal.WindowsIdentity> není téct přes asynchronní body, bez ohledu <xref:System.Threading.ExecutionContext> tok nastavení pro aktuální vlákno.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 V rozhraní .NET Framework verze 1.0 a 1.1 <xref:System.Security.Principal.WindowsIdentity> není téct přes asynchronní body žádné definované uživatelem. Od verze rozhraní .NET Framework verze 2.0, je <xref:System.Threading.ExecutionContext> toků, který obsahuje informace o aktuálně spuštěné vlákno a to přes asynchronní body v rámci domény aplikace. <xref:System.Security.Principal.WindowsIdentity> Je zahrnutá v tomto kontextu spuštění a proto se přenášejí také přes asynchronní body, což znamená, že pokud existuje objekt context zosobnění, se budou směrovat také.  
  
 Od verze rozhraní .NET Framework 2.0, můžete použít `<legacyImpersonationPolicy>` elementu, chcete-li určit, že <xref:System.Security.Principal.WindowsIdentity> není téct přes asynchronní body.  
  
> [!NOTE]
>  Modul CLR (CLR) je seznámen zosobnění operací provedených pomocí pouze spravovaný kód, ne o zosobnění provést mimo spravovaný kód, například prostřednictvím platformy volání nespravovaného kódu nebo prostřednictvím přímé volání funkcí Win32. Pouze spravované <xref:System.Security.Principal.WindowsIdentity> objekty může téct přes asynchronní body, pokud `alwaysFlowImpersonationPolicy` prvku je nastavená na hodnotu true (`<alwaysFlowImpersonationPolicy enabled="true"/>`). Nastavení `alwaysFlowImpersonationPolicy` prvku na hodnotu true Určuje, že identita Windows vždy toky přes asynchronní body, bez ohledu na to, jak se provádí zosobnění. Další informace o toku nespravované zosobnění přes asynchronní body, přečtěte si téma [ \<alwaysflowimpersonationpolicy – > Element](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).  
  
 Je-li změnit toto výchozí chování dvěma dalšími způsoby:  
  
1. Ve spravovaném kódu na základě vlákno.  
  
     Tok na základě vlákna můžete potlačit pomocí úpravy <xref:System.Threading.ExecutionContext> a <xref:System.Security.SecurityContext> nastavení pomocí <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> nebo <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> metody.  
  
2. Ve volání nespravovaných hostitelských rozhraní načíst modul CLR (CLR).  
  
     Pokud nespravovaných hostitelských rozhraní (místo jednoduchých spustitelný soubor spravovaný) slouží k načtení modulu CLR, můžete zadat speciální příznak ve volání [CorBindToRuntimeEx – funkce](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funkce. Chcete-li povolit režim kompatibility pro celý proces, nastavte `flags` parametr pro [CorBindToRuntimeEx – funkce](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) k STARTUP_LEGACY_IMPERSONATION.  
  
 Další informace najdete v tématu [ \<alwaysflowimpersonationpolicy – > Element](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 V aplikaci .NET Framework Tento element lze použít pouze v konfiguračním souboru aplikace.  
  
 Pro aplikace ASP.NET se dá nakonfigurovat tok zosobnění v soubor aspnet.config součástí \<složky Windows > \Microsoft.NET\Framework\vx.x.xxxx adresáře.  
  
 Technologie ASP.NET ve výchozím nastavení zakáže zosobnění tok v soubor aspnet.config pomocí následujících nastavení:  
  
``` xml
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
 Následující příklad ukazuje, jak určit starší chování, které není identita Windows téct přes asynchronní body.  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [\<alwaysFlowImpersonationPolicy> Element](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)
