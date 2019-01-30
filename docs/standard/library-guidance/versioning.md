---
title: Knihovny správy verzí a .NET
description: Doporučené osvědčené postupy pro správu verzí knihovny .NET.
author: jamesnk
ms.author: mairaw
ms.date: 12/10/2018
ms.openlocfilehash: e6f811039f74649564cbfb42ef67e0a406e4cd70
ms.sourcegitcommit: e39d93d358974b9ed4541cedf4e25c0101015c3c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2019
ms.locfileid: "55204740"
---
# <a name="versioning"></a><span data-ttu-id="e7a19-103">Správa verzí</span><span class="sxs-lookup"><span data-stu-id="e7a19-103">Versioning</span></span>

<span data-ttu-id="e7a19-104">Softwarová knihovna je jen zřídka dokončena ve verzi 1.0.</span><span class="sxs-lookup"><span data-stu-id="e7a19-104">A software library is rarely complete in version 1.0.</span></span> <span data-ttu-id="e7a19-105">Dobré knihovny postupně měnit, přidává funkce, opravy chyb a zvýšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="e7a19-105">Good libraries evolve over time, adding features, fixing bugs and improving performance.</span></span> <span data-ttu-id="e7a19-106">Je důležité, že vydání nové verze knihovny .NET, zadání další hodnoty s jednotlivými verzemi, aniž by vás to stávající uživatele.</span><span class="sxs-lookup"><span data-stu-id="e7a19-106">It is important that you can release new versions of a .NET library, providing additional value with each version, without breaking existing users.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="e7a19-107">Změny způsobující chyby</span><span class="sxs-lookup"><span data-stu-id="e7a19-107">Breaking changes</span></span>

<span data-ttu-id="e7a19-108">Informace o zpracování zásadní změny mezi verzí najdete v tématu [Rozbíjející změny v](./breaking-changes.md).</span><span class="sxs-lookup"><span data-stu-id="e7a19-108">For information about handling breaking changes between versions, see [Breaking changes](./breaking-changes.md).</span></span>

## <a name="version-numbers"></a><span data-ttu-id="e7a19-109">Čísla verzí</span><span class="sxs-lookup"><span data-stu-id="e7a19-109">Version numbers</span></span>

<span data-ttu-id="e7a19-110">Knihovna .NET má mnoho způsobů, jak určit verzi.</span><span class="sxs-lookup"><span data-stu-id="e7a19-110">A .NET library has many ways to specify a version.</span></span> <span data-ttu-id="e7a19-111">Tyto verze jsou nejdůležitější:</span><span class="sxs-lookup"><span data-stu-id="e7a19-111">These versions are the most important:</span></span>

### <a name="nuget-package-version"></a><span data-ttu-id="e7a19-112">Verze balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="e7a19-112">NuGet package version</span></span>

<span data-ttu-id="e7a19-113">[Verze balíčku NuGet](/nuget/reference/package-versioning) se zobrazí na NuGet.org, Správce balíčků NuGet aplikace Visual Studio a že je přidaný do zdrojového kódu při použití balíčku.</span><span class="sxs-lookup"><span data-stu-id="e7a19-113">The [NuGet package version](/nuget/reference/package-versioning) is displayed on NuGet.org, the Visual Studio NuGet package manager, and is added to source code when the package is used.</span></span> <span data-ttu-id="e7a19-114">Verze balíčku NuGet je běžně uvidí uživatelé. číslo verze a budete si ji po hovoří o verzi knihovny, které jste používali.</span><span class="sxs-lookup"><span data-stu-id="e7a19-114">The NuGet package version is the version number users will commonly see, and they'll refer to it when they talk about the version of a library they're using.</span></span> <span data-ttu-id="e7a19-115">Verze balíčku NuGet používá NuGet a nemá žádný vliv na chování modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="e7a19-115">The NuGet package version is used by NuGet and has no effect on runtime behavior.</span></span>

```xml
<PackageVersion>1.0.0-alpha1</PackageVersion>
```

