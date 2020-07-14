---
title: Kompatibilita a migrace zásad zabezpečení přístupu kódu
description: Přečtěte si Shrnutí a podívejte se na odkazy týkající se kompatibility a migrace zásad zabezpečení přístupu kódu v rozhraní .NET 4.
ms.date: 03/30/2017
helpviewer_keywords:
- policy migration, compatibility
- CLR policy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
ms.openlocfilehash: e5affd9d16635fa28342b5b7390a083185975f2b
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281729"
---
# <a name="code-access-security-policy-compatibility-and-migration"></a><span data-ttu-id="a55fa-103">Kompatibilita a migrace zásad zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="a55fa-103">Code Access Security Policy Compatibility and Migration</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="a55fa-104">Část zásad zabezpečení přístupu kódu (CAS) byla v .NET Framework 4 zastaralá.</span><span class="sxs-lookup"><span data-stu-id="a55fa-104">The policy portion of code access security (CAS) has been made obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="a55fa-105">V důsledku toho může dojít k upozorněním na kompilaci a výjimkám modulu runtime, pokud voláte zastaralé typy zásad a členy [explicitně](#explicit_use) nebo [implicitně](#implicit_use) (prostřednictvím jiných typů a členů).</span><span class="sxs-lookup"><span data-stu-id="a55fa-105">As a result, you may encounter compilation warnings and runtime exceptions if you call the obsolete policy types and members [explicitly](#explicit_use) or [implicitly](#implicit_use) (through other types and members).</span></span>

<span data-ttu-id="a55fa-106">Upozornění a chyby můžete zabránit pomocí těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="a55fa-106">You can avoid the warnings and errors by either:</span></span>

