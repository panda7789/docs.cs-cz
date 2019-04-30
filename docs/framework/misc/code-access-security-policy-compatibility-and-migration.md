---
title: Kompatibilita a migrace zásad zabezpečení přístupu kódu
ms.date: 03/30/2017
helpviewer_keywords:
- policy migration, compatibility
- CLR policy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d9281e52de43391a92262f85084715ccabd5515
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61868911"
---
# <a name="code-access-security-policy-compatibility-and-migration"></a><span data-ttu-id="1742a-102">Kompatibilita a migrace zásad zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="1742a-102">Code Access Security Policy Compatibility and Migration</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="1742a-103">Část zásad zabezpečení přístupu kódu (CAS) byly provedeny v zastaralé [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1742a-103">The policy portion of code access security (CAS) has been made obsolete in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="1742a-104">V důsledku toho může dojít upozornění kompilace a výjimky běhového modulu při volání zásad zastaralé typy a členy [explicitně](#explicit_use) nebo [implicitně](#implicit_use) (pomocí jiných typů a členů).</span><span class="sxs-lookup"><span data-stu-id="1742a-104">As a result, you may encounter compilation warnings and runtime exceptions if you call the obsolete policy types and members [explicitly](#explicit_use) or [implicitly](#implicit_use) (through other types and members).</span></span>

<span data-ttu-id="1742a-105">Můžete se vyhnout upozornění a chyby buď:</span><span class="sxs-lookup"><span data-stu-id="1742a-105">You can avoid the warnings and errors by either:</span></span>