<span data-ttu-id="e7a19-116">Identifikátor balíčku NuGet, v kombinaci s verzí balíčku NuGet se používá k identifikaci balíčku nuget.</span><span class="sxs-lookup"><span data-stu-id="e7a19-116">The NuGet package identifier combined with the NuGet package version is used to identify a package in NuGet.</span></span> <span data-ttu-id="e7a19-117">Například `Newtonsoft.Json`  +  `11.0.2`.</span><span class="sxs-lookup"><span data-stu-id="e7a19-117">For example, `Newtonsoft.Json` + `11.0.2`.</span></span> <span data-ttu-id="e7a19-118">Balíček s příponu předběžné verze balíčků a má zvláštní chování, které je ideální pro testování.</span><span class="sxs-lookup"><span data-stu-id="e7a19-118">A package with a suffix is a pre-release package and has special behavior that makes it ideal for testing.</span></span> <span data-ttu-id="e7a19-119">Další informace najdete v tématu [balíčky v předběžné verzi](./nuget.md#pre-release-packages).</span><span class="sxs-lookup"><span data-stu-id="e7a19-119">For more information, see [Pre-release packages](./nuget.md#pre-release-packages).</span></span>

<span data-ttu-id="e7a19-120">Protože verze balíčku NuGet je nejviditelnější verze pro vývojáře, je vhodné jej aktualizovat pomocí [Semantic Versioning (SemVer)](https://semver.org/).</span><span class="sxs-lookup"><span data-stu-id="e7a19-120">Because the NuGet package version is the most visible version to developers, it's a good idea to update it using [Semantic Versioning (SemVer)](https://semver.org/).</span></span> <span data-ttu-id="e7a19-121">SemVer určuje význam změny mezi vydání a pomáhá vývojářům provést informované rozhodnutí při výběru jaké verze se má použít.</span><span class="sxs-lookup"><span data-stu-id="e7a19-121">SemVer indicates the significance of changes between release and helps developers make an informed decision when choosing what version to use.</span></span> <span data-ttu-id="e7a19-122">Například, že přejdete z `1.0` k `2.0` označuje, že můžou být dostupné nejnovější změny.</span><span class="sxs-lookup"><span data-stu-id="e7a19-122">For example, going from `1.0` to `2.0` indicates that there are potentially breaking changes.</span></span>

<span data-ttu-id="e7a19-123">**✔️ ZVAŽTE** pomocí [SemVer 2.0.0](https://semver.org/) verzi balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="e7a19-123">**✔️ CONSIDER** using [SemVer 2.0.0](https://semver.org/) to version your NuGet package.</span></span>

<span data-ttu-id="e7a19-124">**PROVEĎTE ✔️** použití verze balíčku NuGet ve veřejné dokumentaci, jako je číslo verze, který uživatelé uvidí běžně.</span><span class="sxs-lookup"><span data-stu-id="e7a19-124">**✔️ DO** use the NuGet package version in public documentation as it's the version number that users will commonly see.</span></span>

<span data-ttu-id="e7a19-125">**PROVEĎTE ✔️** obsahovat příponu předběžné verze při uvolnění-stabilní verze balíčku.</span><span class="sxs-lookup"><span data-stu-id="e7a19-125">**✔️ DO** include a pre-release suffix when releasing a non-stable package.</span></span>

> <span data-ttu-id="e7a19-126">Uživatelé musí přihlásit se k získání balíčky v předběžné verzi, abyste pochopili, že balíček není úplný.</span><span class="sxs-lookup"><span data-stu-id="e7a19-126">Users must opt in to getting pre-release packages, so they will understand that the package is not complete.</span></span>

### <a name="assembly-version"></a><span data-ttu-id="e7a19-127">Verze sestavení</span><span class="sxs-lookup"><span data-stu-id="e7a19-127">Assembly version</span></span>

<span data-ttu-id="e7a19-128">Verze sestavení je co používá modul CLR za běhu k výběru, kterou verzi sestavení, které chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="e7a19-128">The assembly version is what the CLR uses at runtime to select which version of an assembly to load.</span></span> <span data-ttu-id="e7a19-129">Výběr sestavení pomocí správy verzí pouze se vztahuje na sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="e7a19-129">Selecting an assembly using versioning only applies to assemblies with a strong name.</span></span>

```xml
<AssemblyVersion>1.0.0.0</AssemblyVersion>
```

<span data-ttu-id="e7a19-130">Windows .NET Framework CLR vyžaduje načtení silné přesnou shodou s názvem sestavení.</span><span class="sxs-lookup"><span data-stu-id="e7a19-130">The Windows .NET Framework CLR demands an exact match to load a strong named assembly.</span></span> <span data-ttu-id="e7a19-131">Například `Libary1, Version=1.0.0.0` byl kompilován s odkazem na `Newtonsoft.Json, Version=11.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="e7a19-131">For example, `Libary1, Version=1.0.0.0` was compiled with a reference to `Newtonsoft.Json, Version=11.0.0.0`.</span></span> <span data-ttu-id="e7a19-132">Rozhraní .NET Framework pouze načte tento přesnou verzi `11.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="e7a19-132">The .NET Framework will only load that exact version `11.0.0.0`.</span></span> <span data-ttu-id="e7a19-133">Načíst jinou verzi za běhu, musí přidat přesměrování vazby do konfiguračního souboru aplikace .NET.</span><span class="sxs-lookup"><span data-stu-id="e7a19-133">To load a different version at runtime, a binding redirect must be added to the .NET application's config file.</span></span>

<span data-ttu-id="e7a19-134">Silné názvy v kombinaci s verzí sestavení umožňuje [načtení verze striktní sestavení](../../framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="e7a19-134">Strong naming combined with assembly version enables [strict assembly version loading](../../framework/app-domains/assembly-versioning.md).</span></span> <span data-ttu-id="e7a19-135">Silné názvy knihovny obsahuje řadu výhod, často výsledkem výjimky modulu CLR, které nelze nalézt sestavení a [vyžaduje přesměrování vazeb](../../framework/configure-apps/redirect-assembly-versions.md) v `app.config` / `web.config` vyřešit.</span><span class="sxs-lookup"><span data-stu-id="e7a19-135">While strong naming a library has a number of benefits, it often results in runtime exceptions that an assembly can't be found and [requires binding redirects](../../framework/configure-apps/redirect-assembly-versions.md) in `app.config`/`web.config` to be fixed.</span></span> <span data-ttu-id="e7a19-136">Bylo volný načítání sestavení .NET core a .NET Core CLR bude automaticky načíst sestavení za běhu s vyšší verzí.</span><span class="sxs-lookup"><span data-stu-id="e7a19-136">.NET Core assembly loading has been relaxed, and the .NET Core CLR will automatically load assemblies at runtime with a higher version.</span></span>

<span data-ttu-id="e7a19-137">**✔️ ZVAŽTE** pouze AssemblyVersion včetně hlavní verze.</span><span class="sxs-lookup"><span data-stu-id="e7a19-137">**✔️ CONSIDER** only including a major version in the AssemblyVersion.</span></span>

> <span data-ttu-id="e7a19-138">například knihovna 1.0 a knihovny 1.0.1 obě mají AssemblyVersion z `1.0.0.0`, zatímco AssemblyVersion z knihovny 2.0 `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="e7a19-138">e.g. Library 1.0 and Library 1.0.1 both have an AssemblyVersion of `1.0.0.0`, while Library 2.0 has AssemblyVersion of `2.0.0.0`.</span></span> <span data-ttu-id="e7a19-139">Při změně verze sestavení méně často, snižuje přesměrování vazby.</span><span class="sxs-lookup"><span data-stu-id="e7a19-139">When the assembly version changes less often, it reduces binding redirects.</span></span>

<span data-ttu-id="e7a19-140">**✔️ ZVAŽTE** udržování synchronizace číslo hlavní verze AssemblyVersion a verze balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="e7a19-140">**✔️ CONSIDER** keeping the major version number of the AssemblyVersion and the NuGet package version in sync.</span></span>

> <span data-ttu-id="e7a19-141">AssemblyVersion je součástí některých informační zprávy zobrazí uživateli, například název sestavení a sestavení kvalifikované názvy typů v zprávy o výjimkách.</span><span class="sxs-lookup"><span data-stu-id="e7a19-141">The AssemblyVersion is included in some informational messages displayed to the user, e.g. the assembly name and assembly qualified type names in exception messages.</span></span> <span data-ttu-id="e7a19-142">Udržování vztahu mezi verzemi poskytuje další informace pro vývojáře o verzi, které využívají.</span><span class="sxs-lookup"><span data-stu-id="e7a19-142">Maintaining a relationship between the versions provides more information to developers about which version they are using.</span></span>

<span data-ttu-id="e7a19-143">**❌ NEPODPORUJÍ** mají pevnou AssemblyVersion.</span><span class="sxs-lookup"><span data-stu-id="e7a19-143">**❌ DO NOT** have a fixed AssemblyVersion.</span></span>

> <span data-ttu-id="e7a19-144">Zatímco neměnné AssemblyVersion se vyhnete nutnosti přesměrování vazby, znamená to, pouze jednu verzi sestavení lze nainstalovat v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="e7a19-144">While an unchanging AssemblyVersion avoids the need for binding redirects, it means that only a single version of the assembly can be installed in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="e7a19-145">Aplikace, které odkazují na toto sestavení v GAC také, přeruší, pokud jiná aplikace aktualizuje s rozbíjející změny v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="e7a19-145">Also, the applications that reference the assembly in the GAC will break if another application updates the GAC assembly with breaking changes.</span></span>

### <a name="assembly-file-version"></a><span data-ttu-id="e7a19-146">Verze souboru sestavení</span><span class="sxs-lookup"><span data-stu-id="e7a19-146">Assembly file version</span></span>

<span data-ttu-id="e7a19-147">Verze souboru sestavení se používá k zobrazení verze souboru ve Windows a nemá žádný vliv na chování modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="e7a19-147">The assembly file version is used to display a file version in Windows and has no effect on runtime behavior.</span></span> <span data-ttu-id="e7a19-148">Nastavení této verze je volitelný.</span><span class="sxs-lookup"><span data-stu-id="e7a19-148">Setting this version is optional.</span></span> <span data-ttu-id="e7a19-149">Je zobrazen v dialogovém okně vlastností souboru v Průzkumníku Windows:</span><span class="sxs-lookup"><span data-stu-id="e7a19-149">It's visible in the File Properties dialog in Windows Explorer:</span></span>

```xml
<FileVersion>11.0.2.21924</FileVersion>
```

<span data-ttu-id="e7a19-150">![Windows Explorer](./media/versioning/win-properties.png "Windows Explorer")</span><span class="sxs-lookup"><span data-stu-id="e7a19-150">![Windows Explorer](./media/versioning/win-properties.png "Windows Explorer")</span></span>

<span data-ttu-id="e7a19-151">**✔️ ZVAŽTE** číslo jako revize AssemblyFileVersion včetně kontinuální integrace sestavení.</span><span class="sxs-lookup"><span data-stu-id="e7a19-151">**✔️ CONSIDER** including a continuous integration build number as the AssemblyFileVersion revision.</span></span>

> <span data-ttu-id="e7a19-152">Například vytváříte verze 1.0.0 vašeho projektu a číslo sestavení kontinuální integrace je 99, takže vaše AssemblyFileVersion je 1.0.0.99.</span><span class="sxs-lookup"><span data-stu-id="e7a19-152">For example, you are building version 1.0.0 of your project, and the continuous integration build number is 99 so your AssemblyFileVersion is 1.0.0.99.</span></span>

<span data-ttu-id="e7a19-153">**PROVEĎTE ✔️** použijte formát `Major.Minor.Build.Revision` verze souboru.</span><span class="sxs-lookup"><span data-stu-id="e7a19-153">**✔️ DO** use the format `Major.Minor.Build.Revision` for file version.</span></span>

> <span data-ttu-id="e7a19-154">Zatímco pomocí .NET, nikdy použita verze souboru [Windows očekává, že verze souboru](/windows/desktop/menurc/versioninfo-resource) v `Major.Minor.Build.Revision` formátu.</span><span class="sxs-lookup"><span data-stu-id="e7a19-154">While the file version is never used by .NET, [Windows expects the file version](/windows/desktop/menurc/versioninfo-resource) to be in the `Major.Minor.Build.Revision` format.</span></span> <span data-ttu-id="e7a19-155">Upozornění je vyvolána, pokud verze nebude mít tento formát.</span><span class="sxs-lookup"><span data-stu-id="e7a19-155">A warning is raised if the version doesn't follow this format.</span></span>

### <a name="assembly-informational-version"></a><span data-ttu-id="e7a19-156">Informační verze sestavení</span><span class="sxs-lookup"><span data-stu-id="e7a19-156">Assembly informational version</span></span>

<span data-ttu-id="e7a19-157">Informační verze sestavení se používá k zaznamenání Další informace o verzi a nemá žádný vliv na chování modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="e7a19-157">The assembly informational version is used to record additional version information and has no effect on runtime behavior.</span></span> <span data-ttu-id="e7a19-158">Nastavení této verze je volitelný.</span><span class="sxs-lookup"><span data-stu-id="e7a19-158">Setting this version is optional.</span></span> <span data-ttu-id="e7a19-159">Pokud používáte odkazu na zdroj, tato verze se nastaví na sestavení se verze balíčku NuGet a verze ovládacího prvku zdroje.</span><span class="sxs-lookup"><span data-stu-id="e7a19-159">If you're using Source Link, this version will be set on build with the NuGet package version plus a source control version.</span></span> <span data-ttu-id="e7a19-160">Například `1.0.0-beta1+204ff0a` obsahuje hodnotu hash potvrzení sestavení byla vytvořena z zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="e7a19-160">For example, `1.0.0-beta1+204ff0a` includes the commit hash of the source code the assembly was built from.</span></span> <span data-ttu-id="e7a19-161">Další informace najdete v tématu [odkazu na zdroj](./sourcelink.md).</span><span class="sxs-lookup"><span data-stu-id="e7a19-161">For more information, see [Source Link](./sourcelink.md).</span></span>

```xml
<AssemblyInformationalVersion>The quick brown fox jumped over the lazy dog.</AssemblyInformationalVersion>
```

> [!NOTE]
> <span data-ttu-id="e7a19-162">Starší verze sady Visual Studio vyvolat upozornění sestavení, pokud tato verze není postupujte z formátu `Major.Minor.Build.Revision`.</span><span class="sxs-lookup"><span data-stu-id="e7a19-162">Older versions of Visual Studio raise a build warning if this version doesn't follow the format `Major.Minor.Build.Revision`.</span></span> <span data-ttu-id="e7a19-163">Upozornění můžete ignorovat.</span><span class="sxs-lookup"><span data-stu-id="e7a19-163">The warning can be safely ignored.</span></span>

<span data-ttu-id="e7a19-164">**❌ Nepoužívejte** nastavení informační verze sestavení sami.</span><span class="sxs-lookup"><span data-stu-id="e7a19-164">**❌ AVOID** setting the assembly informational version yourself.</span></span>

> <span data-ttu-id="e7a19-165">Povolte SourceLink automaticky generovat verze obsahuje NuGet a zdrojový ovládací prvek metadat.</span><span class="sxs-lookup"><span data-stu-id="e7a19-165">Allow SourceLink to automatically generate the version containing NuGet and source control metadata.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e7a19-166">[Předchozí](publish-nuget-package.md)
>[další](breaking-changes.md)</span><span class="sxs-lookup"><span data-stu-id="e7a19-166">[Previous](publish-nuget-package.md)
[Next](breaking-changes.md)</span></span>
