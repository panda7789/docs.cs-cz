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
ms.openlocfilehash: cd09598800b74c4807163bc921806f5b470e0d24
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252501"
---
# <a name="legacyimpersonationpolicy-element"></a>\<legacyImpersonationPolicy – element >
Určuje, že identita systému Windows není v rámci asynchronních bodů předávána bez ohledu na nastavení toku pro kontext spuštění v aktuálním vlákně.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> modulu runtime**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<legacyImpersonationPolicy>**  
  
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
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, že <xref:System.Security.Principal.WindowsIdentity> nedojde k toku mezi asynchronními body bez ohledu na <xref:System.Threading.ExecutionContext> nastavení toku v aktuálním vlákně.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Value|Popis|  
|-----------|-----------------|  
|`false`|<xref:System.Security.Principal.WindowsIdentity>toky napříč asynchronními body v závislosti <xref:System.Threading.ExecutionContext> na nastavení toku pro aktuální vlákno. Toto nastavení je výchozí.|  
|`true`|<xref:System.Security.Principal.WindowsIdentity>neprovádí tok mezi asynchronními body bez ohledu na <xref:System.Threading.ExecutionContext> nastavení toku v aktuálním vlákně.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 V .NET Framework verzích 1,0 a 1,1 <xref:System.Security.Principal.WindowsIdentity> není tok rozložen mezi žádné uživatelem definované asynchronní body. .NET Framework počínaje verzí 2,0 je <xref:System.Threading.ExecutionContext> objekt, který obsahuje informace o aktuálně zpracovávaném vlákně a který je v rámci domény aplikace tok mezi asynchronními body. <xref:System.Security.Principal.WindowsIdentity> Je součástí tohoto kontextu spuštění, a proto také toků napříč asynchronními body, což znamená, že pokud existuje kontext zosobnění, bude tok také.  
  
 Počínaje .NET Framework 2,0 můžete použít `<legacyImpersonationPolicy>` element k určení, které <xref:System.Security.Principal.WindowsIdentity> není v rámci asynchronních bodů natéká.  
  
> [!NOTE]
> Modul CLR (Common Language Runtime) ví o operacích zosobnění provedených pomocí pouze spravovaného kódu, nikoli zosobnění prováděné mimo spravovaný kód, jako je například volání platformy do nespravovaného kódu nebo prostřednictvím přímých volání funkcí Win32. Pouze spravované <xref:System.Security.Principal.WindowsIdentity> objekty mohou procházet přes asynchronní body, `alwaysFlowImpersonationPolicy` Pokud prvek nebyl nastaven na hodnotu true (`<alwaysFlowImpersonationPolicy enabled="true"/>`). `alwaysFlowImpersonationPolicy` Nastavení elementu na hodnotu true Určuje, že identita systému Windows je vždy přenášena přes asynchronní body bez ohledu na to, jak byla provedena zosobnění. Další informace o tom, jak přesměrovat nespravované zosobnění přes asynchronní body, naleznete v tématu [ \<alwaysFlowImpersonationPolicy > element](alwaysflowimpersonationpolicy-element.md).  
  
 Výchozí chování můžete změnit dvěma způsoby:  
  
1. Ve spravovaném kódu v závislosti na vlákně.  
  
     Tok <xref:System.Threading.ExecutionContext> můžete potlačit na základě jednotlivých vláken úpravou <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> nastavení a <xref:System.Security.SecurityContext> pomocí <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>metody nebo <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> .  
  
2. Ve volání nespravovaného hostitelského rozhraní pro načtení modulu CLR (Common Language Runtime).  
  
     Pokud se pro načtení CLR používá nespravované rozhraní hostování (namísto jednoduchého spravovaného spustitelného souboru), můžete zadat speciální příznak ve volání funkce [CorBindToRuntimeEx – funkce](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) . Chcete-li povolit režim kompatibility pro celý proces, nastavte `flags` parametr pro [funkci CorBindToRuntimeEx –](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) na STARTUP_LEGACY_IMPERSONATION.  
  
 Další informace naleznete v [ \<tématu alwaysFlowImpersonationPolicy > element](alwaysflowimpersonationpolicy-element.md).  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 V .NET Framework aplikaci lze tento prvek použít pouze v konfiguračním souboru aplikace.  
  
 V případě aplikace ASP.NET může být tok zosobnění konfigurován v souboru ASPNET. config, který se nachází ve \<složce Windows > adresáři \Microsoft.NET\Framework\vx.x.xxxx.  
  
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
- [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md)
