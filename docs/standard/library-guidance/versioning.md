---
title: Správa verzí a knihovny .NET
description: Doporučení osvědčených postupů pro správu verzí knihoven .NET.
ms.date: 12/10/2018
ms.openlocfilehash: ab15d56e40abedd842b681496b9e5ee737c8b1cd
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290120"
---
# <a name="versioning"></a><span data-ttu-id="e1dac-103">Správa verzí</span><span class="sxs-lookup"><span data-stu-id="e1dac-103">Versioning</span></span>

<span data-ttu-id="e1dac-104">Knihovna softwaru je ve verzi 1,0 jenom zřídka.</span><span class="sxs-lookup"><span data-stu-id="e1dac-104">A software library is rarely complete in version 1.0.</span></span> <span data-ttu-id="e1dac-105">Dobrá knihovna se vyvíjí v průběhu času, přidávání funkcí, opravy chyb a zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="e1dac-105">Good libraries evolve over time, adding features, fixing bugs, and improving performance.</span></span> <span data-ttu-id="e1dac-106">Je důležité, abyste si vyuvolnili nové verze knihovny .NET, která poskytuje další hodnotu s každou verzí bez přerušení stávajících uživatelů.</span><span class="sxs-lookup"><span data-stu-id="e1dac-106">It is important that you can release new versions of a .NET library, providing additional value with each version, without breaking existing users.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="e1dac-107">Změny způsobující chyby</span><span class="sxs-lookup"><span data-stu-id="e1dac-107">Breaking changes</span></span>

<span data-ttu-id="e1dac-108">Informace o zpracování nejnovějších změn mezi verzemi najdete v tématu [přerušující změny](./breaking-changes.md).</span><span class="sxs-lookup"><span data-stu-id="e1dac-108">For information about handling breaking changes between versions, see [Breaking changes](./breaking-changes.md).</span></span>

## <a name="version-numbers"></a><span data-ttu-id="e1dac-109">Čísla verzí</span><span class="sxs-lookup"><span data-stu-id="e1dac-109">Version numbers</span></span>

<span data-ttu-id="e1dac-110">Knihovna .NET má mnoho způsobů, jak určit verzi.</span><span class="sxs-lookup"><span data-stu-id="e1dac-110">A .NET library has many ways to specify a version.</span></span> <span data-ttu-id="e1dac-111">Nejdůležitější jsou tyto verze:</span><span class="sxs-lookup"><span data-stu-id="e1dac-111">These versions are the most important:</span></span>

### <a name="nuget-package-version"></a><span data-ttu-id="e1dac-112">Verze balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="e1dac-112">NuGet package version</span></span>

<span data-ttu-id="e1dac-113">[Verze balíčku NuGet](/nuget/reference/package-versioning) se zobrazuje v NuGet.org, správce balíčků NuGet sady Visual Studio a při použití balíčku se přidá do zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="e1dac-113">The [NuGet package version](/nuget/reference/package-versioning) is displayed on NuGet.org, the Visual Studio NuGet package manager, and is added to source code when the package is used.</span></span> <span data-ttu-id="e1dac-114">Verze balíčku NuGet je číslo verze, které se uživatelům obvykle uvidí a na něj budou odkazovat, když budou komunikovat s verzí knihovny, kterou používají.</span><span class="sxs-lookup"><span data-stu-id="e1dac-114">The NuGet package version is the version number users will commonly see, and they'll refer to it when they talk about the version of a library they're using.</span></span> <span data-ttu-id="e1dac-115">Verzi balíčku NuGet používá NuGet a nemá žádný vliv na chování za běhu.</span><span class="sxs-lookup"><span data-stu-id="e1dac-115">The NuGet package version is used by NuGet and has no effect on runtime behavior.</span></span>

```xml
<PackageVersion>1.0.0-alpha1</PackageVersion>
```

