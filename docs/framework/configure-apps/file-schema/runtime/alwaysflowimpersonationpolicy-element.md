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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154480"
---
# <a name="alwaysflowimpersonationpolicy-element"></a>\<alwaysFlowImpersonationPolicy> Element
Určuje, že identita systému Windows vždy proudí přes asynchronní body, bez ohledu na to, jak bylo zosobnění provedeno.  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)\
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
|`enabled`|Požadovaný atribut.<br /><br /> Označuje, zda identita systému Windows proudí přes asynchronní body.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Identita systému Windows neprochází přes asynchronní body, pokud se zosobnění neprovádí pomocí spravovaných metod, jako je například <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>. Toto nastavení je výchozí.|  
|`true`|Identita systému Windows vždy proudí přes asynchronní body, bez ohledu na to, jak bylo zosobnění provedeno.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 V rozhraní .NET Framework verze 1.0 a 1.1 identita systému Windows neprobíhá přes asynchronní body. V rozhraní .NET Framework verze 2.0 je <xref:System.Threading.ExecutionContext> objekt, který obsahuje informace o aktuálně spuštěné vlákno a toky přes asynchronní body v rámci domény aplikace. Také <xref:System.Security.Principal.WindowsIdentity> toky jako součást informací, které toky přes asynchronní body, za předpokladu, <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> že zosobnění bylo dosaženo pomocí spravovaných metod, jako jsou a nikoli prostřednictvím jiných prostředků, jako je například platforma vyvolat nativní metody. Tento prvek se používá k určení, že identita systému Windows tok přes asynchronní body, bez ohledu na to, jak bylo dosaženo zosobnění.  
  
 Toto výchozí chování můžete změnit dvěma dalšími způsoby:  
  
1. Ve spravovaném kódu pro vlákno.  
  
     Tok můžete potlačit na základě vlákno úpravou <xref:System.Threading.ExecutionContext> <xref:System.Security.SecurityContext> nastavení a <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>pomocí <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> nebo metoda.  
  
2. Při volání nespravovaného hostitelského rozhraní načíst modul CLR (COMMON Language runtime).  
  
     Pokud nespravované hostitelské rozhraní (namísto jednoduchého spravovaného spustitelného souboru) se používá k načtení CLR, můžete zadat speciální příznak ve volání [funkce CorBindToRuntimeEx.](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) Chcete-li povolit režim kompatibility `flags` pro celý proces, nastavte parametr `STARTUP_ALWAYSFLOW_IMPERSONATION` [funkce CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) na .  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 V aplikaci rozhraní .NET Framework lze tento prvek použít pouze v konfiguračním souboru aplikace.  
  
 Pro ASP.NET aplikaci lze tok zosobnění nakonfigurovat v souboru aspnet.config, který se nachází v \<adresáři Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx.  
  
 ASP.NET ve výchozím nastavení zakáže tok zosobnění v souboru aspnet.config pomocí následujících nastavení konfigurace:  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 V ASP.NET, pokud chcete povolit tok zosobnění místo, musíte explicitně použít následující nastavení konfigurace:  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit, že identita systému Windows toky přes asynchronní body, i v případě, že zosobnění je dosaženo prostřednictvím prostředků než spravované metody.  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [\<starší verze ImpersonationPolicy> Element](legacyimpersonationpolicy-element.md)
