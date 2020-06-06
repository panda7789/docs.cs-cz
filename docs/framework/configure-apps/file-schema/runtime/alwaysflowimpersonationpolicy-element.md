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
ms.openlocfilehash: 7c8ac37932a528ff0f000cbaab49124dec51b88c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154480"
---
# <a name="alwaysflowimpersonationpolicy-element"></a>Element \<alwaysFlowImpersonationPolicy>
Určuje, že identita Windows má vždycky tok napříč asynchronními body bez ohledu na to, jak byla provedena zosobnění.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowImpersonationPolicy>**\  
  
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
  
|Hodnota|Description|  
|-----------|-----------------|  
|`false`|Identita systému Windows není předávána mezi asynchronními body, pokud zosobnění není provedeno prostřednictvím spravovaných metod, jako je <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> . Toto nastavení je výchozí.|  
|`true`|Identita systému Windows vždy přetéká napříč asynchronními body bez ohledu na to, jak byla provedena zosobnění.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 V .NET Framework verzích 1,0 a 1,1 neprovádí identita systému Windows tok mezi asynchronními body. V .NET Framework verze 2,0 je <xref:System.Threading.ExecutionContext> objekt, který obsahuje informace o aktuálně vykonávajícím vlákně a přenáší je napříč asynchronními body v rámci domény aplikace. Také se přenáší <xref:System.Security.Principal.WindowsIdentity> jako součást informací, které jsou v průběhu asynchronních bodů za předpokladu, že došlo k zosobnění pomocí spravovaných metod, jako je <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> a nikoli prostřednictvím jiných prostředků, jako je vyvolání platformy pro nativní metody. Tento prvek slouží k určení toho, že identita systému Windows probíhá přes asynchronní body bez ohledu na to, jakým způsobem bylo dosaženo zosobnění.  
  
 Výchozí chování můžete změnit dvěma způsoby:  
  
1. Ve spravovaném kódu v závislosti na vlákně.  
  
     Tok můžete potlačit na základě jednotlivých vláken úpravou <xref:System.Threading.ExecutionContext> <xref:System.Security.SecurityContext> nastavení a pomocí <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType> <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> metody, nebo <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> .  
  
2. Ve volání nespravovaného hostitelského rozhraní pro načtení modulu CLR (Common Language Runtime).  
  
     Pokud se pro načtení CLR používá nespravované rozhraní hostování (namísto jednoduchého spravovaného spustitelného souboru), můžete zadat speciální příznak ve volání funkce [CorBindToRuntimeEx – funkce](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) . Chcete-li povolit režim kompatibility pro celý proces, nastavte `flags` parametr pro [funkci CorBindToRuntimeEx –](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) na `STARTUP_ALWAYSFLOW_IMPERSONATION` .  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 V .NET Framework aplikaci lze tento prvek použít pouze v konfiguračním souboru aplikace.  
  
 V případě aplikace ASP.NET může být tok zosobnění konfigurován v souboru ASPNET. config, který najdete v \<Windows Folder> adresáři \Microsoft.NET\Framework\vx.x.xxxx.  
  
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
  
## <a name="see-also"></a>Viz také

- [Schéma nastavení modulu runtime](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [\<legacyImpersonationPolicy>Objekt](legacyimpersonationpolicy-element.md)
