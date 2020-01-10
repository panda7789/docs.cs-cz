---
title: Správa verzí a knihovny .NET
description: Doporučení osvědčených postupů pro správu verzí knihoven .NET.
ms.date: 12/10/2018
ms.openlocfilehash: 8ed3217e39b1fe0f330a650ec72cda224866e207
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706410"
---
# <a name="versioning"></a><span data-ttu-id="f3304-103">Správa verzí</span><span class="sxs-lookup"><span data-stu-id="f3304-103">Versioning</span></span>

<span data-ttu-id="f3304-104">Knihovna softwaru je ve verzi 1,0 jenom zřídka.</span><span class="sxs-lookup"><span data-stu-id="f3304-104">A software library is rarely complete in version 1.0.</span></span> <span data-ttu-id="f3304-105">Dobrá knihovna se vyvíjí v průběhu času, přidávání funkcí, opravy chyb a zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="f3304-105">Good libraries evolve over time, adding features, fixing bugs and improving performance.</span></span> <span data-ttu-id="f3304-106">Je důležité, abyste si vyuvolnili nové verze knihovny .NET, která poskytuje další hodnotu s každou verzí bez přerušení stávajících uživatelů.</span><span class="sxs-lookup"><span data-stu-id="f3304-106">It is important that you can release new versions of a .NET library, providing additional value with each version, without breaking existing users.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="f3304-107">Změny způsobující chyby</span><span class="sxs-lookup"><span data-stu-id="f3304-107">Breaking changes</span></span>

<span data-ttu-id="f3304-108">Informace o zpracování nejnovějších změn mezi verzemi najdete v tématu [přerušující změny](./breaking-changes.md).</span><span class="sxs-lookup"><span data-stu-id="f3304-108">For information about handling breaking changes between versions, see [Breaking changes](./breaking-changes.md).</span></span>

## <a name="version-numbers"></a><span data-ttu-id="f3304-109">Čísla verzí</span><span class="sxs-lookup"><span data-stu-id="f3304-109">Version numbers</span></span>

<span data-ttu-id="f3304-110">Knihovna .NET má mnoho způsobů, jak určit verzi.</span><span class="sxs-lookup"><span data-stu-id="f3304-110">A .NET library has many ways to specify a version.</span></span> <span data-ttu-id="f3304-111">Nejdůležitější jsou tyto verze:</span><span class="sxs-lookup"><span data-stu-id="f3304-111">These versions are the most important:</span></span>

### <a name="nuget-package-version"></a><span data-ttu-id="f3304-112">Verze balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="f3304-112">NuGet package version</span></span>

<span data-ttu-id="f3304-113">[Verze balíčku NuGet](/nuget/reference/package-versioning) se zobrazuje v NuGet.org, správce balíčků NuGet sady Visual Studio a při použití balíčku se přidá do zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="f3304-113">The [NuGet package version](/nuget/reference/package-versioning) is displayed on NuGet.org, the Visual Studio NuGet package manager, and is added to source code when the package is used.</span></span> <span data-ttu-id="f3304-114">Verze balíčku NuGet je číslo verze, které se uživatelům obvykle uvidí a na něj budou odkazovat, když budou komunikovat s verzí knihovny, kterou používají.</span><span class="sxs-lookup"><span data-stu-id="f3304-114">The NuGet package version is the version number users will commonly see, and they'll refer to it when they talk about the version of a library they're using.</span></span> <span data-ttu-id="f3304-115">Verzi balíčku NuGet používá NuGet a nemá žádný vliv na chování za běhu.</span><span class="sxs-lookup"><span data-stu-id="f3304-115">The NuGet package version is used by NuGet and has no effect on runtime behavior.</span></span>

```xml
<PackageVersion>1.0.0-alpha1</PackageVersion>
```

