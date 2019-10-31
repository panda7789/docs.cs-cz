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
ms.openlocfilehash: 18a027bc09f2400a10a06efdc4c5355686bcb56d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116531"
---
# <a name="legacyimpersonationpolicy-element"></a>\<element > legacyImpersonationPolicy
Určuje, že identita systému Windows není v rámci asynchronních bodů předávána bez ohledu na nastavení toku pro kontext spuštění v aktuálním vlákně.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<legacyImpersonationPolicy >**  
  
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
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, že <xref:System.Security.Principal.WindowsIdentity> neprovádí tok mezi asynchronními body bez ohledu na nastavení toku <xref:System.Threading.ExecutionContext> v aktuálním vlákně.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|<xref:System.Security.Principal.WindowsIdentity> toků napříč asynchronními body v závislosti na nastavení <xref:System.Threading.ExecutionContext> Flow pro aktuální vlákno. Toto nastavení je výchozí.|  
|`true`|<xref:System.Security.Principal.WindowsIdentity> neprovádí tok mezi asynchronními body bez ohledu na nastavení toku <xref:System.Threading.ExecutionContext> v aktuálním vlákně.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 V .NET Framework verzích 1,0 a 1,1 není <xref:System.Security.Principal.WindowsIdentity> tok napříč žádnými asynchronními body definovanými uživatelem. .NET Framework počínaje verzí 2,0 je k dispozici objekt <xref:System.Threading.ExecutionContext>, který obsahuje informace o aktuálně zpracovávaném vlákně a přetéká mezi asynchronními body v rámci domény aplikace. <xref:System.Security.Principal.WindowsIdentity> je obsažen v tomto kontextu spuštění, a proto také toků napříč asynchronními body, což znamená, že pokud existuje kontext zosobnění, bude tok také.  
  
 Počínaje .NET Framework 2,0 lze pomocí elementu `<legacyImpersonationPolicy>` určit, že <xref:System.Security.Principal.WindowsIdentity> neprovádí tok mezi asynchronními body.  
  
> [!NOTE]
> Modul CLR (Common Language Runtime) ví o operacích zosobnění provedených pomocí pouze spravovaného kódu, nikoli zosobnění prováděné mimo spravovaný kód, jako je například volání platformy do nespravovaného kódu nebo prostřednictvím přímých volání funkcí Win32. Pouze spravované <xref:System.Security.Principal.WindowsIdentity> objekty mohou procházet přes asynchronní body, pokud prvek `alwaysFlowImpersonationPolicy` nebyl nastaven na hodnotu true (`<alwaysFlowImpersonationPolicy enabled="true"/>`). Nastavením prvku `alwaysFlowImpersonationPolicy` na hodnotu true Určuje, že identita Windows je vždy přenášena přes asynchronní body bez ohledu na to, jak byla provedena zosobnění. Další informace o tom, jak přesměrovat nespravované zosobnění přes asynchronní body, naleznete v tématu [\<alwaysFlowImpersonationPolicy > elementu](alwaysflowimpersonationpolicy-element.md).  
  
 Výchozí chování můžete změnit dvěma způsoby:  
  
1. Ve spravovaném kódu v závislosti na vlákně.  
  
     Tok můžete potlačit v závislosti na vlákně změnou nastavení <xref:System.Threading.ExecutionContext> a <xref:System.Security.SecurityContext> pomocí metody <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> nebo <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType>.  
  
2. Ve volání nespravovaného hostitelského rozhraní pro načtení modulu CLR (Common Language Runtime).  
  
     Pokud se pro načtení CLR používá nespravované rozhraní hostování (namísto jednoduchého spravovaného spustitelného souboru), můžete zadat speciální příznak ve volání funkce [CorBindToRuntimeEx – funkce](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) . Chcete-li povolit režim kompatibility pro celý proces, nastavte parametr `flags` pro [funkci CorBindToRuntimeEx –](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) na STARTUP_LEGACY_IMPERSONATION.  
  
 Další informace naleznete v tématu [\<alwaysFlowImpersonationPolicy > elementu](alwaysflowimpersonationpolicy-element.md).  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 V .NET Framework aplikaci lze tento prvek použít pouze v konfiguračním souboru aplikace.  
  
 V případě aplikace ASP.NET může být tok zosobnění konfigurován v souboru ASPNET. config, který se nachází ve složce \<Windows > adresáři \Microsoft.NET\Framework\vx.x.xxxx.  
  
 ASP.NET ve výchozím nastavení zakáže tok zosobnění v souboru ASPNET. config pomocí následujících nastavení konfigurace:  
  
``` xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 Pokud chcete místo toho použít tok zosobnění, musíte v ASP.NET explicitně použít následující nastavení konfigurace:  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit starší chování, které neflowuje identitu systému Windows napříč asynchronními body.  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [\<element > alwaysFlowImpersonationPolicy](alwaysflowimpersonationpolicy-element.md)
