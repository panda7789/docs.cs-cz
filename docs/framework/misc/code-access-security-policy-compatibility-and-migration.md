---
title: Kompatibilita a migrace zásad zabezpečení přístupu kódu
ms.date: 03/30/2017
helpviewer_keywords:
- policy migration, compatibility
- CLR policy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9563dae9ba5d144300549e7f33f5f5a9feb1d410
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205622"
---
# <a name="code-access-security-policy-compatibility-and-migration"></a>Kompatibilita a migrace zásad zabezpečení přístupu kódu

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Část zásad zabezpečení přístupu kódu (CAS) byla v .NET Framework 4 zastaralá. V důsledku toho může dojít k upozorněním na kompilaci a výjimkám modulu runtime, pokud voláte zastaralé typy zásad a členy [explicitně](#explicit_use) nebo [implicitně](#implicit_use) (prostřednictvím jiných typů a členů).

Upozornění a chyby můžete zabránit pomocí těchto akcí:

- [Migrace](#migration) na .NET Framework 4 nahrazení pro zastaralá volání.

   \- nebo –

- Pomocí elementu NetFx40_LegacySecurityPolicy > [Configuration se můžete vyjádřit ke staršímu chování zásad CAS. \<](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)

Toto téma obsahuje následující oddíly:

- [Explicitní použití](#explicit_use)

- [Implicitní použití](#implicit_use)

- [Chyby a upozornění](#errors_and_warnings)

- [Migrace Náhrada pro zastaralá volání](#migration)

- [Režim Použití možnosti starší verze zásad CAS](#compatibility)

<a name="explicit_use"></a>

## <a name="explicit-use"></a>Explicitní použití

Členové, kteří přímo pracují se zásadami zabezpečení nebo vyžadují zásady CAS pro izolovaný prostor (sandbox), jsou zastaralé a ve výchozím nastavení vytvoří chyby.

Příklady těchto akcí:

- <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.HostSecurityManager.DomainPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.Policy.PolicyLevel.CreateAppDomainLevel%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.LoadPolicyLevelFromString%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.LoadPolicyLevelFromFile%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolveSystemPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolvePolicyGroups%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.PolicyHierarchy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.SavePolicy%2A?displayProperty=nameWithType>

<a name="implicit_use"></a>

## <a name="implicit-use"></a>Implicitní použití

Několik přetížení načítání sestavení vytváří chyby kvůli implicitnímu použití zásad CAS. Tato přetížení přebírají <xref:System.Security.Policy.Evidence> parametr, který se používá k vyřešení zásad CAS a poskytnutí oprávnění pro udělení oprávnění pro sestavení.

Zde je několik příkladů: Zastaralá přetížení jsou ta, která přijímá <xref:System.Security.Policy.Evidence> jako parametr:

- <xref:System.Activator.CreateInstanceFrom%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.ExecuteAssemblyByName%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

<a name="errors_and_warnings"></a>

## <a name="errors-and-warnings"></a>Chyby a upozornění

Zastaralé typy a členy vytváří při použití následující chybové zprávy. Všimněte si, <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> že samotný typ není zastaralý.

Upozornění při kompilaci:

`warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`

Běhová výjimka:

<xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`

<a name="migration"></a>

## <a name="migration-replacement-for-obsolete-calls"></a>Migrace Náhrada pro zastaralá volání

### <a name="determining-an-assemblys-trust-level"></a>Určení úrovně důvěryhodnosti sestavení

Zásada CAS se často používá k určení sady oprávnění pro udělení oprávnění nebo domény aplikace nebo úrovně důvěryhodnosti. .NET Framework 4 zpřístupňuje následující užitečné vlastnosti, které nepotřebují vyřešit zásady zabezpečení:

- <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>

### <a name="application-domain-sandboxing"></a>Sandboxing domény aplikace

<xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> Metoda se obvykle používá pro sandboxing sestavení v doméně aplikace. .NET Framework 4 zpřístupňuje členy, které pro tento účel nemusíte používat <xref:System.Security.Policy.PolicyLevel> . Další informace najdete v tématu [jak: Spustit částečně důvěryhodný kód v izolovaném](how-to-run-partially-trusted-code-in-a-sandbox.md)prostoru (sandboxu).

### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a>Určení bezpečné nebo přiměřené sady oprávnění pro částečně důvěryhodný kód

Hostitelé často potřebují určit oprávnění, která jsou vhodná pro hostovaný kód izolovaného prostoru (sandbox). Předtím, než .NET Framework 4, poskytuje zásada CAS způsob, jak to provést s <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> metodou. V rámci nahrazení .NET Framework 4 poskytuje <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> metodu, která vrací bezpečnou standardní sadu oprávnění pro poskytnuté legitimace.

### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a>Scénáře, které nepatří do izolovaného prostoru: Přetížení pro načtení sestavení

Důvodem použití přetížení zatížení sestavení může být použití parametrů, které nejsou jinak k dispozici, namísto sestavování sestavení v izolovaném prostoru. Počínaje .NET Framework 4 se přetížení zátěže sestavení, která nevyžadují <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> objekt jako parametr, <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>například, povoluje tento scénář.

Pokud chcete sestavení izolovaného prostoru (sandbox), <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> použijte přetížení.

<a name="compatibility"></a>

## <a name="compatibility-using-the-cas-policy-legacy-option"></a>Režim Použití možnosti starší verze zásad CAS

[Prvek konfigurace > NetFx40_LegacySecurityPolicyumožňujeurčit,žeprocesneboknihovnapoužívástaršízásadyCAS.\<](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) Pokud povolíte tento prvek, přetížení zásad a legitimace budou fungovat stejně jako v předchozích verzích rozhraní.

> [!NOTE]
> Chování zásad CAS je určeno pro verzi modulu runtime, takže změna zásad CAS pro jednu verzi modulu runtime nemá vliv na zásady CAS jiné verze.

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Viz také:

- [Postupy: Spustit částečně důvěryhodný kód v izolovaném prostoru](how-to-run-partially-trusted-code-in-a-sandbox.md)
- [Pokyny pro zabezpečené kódování](../../standard/security/secure-coding-guidelines.md)