- <span data-ttu-id="1742a-106">[Migrace](#migration) k [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] nahrazení pro zastaralý volání.</span><span class="sxs-lookup"><span data-stu-id="1742a-106">[Migrating](#migration) to the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] replacements for the obsolete calls.</span></span>

   <span data-ttu-id="1742a-107">\- nebo –</span><span class="sxs-lookup"><span data-stu-id="1742a-107">\- or -</span></span>

- <span data-ttu-id="1742a-108">Použití [element < NetFx40_LegacySecurityPolicy > Konfigurace](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) do starší chování zásad CAS.</span><span class="sxs-lookup"><span data-stu-id="1742a-108">Using the [<NetFx40_LegacySecurityPolicy> configuration element](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) to opt into the legacy CAS policy behavior.</span></span>

<span data-ttu-id="1742a-109">Toto téma obsahuje následující oddíly:</span><span class="sxs-lookup"><span data-stu-id="1742a-109">This topic contains the following sections:</span></span>

- [<span data-ttu-id="1742a-110">Explicitní použití</span><span class="sxs-lookup"><span data-stu-id="1742a-110">Explicit Use</span></span>](#explicit_use)

- [<span data-ttu-id="1742a-111">Implicitní použití</span><span class="sxs-lookup"><span data-stu-id="1742a-111">Implicit Use</span></span>](#implicit_use)

- [<span data-ttu-id="1742a-112">Chyby a upozornění</span><span class="sxs-lookup"><span data-stu-id="1742a-112">Errors and Warnings</span></span>](#errors_and_warnings)

- [<span data-ttu-id="1742a-113">Migrace: Nahrazení pro zastaralý volání</span><span class="sxs-lookup"><span data-stu-id="1742a-113">Migration: Replacement for Obsolete Calls</span></span>](#migration)

- [<span data-ttu-id="1742a-114">Kompatibility: Pomocí možnosti zásad CAS starší verze</span><span class="sxs-lookup"><span data-stu-id="1742a-114">Compatibility: Using the CAS Policy Legacy Option</span></span>](#compatibility)

<a name="explicit_use"></a>

## <a name="explicit-use"></a><span data-ttu-id="1742a-115">Explicitní použití</span><span class="sxs-lookup"><span data-stu-id="1742a-115">Explicit Use</span></span>

<span data-ttu-id="1742a-116">Členy, které přímo pracovat s zásady zabezpečení nebo vyžadují zásady CAS do izolovaného prostoru jsou zastaralé a vygeneruje chyby ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="1742a-116">Members that directly manipulate security policy or require CAS policy to sandbox are obsolete and will produce errors by default.</span></span>

<span data-ttu-id="1742a-117">Mezi ty patří:</span><span class="sxs-lookup"><span data-stu-id="1742a-117">Examples of these are:</span></span>

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

## <a name="implicit-use"></a><span data-ttu-id="1742a-118">Implicitní použití</span><span class="sxs-lookup"><span data-stu-id="1742a-118">Implicit Use</span></span>

<span data-ttu-id="1742a-119">Několik přetížení načítání sestavení vytvořit chyby z důvodu jejich implicitního použití zásad CAS.</span><span class="sxs-lookup"><span data-stu-id="1742a-119">Several assembly loading overloads produce errors because of their implicit use of CAS policy.</span></span> <span data-ttu-id="1742a-120">Tato přetížení používají <xref:System.Security.Policy.Evidence> parametr, který se používá k řešení certifikační Autority zásad a poskytnout oprávnění udělit sady pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="1742a-120">These overloads take an <xref:System.Security.Policy.Evidence> parameter that is used to resolve CAS policy and provide a permission grant set for an assembly.</span></span>

<span data-ttu-id="1742a-121">Zde je několik příkladů:</span><span class="sxs-lookup"><span data-stu-id="1742a-121">Here are some examples.</span></span> <span data-ttu-id="1742a-122">Zastaralá přetížení jsou ty, které trvat <xref:System.Security.Policy.Evidence> jako parametr:</span><span class="sxs-lookup"><span data-stu-id="1742a-122">The obsolete overloads are those that take <xref:System.Security.Policy.Evidence> as a parameter:</span></span>

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

## <a name="errors-and-warnings"></a><span data-ttu-id="1742a-123">Chyby a upozornění</span><span class="sxs-lookup"><span data-stu-id="1742a-123">Errors and Warnings</span></span>

<span data-ttu-id="1742a-124">Zastaralé typy a členy vytvořit následující chybové zprávy při jejich použití.</span><span class="sxs-lookup"><span data-stu-id="1742a-124">The obsolete types and members produce the following error messages when they are used.</span></span> <span data-ttu-id="1742a-125">Všimněte si, že <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> samotného typu není zastaralá.</span><span class="sxs-lookup"><span data-stu-id="1742a-125">Note that the <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> type itself is not obsolete.</span></span>

<span data-ttu-id="1742a-126">Upozornění kompilace:</span><span class="sxs-lookup"><span data-stu-id="1742a-126">Compile-time warning:</span></span>

`warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`

<span data-ttu-id="1742a-127">Výjimka za běhu:</span><span class="sxs-lookup"><span data-stu-id="1742a-127">Run-time exception:</span></span>

<span data-ttu-id="1742a-128"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span><span class="sxs-lookup"><span data-stu-id="1742a-128"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span></span>

<a name="migration"></a>

## <a name="migration-replacement-for-obsolete-calls"></a><span data-ttu-id="1742a-129">Migrace: Nahrazení pro zastaralý volání</span><span class="sxs-lookup"><span data-stu-id="1742a-129">Migration: Replacement for Obsolete Calls</span></span>

### <a name="determining-an-assemblys-trust-level"></a><span data-ttu-id="1742a-130">Určení úroveň důvěryhodnosti sestavení</span><span class="sxs-lookup"><span data-stu-id="1742a-130">Determining an Assembly’s Trust Level</span></span>

<span data-ttu-id="1742a-131">Zásady CAS z se často používá k určení sestavení nebo doména aplikace oprávnění sada udělení oprávnění nebo úroveň důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="1742a-131">CAS policy is often used to determine an assembly’s or application domain’s permission grant set or trust level.</span></span> <span data-ttu-id="1742a-132">[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Zveřejňuje následující užitečné vlastnosti, které není potřeba řešit zásady zabezpečení:</span><span class="sxs-lookup"><span data-stu-id="1742a-132">The [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] exposes the following useful properties that do not need to resolve security policy:</span></span>

- <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>

### <a name="application-domain-sandboxing"></a><span data-ttu-id="1742a-133">Sandboxing domény aplikace</span><span class="sxs-lookup"><span data-stu-id="1742a-133">Application Domain Sandboxing</span></span>

<span data-ttu-id="1742a-134"><xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> Metoda se obvykle používá pro sandboxing sestavení v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="1742a-134">The <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> method is typically used for sandboxing the assemblies in an application domain.</span></span> <span data-ttu-id="1742a-135">[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] Zpřístupňuje členy, které není nutné používat <xref:System.Security.Policy.PolicyLevel> pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="1742a-135">The [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] exposes members that do not have to use <xref:System.Security.Policy.PolicyLevel> for this purpose.</span></span> <span data-ttu-id="1742a-136">Další informace najdete v tématu [jak: Spuštění částečně důvěryhodného kódu v izolovaném prostoru](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).</span><span class="sxs-lookup"><span data-stu-id="1742a-136">For more information, see [How to: Run Partially Trusted Code in a Sandbox](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).</span></span>

### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a><span data-ttu-id="1742a-137">Určení sady bezpečné nebo přiměřené oprávnění pro částečně důvěryhodný kód.</span><span class="sxs-lookup"><span data-stu-id="1742a-137">Determining a Safe or Reasonable Permission Set for Partially Trusted Code</span></span>

<span data-ttu-id="1742a-138">Hostitelé často nutné určit oprávnění, které jsou vhodné pro kód izolace (sandbox), které jsou hostované.</span><span class="sxs-lookup"><span data-stu-id="1742a-138">Hosts often need to determine the permissions that are appropriate for sandboxing hosted code.</span></span> <span data-ttu-id="1742a-139">Před [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], poskytuje způsob, jak to provést pomocí zásad CAS <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="1742a-139">Before the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], CAS policy provided a way to do this with the <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="1742a-140">Jako náhradu [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] poskytuje <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> metodu, která vrací sadu pro zadaný důkazy bezpečný, standardní oprávnění.</span><span class="sxs-lookup"><span data-stu-id="1742a-140">As a replacement, [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] provides the <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> method, which returns a safe, standard permission set for the provided evidence.</span></span>

### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a><span data-ttu-id="1742a-141">Non-Sandboxing scénáře: Přetížení pro načtení sestavení</span><span class="sxs-lookup"><span data-stu-id="1742a-141">Non-Sandboxing Scenarios: Overloads for Assembly Loads</span></span>

<span data-ttu-id="1742a-142">Použití parametrů, které jinak nejsou k dispozici, namísto sandboxing sestavení může být důvod pomocí přetížení načtení sestavení.</span><span class="sxs-lookup"><span data-stu-id="1742a-142">The reason for using an assembly load overload might be to use parameters that are not otherwise available, instead of sandboxing the assembly.</span></span> <span data-ttu-id="1742a-143">Počínaje [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], přetížení načtení sestavení, které nevyžadují, aby <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> objektu jako parametr, například <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, povolit tento scénář.</span><span class="sxs-lookup"><span data-stu-id="1742a-143">Starting with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], assembly load overloads that do not require a <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> object as a parameter, for example, <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, enable this scenario.</span></span>

<span data-ttu-id="1742a-144">Pokud chcete do izolovaného prostoru sestavení, použijte <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> přetížení.</span><span class="sxs-lookup"><span data-stu-id="1742a-144">If you want to sandbox an assembly, use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> overload.</span></span>

<a name="compatibility"></a>

## <a name="compatibility-using-the-cas-policy-legacy-option"></a><span data-ttu-id="1742a-145">Kompatibility: Pomocí možnosti zásad CAS starší verze</span><span class="sxs-lookup"><span data-stu-id="1742a-145">Compatibility: Using the CAS Policy Legacy Option</span></span>

<span data-ttu-id="1742a-146">[Element < NetFx40_LegacySecurityPolicy > Konfigurace](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) umožňuje určit, který proces nebo knihovna používá starší zásadu CAS.</span><span class="sxs-lookup"><span data-stu-id="1742a-146">The [<NetFx40_LegacySecurityPolicy> configuration element](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) lets you specify that a process or library uses legacy CAS policy.</span></span> <span data-ttu-id="1742a-147">Po povolení tohoto prvku přetížení zásady a důkazy bude fungovat stejně jako v předchozích verzích rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1742a-147">When you enable this element, the policy and evidence overloads will work as they did in previous versions of the framework.</span></span>

> [!NOTE]
> <span data-ttu-id="1742a-148">Na základě verze modulu runtime, je specifikováno chování zásady CAS, tak úprava zásad CAS pro jednu verzi modulu runtime neovlivní zásady CAS z jiné verze.</span><span class="sxs-lookup"><span data-stu-id="1742a-148">CAS policy behavior is specified on a runtime version basis, so modifying CAS policy for one runtime version does not affect the CAS policy of another version.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="1742a-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1742a-149">See also</span></span>

- [<span data-ttu-id="1742a-150">Postupy: Spuštění částečně důvěryhodného kódu v izolovaném prostoru</span><span class="sxs-lookup"><span data-stu-id="1742a-150">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="1742a-151">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="1742a-151">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
