---
title: "Kompatibilita a migrace zásad zabezpečení přístupu kódu"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- policy migration, compatibility
- CLR poliicy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 11c64d3ece454e95adfc41c7d89913e9ce7363dc
ms.sourcegitcommit: 9bee08539b1886c9d57fa3d5bd8a58dfdd7cad94
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2017
---
# <a name="code-access-security-policy-compatibility-and-migration"></a>Kompatibilita a migrace zásad zabezpečení přístupu kódu
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Část zásad zabezpečení přístupu kódu (CAS) byly provedeny v zastaralé [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. V důsledku toho může dojít upozornění kompilace a výjimky za běhu při volání zastaralé typy a členy [explicitně](#explicit_use) nebo [implicitně](#implicit_use) (prostřednictvím jiných typů a členů).  
  
 Buď se můžete vyhnout chyby a varování:  
  
-   [Migrace](#migration) k [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] náhrady za zastaralé volání.  
  
     \-nebo –  
  
-   Pomocí [< NetFx40_LegacySecurityPolicy – > Konfigurace element](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) se vyjádřit výslovný do starší verze chování zásad CAS.  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Explicitní použití](#explicit_use)  
  
-   [Implicitní použití](#implicit_use)  
  
-   [Chyby a upozornění](#errors_and_warnings)  
  
-   [Migrace: Nahrazení pro zastaralé volání](#migration)  
  
-   [Kompatibilita: Pomocí možnosti starší zásadu CAS](#compatibility)  
  
<a name="explicit_use"></a>   
## <a name="explicit-use"></a>Explicitní použití  
 Členové, které přímo upravit zásady zabezpečení nebo vyžadují zásadu CAS do izolovaného prostoru jsou zastaralé a vygeneruje chyby ve výchozím nastavení.  
  
 Tyto příklady:  
  
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
 Několik přetížení načítání sestavení produkuje chyby kvůli implicitně používají certifikační Autority zásad. Tato přetížení používají <xref:System.Security.Policy.Evidence> parametr, který se používá k vyřešení zásad CAS a poskytnout oprávnění udělit sada pro sestavení.  
  
 Zde jsou některé příklady. Zastaralá přetížení jsou ty, které provést <xref:System.Security.Policy.Evidence> jako parametr:  
  
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
 Zastaralé typy a členy vytvořit následující chybové zprávy, když se používají. Všimněte si, že <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> vlastní typ není zastaralá.  
  
 Kompilace upozornění:  
  
 `warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`  
  
 Výjimka:  
  
 <xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`  
  
<a name="migration"></a>   
## <a name="migration-replacement-for-obsolete-calls"></a>Migrace: Nahrazení pro zastaralé volání  
  
### <a name="determining-an-assemblys-trust-level"></a>Určení úrovně důvěryhodnosti sestavení  
 Zásady CAS se často používá k určení sestavení nebo doménu aplikace oprávnění udělit sady nebo úroveň důvěryhodnosti. [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Zpřístupňuje následující užitečné vlastnosti, které není potřeba řešit zásady zabezpečení:  
  
-   <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>  
  
### <a name="application-domain-sandboxing"></a>Sandboxing domény aplikace  
 <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> Metoda se obvykle používá pro sandboxing sestavení v doméně aplikace. [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Zveřejňuje členy, které nemají používat <xref:System.Security.Policy.PolicyLevel> pro tento účel. Další informace najdete v tématu [postupy: spuštění částečně důvěryhodného kódu v izolovaném prostoru](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a>Určení sady bezpečné nebo přiměřené oprávnění pro částečně důvěryhodný kód  
 Hostitelé často potřebují, určují oprávnění, které jsou vhodné pro hostovaný kód sandboxing. Před [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], certifikační Autority zásady poskytují způsob, jak to provést pomocí <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> metoda. Jako náhrada [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] poskytuje <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> metodu, která vrací bezpečnou standardní oprávnění nastavit pro zadaný důkaz.  
  
### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a>Non-Sandboxing scénáře: Přetížení pro načtení sestavení  
 Pokud chcete používat parametry, které jinak nejsou k dispozici místo sandboxing sestavení může být z důvodu pro používání přetížení načtení sestavení. Od verze [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], přetížení načtení sestavení, které nevyžadují <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> objekt jako parametr, například <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, povolit tento scénář.  
  
 Pokud chcete izolovat sestavení, použijte <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> přetížení.  
  
<a name="compatibility"></a>   
## <a name="compatibility-using-the-cas-policy-legacy-option"></a>Kompatibilita: Pomocí možnosti starší zásadu CAS  
 [< NetFx40_LegacySecurityPolicy – > Konfigurace element](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) umožňuje určit, který proces nebo knihovna používá starší zásadu CAS. Když povolíte tento element, zásady a důkaz přetížení bude fungovat stejně jako v předchozích verzích rozhraní.  
  
> [!NOTE]
>  Chování zásad CAS je zadán na základě verze modulu runtime, takže úprava zásad CAS pro jednu verzi modulu runtime neovlivní zásady CAS jinou verzi.  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Postupy: spuštění částečně důvěryhodného kódu v izolovaném prostoru](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)  
 [Pokyny pro zabezpečené kódování](../../standard/security/secure-coding-guidelines.md)
