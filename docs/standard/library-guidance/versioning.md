---
title: Správa verzí a knihovny .NET
description: Doporučení osvědčených postupů pro správu verzí knihoven .NET.
ms.date: 12/10/2018
ms.openlocfilehash: a274410714791e2790da0e3deb2a595390ee9389
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400398"
---
# <a name="versioning"></a><span data-ttu-id="5b97a-103">Správa verzí</span><span class="sxs-lookup"><span data-stu-id="5b97a-103">Versioning</span></span>

<span data-ttu-id="5b97a-104">Softwarová knihovna je zřídka dokončena ve verzi 1.0.</span><span class="sxs-lookup"><span data-stu-id="5b97a-104">A software library is rarely complete in version 1.0.</span></span> <span data-ttu-id="5b97a-105">Dobré knihovny se v průběhu času vyvíjejí, přidávají funkce, opravují chyby a zlepšují výkon.</span><span class="sxs-lookup"><span data-stu-id="5b97a-105">Good libraries evolve over time, adding features, fixing bugs and improving performance.</span></span> <span data-ttu-id="5b97a-106">Je důležité, abyste uvolnili nové verze knihovny .NET, které poskytují další hodnotu s každou verzí, aniž by došlo k porušení stávajících uživatelů.</span><span class="sxs-lookup"><span data-stu-id="5b97a-106">It is important that you can release new versions of a .NET library, providing additional value with each version, without breaking existing users.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="5b97a-107">Změny způsobující chyby</span><span class="sxs-lookup"><span data-stu-id="5b97a-107">Breaking changes</span></span>

<span data-ttu-id="5b97a-108">Informace o zpracování narušujících změn mezi verzemi naleznete v tématu [Breaking changes](./breaking-changes.md).</span><span class="sxs-lookup"><span data-stu-id="5b97a-108">For information about handling breaking changes between versions, see [Breaking changes](./breaking-changes.md).</span></span>

## <a name="version-numbers"></a><span data-ttu-id="5b97a-109">Čísla verzí</span><span class="sxs-lookup"><span data-stu-id="5b97a-109">Version numbers</span></span>

<span data-ttu-id="5b97a-110">Knihovna .NET má mnoho způsobů, jak určit verzi.</span><span class="sxs-lookup"><span data-stu-id="5b97a-110">A .NET library has many ways to specify a version.</span></span> <span data-ttu-id="5b97a-111">Tyto verze jsou nejdůležitější:</span><span class="sxs-lookup"><span data-stu-id="5b97a-111">These versions are the most important:</span></span>

### <a name="nuget-package-version"></a><span data-ttu-id="5b97a-112">Verze balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="5b97a-112">NuGet package version</span></span>

<span data-ttu-id="5b97a-113">[Verze balíčku NuGet](/nuget/reference/package-versioning) se zobrazí na NuGet.org, Visual Studio NuGet správce balíčků a je přidán do zdrojového kódu při použití balíčku.</span><span class="sxs-lookup"><span data-stu-id="5b97a-113">The [NuGet package version](/nuget/reference/package-versioning) is displayed on NuGet.org, the Visual Studio NuGet package manager, and is added to source code when the package is used.</span></span> <span data-ttu-id="5b97a-114">Verze balíčku NuGet je číslo verze, které uživatelé běžně uvidí, a budou na něj odkazovat, když mluví o verzi knihovny, kterou používají.</span><span class="sxs-lookup"><span data-stu-id="5b97a-114">The NuGet package version is the version number users will commonly see, and they'll refer to it when they talk about the version of a library they're using.</span></span> <span data-ttu-id="5b97a-115">Verze balíčku NuGet se používá NuGet a nemá žádný vliv na chování za běhu.</span><span class="sxs-lookup"><span data-stu-id="5b97a-115">The NuGet package version is used by NuGet and has no effect on runtime behavior.</span></span>

```xml
<PackageVersion>1.0.0-alpha1</PackageVersion>
```

