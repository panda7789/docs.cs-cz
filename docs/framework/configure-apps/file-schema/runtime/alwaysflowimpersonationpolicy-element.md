---
title: '&lt;alwaysFlowImpersonationPolicy&gt; Element'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/alwaysFlowImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#alwaysFlowImpersonationPolicy
helpviewer_keywords:
- alwaysFlowImpersonationPolicy element
- <alwaysFlowImpersonationPolicy> element
ms.assetid: ee622801-9e46-470b-85ab-88c4b1dd2ee1
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e32274c6371a73b882f5494c7093945a84d67adf
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2018
---
# <a name="ltalwaysflowimpersonationpolicygt-element"></a>&lt;alwaysFlowImpersonationPolicy&gt; Element
Určuje, že Windows identity vždy přeteče asynchronní bodů, bez ohledu na to, jak byla provedena zosobnění.  
  
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
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda identitu Windows toků mezi asynchronní body.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Identita není toku přes asynchronní body, pokud zosobnění se provádí prostřednictvím systému Windows, jako spravované metody <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>. Toto nastavení je výchozí.|  
|`true`|Identitu systému Windows vždycky přeteče asynchronní bodů, bez ohledu na to, jak byla provedena zosobnění.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 V rozhraní .NET Framework verze 1.0 a 1.1 identitu systému Windows není procházet přes asynchronní body. V rozhraní .NET Framework verze 2.0, je <xref:System.Threading.ExecutionContext> objekt, který obsahuje informace o aktuálně spuštěném vlákno a toků mezi asynchronní body v rámci domény aplikace. <xref:System.Security.Principal.WindowsIdentity> Také toků v rámci přenášeného přes asynchronní body zadaný zosobnění bylo dosaženo pomocí informací, jako spravované metody <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> a ne prostřednictvím jiným způsobem, jako je například platforma vyvolání pro nativní metody. Tento element slouží k určení, že mezi asynchronní bodů, bez ohledu na to, jak se dá dosáhnout zosobnění toku identitu systému Windows.  
  
 Chcete-li změnit toto výchozí chování v dva způsoby, jak:  
  
1.  Ve spravovaném kódu na základě vlákna.  
  
     Můžete potlačit toku na základě vlákna změnou <xref:System.Threading.ExecutionContext> a <xref:System.Security.SecurityContext> nastavení pomocí <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, nebo <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> metoda.  
  
2.  Ve volání rozhraní nespravované hostingu načíst modul CLR (CLR).  
  
     Pokud nespravované rozhraní hostování (namísto jednoduché spustitelný soubor spravovaných) se používá k načtení modulu CLR, můžete zadat speciální příznak ve volání [CorBindToRuntimeEx – funkce](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funkce. Chcete-li povolit režim kompatibility pro celý proces, nastavte `flags` parametr pro [CorBindToRuntimeEx – funkce](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) k `STARTUP_ALWAYSFLOW_IMPERSONATION`.  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 V aplikaci rozhraní .NET Framework Tento element lze použít pouze v konfiguračním souboru aplikace.  
  
 Pro aplikaci ASP.NET toku zosobnění lze konfigurovat v nalezen v souboru aspnet.config \<složka systému Windows > \Microsoft.NET\Framework\vx.x.xxxx adresáře.  
  
 Technologie ASP.NET ve výchozím nastavení zakáže zosobnění tok v souboru aspnet.config pomocí následujících nastavení:  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 V technologii ASP.NET Pokud chcete povolit tok zosobnění místo toho je nutné explicitně zadat následující nastavení:  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit, že identitu Windows toků přes asynchronní body i v případě, že zosobnění je dosaženo pomocí znamená než spravované metody.  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<legacyImpersonationPolicy> Element](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)