<span data-ttu-id="f3304-116">Identifikátor balíčku NuGet v kombinaci s verzí balíčku NuGet se používá k identifikaci balíčku v NuGet.</span><span class="sxs-lookup"><span data-stu-id="f3304-116">The NuGet package identifier combined with the NuGet package version is used to identify a package in NuGet.</span></span> <span data-ttu-id="f3304-117">Příklad: `Newtonsoft.Json` + `11.0.2`.</span><span class="sxs-lookup"><span data-stu-id="f3304-117">For example, `Newtonsoft.Json` + `11.0.2`.</span></span> <span data-ttu-id="f3304-118">Balíček s příponou je předběžná verze balíčku a má speciální chování, které je ideální pro testování.</span><span class="sxs-lookup"><span data-stu-id="f3304-118">A package with a suffix is a pre-release package and has special behavior that makes it ideal for testing.</span></span> <span data-ttu-id="f3304-119">Další informace najdete v tématu [předběžné verze balíčků](./nuget.md#pre-release-packages).</span><span class="sxs-lookup"><span data-stu-id="f3304-119">For more information, see [Pre-release packages](./nuget.md#pre-release-packages).</span></span>

<span data-ttu-id="f3304-120">Vzhledem k tomu, že verze balíčku NuGet je nejvíce viditelná pro vývojáře, je vhodné ji aktualizovat pomocí [sémantického správy verzí (SemVer)](https://semver.org/).</span><span class="sxs-lookup"><span data-stu-id="f3304-120">Because the NuGet package version is the most visible version to developers, it's a good idea to update it using [Semantic Versioning (SemVer)](https://semver.org/).</span></span> <span data-ttu-id="f3304-121">SemVer označuje význam změn mezi vydanými verzemi a pomáhá vývojářům v rozhodování o tom, jaká verze se má použít.</span><span class="sxs-lookup"><span data-stu-id="f3304-121">SemVer indicates the significance of changes between release and helps developers make an informed decision when choosing what version to use.</span></span> <span data-ttu-id="f3304-122">Například z `1.0` na `2.0` znamená, že existují potenciálně zásadní změny.</span><span class="sxs-lookup"><span data-stu-id="f3304-122">For example, going from `1.0` to `2.0` indicates that there are potentially breaking changes.</span></span>

<span data-ttu-id="f3304-123">**✔️ zvažte** použití [2.0.0 SemVer](https://semver.org/) k verzi balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="f3304-123">**✔️ CONSIDER** using [SemVer 2.0.0](https://semver.org/) to version your NuGet package.</span></span>

<span data-ttu-id="f3304-124">**✔️** použít verzi balíčku NuGet ve veřejné dokumentaci, protože se jedná o číslo verze, které se uživatelům běžně zobrazuje.</span><span class="sxs-lookup"><span data-stu-id="f3304-124">**✔️ DO** use the NuGet package version in public documentation as it's the version number that users will commonly see.</span></span>

<span data-ttu-id="f3304-125">při uvolňování nestabilního balíčku **✔️** zahrnout příponu předběžné verze.</span><span class="sxs-lookup"><span data-stu-id="f3304-125">**✔️ DO** include a pre-release suffix when releasing a non-stable package.</span></span>

> <span data-ttu-id="f3304-126">Uživatelé musí souhlasit s načtením předběžných balíčků, aby porozuměli tomu, že balíček není kompletní.</span><span class="sxs-lookup"><span data-stu-id="f3304-126">Users must opt in to getting pre-release packages, so they will understand that the package is not complete.</span></span>

### <a name="assembly-version"></a><span data-ttu-id="f3304-127">Verze sestavení</span><span class="sxs-lookup"><span data-stu-id="f3304-127">Assembly version</span></span>

<span data-ttu-id="f3304-128">Verze sestavení je to, co modul CLR používá za běhu k výběru verze sestavení, které se má načíst.</span><span class="sxs-lookup"><span data-stu-id="f3304-128">The assembly version is what the CLR uses at runtime to select which version of an assembly to load.</span></span> <span data-ttu-id="f3304-129">Výběr sestavení pomocí správy verzí se vztahuje pouze na sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="f3304-129">Selecting an assembly using versioning only applies to assemblies with a strong name.</span></span>

```xml
<AssemblyVersion>1.0.0.0</AssemblyVersion>
```

<span data-ttu-id="f3304-130">Windows .NET Framework CLR požaduje přesnou shodu pro načtení silného pojmenovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="f3304-130">The Windows .NET Framework CLR demands an exact match to load a strong named assembly.</span></span> <span data-ttu-id="f3304-131">Například `Libary1, Version=1.0.0.0` byla zkompilována s odkazem na `Newtonsoft.Json, Version=11.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="f3304-131">For example, `Libary1, Version=1.0.0.0` was compiled with a reference to `Newtonsoft.Json, Version=11.0.0.0`.</span></span> <span data-ttu-id="f3304-132">.NET Framework načte jenom přesnou verzi `11.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="f3304-132">The .NET Framework will only load that exact version `11.0.0.0`.</span></span> <span data-ttu-id="f3304-133">Pro načtení jiné verze za běhu musí být přesměrování vazby přidáno do konfiguračního souboru aplikace .NET.</span><span class="sxs-lookup"><span data-stu-id="f3304-133">To load a different version at runtime, a binding redirect must be added to the .NET application's config file.</span></span>

<span data-ttu-id="f3304-134">Silné pojmenování v kombinaci s verzí sestavení umožňuje [striktní načítání verzí sestavení](../assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="f3304-134">Strong naming combined with assembly version enables [strict assembly version loading](../assembly/versioning.md).</span></span> <span data-ttu-id="f3304-135">I když silné pojmenování knihovny má několik výhod, často má za následek výjimku za běhu, kterou nelze najít, a [vyžaduje přesměrování vazby](../../framework/configure-apps/redirect-assembly-versions.md) v `app.config`/`web.config` k tomu, aby je bylo možné opravit.</span><span class="sxs-lookup"><span data-stu-id="f3304-135">While strong naming a library has a number of benefits, it often results in runtime exceptions that an assembly can't be found and [requires binding redirects](../../framework/configure-apps/redirect-assembly-versions.md) in `app.config`/`web.config` to be fixed.</span></span> <span data-ttu-id="f3304-136">Načítání sestavení .NET Core bylo uvolněno a modul CLR .NET Core bude automaticky načítat sestavení za běhu s vyšší verzí.</span><span class="sxs-lookup"><span data-stu-id="f3304-136">.NET Core assembly loading has been relaxed, and the .NET Core CLR will automatically load assemblies at runtime with a higher version.</span></span>

<span data-ttu-id="f3304-137">**✔️ zvažte** pouze hlavní verzi v AssemblyVersion.</span><span class="sxs-lookup"><span data-stu-id="f3304-137">**✔️ CONSIDER** only including a major version in the AssemblyVersion.</span></span>

> <span data-ttu-id="f3304-138">například knihovna 1,0 a 1.0.1 knihovny mají AssemblyVersion `1.0.0.0`, zatímco knihovna 2,0 obsahuje AssemblyVersion `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="f3304-138">e.g. Library 1.0 and Library 1.0.1 both have an AssemblyVersion of `1.0.0.0`, while Library 2.0 has AssemblyVersion of `2.0.0.0`.</span></span> <span data-ttu-id="f3304-139">Pokud se verze sestavení nemění méně často, snižuje se přesměrování vazby.</span><span class="sxs-lookup"><span data-stu-id="f3304-139">When the assembly version changes less often, it reduces binding redirects.</span></span>

<span data-ttu-id="f3304-140">**✔️ zvažte** zachování hlavního čísla verze AssemblyVersion a verze balíčku NuGet v synchronizaci.</span><span class="sxs-lookup"><span data-stu-id="f3304-140">**✔️ CONSIDER** keeping the major version number of the AssemblyVersion and the NuGet package version in sync.</span></span>

> <span data-ttu-id="f3304-141">AssemblyVersion je součástí některých informačních zpráv zobrazených uživateli, například název sestavení a kvalifikované typy názvů sestavení ve zprávách o výjimkách.</span><span class="sxs-lookup"><span data-stu-id="f3304-141">The AssemblyVersion is included in some informational messages displayed to the user, e.g. the assembly name and assembly qualified type names in exception messages.</span></span> <span data-ttu-id="f3304-142">Udržování vztahu mezi verzemi poskytuje další informace pro vývojáře, kteří používají verzi.</span><span class="sxs-lookup"><span data-stu-id="f3304-142">Maintaining a relationship between the versions provides more information to developers about which version they are using.</span></span>

<span data-ttu-id="f3304-143">**❌** nemají pevně AssemblyVersion.</span><span class="sxs-lookup"><span data-stu-id="f3304-143">**❌ DO NOT** have a fixed AssemblyVersion.</span></span>

> <span data-ttu-id="f3304-144">I když nezměněný AssemblyVersion vybrání nutnosti přesměrování vazby, znamená to, že v globální mezipaměti sestavení (GAC) může být nainstalována pouze jedna verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="f3304-144">While an unchanging AssemblyVersion avoids the need for binding redirects, it means that only a single version of the assembly can be installed in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="f3304-145">Aplikace, které odkazují na sestavení v globální mezipaměti sestavení (GAC), budou také přerušit, pokud jiná aplikace aktualizuje sestavení GAC s nezměněnými změnami.</span><span class="sxs-lookup"><span data-stu-id="f3304-145">Also, the applications that reference the assembly in the GAC will break if another application updates the GAC assembly with breaking changes.</span></span>

### <a name="assembly-file-version"></a><span data-ttu-id="f3304-146">Verze souboru sestavení</span><span class="sxs-lookup"><span data-stu-id="f3304-146">Assembly file version</span></span>

<span data-ttu-id="f3304-147">Verze souboru sestavení se používá k zobrazení verze souboru ve Windows a nemá žádný vliv na chování za běhu.</span><span class="sxs-lookup"><span data-stu-id="f3304-147">The assembly file version is used to display a file version in Windows and has no effect on runtime behavior.</span></span> <span data-ttu-id="f3304-148">Nastavení této verze je volitelné.</span><span class="sxs-lookup"><span data-stu-id="f3304-148">Setting this version is optional.</span></span> <span data-ttu-id="f3304-149">Zobrazuje se v dialogovém okně Vlastnosti souboru v Průzkumníkovi Windows:</span><span class="sxs-lookup"><span data-stu-id="f3304-149">It's visible in the File Properties dialog in Windows Explorer:</span></span>

```xml
<FileVersion>11.0.2.21924</FileVersion>
```

<span data-ttu-id="f3304-150">![Průzkumník Windows](./media/versioning/win-properties.png "Průzkumník Windows")</span><span class="sxs-lookup"><span data-stu-id="f3304-150">![Windows Explorer](./media/versioning/win-properties.png "Windows Explorer")</span></span>

<span data-ttu-id="f3304-151">**✔️ zvažte** zahrnutí čísla sestavení průběžné integrace jako revize AssemblyFileVersion.</span><span class="sxs-lookup"><span data-stu-id="f3304-151">**✔️ CONSIDER** including a continuous integration build number as the AssemblyFileVersion revision.</span></span>

> <span data-ttu-id="f3304-152">Například sestavíte 1.0.0 verze projektu a číslo sestavení průběžné integrace je 99, takže vaše AssemblyFileVersion je 1.0.0.99.</span><span class="sxs-lookup"><span data-stu-id="f3304-152">For example, you are building version 1.0.0 of your project, and the continuous integration build number is 99 so your AssemblyFileVersion is 1.0.0.99.</span></span>

<span data-ttu-id="f3304-153">pro verzi souboru **✔️** použít formát `Major.Minor.Build.Revision`.</span><span class="sxs-lookup"><span data-stu-id="f3304-153">**✔️ DO** use the format `Major.Minor.Build.Revision` for file version.</span></span>

> <span data-ttu-id="f3304-154">I když verze souboru není rozhraním .NET nikdy používána, [systém Windows očekává, že verze souboru](/windows/desktop/menurc/versioninfo-resource) je ve formátu `Major.Minor.Build.Revision`.</span><span class="sxs-lookup"><span data-stu-id="f3304-154">While the file version is never used by .NET, [Windows expects the file version](/windows/desktop/menurc/versioninfo-resource) to be in the `Major.Minor.Build.Revision` format.</span></span> <span data-ttu-id="f3304-155">Pokud verze nedodržuje tento formát, bude vyvolána výstraha.</span><span class="sxs-lookup"><span data-stu-id="f3304-155">A warning is raised if the version doesn't follow this format.</span></span>

### <a name="assembly-informational-version"></a><span data-ttu-id="f3304-156">Informační verze sestavení</span><span class="sxs-lookup"><span data-stu-id="f3304-156">Assembly informational version</span></span>

<span data-ttu-id="f3304-157">Informační verze sestavení se používá k záznamu dalších informací o verzi a nemá žádný vliv na chování za běhu.</span><span class="sxs-lookup"><span data-stu-id="f3304-157">The assembly informational version is used to record additional version information and has no effect on runtime behavior.</span></span> <span data-ttu-id="f3304-158">Nastavení této verze je volitelné.</span><span class="sxs-lookup"><span data-stu-id="f3304-158">Setting this version is optional.</span></span> <span data-ttu-id="f3304-159">Pokud používáte zdrojový odkaz, bude tato verze nastavena pro sestavení s verzí balíčku NuGet a verzí správy zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="f3304-159">If you're using Source Link, this version will be set on build with the NuGet package version plus a source control version.</span></span> <span data-ttu-id="f3304-160">Například `1.0.0-beta1+204ff0a` obsahuje hodnotu hash potvrzení zdrojového kódu, ze kterého bylo sestavení sestaveno.</span><span class="sxs-lookup"><span data-stu-id="f3304-160">For example, `1.0.0-beta1+204ff0a` includes the commit hash of the source code the assembly was built from.</span></span> <span data-ttu-id="f3304-161">Další informace najdete v tématu [zdrojový odkaz](./sourcelink.md).</span><span class="sxs-lookup"><span data-stu-id="f3304-161">For more information, see [Source Link](./sourcelink.md).</span></span>

```xml
<AssemblyInformationalVersion>The quick brown fox jumped over the lazy dog.</AssemblyInformationalVersion>
```

> [!NOTE]
> <span data-ttu-id="f3304-162">Starší verze sady Visual Studio vyvolají upozornění sestavení, pokud tato verze nedodržuje formát `Major.Minor.Build.Revision`.</span><span class="sxs-lookup"><span data-stu-id="f3304-162">Older versions of Visual Studio raise a build warning if this version doesn't follow the format `Major.Minor.Build.Revision`.</span></span> <span data-ttu-id="f3304-163">Upozornění lze bezpečně ignorovat.</span><span class="sxs-lookup"><span data-stu-id="f3304-163">The warning can be safely ignored.</span></span>

<span data-ttu-id="f3304-164">**❌ se vyhnout** nastavení informační verze sestavení sami.</span><span class="sxs-lookup"><span data-stu-id="f3304-164">**❌ AVOID** setting the assembly informational version yourself.</span></span>

> <span data-ttu-id="f3304-165">Povolí, aby SourceLink automaticky vygenerovala verzi, která obsahuje metadata nástroje NuGet a správy zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="f3304-165">Allow SourceLink to automatically generate the version containing NuGet and source control metadata.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f3304-166">[Předchozí](publish-nuget-package.md)
>[Další](breaking-changes.md)</span><span class="sxs-lookup"><span data-stu-id="f3304-166">[Previous](publish-nuget-package.md)
[Next](breaking-changes.md)</span></span>