- <span data-ttu-id="a55fa-107">[Migrace](#migration) na .NET Framework 4 nahrazení pro zastaralá volání.</span><span class="sxs-lookup"><span data-stu-id="a55fa-107">[Migrating](#migration) to the .NET Framework 4 replacements for the obsolete calls.</span></span>

   <span data-ttu-id="a55fa-108">\-ani</span><span class="sxs-lookup"><span data-stu-id="a55fa-108">\- or -</span></span>

- <span data-ttu-id="a55fa-109">Pomocí [ \<NetFx40_LegacySecurityPolicy> elementu konfigurace](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) se můžete vyjádřit ke staršímu chování zásad CAS.</span><span class="sxs-lookup"><span data-stu-id="a55fa-109">Using the [\<NetFx40_LegacySecurityPolicy> configuration element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) to opt into the legacy CAS policy behavior.</span></span>

<span data-ttu-id="a55fa-110">Toto téma obsahuje následující oddíly:</span><span class="sxs-lookup"><span data-stu-id="a55fa-110">This topic contains the following sections:</span></span>

- [<span data-ttu-id="a55fa-111">Explicitní použití</span><span class="sxs-lookup"><span data-stu-id="a55fa-111">Explicit Use</span></span>](#explicit_use)

- [<span data-ttu-id="a55fa-112">Implicitní použití</span><span class="sxs-lookup"><span data-stu-id="a55fa-112">Implicit Use</span></span>](#implicit_use)

- [<span data-ttu-id="a55fa-113">Chyby a upozornění</span><span class="sxs-lookup"><span data-stu-id="a55fa-113">Errors and Warnings</span></span>](#errors_and_warnings)

- [<span data-ttu-id="a55fa-114">Migrace: náhrada pro zastaralá volání</span><span class="sxs-lookup"><span data-stu-id="a55fa-114">Migration: Replacement for Obsolete Calls</span></span>](#migration)

- [<span data-ttu-id="a55fa-115">Kompatibilita: použití možnosti starší verze zásad CAS</span><span class="sxs-lookup"><span data-stu-id="a55fa-115">Compatibility: Using the CAS Policy Legacy Option</span></span>](#compatibility)

<a name="explicit_use"></a>

## <a name="explicit-use"></a><span data-ttu-id="a55fa-116">Explicitní použití</span><span class="sxs-lookup"><span data-stu-id="a55fa-116">Explicit Use</span></span>

<span data-ttu-id="a55fa-117">Členové, kteří přímo pracují se zásadami zabezpečení nebo vyžadují zásady CAS pro izolovaný prostor (sandbox), jsou zastaralé a ve výchozím nastavení vytvoří chyby.</span><span class="sxs-lookup"><span data-stu-id="a55fa-117">Members that directly manipulate security policy or require CAS policy to sandbox are obsolete and will produce errors by default.</span></span>

<span data-ttu-id="a55fa-118">Příklady těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="a55fa-118">Examples of these are:</span></span>

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

## <a name="implicit-use"></a><span data-ttu-id="a55fa-119">Implicitní použití</span><span class="sxs-lookup"><span data-stu-id="a55fa-119">Implicit Use</span></span>

<span data-ttu-id="a55fa-120">Několik přetížení načítání sestavení vytváří chyby kvůli implicitnímu použití zásad CAS.</span><span class="sxs-lookup"><span data-stu-id="a55fa-120">Several assembly loading overloads produce errors because of their implicit use of CAS policy.</span></span> <span data-ttu-id="a55fa-121">Tato přetížení přebírají <xref:System.Security.Policy.Evidence> parametr, který se používá k vyřešení zásad CAS a poskytnutí oprávnění pro udělení oprávnění pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="a55fa-121">These overloads take an <xref:System.Security.Policy.Evidence> parameter that is used to resolve CAS policy and provide a permission grant set for an assembly.</span></span>

<span data-ttu-id="a55fa-122">Tady je několik příkladů.</span><span class="sxs-lookup"><span data-stu-id="a55fa-122">Here are some examples.</span></span> <span data-ttu-id="a55fa-123">Zastaralá přetížení jsou ta, která přijímá <xref:System.Security.Policy.Evidence> jako parametr:</span><span class="sxs-lookup"><span data-stu-id="a55fa-123">The obsolete overloads are those that take <xref:System.Security.Policy.Evidence> as a parameter:</span></span>

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

## <a name="errors-and-warnings"></a><span data-ttu-id="a55fa-124">Chyby a upozornění</span><span class="sxs-lookup"><span data-stu-id="a55fa-124">Errors and Warnings</span></span>

<span data-ttu-id="a55fa-125">Zastaralé typy a členy vytváří při použití následující chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="a55fa-125">The obsolete types and members produce the following error messages when they are used.</span></span> <span data-ttu-id="a55fa-126">Všimněte si, že <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> samotný typ není zastaralý.</span><span class="sxs-lookup"><span data-stu-id="a55fa-126">Note that the <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> type itself is not obsolete.</span></span>

<span data-ttu-id="a55fa-127">Upozornění při kompilaci:</span><span class="sxs-lookup"><span data-stu-id="a55fa-127">Compile-time warning:</span></span>

`warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`

<span data-ttu-id="a55fa-128">Běhová výjimka:</span><span class="sxs-lookup"><span data-stu-id="a55fa-128">Run-time exception:</span></span>

<span data-ttu-id="a55fa-129"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span><span class="sxs-lookup"><span data-stu-id="a55fa-129"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span></span>

<a name="migration"></a>

## <a name="migration-replacement-for-obsolete-calls"></a><span data-ttu-id="a55fa-130">Migrace: náhrada pro zastaralá volání</span><span class="sxs-lookup"><span data-stu-id="a55fa-130">Migration: Replacement for Obsolete Calls</span></span>

### <a name="determining-an-assemblys-trust-level"></a><span data-ttu-id="a55fa-131">Určení úrovně důvěryhodnosti sestavení</span><span class="sxs-lookup"><span data-stu-id="a55fa-131">Determining an Assembly’s Trust Level</span></span>

<span data-ttu-id="a55fa-132">Zásada CAS se často používá k určení sady oprávnění pro udělení oprávnění nebo domény aplikace nebo úrovně důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="a55fa-132">CAS policy is often used to determine an assembly’s or application domain’s permission grant set or trust level.</span></span> <span data-ttu-id="a55fa-133">.NET Framework 4 zpřístupňuje následující užitečné vlastnosti, které nepotřebují vyřešit zásady zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="a55fa-133">The .NET Framework 4 exposes the following useful properties that do not need to resolve security policy:</span></span>

- <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>

### <a name="application-domain-sandboxing"></a><span data-ttu-id="a55fa-134">Sandboxing domény aplikace</span><span class="sxs-lookup"><span data-stu-id="a55fa-134">Application Domain Sandboxing</span></span>

<span data-ttu-id="a55fa-135"><xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType>Metoda se obvykle používá pro sandboxing sestavení v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="a55fa-135">The <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> method is typically used for sandboxing the assemblies in an application domain.</span></span> <span data-ttu-id="a55fa-136">.NET Framework 4 zpřístupňuje členy, které pro tento účel nemusíte používat <xref:System.Security.Policy.PolicyLevel> .</span><span class="sxs-lookup"><span data-stu-id="a55fa-136">The .NET Framework 4 exposes members that do not have to use <xref:System.Security.Policy.PolicyLevel> for this purpose.</span></span> <span data-ttu-id="a55fa-137">Další informace naleznete v tématu [How to: Run částečně důvěryhodný kód v izolovaném prostoru (sandboxu)](how-to-run-partially-trusted-code-in-a-sandbox.md).</span><span class="sxs-lookup"><span data-stu-id="a55fa-137">For more information, see [How to: Run Partially Trusted Code in a Sandbox](how-to-run-partially-trusted-code-in-a-sandbox.md).</span></span>

### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a><span data-ttu-id="a55fa-138">Určení bezpečné nebo přiměřené sady oprávnění pro částečně důvěryhodný kód</span><span class="sxs-lookup"><span data-stu-id="a55fa-138">Determining a Safe or Reasonable Permission Set for Partially Trusted Code</span></span>

<span data-ttu-id="a55fa-139">Hostitelé často potřebují určit oprávnění, která jsou vhodná pro hostovaný kód izolovaného prostoru (sandbox).</span><span class="sxs-lookup"><span data-stu-id="a55fa-139">Hosts often need to determine the permissions that are appropriate for sandboxing hosted code.</span></span> <span data-ttu-id="a55fa-140">Předtím, než .NET Framework 4, poskytuje zásada CAS způsob, jak to provést s <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> metodou.</span><span class="sxs-lookup"><span data-stu-id="a55fa-140">Before the .NET Framework 4, CAS policy provided a way to do this with the <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a55fa-141">V rámci nahrazení .NET Framework 4 poskytuje <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> metodu, která vrací bezpečnou standardní sadu oprávnění pro poskytnuté legitimace.</span><span class="sxs-lookup"><span data-stu-id="a55fa-141">As a replacement, .NET Framework 4 provides the <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> method, which returns a safe, standard permission set for the provided evidence.</span></span>

### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a><span data-ttu-id="a55fa-142">Scénáře, které nepatří do izolovaného prostoru: přetížení pro načtení sestavení</span><span class="sxs-lookup"><span data-stu-id="a55fa-142">Non-Sandboxing Scenarios: Overloads for Assembly Loads</span></span>

<span data-ttu-id="a55fa-143">Důvodem použití přetížení zatížení sestavení může být použití parametrů, které nejsou jinak k dispozici, namísto sestavování sestavení v izolovaném prostoru.</span><span class="sxs-lookup"><span data-stu-id="a55fa-143">The reason for using an assembly load overload might be to use parameters that are not otherwise available, instead of sandboxing the assembly.</span></span> <span data-ttu-id="a55fa-144">Počínaje .NET Framework 4 se přetížení zátěže sestavení, která nevyžadují <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> objekt jako parametr, například <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType> , povoluje tento scénář.</span><span class="sxs-lookup"><span data-stu-id="a55fa-144">Starting with the .NET Framework 4, assembly load overloads that do not require a <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> object as a parameter, for example, <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, enable this scenario.</span></span>

<span data-ttu-id="a55fa-145">Pokud chcete sestavení izolovaného prostoru (sandbox), použijte <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> přetížení.</span><span class="sxs-lookup"><span data-stu-id="a55fa-145">If you want to sandbox an assembly, use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> overload.</span></span>

<a name="compatibility"></a>

## <a name="compatibility-using-the-cas-policy-legacy-option"></a><span data-ttu-id="a55fa-146">Kompatibilita: použití možnosti starší verze zásad CAS</span><span class="sxs-lookup"><span data-stu-id="a55fa-146">Compatibility: Using the CAS Policy Legacy Option</span></span>

<span data-ttu-id="a55fa-147">[ \<NetFx40_LegacySecurityPolicy> Prvek konfigurace](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) umožňuje určit, že proces nebo knihovna používá starší zásady CAS.</span><span class="sxs-lookup"><span data-stu-id="a55fa-147">The [\<NetFx40_LegacySecurityPolicy> configuration element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) lets you specify that a process or library uses legacy CAS policy.</span></span> <span data-ttu-id="a55fa-148">Pokud povolíte tento prvek, přetížení zásad a legitimace budou fungovat stejně jako v předchozích verzích rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a55fa-148">When you enable this element, the policy and evidence overloads will work as they did in previous versions of the framework.</span></span>

> [!NOTE]
> <span data-ttu-id="a55fa-149">Chování zásad CAS je určeno pro verzi modulu runtime, takže změna zásad CAS pro jednu verzi modulu runtime nemá vliv na zásady CAS jiné verze.</span><span class="sxs-lookup"><span data-stu-id="a55fa-149">CAS policy behavior is specified on a runtime version basis, so modifying CAS policy for one runtime version does not affect the CAS policy of another version.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="a55fa-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="a55fa-150">See also</span></span>

- [<span data-ttu-id="a55fa-151">Postupy: Spuštění částečně důvěryhodného kódu v izolovaném prostoru</span><span class="sxs-lookup"><span data-stu-id="a55fa-151">How to: Run Partially Trusted Code in a Sandbox</span></span>](how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="a55fa-152">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="a55fa-152">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