<span data-ttu-id="e1dac-116">Identifikátor balíčku NuGet v kombinaci s verzí balíčku NuGet se používá k identifikaci balíčku v NuGet.</span><span class="sxs-lookup"><span data-stu-id="e1dac-116">The NuGet package identifier combined with the NuGet package version is used to identify a package in NuGet.</span></span> <span data-ttu-id="e1dac-117">Příklad: `Newtonsoft.Json` + `11.0.2`.</span><span class="sxs-lookup"><span data-stu-id="e1dac-117">For example, `Newtonsoft.Json` + `11.0.2`.</span></span> <span data-ttu-id="e1dac-118">Balíček s příponou je předběžná verze balíčku a má speciální chování, které je ideální pro testování.</span><span class="sxs-lookup"><span data-stu-id="e1dac-118">A package with a suffix is a pre-release package and has special behavior that makes it ideal for testing.</span></span> <span data-ttu-id="e1dac-119">Další informace najdete v tématu [předběžné verze balíčků](./nuget.md#pre-release-packages).</span><span class="sxs-lookup"><span data-stu-id="e1dac-119">For more information, see [Pre-release packages](./nuget.md#pre-release-packages).</span></span>

<span data-ttu-id="e1dac-120">Vzhledem k tomu, že verze balíčku NuGet je nejvíce viditelná pro vývojáře, je vhodné ji aktualizovat pomocí [sémantického správy verzí (SemVer)](https://semver.org/).</span><span class="sxs-lookup"><span data-stu-id="e1dac-120">Because the NuGet package version is the most visible version to developers, it's a good idea to update it using [Semantic Versioning (SemVer)](https://semver.org/).</span></span> <span data-ttu-id="e1dac-121">SemVer označuje význam změn mezi vydanými verzemi a pomáhá vývojářům v rozhodování o tom, jaká verze se má použít.</span><span class="sxs-lookup"><span data-stu-id="e1dac-121">SemVer indicates the significance of changes between release and helps developers make an informed decision when choosing what version to use.</span></span> <span data-ttu-id="e1dac-122">Například v případě, `1.0` `2.0` že znamená, že existují potenciálně zásadní změny.</span><span class="sxs-lookup"><span data-stu-id="e1dac-122">For example, going from `1.0` to `2.0` indicates that there are potentially breaking changes.</span></span>

<span data-ttu-id="e1dac-123">✔️ Zvažte použití [2.0.0 SemVer](https://semver.org/) k verzi balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="e1dac-123">✔️ CONSIDER using [SemVer 2.0.0](https://semver.org/) to version your NuGet package.</span></span>

<span data-ttu-id="e1dac-124">✔️ použít verzi balíčku NuGet ve veřejné dokumentaci, protože se jedná o číslo verze, které se uživatelům běžně zobrazuje.</span><span class="sxs-lookup"><span data-stu-id="e1dac-124">✔️ DO use the NuGet package version in public documentation as it's the version number that users will commonly see.</span></span>

<span data-ttu-id="e1dac-125">při uvolňování nestabilního balíčku ✔️ zahrnout příponu předběžné verze.</span><span class="sxs-lookup"><span data-stu-id="e1dac-125">✔️ DO include a pre-release suffix when releasing a non-stable package.</span></span>

> <span data-ttu-id="e1dac-126">Uživatelé musí souhlasit s načtením předběžných balíčků, aby porozuměli tomu, že balíček není kompletní.</span><span class="sxs-lookup"><span data-stu-id="e1dac-126">Users must opt in to getting pre-release packages, so they will understand that the package is not complete.</span></span>

### <a name="assembly-version"></a><span data-ttu-id="e1dac-127">Verze sestavení</span><span class="sxs-lookup"><span data-stu-id="e1dac-127">Assembly version</span></span>

<span data-ttu-id="e1dac-128">Verze sestavení je to, co modul CLR používá v době běhu k výběru verze sestavení, které se má načíst.</span><span class="sxs-lookup"><span data-stu-id="e1dac-128">The assembly version is what the CLR uses at run time to select which version of an assembly to load.</span></span> <span data-ttu-id="e1dac-129">Výběr sestavení pomocí správy verzí se vztahuje pouze na sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="e1dac-129">Selecting an assembly using versioning only applies to assemblies with a strong name.</span></span>

```xml
<AssemblyVersion>1.0.0.0</AssemblyVersion>
```

<span data-ttu-id="e1dac-130">.NET Framework CLR požaduje přesnou shodu pro načtení sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="e1dac-130">The .NET Framework CLR demands an exact match to load a strong-named assembly.</span></span> <span data-ttu-id="e1dac-131">Například `Libary1, Version=1.0.0.0` byl zkompilován s odkazem na `Newtonsoft.Json, Version=11.0.0.0` .</span><span class="sxs-lookup"><span data-stu-id="e1dac-131">For example, `Libary1, Version=1.0.0.0` was compiled with a reference to `Newtonsoft.Json, Version=11.0.0.0`.</span></span> <span data-ttu-id="e1dac-132">.NET Framework načte jenom tuto přesnou verzi `11.0.0.0` .</span><span class="sxs-lookup"><span data-stu-id="e1dac-132">.NET Framework will only load that exact version `11.0.0.0`.</span></span> <span data-ttu-id="e1dac-133">Pro načtení jiné verze v době běhu musí být přesměrování vazby přidáno do konfiguračního souboru aplikace .NET.</span><span class="sxs-lookup"><span data-stu-id="e1dac-133">To load a different version at run time, a binding redirect must be added to the .NET application's config file.</span></span>

<span data-ttu-id="e1dac-134">Silné pojmenování v kombinaci s verzí sestavení umožňuje [striktní načítání verzí sestavení](../assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="e1dac-134">Strong naming combined with assembly version enables [strict assembly version loading](../assembly/versioning.md).</span></span> <span data-ttu-id="e1dac-135">I když silné pojmenování knihovny má několik výhod, často to vede k výjimkám za běhu, že sestavení se nenašlo a vyžaduje, aby se vytvořily [přesměrování vazby](../../framework/configure-apps/redirect-assembly-versions.md) `app.config` nebo `web.config` aby se opravilo.</span><span class="sxs-lookup"><span data-stu-id="e1dac-135">While strong naming a library has a number of benefits, it often results in run-time exceptions that an assembly can't be found and [requires binding redirects](../../framework/configure-apps/redirect-assembly-versions.md) in `app.config` or `web.config` to be fixed.</span></span> <span data-ttu-id="e1dac-136">V rozhraní .NET Core je načítání sestavení více uvolněno.</span><span class="sxs-lookup"><span data-stu-id="e1dac-136">In .NET Core, assembly loading is more relaxed.</span></span> <span data-ttu-id="e1dac-137">Modul runtime .NET Core automaticky načítá sestavení s vyšší verzí v době běhu.</span><span class="sxs-lookup"><span data-stu-id="e1dac-137">The .NET Core runtime automatically loads assemblies with a higher version at run time.</span></span>

<span data-ttu-id="e1dac-138">✔️ Zvažte pouze hlavní verzi v AssemblyVersion.</span><span class="sxs-lookup"><span data-stu-id="e1dac-138">✔️ CONSIDER only including a major version in the AssemblyVersion.</span></span>

> <span data-ttu-id="e1dac-139">například knihovna 1,0 a 1.0.1 knihovny mají AssemblyVersion `1.0.0.0` , zatímco knihovna 2,0 obsahuje AssemblyVersion `2.0.0.0` .</span><span class="sxs-lookup"><span data-stu-id="e1dac-139">e.g. Library 1.0 and Library 1.0.1 both have an AssemblyVersion of `1.0.0.0`, while Library 2.0 has AssemblyVersion of `2.0.0.0`.</span></span> <span data-ttu-id="e1dac-140">Pokud se verze sestavení nemění méně často, snižuje se přesměrování vazby.</span><span class="sxs-lookup"><span data-stu-id="e1dac-140">When the assembly version changes less often, it reduces binding redirects.</span></span>

<span data-ttu-id="e1dac-141">✔️ Zvažte zachování hlavního čísla verze AssemblyVersion a verze balíčku NuGet v synchronizaci.</span><span class="sxs-lookup"><span data-stu-id="e1dac-141">✔️ CONSIDER keeping the major version number of the AssemblyVersion and the NuGet package version in sync.</span></span>

> <span data-ttu-id="e1dac-142">AssemblyVersion je součástí některých informačních zpráv zobrazených uživateli, například název sestavení a kvalifikované typy názvů sestavení ve zprávách o výjimkách.</span><span class="sxs-lookup"><span data-stu-id="e1dac-142">The AssemblyVersion is included in some informational messages displayed to the user, e.g. the assembly name and assembly qualified type names in exception messages.</span></span> <span data-ttu-id="e1dac-143">Udržování vztahu mezi verzemi poskytuje další informace pro vývojáře, kteří používají verzi.</span><span class="sxs-lookup"><span data-stu-id="e1dac-143">Maintaining a relationship between the versions provides more information to developers about which version they are using.</span></span>

<span data-ttu-id="e1dac-144">❌Nepoužívejte pevný AssemblyVersion.</span><span class="sxs-lookup"><span data-stu-id="e1dac-144">❌ DO NOT have a fixed AssemblyVersion.</span></span>

> <span data-ttu-id="e1dac-145">I když nezměněný AssemblyVersion vybrání nutnosti přesměrování vazby, znamená to, že v globální mezipaměti sestavení (GAC) může být nainstalována pouze jedna verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="e1dac-145">While an unchanging AssemblyVersion avoids the need for binding redirects, it means that only a single version of the assembly can be installed in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="e1dac-146">Aplikace, které odkazují na sestavení v globální mezipaměti sestavení (GAC), budou také přerušit, pokud jiná aplikace aktualizuje sestavení GAC s nezměněnými změnami.</span><span class="sxs-lookup"><span data-stu-id="e1dac-146">Also, the applications that reference the assembly in the GAC will break if another application updates the GAC assembly with breaking changes.</span></span>

### <a name="assembly-file-version"></a><span data-ttu-id="e1dac-147">Verze souboru sestavení</span><span class="sxs-lookup"><span data-stu-id="e1dac-147">Assembly file version</span></span>

<span data-ttu-id="e1dac-148">Verze souboru sestavení se používá k zobrazení verze souboru ve Windows a nemá žádný vliv na chování za běhu.</span><span class="sxs-lookup"><span data-stu-id="e1dac-148">The assembly file version is used to display a file version in Windows and has no effect on run-time behavior.</span></span> <span data-ttu-id="e1dac-149">Nastavení této verze je volitelné.</span><span class="sxs-lookup"><span data-stu-id="e1dac-149">Setting this version is optional.</span></span> <span data-ttu-id="e1dac-150">Zobrazuje se v dialogovém okně Vlastnosti souboru v Průzkumníkovi Windows:</span><span class="sxs-lookup"><span data-stu-id="e1dac-150">It's visible in the File Properties dialog in Windows Explorer:</span></span>

```xml
<FileVersion>11.0.2.21924</FileVersion>
```

<span data-ttu-id="e1dac-151">![Průzkumník Windows](./media/versioning/win-properties.png "Průzkumník Windows")</span><span class="sxs-lookup"><span data-stu-id="e1dac-151">![Windows Explorer](./media/versioning/win-properties.png "Windows Explorer")</span></span>

<span data-ttu-id="e1dac-152">✔️ Zvažte zahrnutí čísla sestavení průběžné integrace jako revize AssemblyFileVersion.</span><span class="sxs-lookup"><span data-stu-id="e1dac-152">✔️ CONSIDER including a continuous integration build number as the AssemblyFileVersion revision.</span></span>

> <span data-ttu-id="e1dac-153">Například sestavíte 1.0.0 verze projektu a číslo sestavení průběžné integrace je 99, takže vaše AssemblyFileVersion je 1.0.0.99.</span><span class="sxs-lookup"><span data-stu-id="e1dac-153">For example, you are building version 1.0.0 of your project, and the continuous integration build number is 99 so your AssemblyFileVersion is 1.0.0.99.</span></span>

<span data-ttu-id="e1dac-154">✔️ použít formát `Major.Minor.Build.Revision` pro verzi souboru.</span><span class="sxs-lookup"><span data-stu-id="e1dac-154">✔️ DO use the format `Major.Minor.Build.Revision` for file version.</span></span>

> <span data-ttu-id="e1dac-155">I když verze souboru není rozhraním .NET nikdy používána, [systém Windows očekává, že verze souboru](/windows/desktop/menurc/versioninfo-resource) je ve `Major.Minor.Build.Revision` formátu.</span><span class="sxs-lookup"><span data-stu-id="e1dac-155">While the file version is never used by .NET, [Windows expects the file version](/windows/desktop/menurc/versioninfo-resource) to be in the `Major.Minor.Build.Revision` format.</span></span> <span data-ttu-id="e1dac-156">Pokud verze nedodržuje tento formát, bude vyvolána výstraha.</span><span class="sxs-lookup"><span data-stu-id="e1dac-156">A warning is raised if the version doesn't follow this format.</span></span>

### <a name="assembly-informational-version"></a><span data-ttu-id="e1dac-157">Informační verze sestavení</span><span class="sxs-lookup"><span data-stu-id="e1dac-157">Assembly informational version</span></span>

<span data-ttu-id="e1dac-158">Informační verze sestavení se používá k záznamu dalších informací o verzi a nemá žádný vliv na chování za běhu.</span><span class="sxs-lookup"><span data-stu-id="e1dac-158">The assembly informational version is used to record additional version information and has no effect on runtime behavior.</span></span> <span data-ttu-id="e1dac-159">Nastavení této verze je volitelné.</span><span class="sxs-lookup"><span data-stu-id="e1dac-159">Setting this version is optional.</span></span> <span data-ttu-id="e1dac-160">Pokud používáte zdrojový odkaz, bude tato verze nastavena pro sestavení s verzí balíčku NuGet a verzí správy zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="e1dac-160">If you're using Source Link, this version will be set on build with the NuGet package version plus a source control version.</span></span> <span data-ttu-id="e1dac-161">Například `1.0.0-beta1+204ff0a` obsahuje hodnotu hash potvrzení zdrojového kódu, ze kterého bylo sestavení sestaveno.</span><span class="sxs-lookup"><span data-stu-id="e1dac-161">For example, `1.0.0-beta1+204ff0a` includes the commit hash of the source code the assembly was built from.</span></span> <span data-ttu-id="e1dac-162">Další informace najdete v tématu [zdrojový odkaz](./sourcelink.md).</span><span class="sxs-lookup"><span data-stu-id="e1dac-162">For more information, see [Source Link](./sourcelink.md).</span></span>

```xml
<AssemblyInformationalVersion>The quick brown fox jumped over the lazy dog.</AssemblyInformationalVersion>
```

> [!NOTE]
> <span data-ttu-id="e1dac-163">Starší verze sady Visual Studio vyvolají upozornění sestavení, pokud tato verze nedodržuje formát `Major.Minor.Build.Revision` .</span><span class="sxs-lookup"><span data-stu-id="e1dac-163">Older versions of Visual Studio raise a build warning if this version doesn't follow the format `Major.Minor.Build.Revision`.</span></span> <span data-ttu-id="e1dac-164">Upozornění lze bezpečně ignorovat.</span><span class="sxs-lookup"><span data-stu-id="e1dac-164">The warning can be safely ignored.</span></span>

<span data-ttu-id="e1dac-165">❌Vyhněte se nastavení informační verze sestavení sami.</span><span class="sxs-lookup"><span data-stu-id="e1dac-165">❌ AVOID setting the assembly informational version yourself.</span></span>

> <span data-ttu-id="e1dac-166">Povolí, aby SourceLink automaticky vygenerovala verzi, která obsahuje metadata nástroje NuGet a správy zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="e1dac-166">Allow SourceLink to automatically generate the version containing NuGet and source control metadata.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e1dac-167">[Předchozí](publish-nuget-package.md) 
> [Další](breaking-changes.md)</span><span class="sxs-lookup"><span data-stu-id="e1dac-167">[Previous](publish-nuget-package.md)
[Next](breaking-changes.md)</span></span>