<span data-ttu-id="5b97a-116">Identifikátor balíčku NuGet v kombinaci s verzí balíčku NuGet se používá k identifikaci balíčku v NuGet.</span><span class="sxs-lookup"><span data-stu-id="5b97a-116">The NuGet package identifier combined with the NuGet package version is used to identify a package in NuGet.</span></span> <span data-ttu-id="5b97a-117">Příklad: `Newtonsoft.Json` + `11.0.2`.</span><span class="sxs-lookup"><span data-stu-id="5b97a-117">For example, `Newtonsoft.Json` + `11.0.2`.</span></span> <span data-ttu-id="5b97a-118">Balíček s příponou je předběžný balíček a má speciální chování, které je ideální pro testování.</span><span class="sxs-lookup"><span data-stu-id="5b97a-118">A package with a suffix is a pre-release package and has special behavior that makes it ideal for testing.</span></span> <span data-ttu-id="5b97a-119">Další informace naleznete [v tématu Předběžné verze balíčků](./nuget.md#pre-release-packages).</span><span class="sxs-lookup"><span data-stu-id="5b97a-119">For more information, see [Pre-release packages](./nuget.md#pre-release-packages).</span></span>

<span data-ttu-id="5b97a-120">Vzhledem k tomu, že verze balíčku NuGet je nejviditelnější verze pro vývojáře, je vhodné ji aktualizovat pomocí [sémantické versioning (SemVer)](https://semver.org/).</span><span class="sxs-lookup"><span data-stu-id="5b97a-120">Because the NuGet package version is the most visible version to developers, it's a good idea to update it using [Semantic Versioning (SemVer)](https://semver.org/).</span></span> <span data-ttu-id="5b97a-121">SemVer označuje význam změn mezi vydáním a pomáhá vývojářům učinit informované rozhodnutí při výběru, jakou verzi použít.</span><span class="sxs-lookup"><span data-stu-id="5b97a-121">SemVer indicates the significance of changes between release and helps developers make an informed decision when choosing what version to use.</span></span> <span data-ttu-id="5b97a-122">Například přejdete `1.0` `2.0` od k označuje, že potenciálně narušují změny.</span><span class="sxs-lookup"><span data-stu-id="5b97a-122">For example, going from `1.0` to `2.0` indicates that there are potentially breaking changes.</span></span>

<span data-ttu-id="5b97a-123">✔️ zvažte použití [SemVer 2.0.0](https://semver.org/) k verzi balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="5b97a-123">✔️ CONSIDER using [SemVer 2.0.0](https://semver.org/) to version your NuGet package.</span></span>

<span data-ttu-id="5b97a-124">✔️ do použít balíček NuGet verze ve veřejné dokumentaci, protože je to číslo verze, které uživatelé budou běžně vidět.</span><span class="sxs-lookup"><span data-stu-id="5b97a-124">✔️ DO use the NuGet package version in public documentation as it's the version number that users will commonly see.</span></span>

<span data-ttu-id="5b97a-125">✔️ DO zahrnují předběžnou příponu při uvolnění nestabilního balíčku.</span><span class="sxs-lookup"><span data-stu-id="5b97a-125">✔️ DO include a pre-release suffix when releasing a non-stable package.</span></span>

> <span data-ttu-id="5b97a-126">Uživatelé se musí přihlásit k získání předběžných balíčků, aby pochopili, že balíček není dokončen.</span><span class="sxs-lookup"><span data-stu-id="5b97a-126">Users must opt in to getting pre-release packages, so they will understand that the package is not complete.</span></span>

### <a name="assembly-version"></a><span data-ttu-id="5b97a-127">Verze sestavení</span><span class="sxs-lookup"><span data-stu-id="5b97a-127">Assembly version</span></span>

<span data-ttu-id="5b97a-128">Verze sestavení je to, co CLR používá za běhu k výběru verze sestavení, které chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="5b97a-128">The assembly version is what the CLR uses at runtime to select which version of an assembly to load.</span></span> <span data-ttu-id="5b97a-129">Výběr sestavení pomocí správy verzí platí pouze pro sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="5b97a-129">Selecting an assembly using versioning only applies to assemblies with a strong name.</span></span>

```xml
<AssemblyVersion>1.0.0.0</AssemblyVersion>
```

<span data-ttu-id="5b97a-130">Rozhraní CLR rozhraní Windows .NET Framework vyžaduje přesnou shodu k načtení silného pojmenovanésestavení.</span><span class="sxs-lookup"><span data-stu-id="5b97a-130">The Windows .NET Framework CLR demands an exact match to load a strong named assembly.</span></span> <span data-ttu-id="5b97a-131">Například `Libary1, Version=1.0.0.0` byl zkompilován `Newtonsoft.Json, Version=11.0.0.0`s odkazem na .</span><span class="sxs-lookup"><span data-stu-id="5b97a-131">For example, `Libary1, Version=1.0.0.0` was compiled with a reference to `Newtonsoft.Json, Version=11.0.0.0`.</span></span> <span data-ttu-id="5b97a-132">Rozhraní .NET Framework načte `11.0.0.0`pouze tuto přesnou verzi .</span><span class="sxs-lookup"><span data-stu-id="5b97a-132">The .NET Framework will only load that exact version `11.0.0.0`.</span></span> <span data-ttu-id="5b97a-133">Chcete-li načíst jinou verzi za běhu, musí být do konfiguračního souboru aplikace .NET přidáno přesměrování vazby.</span><span class="sxs-lookup"><span data-stu-id="5b97a-133">To load a different version at runtime, a binding redirect must be added to the .NET application's config file.</span></span>

<span data-ttu-id="5b97a-134">Silné pojmenování v kombinaci s verzí sestavení umožňuje [přísné načítání verze sestavení](../assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="5b97a-134">Strong naming combined with assembly version enables [strict assembly version loading](../assembly/versioning.md).</span></span> <span data-ttu-id="5b97a-135">Zatímco silné pojmenování knihovny má řadu výhod, často vede k výjimkám za běhu, že sestavení `app.config` / `web.config` nelze najít a vyžaduje, aby byla [opravena přesměrování vazeb.](../../framework/configure-apps/redirect-assembly-versions.md)</span><span class="sxs-lookup"><span data-stu-id="5b97a-135">While strong naming a library has a number of benefits, it often results in runtime exceptions that an assembly can't be found and [requires binding redirects](../../framework/configure-apps/redirect-assembly-versions.md) in `app.config`/`web.config` to be fixed.</span></span> <span data-ttu-id="5b97a-136">Načítání sestavení .NET Core bylo uvolněno a clr jádra .NET bude automaticky načítat sestavení za běhu s vyšší verzí.</span><span class="sxs-lookup"><span data-stu-id="5b97a-136">.NET Core assembly loading has been relaxed, and the .NET Core CLR will automatically load assemblies at runtime with a higher version.</span></span>

<span data-ttu-id="5b97a-137">✔️ ZVÁŽIT pouze včetně hlavní verze v AssemblyVersion.</span><span class="sxs-lookup"><span data-stu-id="5b97a-137">✔️ CONSIDER only including a major version in the AssemblyVersion.</span></span>

> <span data-ttu-id="5b97a-138">například Knihovna 1.0 a Knihovna 1.0.1 `1.0.0.0`mají verzi AssemblyVersion of , `2.0.0.0`zatímco knihovna 2.0 má Version assemblyversion .</span><span class="sxs-lookup"><span data-stu-id="5b97a-138">e.g. Library 1.0 and Library 1.0.1 both have an AssemblyVersion of `1.0.0.0`, while Library 2.0 has AssemblyVersion of `2.0.0.0`.</span></span> <span data-ttu-id="5b97a-139">Když se verze sestavení mění méně často, snižuje přesměrování vazby.</span><span class="sxs-lookup"><span data-stu-id="5b97a-139">When the assembly version changes less often, it reduces binding redirects.</span></span>

<span data-ttu-id="5b97a-140">✔️ zvážit zachování hlavní číslo verze AssemblyVersion a NuGet verze balíčku v synchronizaci.</span><span class="sxs-lookup"><span data-stu-id="5b97a-140">✔️ CONSIDER keeping the major version number of the AssemblyVersion and the NuGet package version in sync.</span></span>

> <span data-ttu-id="5b97a-141">AssemblyVersion je součástí některých informačních zpráv zobrazených uživateli, například název sestavení a sestavení kvalifikované názvy typů ve zprávách výjimek.</span><span class="sxs-lookup"><span data-stu-id="5b97a-141">The AssemblyVersion is included in some informational messages displayed to the user, e.g. the assembly name and assembly qualified type names in exception messages.</span></span> <span data-ttu-id="5b97a-142">Udržování vztahu mezi verzemi poskytuje vývojářům další informace o tom, kterou verzi používají.</span><span class="sxs-lookup"><span data-stu-id="5b97a-142">Maintaining a relationship between the versions provides more information to developers about which version they are using.</span></span>

<span data-ttu-id="5b97a-143">❌Nemají pevnou AssemblyVersion.</span><span class="sxs-lookup"><span data-stu-id="5b97a-143">❌ DO NOT have a fixed AssemblyVersion.</span></span>

> <span data-ttu-id="5b97a-144">Zatímco neměnné AssemblyVersion vyhýbá nutnosti přesměrování vazby, znamená to, že pouze jednu verzi sestavení lze nainstalovat v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="5b97a-144">While an unchanging AssemblyVersion avoids the need for binding redirects, it means that only a single version of the assembly can be installed in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="5b97a-145">Také aplikace, které odkazují na sestavení v GAC se přeruší, pokud jiná aplikace aktualizuje sestavení GAC s nejnovější změny.</span><span class="sxs-lookup"><span data-stu-id="5b97a-145">Also, the applications that reference the assembly in the GAC will break if another application updates the GAC assembly with breaking changes.</span></span>

### <a name="assembly-file-version"></a><span data-ttu-id="5b97a-146">Verze souboru sestavení</span><span class="sxs-lookup"><span data-stu-id="5b97a-146">Assembly file version</span></span>

<span data-ttu-id="5b97a-147">Verze souboru sestavení se používá k zobrazení verze souboru v systému Windows a nemá žádný vliv na chování za běhu.</span><span class="sxs-lookup"><span data-stu-id="5b97a-147">The assembly file version is used to display a file version in Windows and has no effect on runtime behavior.</span></span> <span data-ttu-id="5b97a-148">Nastavení této verze je volitelné.</span><span class="sxs-lookup"><span data-stu-id="5b97a-148">Setting this version is optional.</span></span> <span data-ttu-id="5b97a-149">Je viditelná v dialogovém okně Vlastnosti souboru v Průzkumníkovi Windows:</span><span class="sxs-lookup"><span data-stu-id="5b97a-149">It's visible in the File Properties dialog in Windows Explorer:</span></span>

```xml
<FileVersion>11.0.2.21924</FileVersion>
```

<span data-ttu-id="5b97a-150">![Průzkumník Windows](./media/versioning/win-properties.png "Průzkumník Windows")</span><span class="sxs-lookup"><span data-stu-id="5b97a-150">![Windows Explorer](./media/versioning/win-properties.png "Windows Explorer")</span></span>

<span data-ttu-id="5b97a-151">✔️ ZVÁŽIT včetně průběžné integrace sestavení číslo jako revize AssemblyFileVersion.</span><span class="sxs-lookup"><span data-stu-id="5b97a-151">✔️ CONSIDER including a continuous integration build number as the AssemblyFileVersion revision.</span></span>

> <span data-ttu-id="5b97a-152">Například vytváříte verzi 1.0.0 projektu a číslo sestavení průběžné integrace je 99, takže vaše AssemblyFileVersion je 1.0.0.99.</span><span class="sxs-lookup"><span data-stu-id="5b97a-152">For example, you are building version 1.0.0 of your project, and the continuous integration build number is 99 so your AssemblyFileVersion is 1.0.0.99.</span></span>

<span data-ttu-id="5b97a-153">✔️ DO použít `Major.Minor.Build.Revision` formát pro verzi souboru.</span><span class="sxs-lookup"><span data-stu-id="5b97a-153">✔️ DO use the format `Major.Minor.Build.Revision` for file version.</span></span>

> <span data-ttu-id="5b97a-154">Zatímco verze souboru není nikdy používána rozhraním .NET, `Major.Minor.Build.Revision` systém Windows [očekává, že verze souboru](/windows/desktop/menurc/versioninfo-resource) bude ve formátu.</span><span class="sxs-lookup"><span data-stu-id="5b97a-154">While the file version is never used by .NET, [Windows expects the file version](/windows/desktop/menurc/versioninfo-resource) to be in the `Major.Minor.Build.Revision` format.</span></span> <span data-ttu-id="5b97a-155">Upozornění je aktivována, pokud verze nesleduje tento formát.</span><span class="sxs-lookup"><span data-stu-id="5b97a-155">A warning is raised if the version doesn't follow this format.</span></span>

### <a name="assembly-informational-version"></a><span data-ttu-id="5b97a-156">Informační verze sestavení</span><span class="sxs-lookup"><span data-stu-id="5b97a-156">Assembly informational version</span></span>

<span data-ttu-id="5b97a-157">Informační verze sestavení se používá k záznamu další informace o verzi a nemá žádný vliv na chování za běhu.</span><span class="sxs-lookup"><span data-stu-id="5b97a-157">The assembly informational version is used to record additional version information and has no effect on runtime behavior.</span></span> <span data-ttu-id="5b97a-158">Nastavení této verze je volitelné.</span><span class="sxs-lookup"><span data-stu-id="5b97a-158">Setting this version is optional.</span></span> <span data-ttu-id="5b97a-159">Pokud používáte zdrojový odkaz, tato verze bude nastavena na sestavení s verzí balíčku NuGet plus verze správy zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="5b97a-159">If you're using Source Link, this version will be set on build with the NuGet package version plus a source control version.</span></span> <span data-ttu-id="5b97a-160">Například `1.0.0-beta1+204ff0a` zahrnuje hash potvrzení zdrojového kódu, ze kterého bylo sestavení sestavení sestavení.</span><span class="sxs-lookup"><span data-stu-id="5b97a-160">For example, `1.0.0-beta1+204ff0a` includes the commit hash of the source code the assembly was built from.</span></span> <span data-ttu-id="5b97a-161">Další informace naleznete [v tématu Zdrojový odkaz](./sourcelink.md).</span><span class="sxs-lookup"><span data-stu-id="5b97a-161">For more information, see [Source Link](./sourcelink.md).</span></span>

```xml
<AssemblyInformationalVersion>The quick brown fox jumped over the lazy dog.</AssemblyInformationalVersion>
```

> [!NOTE]
> <span data-ttu-id="5b97a-162">Starší verze sady Visual Studio vyvolávají upozornění sestavení, pokud `Major.Minor.Build.Revision`tato verze nedodržuje formát .</span><span class="sxs-lookup"><span data-stu-id="5b97a-162">Older versions of Visual Studio raise a build warning if this version doesn't follow the format `Major.Minor.Build.Revision`.</span></span> <span data-ttu-id="5b97a-163">Upozornění lze bezpečně ignorovat.</span><span class="sxs-lookup"><span data-stu-id="5b97a-163">The warning can be safely ignored.</span></span>

<span data-ttu-id="5b97a-164">❌Vyhněte se nastavení informační verze sestavení sami.</span><span class="sxs-lookup"><span data-stu-id="5b97a-164">❌ AVOID setting the assembly informational version yourself.</span></span>

> <span data-ttu-id="5b97a-165">Povolit SourceLink automaticky generovat verzi obsahující NuGet a source control metadata.</span><span class="sxs-lookup"><span data-stu-id="5b97a-165">Allow SourceLink to automatically generate the version containing NuGet and source control metadata.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5b97a-166">[Předchozí](publish-nuget-package.md)
>[další](breaking-changes.md)</span><span class="sxs-lookup"><span data-stu-id="5b97a-166">[Previous](publish-nuget-package.md)
[Next](breaking-changes.md)</span></span>
