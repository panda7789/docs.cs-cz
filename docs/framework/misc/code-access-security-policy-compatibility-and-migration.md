---
title: Kompatibilita a migrace zásad zabezpečení přístupu kódu
ms.date: 03/30/2017
helpviewer_keywords:
- policy migration, compatibility
- CLR policy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
ms.openlocfilehash: 949739b3336a9182eef583cc405e60e09d7ec09d
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217152"
---
# <a name="code-access-security-policy-compatibility-and-migration"></a><span data-ttu-id="de97b-102">Kompatibilita a migrace zásad zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="de97b-102">Code Access Security Policy Compatibility and Migration</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="de97b-103">Část zásad zabezpečení přístupu kódu (CAS) byla v .NET Framework 4 zastaralá.</span><span class="sxs-lookup"><span data-stu-id="de97b-103">The policy portion of code access security (CAS) has been made obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="de97b-104">V důsledku toho může dojít k upozorněním na kompilaci a výjimkám modulu runtime, pokud voláte zastaralé typy zásad a členy [explicitně](#explicit_use) nebo [implicitně](#implicit_use) (prostřednictvím jiných typů a členů).</span><span class="sxs-lookup"><span data-stu-id="de97b-104">As a result, you may encounter compilation warnings and runtime exceptions if you call the obsolete policy types and members [explicitly](#explicit_use) or [implicitly](#implicit_use) (through other types and members).</span></span>

<span data-ttu-id="de97b-105">Upozornění a chyby můžete zabránit pomocí těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="de97b-105">You can avoid the warnings and errors by either:</span></span>

