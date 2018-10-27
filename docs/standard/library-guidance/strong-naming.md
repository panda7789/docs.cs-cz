---
title: Silné názvy a knihoven .NET
description: Doporučené osvědčené postupy pro silné pojmenovávání knihovny .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/16/2018
ms.openlocfilehash: 6f5743c7a8c6fdbdcdcf3aa80d2f92f2e04621f2
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50041762"
---
# <a name="strong-naming"></a><span data-ttu-id="5496d-103">Silné názvy</span><span class="sxs-lookup"><span data-stu-id="5496d-103">Strong naming</span></span>

<span data-ttu-id="5496d-104">Silné názvy odkazuje na podepsání sestavení s klíčem, vytváření [sestavení se silným názvem](../../framework/app-domains/strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="5496d-104">Strong naming refers to signing an assembly with a key, producing a [strong-named assembly](../../framework/app-domains/strong-named-assemblies.md).</span></span> <span data-ttu-id="5496d-105">Po sestavení se silným názvem ho vytvoří jedinečnou identitu na základě čísla verze název a sestavení a může pomoci zabránit konfliktům při sestavení.</span><span class="sxs-lookup"><span data-stu-id="5496d-105">When an assembly is strong-named, it creates a unique identity based on the name and assembly version number, and it can help prevent assembly conflicts.</span></span>

<span data-ttu-id="5496d-106">Silné názvy nevýhodou je, že rozhraní .NET Framework ve Windows umožňuje striktní načítání sestavení po sestavení je silný název.</span><span class="sxs-lookup"><span data-stu-id="5496d-106">The downside to strong naming is that the .NET Framework on Windows enables strict loading of assemblies once an assembly is strong named.</span></span> <span data-ttu-id="5496d-107">Odkaz sestavení se silným názvem musí přesně shodovat s verzí odkazuje sestavení, vynucení vývojářům [konfigurace přesměrování vazby](../../framework/configure-apps/redirect-assembly-versions.md) při použití sestavení:</span><span class="sxs-lookup"><span data-stu-id="5496d-107">A strong-named assembly reference must exactly match the version referenced by an assembly, forcing developers to [configure binding redirects](../../framework/configure-apps/redirect-assembly-versions.md) when using the assembly:</span></span>

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

<span data-ttu-id="5496d-108">Vývojáři na platformě .NET stěžovat silné názvy, co se budete obvykle stěžovat při načítání striktní sestavení.</span><span class="sxs-lookup"><span data-stu-id="5496d-108">When .NET developers complain about strong naming, what they're usually complaining about is strict assembly loading.</span></span> <span data-ttu-id="5496d-109">Naštěstí tento problém je izolovaná na rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5496d-109">Fortunately, this issue is isolated to the .NET Framework.</span></span> <span data-ttu-id="5496d-110">.NET core, Xamarin, UPW a většina jiných implementace .NET není nutné přísnou načítání sestavení a odebere Hlavní nevýhodou silné názvy.</span><span class="sxs-lookup"><span data-stu-id="5496d-110">.NET Core, Xamarin, UWP, and most other .NET implementations don't have strict assembly loading and removes the main downside of strong naming.</span></span>

<span data-ttu-id="5496d-111">Jeden důležitý aspekt silné názvy je, že se jedná o virálního: silné s názvem pouze odkaz na sestavení mohou ostatní silné s názvem sestavení.</span><span class="sxs-lookup"><span data-stu-id="5496d-111">One important aspect of strong naming is that it's viral: a strong named assembly can only reference other strong named assemblies.</span></span> <span data-ttu-id="5496d-112">Pokud vaše knihovna není silné s názvem, pak jste vyloučili vývojáři, kteří vytvářejí aplikace nebo knihovna, která musí využívat silné názvy.</span><span class="sxs-lookup"><span data-stu-id="5496d-112">If your library isn't strong named, then you have excluded developers who are building an application or library that needs strong naming from using it.</span></span>

<span data-ttu-id="5496d-113">Výhody silné názvy jsou:</span><span class="sxs-lookup"><span data-stu-id="5496d-113">The benefits of strong naming are:</span></span>

1. <span data-ttu-id="5496d-114">Sestavení lze odkazovat a používat jiné sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="5496d-114">The assembly can be referenced and used by other strong-named assemblies.</span></span>
2. <span data-ttu-id="5496d-115">Sestavení mohou být uloženy v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="5496d-115">The assembly can be stored in the Global Assembly Cache (GAC).</span></span>
3. <span data-ttu-id="5496d-116">Sestavení lze načíst souběžně s jinými verzemi sestavení.</span><span class="sxs-lookup"><span data-stu-id="5496d-116">The assembly can be loaded side by side with other versions of the assembly.</span></span> <span data-ttu-id="5496d-117">Načítání sestavení vedle sebe je běžně potřebné pro aplikace pomocí modulu plug-in architektury.</span><span class="sxs-lookup"><span data-stu-id="5496d-117">Side-by-side assembly loading is commonly required by applications with plug-in architectures.</span></span>

## <a name="create-strong-named-net-libraries"></a><span data-ttu-id="5496d-118">Vytvořit silné s názvem knihovny pro .NET</span><span class="sxs-lookup"><span data-stu-id="5496d-118">Create strong named .NET libraries</span></span>

<span data-ttu-id="5496d-119">Open source knihoven .NET by měl silný název.</span><span class="sxs-lookup"><span data-stu-id="5496d-119">You should strong name your open-source .NET libraries.</span></span> <span data-ttu-id="5496d-120">Silné názvy sestavení zajistí ho většina lidí může použít a ovlivňuje pouze načítání striktní sestavení rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5496d-120">Strong naming an assembly ensures the most people can use it, and strict assembly loading only affects the .NET Framework.</span></span>

> [!NOTE]
> <span data-ttu-id="5496d-121">Tento návod je specifický pro veřejně distribuované knihovny .NET, například knihovny .NET publikovaná na NuGet.org. Silné názvy není vyžadováno pro většinu aplikací .NET a by neměla být provedena ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="5496d-121">This guidance is specific to publicly distributed .NET libraries, such as .NET libraries published on NuGet.org. Strong naming is not required by most .NET applications and should not be done by default.</span></span>

<span data-ttu-id="5496d-122">**✔️ ZVAŽTE** silné názvy sestavení své knihovny.</span><span class="sxs-lookup"><span data-stu-id="5496d-122">**✔️ CONSIDER** strong naming your library's assemblies.</span></span>

<span data-ttu-id="5496d-123">**✔️ ZVAŽTE** přidání silného pojmenování klíče do systému správy zdrojů.</span><span class="sxs-lookup"><span data-stu-id="5496d-123">**✔️ CONSIDER** adding the strong naming key to your source control system.</span></span>

> <span data-ttu-id="5496d-124">Veřejně dostupné klíče umožňuje vývojářům upravit a znovu zkompilovat zdrojový kód knihovny se stejným klíčem.</span><span class="sxs-lookup"><span data-stu-id="5496d-124">A publicly available key lets developers modify and recompile your library source code with the same key.</span></span>
> 
> <span data-ttu-id="5496d-125">Silného pojmenování klíče by neměla provést veřejné, pokud byl udělit zvláštní oprávnění použili v minulosti [částečnou důvěryhodností scénářích](/dotnet/framework/misc/using-libraries-from-partially-trusted-code).</span><span class="sxs-lookup"><span data-stu-id="5496d-125">You shouldn't make the strong naming key public if it has been used in the past to give special permissions in [partial-trust scenarios](/dotnet/framework/misc/using-libraries-from-partially-trusted-code).</span></span> <span data-ttu-id="5496d-126">V opačném případě by mohlo ohrozit existující prostředí.</span><span class="sxs-lookup"><span data-stu-id="5496d-126">Otherwise, you might compromise existing environments.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5496d-127">Potřebujete identity vydavatele kód [Authenticode](/windows-hardware/drivers/install/authenticode) a [podepisování balíčků NuGet](/nuget/create-packages/sign-a-package) doporučují.</span><span class="sxs-lookup"><span data-stu-id="5496d-127">When the identity of the publisher of the code is desired, [Authenticode](/windows-hardware/drivers/install/authenticode) and [NuGet Package Signing](/nuget/create-packages/sign-a-package) are recommended.</span></span> <span data-ttu-id="5496d-128">Zabezpečení přístupu kódu (CAS) není vhodné používat jako omezení rizik zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5496d-128">Code Access Security (CAS) should not be used as a security mitigation.</span></span>

<span data-ttu-id="5496d-129">**✔️ ZVAŽTE** zvyšování verze sestavení na změny jenom hlavní verzi k poskytování pomoci uživatelům omezit přesměrování vazby a jak často se aktualizuje.</span><span class="sxs-lookup"><span data-stu-id="5496d-129">**✔️ CONSIDER** incrementing the assembly version on only major version changes to help users reduce binding redirects, and how often they're updated.</span></span>

> <span data-ttu-id="5496d-130">Další informace o [správy verzí a verzí sestavení](./versioning.md#assembly-version).</span><span class="sxs-lookup"><span data-stu-id="5496d-130">Read more about [versioning and the assembly version](./versioning.md#assembly-version).</span></span>

<span data-ttu-id="5496d-131">**❌ NEPODPORUJÍ** přidat, odebrat nebo změnit silného pojmenování klíče.</span><span class="sxs-lookup"><span data-stu-id="5496d-131">**❌ DO NOT** add, remove, or change the strong naming key.</span></span>

> <span data-ttu-id="5496d-132">Úprava silného pojmenování klíče sestavení změní identitu sestavení a přeruší zkompilovaný kód, který ji používá.</span><span class="sxs-lookup"><span data-stu-id="5496d-132">Modifying an assembly's strong naming key changes the assembly's identity and breaks compiled code that uses it.</span></span> <span data-ttu-id="5496d-133">Další informace najdete v tématu [binární rozbíjející změny v](./breaking-changes.md#binary-breaking-change).</span><span class="sxs-lookup"><span data-stu-id="5496d-133">For more information, see [binary breaking changes](./breaking-changes.md#binary-breaking-change).</span></span>

<span data-ttu-id="5496d-134">**❌ NEPODPORUJÍ** publikování silným názvem a jiných silným názvem verzí knihovny.</span><span class="sxs-lookup"><span data-stu-id="5496d-134">**❌ DO NOT** publish strong-named and non-strong-named versions of your library.</span></span> <span data-ttu-id="5496d-135">Například `Contoso.Api` a `Contoso.Api.StrongNamed`.</span><span class="sxs-lookup"><span data-stu-id="5496d-135">For example, `Contoso.Api` and `Contoso.Api.StrongNamed`.</span></span>

> <span data-ttu-id="5496d-136">Publikování větve dva balíčky vaše vývojářské ekosystému.</span><span class="sxs-lookup"><span data-stu-id="5496d-136">Publishing two packages forks your developer eco-system.</span></span> <span data-ttu-id="5496d-137">Také pokud aplikace končí v závislosti na oba balíčky vývojáři můžou mít typ název je v konfliktu.</span><span class="sxs-lookup"><span data-stu-id="5496d-137">Also, if an application ends up depending on both packages the developer can encounter type name conflicts.</span></span> <span data-ttu-id="5496d-138">Co se týče .NET jsou různé typy v různých sestaveních.</span><span class="sxs-lookup"><span data-stu-id="5496d-138">As far as .NET is concerned they are different types in different assemblies.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="5496d-139">[Předchozí](./cross-platform-targeting.md)
[další](./nuget.md)</span><span class="sxs-lookup"><span data-stu-id="5496d-139">[Previous](./cross-platform-targeting.md)
[Next](./nuget.md)</span></span>
