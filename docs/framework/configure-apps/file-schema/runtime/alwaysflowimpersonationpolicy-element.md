---
title: Element <alwaysFlowImpersonationPolicy>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/alwaysFlowImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#alwaysFlowImpersonationPolicy
helpviewer_keywords:
- alwaysFlowImpersonationPolicy element
- <alwaysFlowImpersonationPolicy> element
ms.assetid: ee622801-9e46-470b-85ab-88c4b1dd2ee1
ms.openlocfilehash: 06e91ea6989dcdf0b2a179e7d6ce79b8d9aaff03
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118343"
---
# <a name="alwaysflowimpersonationpolicy-element"></a>\<element > alwaysFlowImpersonationPolicy
Určuje, že identita Windows má vždycky tok napříč asynchronními body bez ohledu na to, jak byla provedena zosobnění.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<alwaysFlowImpersonationPolicy >** \  
  
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
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda se v rámci asynchronních bodů využívá identita systému Windows.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Identita systému Windows není předávána mezi asynchronními body, pokud zosobnění není provedeno prostřednictvím spravovaných metod, jako je <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>. Toto nastavení je výchozí.|  
|`true`|Identita systému Windows vždy přetéká napříč asynchronními body bez ohledu na to, jak byla provedena zosobnění.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 V .NET Framework verzích 1,0 a 1,1 neprovádí identita systému Windows tok mezi asynchronními body. V .NET Framework verze 2,0 je k dispozici <xref:System.Threading.ExecutionContext> objekt, který obsahuje informace o aktuálně zpracovávaném vlákně a zpracovává ho napříč asynchronními body v rámci domény aplikace. <xref:System.Security.Principal.WindowsIdentity> také toků jako součást informací, které jsou v průběhu asynchronních bodů, za předpokladu, že došlo k zosobnění pomocí spravovaných metod, jako je například <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> a nikoli prostřednictvím jiných prostředků, jako je vyvolání platformy pro nativní metody. Tento prvek slouží k určení toho, že identita systému Windows probíhá přes asynchronní body bez ohledu na to, jakým způsobem bylo dosaženo zosobnění.  
  
 Výchozí chování můžete změnit dvěma způsoby:  
  
1. Ve spravovaném kódu v závislosti na vlákně.  
  
     Tok můžete potlačit v závislosti na vláknech změnou nastavení <xref:System.Threading.ExecutionContext> a <xref:System.Security.SecurityContext> pomocí metody <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>nebo <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType>.  
  
2. Ve volání nespravovaného hostitelského rozhraní pro načtení modulu CLR (Common Language Runtime).  
  
     Pokud se pro načtení CLR používá nespravované rozhraní hostování (namísto jednoduchého spravovaného spustitelného souboru), můžete zadat speciální příznak ve volání funkce [CorBindToRuntimeEx – funkce](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) . Chcete-li povolit režim kompatibility pro celý proces, nastavte parametr `flags` [funkce CorBindToRuntimeEx –](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) na hodnotu `STARTUP_ALWAYSFLOW_IMPERSONATION`.  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 V .NET Framework aplikaci lze tento prvek použít pouze v konfiguračním souboru aplikace.  
  
 V případě aplikace ASP.NET může být tok zosobnění konfigurován v souboru ASPNET. config, který se nachází ve složce \<Windows > adresáři \Microsoft.NET\Framework\vx.x.xxxx.  
  
 ASP.NET ve výchozím nastavení zakáže tok zosobnění v souboru ASPNET. config pomocí následujících nastavení konfigurace:  
  
```xml
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
 Následující příklad ukazuje, jak určit, že se má identita systému Windows provádět napříč asynchronními body, a to i v případě, že je možné zosobnění dosáhnout prostřednictvím jiných prostředků než spravovaných metod.  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [\<element > legacyImpersonationPolicy](legacyimpersonationpolicy-element.md)
