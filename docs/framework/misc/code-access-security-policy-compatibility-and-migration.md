---
title: Kompatibilita a migrace zásad zabezpečení přístupu kódu
ms.date: 03/30/2017
helpviewer_keywords:
- policy migration, compatibility
- CLR poliicy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 219b511662a2e59fb6e0e55b6630bd54015fcc79
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620094"
---
# <a name="code-access-security-policy-compatibility-and-migration"></a>Kompatibilita a migrace zásad zabezpečení přístupu kódu
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Část zásad zabezpečení přístupu kódu (CAS) byly provedeny v zastaralé [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. V důsledku toho může dojít upozornění kompilace a výjimky běhového modulu při volání zásad zastaralé typy a členy [explicitně](#explicit_use) nebo [implicitně](#implicit_use) (pomocí jiných typů a členů).  
  
 Můžete se vyhnout upozornění a chyby buď:  
  
-   [Migrace](#migration) k [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] nahrazení pro zastaralý volání.  
  
     \- nebo –  
  
-   Použití [element < NetFx40_LegacySecurityPolicy > Konfigurace](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) do starší chování zásad CAS.  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Explicitní použití](#explicit_use)  
  
-   [Implicitní použití](#implicit_use)  
  
-   [Chyby a upozornění](#errors_and_warnings)  
  
-   [Migrace: Nahrazení pro zastaralý volání](#migration)  
  
-   [Kompatibility: Pomocí možnosti zásad CAS starší verze](#compatibility)  
  
<a name="explicit_use"></a>   
## <a name="explicit-use"></a>Explicitní použití  
 Členy, které přímo pracovat s zásady zabezpečení nebo vyžadují zásady CAS do izolovaného prostoru jsou zastaralé a vygeneruje chyby ve výchozím nastavení.  
  
 Mezi ty patří:  
  
-   <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.HostSecurityManager.DomainPolicy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.Policy.PolicyLevel.CreateAppDomainLevel%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.LoadPolicyLevelFromString%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.LoadPolicyLevelFromFile%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.ResolveSystemPolicy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.ResolvePolicyGroups%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.PolicyHierarchy%2A?displayProperty=nameWithType>  
  
-   <xref:System.Security.SecurityManager.SavePolicy%2A?displayProperty=nameWithType>  
  
<a name="implicit_use"></a>   
## <a name="implicit-use"></a>Implicitní použití  
 Několik přetížení načítání sestavení vytvořit chyby z důvodu jejich implicitního použití zásad CAS. Tato přetížení používají <xref:System.Security.Policy.Evidence> parametr, který se používá k řešení certifikační Autority zásad a poskytnout oprávnění udělit sady pro sestavení.  
  
 Zde je několik příkladů: Zastaralá přetížení jsou ty, které trvat <xref:System.Security.Policy.Evidence> jako parametr:  
  
-   <xref:System.Activator.CreateInstanceFrom%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.ExecuteAssemblyByName%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
<a name="errors_and_warnings"></a>   
## <a name="errors-and-warnings"></a>Chyby a upozornění  
 Zastaralé typy a členy vytvořit následující chybové zprávy při jejich použití. Všimněte si, že <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> samotného typu není zastaralá.  
  
 Upozornění kompilace:  
  
 `warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`  
  
 Výjimka za běhu:  
  
 <xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`  
  
<a name="migration"></a>   
## <a name="migration-replacement-for-obsolete-calls"></a>Migrace: Nahrazení pro zastaralý volání  
  
### <a name="determining-an-assemblys-trust-level"></a>Určení úroveň důvěryhodnosti sestavení  
 Zásady CAS z se často používá k určení sestavení nebo doména aplikace oprávnění sada udělení oprávnění nebo úroveň důvěryhodnosti. [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Zveřejňuje následující užitečné vlastnosti, které není potřeba řešit zásady zabezpečení:  
  
-   <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>  
  
### <a name="application-domain-sandboxing"></a>Sandboxing domény aplikace  
 <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> Metoda se obvykle používá pro sandboxing sestavení v doméně aplikace. [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Zpřístupňuje členy, které není nutné používat <xref:System.Security.Policy.PolicyLevel> pro tento účel. Další informace najdete v tématu [jak: Spuštění částečně důvěryhodného kódu v izolovaném prostoru](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a>Určení sady bezpečné nebo přiměřené oprávnění pro částečně důvěryhodný kód.  
 Hostitelé často nutné určit oprávnění, které jsou vhodné pro kód izolace (sandbox), které jsou hostované. Před [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], poskytuje způsob, jak to provést pomocí zásad CAS <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> metoda. Jako náhradu [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] poskytuje <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> metodu, která vrací sadu pro zadaný důkazy bezpečný, standardní oprávnění.  
  
### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a>Non-Sandboxing scénáře: Přetížení pro načtení sestavení  
 Použití parametrů, které jinak nejsou k dispozici, namísto sandboxing sestavení může být důvod pomocí přetížení načtení sestavení. Počínaje [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], přetížení načtení sestavení, které nevyžadují, aby <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> objektu jako parametr, například <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, povolit tento scénář.  
  
 Pokud chcete do izolovaného prostoru sestavení, použijte <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> přetížení.  
  
<a name="compatibility"></a>   
## <a name="compatibility-using-the-cas-policy-legacy-option"></a>Kompatibility: Pomocí možnosti zásad CAS starší verze  
 [Element < NetFx40_LegacySecurityPolicy > Konfigurace](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) umožňuje určit, který proces nebo knihovna používá starší zásadu CAS. Po povolení tohoto prvku přetížení zásady a důkazy bude fungovat stejně jako v předchozích verzích rozhraní.  
  
> [!NOTE]
>  Na základě verze modulu runtime, je specifikováno chování zásady CAS, tak úprava zásad CAS pro jednu verzi modulu runtime neovlivní zásady CAS z jiné verze.  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Spuštění částečně důvěryhodného kódu v izolovaném prostoru](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [Pokyny pro zabezpečené kódování](../../standard/security/secure-coding-guidelines.md)
