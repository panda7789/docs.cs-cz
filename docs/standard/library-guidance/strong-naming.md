---
title: Silné pojmenování a knihovny .NET
description: Doporučení osvědčených postupů pro silné pojmenování knihoven .NET.
ms.date: 10/16/2018
ms.openlocfilehash: db268093b07a2ece7cdb8329fd789b52da9c5c32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "76744534"
---
# <a name="strong-naming"></a><span data-ttu-id="61601-103">Vytváření silných názvů</span><span class="sxs-lookup"><span data-stu-id="61601-103">Strong naming</span></span>

<span data-ttu-id="61601-104">Silné pojmenování odkazuje na podepsání sestavení pomocí klíče, vytvoření [sestavení se silným názvem](../assembly/strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="61601-104">Strong naming refers to signing an assembly with a key, producing a [strong-named assembly](../assembly/strong-named.md).</span></span> <span data-ttu-id="61601-105">Pokud je sestavení silně pojmenované, vytvoří jedinečnou identitu založenou na názvu a čísle verze sestavení a může pomoci zabránit konfliktům sestavení.</span><span class="sxs-lookup"><span data-stu-id="61601-105">When an assembly is strong-named, it creates a unique identity based on the name and assembly version number, and it can help prevent assembly conflicts.</span></span>

<span data-ttu-id="61601-106">Nevýhodou silného pojmenování je, že rozhraní .NET Framework v systému Windows umožňuje přísné načítání sestavení, jakmile je sestavení silné s názvem.</span><span class="sxs-lookup"><span data-stu-id="61601-106">The downside to strong naming is that the .NET Framework on Windows enables strict loading of assemblies once an assembly is strong named.</span></span> <span data-ttu-id="61601-107">Odkaz na sestavení se silným názvem se musí přesně shodovat s verzí, na kterou odkazuje sestavení, což nutí vývojáře [konfigurovat přesměrování vazeb](../../framework/configure-apps/redirect-assembly-versions.md) při použití sestavení:</span><span class="sxs-lookup"><span data-stu-id="61601-107">A strong-named assembly reference must exactly match the version referenced by an assembly, forcing developers to [configure binding redirects](../../framework/configure-apps/redirect-assembly-versions.md) when using the assembly:</span></span>

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
         <dependentAssembly>
            <assemblyIdentity name="myAssembly" publicKeyToken="32ab4ba45e0a69a1" culture="neutral" />
            <bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0"/>
         </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

<span data-ttu-id="61601-108">Když si vývojáři rozhraní .NET stěžují na silné pojmenování, obvykle si stěžují na přísné načítání sestavení.</span><span class="sxs-lookup"><span data-stu-id="61601-108">When .NET developers complain about strong naming, what they're usually complaining about is strict assembly loading.</span></span> <span data-ttu-id="61601-109">Naštěstí tento problém je izolován a rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="61601-109">Fortunately, this issue is isolated to the .NET Framework.</span></span> <span data-ttu-id="61601-110">.NET Core, Xamarin, UPW a většina ostatních implementací .NET nemají přísné načítání sestavení a odebere hlavní nevýhodu silného pojmenování.</span><span class="sxs-lookup"><span data-stu-id="61601-110">.NET Core, Xamarin, UWP, and most other .NET implementations don't have strict assembly loading and removes the main downside of strong naming.</span></span>

<span data-ttu-id="61601-111">Jedním z důležitých aspektů silného pojmenování je, že je virové: silné pojmenované sestavení může odkazovat pouze na další silná pojmenovaná sestavení.</span><span class="sxs-lookup"><span data-stu-id="61601-111">One important aspect of strong naming is that it's viral: a strong named assembly can only reference other strong named assemblies.</span></span> <span data-ttu-id="61601-112">Pokud vaše knihovna není silná s názvem, pak jste vyloučili vývojáře, kteří budují aplikaci nebo knihovnu, která potřebuje silné pojmenování z jeho použití.</span><span class="sxs-lookup"><span data-stu-id="61601-112">If your library isn't strong named, then you have excluded developers who are building an application or library that needs strong naming from using it.</span></span>

<span data-ttu-id="61601-113">Výhody silného pojmenování jsou:</span><span class="sxs-lookup"><span data-stu-id="61601-113">The benefits of strong naming are:</span></span>

1. <span data-ttu-id="61601-114">Na sestavení lze odkazovat a používat je jinými sestaveními se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="61601-114">The assembly can be referenced and used by other strong-named assemblies.</span></span>
2. <span data-ttu-id="61601-115">Sestavení lze uložit do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="61601-115">The assembly can be stored in the Global Assembly Cache (GAC).</span></span>
3. <span data-ttu-id="61601-116">Sestava může být načtena vedle sebe s jinými verzemi sestavení.</span><span class="sxs-lookup"><span data-stu-id="61601-116">The assembly can be loaded side by side with other versions of the assembly.</span></span> <span data-ttu-id="61601-117">Zatížení sestavy vedle sebe je běžně vyžadováno aplikacemi s architekturou modulu plug-in.</span><span class="sxs-lookup"><span data-stu-id="61601-117">Side-by-side assembly loading is commonly required by applications with plug-in architectures.</span></span>

## <a name="create-strong-named-net-libraries"></a><span data-ttu-id="61601-118">Vytvoření silných pojmenovaných knihoven .NET</span><span class="sxs-lookup"><span data-stu-id="61601-118">Create strong named .NET libraries</span></span>

<span data-ttu-id="61601-119">Měli byste silné jméno open-source knihovny .NET.</span><span class="sxs-lookup"><span data-stu-id="61601-119">You should strong name your open-source .NET libraries.</span></span> <span data-ttu-id="61601-120">Silné pojmenování sestavení zajišťuje, že ji může používat většina lidí a přísné načítání sestavení ovlivní pouze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="61601-120">Strong naming an assembly ensures the most people can use it, and strict assembly loading only affects the .NET Framework.</span></span>

> [!NOTE]
> <span data-ttu-id="61601-121">Tento návod je specifický pro veřejně distribuované knihovny .NET, jako jsou například knihovny .NET publikované v NuGet.org. Silné pojmenování není vyžadováno většinou aplikací .NET a ve výchozím nastavení by nemělo být prováděno.</span><span class="sxs-lookup"><span data-stu-id="61601-121">This guidance is specific to publicly distributed .NET libraries, such as .NET libraries published on NuGet.org. Strong naming is not required by most .NET applications and should not be done by default.</span></span>

<span data-ttu-id="61601-122">✔️ ZVAŽTE silné pojmenování sestavení knihovny.</span><span class="sxs-lookup"><span data-stu-id="61601-122">✔️ CONSIDER strong naming your library's assemblies.</span></span>

<span data-ttu-id="61601-123">✔️ ZVAŽTe přidání silného pojmenovávacího klíče do systému správy zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="61601-123">✔️ CONSIDER adding the strong naming key to your source control system.</span></span>

> <span data-ttu-id="61601-124">Veřejně dostupný klíč umožňuje vývojářům upravit a znovu zkompilovat zdrojový kód knihovny se stejným klíčem.</span><span class="sxs-lookup"><span data-stu-id="61601-124">A publicly available key lets developers modify and recompile your library source code with the same key.</span></span>
>
> <span data-ttu-id="61601-125">Silný pojmenovávací klíč byste neměli zveřejňovat, pokud byl v minulosti použit k udělení zvláštních oprávnění ve [scénářích částečné důvěryhodnosti](../../framework/misc/using-libraries-from-partially-trusted-code.md).</span><span class="sxs-lookup"><span data-stu-id="61601-125">You shouldn't make the strong naming key public if it has been used in the past to give special permissions in [partial-trust scenarios](../../framework/misc/using-libraries-from-partially-trusted-code.md).</span></span> <span data-ttu-id="61601-126">V opačném případě může dojít k ohrožení existujících prostředí.</span><span class="sxs-lookup"><span data-stu-id="61601-126">Otherwise, you might compromise existing environments.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="61601-127">Pokud je požadována identita vydavatele kódu, [authenticode](/windows-hardware/drivers/install/authenticode) a NuGet package signing jsou [doporučeny.](/nuget/create-packages/sign-a-package)</span><span class="sxs-lookup"><span data-stu-id="61601-127">When the identity of the publisher of the code is desired, [Authenticode](/windows-hardware/drivers/install/authenticode) and [NuGet Package Signing](/nuget/create-packages/sign-a-package) are recommended.</span></span> <span data-ttu-id="61601-128">Zabezpečení přístupu kódu (CAS) by nemělbýt používán jako zmírnění zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="61601-128">Code Access Security (CAS) should not be used as a security mitigation.</span></span>

<span data-ttu-id="61601-129">✔️ ZVAŽTE zvýšení verze sestavení pouze na hlavní verze změny pomoci uživatelům snížit přesměrování vazby a jak často jsou aktualizovány.</span><span class="sxs-lookup"><span data-stu-id="61601-129">✔️ CONSIDER incrementing the assembly version on only major version changes to help users reduce binding redirects, and how often they're updated.</span></span>

> <span data-ttu-id="61601-130">Přečtěte si další informace o [správu verzí a verzi sestavení](./versioning.md#assembly-version).</span><span class="sxs-lookup"><span data-stu-id="61601-130">Read more about [versioning and the assembly version](./versioning.md#assembly-version).</span></span>

<span data-ttu-id="61601-131">❌NEPŘIdávejte, neodebírejte ani neměňte silný pojmenovávacím klíčem.</span><span class="sxs-lookup"><span data-stu-id="61601-131">❌ DO NOT add, remove, or change the strong naming key.</span></span>

> <span data-ttu-id="61601-132">Úprava silného pojmenovávacího klíče sestavení změní identitu sestavení a přeruší zkompilovaný kód, který jej používá.</span><span class="sxs-lookup"><span data-stu-id="61601-132">Modifying an assembly's strong naming key changes the assembly's identity and breaks compiled code that uses it.</span></span> <span data-ttu-id="61601-133">Další informace naleznete v [tématu binární narušující změny](./breaking-changes.md#binary-breaking-change).</span><span class="sxs-lookup"><span data-stu-id="61601-133">For more information, see [binary breaking changes](./breaking-changes.md#binary-breaking-change).</span></span>

<span data-ttu-id="61601-134">❌NEPublikujte verze knihovny se silným názvem a bez silného název.</span><span class="sxs-lookup"><span data-stu-id="61601-134">❌ DO NOT publish strong-named and non-strong-named versions of your library.</span></span> <span data-ttu-id="61601-135">Například `Contoso.Api` a `Contoso.Api.StrongNamed`.</span><span class="sxs-lookup"><span data-stu-id="61601-135">For example, `Contoso.Api` and `Contoso.Api.StrongNamed`.</span></span>

> <span data-ttu-id="61601-136">Publikování dvou balíčků rozpisy váš vývojář ský eco-systém.</span><span class="sxs-lookup"><span data-stu-id="61601-136">Publishing two packages forks your developer eco-system.</span></span> <span data-ttu-id="61601-137">Také pokud aplikace skončí v závislosti na obou balíčcích vývojář může dojít ke konfliktům názvu typu.</span><span class="sxs-lookup"><span data-stu-id="61601-137">Also, if an application ends up depending on both packages the developer can encounter type name conflicts.</span></span> <span data-ttu-id="61601-138">Pokud jde o rozhraní .NET, jsou různé typy v různých sestaveních.</span><span class="sxs-lookup"><span data-stu-id="61601-138">As far as .NET is concerned they are different types in different assemblies.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="61601-139">[Předchozí](cross-platform-targeting.md)
>[další](nuget.md)</span><span class="sxs-lookup"><span data-stu-id="61601-139">[Previous](cross-platform-targeting.md)
[Next](nuget.md)</span></span>