- <span data-ttu-id="de97b-106">[Migrace](#migration) na .NET Framework 4 nahrazení pro zastaralá volání.</span><span class="sxs-lookup"><span data-stu-id="de97b-106">[Migrating](#migration) to the .NET Framework 4 replacements for the obsolete calls.</span></span>

   <span data-ttu-id="de97b-107">\- nebo-</span><span class="sxs-lookup"><span data-stu-id="de97b-107">\- or -</span></span>

- <span data-ttu-id="de97b-108">Pomocí [elementu\<NetFx40_LegacySecurityPolicy > Konfigurace](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) se můžete vyjádřit ke staršímu chování zásad CAS.</span><span class="sxs-lookup"><span data-stu-id="de97b-108">Using the [\<NetFx40_LegacySecurityPolicy> configuration element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) to opt into the legacy CAS policy behavior.</span></span>

<span data-ttu-id="de97b-109">Toto téma obsahuje následující oddíly:</span><span class="sxs-lookup"><span data-stu-id="de97b-109">This topic contains the following sections:</span></span>

- [<span data-ttu-id="de97b-110">Explicitní použití</span><span class="sxs-lookup"><span data-stu-id="de97b-110">Explicit Use</span></span>](#explicit_use)

- [<span data-ttu-id="de97b-111">Implicitní použití</span><span class="sxs-lookup"><span data-stu-id="de97b-111">Implicit Use</span></span>](#implicit_use)

- [<span data-ttu-id="de97b-112">Chyby a upozornění</span><span class="sxs-lookup"><span data-stu-id="de97b-112">Errors and Warnings</span></span>](#errors_and_warnings)

- [<span data-ttu-id="de97b-113">Migrace: náhrada pro zastaralá volání</span><span class="sxs-lookup"><span data-stu-id="de97b-113">Migration: Replacement for Obsolete Calls</span></span>](#migration)

- [<span data-ttu-id="de97b-114">Kompatibilita: použití možnosti starší verze zásad CAS</span><span class="sxs-lookup"><span data-stu-id="de97b-114">Compatibility: Using the CAS Policy Legacy Option</span></span>](#compatibility)

<a name="explicit_use"></a>

## <a name="explicit-use"></a><span data-ttu-id="de97b-115">Explicitní použití</span><span class="sxs-lookup"><span data-stu-id="de97b-115">Explicit Use</span></span>

<span data-ttu-id="de97b-116">Členové, kteří přímo pracují se zásadami zabezpečení nebo vyžadují zásady CAS pro izolovaný prostor (sandbox), jsou zastaralé a ve výchozím nastavení vytvoří chyby.</span><span class="sxs-lookup"><span data-stu-id="de97b-116">Members that directly manipulate security policy or require CAS policy to sandbox are obsolete and will produce errors by default.</span></span>

<span data-ttu-id="de97b-117">Příklady těchto akcí:</span><span class="sxs-lookup"><span data-stu-id="de97b-117">Examples of these are:</span></span>

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

## <a name="implicit-use"></a><span data-ttu-id="de97b-118">Implicitní použití</span><span class="sxs-lookup"><span data-stu-id="de97b-118">Implicit Use</span></span>

<span data-ttu-id="de97b-119">Několik přetížení načítání sestavení vytváří chyby kvůli implicitnímu použití zásad CAS.</span><span class="sxs-lookup"><span data-stu-id="de97b-119">Several assembly loading overloads produce errors because of their implicit use of CAS policy.</span></span> <span data-ttu-id="de97b-120">Tato přetížení přebírají <xref:System.Security.Policy.Evidence> parametr, který se používá k vyřešení zásad CAS a poskytnutí oprávnění pro udělení oprávnění pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="de97b-120">These overloads take an <xref:System.Security.Policy.Evidence> parameter that is used to resolve CAS policy and provide a permission grant set for an assembly.</span></span>

<span data-ttu-id="de97b-121">Zde je několik příkladů:</span><span class="sxs-lookup"><span data-stu-id="de97b-121">Here are some examples.</span></span> <span data-ttu-id="de97b-122">Zastaralá přetížení jsou ta, která přijímají <xref:System.Security.Policy.Evidence> jako parametr:</span><span class="sxs-lookup"><span data-stu-id="de97b-122">The obsolete overloads are those that take <xref:System.Security.Policy.Evidence> as a parameter:</span></span>

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

## <a name="errors-and-warnings"></a><span data-ttu-id="de97b-123">Chyby a upozornění</span><span class="sxs-lookup"><span data-stu-id="de97b-123">Errors and Warnings</span></span>

<span data-ttu-id="de97b-124">Zastaralé typy a členy vytváří při použití následující chybové zprávy.</span><span class="sxs-lookup"><span data-stu-id="de97b-124">The obsolete types and members produce the following error messages when they are used.</span></span> <span data-ttu-id="de97b-125">Všimněte si, že samotný typ <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> není zastaralý.</span><span class="sxs-lookup"><span data-stu-id="de97b-125">Note that the <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> type itself is not obsolete.</span></span>

<span data-ttu-id="de97b-126">Upozornění při kompilaci:</span><span class="sxs-lookup"><span data-stu-id="de97b-126">Compile-time warning:</span></span>

`warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`

<span data-ttu-id="de97b-127">Běhová výjimka:</span><span class="sxs-lookup"><span data-stu-id="de97b-127">Run-time exception:</span></span>

<span data-ttu-id="de97b-128"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span><span class="sxs-lookup"><span data-stu-id="de97b-128"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span></span>

<a name="migration"></a>

## <a name="migration-replacement-for-obsolete-calls"></a><span data-ttu-id="de97b-129">Migrace: náhrada pro zastaralá volání</span><span class="sxs-lookup"><span data-stu-id="de97b-129">Migration: Replacement for Obsolete Calls</span></span>

### <a name="determining-an-assemblys-trust-level"></a><span data-ttu-id="de97b-130">Určení úrovně důvěryhodnosti sestavení</span><span class="sxs-lookup"><span data-stu-id="de97b-130">Determining an Assembly’s Trust Level</span></span>

<span data-ttu-id="de97b-131">Zásada CAS se často používá k určení sady oprávnění pro udělení oprávnění nebo domény aplikace nebo úrovně důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="de97b-131">CAS policy is often used to determine an assembly’s or application domain’s permission grant set or trust level.</span></span> <span data-ttu-id="de97b-132">.NET Framework 4 zpřístupňuje následující užitečné vlastnosti, které nepotřebují vyřešit zásady zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="de97b-132">The .NET Framework 4 exposes the following useful properties that do not need to resolve security policy:</span></span>

- <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>

### <a name="application-domain-sandboxing"></a><span data-ttu-id="de97b-133">Sandboxing domény aplikace</span><span class="sxs-lookup"><span data-stu-id="de97b-133">Application Domain Sandboxing</span></span>

<span data-ttu-id="de97b-134">Metoda <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> se obvykle používá pro sandboxing sestavení v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="de97b-134">The <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> method is typically used for sandboxing the assemblies in an application domain.</span></span> <span data-ttu-id="de97b-135">.NET Framework 4 zpřístupňuje členy, které nemusejí pro tento účel používat <xref:System.Security.Policy.PolicyLevel>.</span><span class="sxs-lookup"><span data-stu-id="de97b-135">The .NET Framework 4 exposes members that do not have to use <xref:System.Security.Policy.PolicyLevel> for this purpose.</span></span> <span data-ttu-id="de97b-136">Další informace naleznete v tématu [How to: Run částečně důvěryhodný kód v izolovaném prostoru (sandboxu)](how-to-run-partially-trusted-code-in-a-sandbox.md).</span><span class="sxs-lookup"><span data-stu-id="de97b-136">For more information, see [How to: Run Partially Trusted Code in a Sandbox](how-to-run-partially-trusted-code-in-a-sandbox.md).</span></span>

### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a><span data-ttu-id="de97b-137">Určení bezpečné nebo přiměřené sady oprávnění pro částečně důvěryhodný kód</span><span class="sxs-lookup"><span data-stu-id="de97b-137">Determining a Safe or Reasonable Permission Set for Partially Trusted Code</span></span>

<span data-ttu-id="de97b-138">Hostitelé často potřebují určit oprávnění, která jsou vhodná pro hostovaný kód izolovaného prostoru (sandbox).</span><span class="sxs-lookup"><span data-stu-id="de97b-138">Hosts often need to determine the permissions that are appropriate for sandboxing hosted code.</span></span> <span data-ttu-id="de97b-139">Předtím, než .NET Framework 4, poskytuje zásada CAS způsob, jak to provést s metodou <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="de97b-139">Before the .NET Framework 4, CAS policy provided a way to do this with the <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="de97b-140">Jako náhrada .NET Framework 4 poskytuje metodu <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType>, která vrací bezpečnou standardní sadu oprávnění pro poskytnuté legitimace.</span><span class="sxs-lookup"><span data-stu-id="de97b-140">As a replacement, .NET Framework 4 provides the <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> method, which returns a safe, standard permission set for the provided evidence.</span></span>

### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a><span data-ttu-id="de97b-141">Scénáře, které nepatří do izolovaného prostoru: přetížení pro načtení sestavení</span><span class="sxs-lookup"><span data-stu-id="de97b-141">Non-Sandboxing Scenarios: Overloads for Assembly Loads</span></span>

<span data-ttu-id="de97b-142">Důvodem použití přetížení zatížení sestavení může být použití parametrů, které nejsou jinak k dispozici, namísto sestavování sestavení v izolovaném prostoru.</span><span class="sxs-lookup"><span data-stu-id="de97b-142">The reason for using an assembly load overload might be to use parameters that are not otherwise available, instead of sandboxing the assembly.</span></span> <span data-ttu-id="de97b-143">Počínaje .NET Framework 4 jsou přetížení zátěže sestavení, která nevyžadují <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> objekt jako parametr, například <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, povolují tento scénář.</span><span class="sxs-lookup"><span data-stu-id="de97b-143">Starting with the .NET Framework 4, assembly load overloads that do not require a <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> object as a parameter, for example, <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, enable this scenario.</span></span>

<span data-ttu-id="de97b-144">Pokud chcete sestavení izolovaného prostoru (sandbox), použijte <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> přetížení.</span><span class="sxs-lookup"><span data-stu-id="de97b-144">If you want to sandbox an assembly, use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> overload.</span></span>

<a name="compatibility"></a>

## <a name="compatibility-using-the-cas-policy-legacy-option"></a><span data-ttu-id="de97b-145">Kompatibilita: použití možnosti starší verze zásad CAS</span><span class="sxs-lookup"><span data-stu-id="de97b-145">Compatibility: Using the CAS Policy Legacy Option</span></span>

<span data-ttu-id="de97b-146">[Konfigurační prvek\<NetFx40_LegacySecurityPolicy >](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) umožňuje určit, že proces nebo knihovna používá starší zásady CAS.</span><span class="sxs-lookup"><span data-stu-id="de97b-146">The [\<NetFx40_LegacySecurityPolicy> configuration element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) lets you specify that a process or library uses legacy CAS policy.</span></span> <span data-ttu-id="de97b-147">Pokud povolíte tento prvek, přetížení zásad a legitimace budou fungovat stejně jako v předchozích verzích rozhraní.</span><span class="sxs-lookup"><span data-stu-id="de97b-147">When you enable this element, the policy and evidence overloads will work as they did in previous versions of the framework.</span></span>

> [!NOTE]
> <span data-ttu-id="de97b-148">Chování zásad CAS je určeno pro verzi modulu runtime, takže změna zásad CAS pro jednu verzi modulu runtime nemá vliv na zásady CAS jiné verze.</span><span class="sxs-lookup"><span data-stu-id="de97b-148">CAS policy behavior is specified on a runtime version basis, so modifying CAS policy for one runtime version does not affect the CAS policy of another version.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="de97b-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="de97b-149">See also</span></span>

- [<span data-ttu-id="de97b-150">Postupy: spuštění částečně důvěryhodného kódu v izolovaném prostoru</span><span class="sxs-lookup"><span data-stu-id="de97b-150">How to: Run Partially Trusted Code in a Sandbox</span></span>](how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="de97b-151">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="de97b-151">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
