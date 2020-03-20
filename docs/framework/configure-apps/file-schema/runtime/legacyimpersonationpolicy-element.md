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
ms.openlocfilehash: 5e43ead278ecd4049014f4000a2f056b2190f7e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154101"
---
# <a name="legacyimpersonationpolicy-element"></a>\<starší verze ImpersonationPolicy> Element
Určuje, že identita systému Windows neprobíhá přes asynchronní body, bez ohledu na nastavení toku pro kontext spuštění v aktuálním vlákně.  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<starší>verze**  
  
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
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, že <xref:System.Security.Principal.WindowsIdentity> netokuje přes asynchronní body, <xref:System.Threading.ExecutionContext> bez ohledu na nastavení toku v aktuálním vlákně.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|<xref:System.Security.Principal.WindowsIdentity>toky přes asynchronní body <xref:System.Threading.ExecutionContext> v závislosti na nastavení toku pro aktuální vlákno. Toto nastavení je výchozí.|  
|`true`|<xref:System.Security.Principal.WindowsIdentity>netokuje přes asynchronní body, <xref:System.Threading.ExecutionContext> bez ohledu na nastavení toku v aktuálním vlákně.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 V rozhraní .NET Framework verze 1.0 a <xref:System.Security.Principal.WindowsIdentity> 1.1 netokuje přes všechny uživatelem definované asynchronní body. Počínaje rozhraním .NET Framework verze 2.0 existuje <xref:System.Threading.ExecutionContext> objekt, který obsahuje informace o aktuálně spuštěném vlákně a toky přes asynchronní body v rámci domény aplikace. Je <xref:System.Security.Principal.WindowsIdentity> součástí tohoto kontextu spuštění a proto také toky přes asynchronní body, což znamená, že pokud existuje kontext zosobnění, bude tok také.  
  
 Počínaje rozhraním .NET Framework 2.0 `<legacyImpersonationPolicy>` můžete pomocí <xref:System.Security.Principal.WindowsIdentity> prvku určit, že neprobíhá přes asynchronní body.  
  
> [!NOTE]
> Clr (COMMON Language runtime) si je vědoma operací zosobnění prováděných pouze pomocí spravovaného kódu, nikoli zosobnění prováděného mimo spravovaný kód, například prostřednictvím vyvolání platformy k nespravovanému kódu nebo prostřednictvím přímých volání funkcí Win32. Pouze <xref:System.Security.Principal.WindowsIdentity> spravované objekty mohou proudit přes `alwaysFlowImpersonationPolicy` asynchronní body,`<alwaysFlowImpersonationPolicy enabled="true"/>`pokud prvek nebyl nastaven na hodnotu true ( ). Nastavení `alwaysFlowImpersonationPolicy` prvku na hodnotu true určuje, že identita systému Windows vždy proudí přes asynchronní body, bez ohledu na to, jak bylo zosobnění provedeno. Další informace o plynulém nespravovaném zosobnění mezi asynchronními body naleznete v tématu [ \<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).  
  
 Toto výchozí chování můžete změnit dvěma dalšími způsoby:  
  
1. Ve spravovaném kódu pro vlákno.  
  
     Tok můžete potlačit na základě vlákno úpravou <xref:System.Threading.ExecutionContext> <xref:System.Security.SecurityContext> a nastavení <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>pomocí <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> , nebo metoda.  
  
2. Při volání nespravovaného hostitelského rozhraní načíst modul CLR (COMMON Language runtime).  
  
     Pokud nespravované hostitelské rozhraní (namísto jednoduchého spravovaného spustitelného souboru) se používá k načtení CLR, můžete zadat speciální příznak ve volání [funkce CorBindToRuntimeEx.](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) Chcete-li povolit režim kompatibility `flags` pro celý proces, nastavte parametr [funkce CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) na STARTUP_LEGACY_IMPERSONATION.  
  
 Další informace naleznete [ \<v tématu alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 V aplikaci rozhraní .NET Framework lze tento prvek použít pouze v konfiguračním souboru aplikace.  
  
 Pro ASP.NET aplikaci lze tok zosobnění nakonfigurovat v souboru aspnet.config, který se nachází v \<adresáři Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx.  
  
 ASP.NET ve výchozím nastavení zakáže tok zosobnění v souboru aspnet.config pomocí následujících nastavení konfigurace:  
  
``` xml
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
 Následující příklad ukazuje, jak určit starší chování, které netokuje identitu systému Windows přes asynchronní body.  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md)
