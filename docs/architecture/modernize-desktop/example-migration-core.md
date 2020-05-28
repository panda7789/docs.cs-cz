---
title: Příklad migrace na .NET Core 3.1
description: Ukazuje, jak migrovat ukázkové aplikace, které cílí na .NET Framework .NET Core 3,1.
ms.date: 05/12/2020
ms.openlocfilehash: 5e8b1219cf4bd89ada5b71a60ef27eaabb94997c
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144268"
---
# <a name="example-of-migrating-to-net-core-31"></a><span data-ttu-id="95346-103">Příklad migrace na .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="95346-103">Example of migrating to .NET Core 3.1</span></span>

<span data-ttu-id="95346-104">V této kapitole máme praktické pokyny, které vám pomohou s migrací vaší stávající aplikace z .NET Framework do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="95346-104">In this chapter, we present practical guidelines to help you perform a migration of your existing application from .NET Framework to .NET Core.</span></span>

<span data-ttu-id="95346-105">Máme dobře strukturovaný proces, který můžete dodržovat, a nejdůležitější věci, které je potřeba vzít v úvahu pro každý krok.</span><span class="sxs-lookup"><span data-stu-id="95346-105">We present a well-structured process you can follow and the most important things to consider on each step.</span></span>

<span data-ttu-id="95346-106">Pak povedeme podrobný postup migrace pro ukázkovou desktopovou aplikaci, od verze WinForms a WPF.</span><span class="sxs-lookup"><span data-stu-id="95346-106">We then document a step-by-step migration process for a sample desktop application, both from WinForms and WPF versions.</span></span>

## <a name="migration-process-overview"></a><span data-ttu-id="95346-107">Přehled procesu migrace</span><span class="sxs-lookup"><span data-stu-id="95346-107">Migration process overview</span></span>

<span data-ttu-id="95346-108">Proces migrace se skládá ze čtyř sekvenčních kroků:</span><span class="sxs-lookup"><span data-stu-id="95346-108">The migration process consists of four sequential steps:</span></span>

1. <span data-ttu-id="95346-109">**Příprava**: Seznámení se závislostmi, které projekt musí mít představu o tom, co je předem.</span><span class="sxs-lookup"><span data-stu-id="95346-109">**Preparation**: Understand the dependencies the project has to have an idea of what's ahead.</span></span> <span data-ttu-id="95346-110">V tomto kroku převezmete aktuální projekt do stavu, který zjednodušuje spouštěcí bod migrace.</span><span class="sxs-lookup"><span data-stu-id="95346-110">In this step, you take the current project into a state that simplifies the startup point for the migration.</span></span>

2. <span data-ttu-id="95346-111">**Migrace souboru projektu:** projekty .NET Core používají nový formát projektu ve stylu sady SDK.</span><span class="sxs-lookup"><span data-stu-id="95346-111">**Migrate Project File:** .NET Core projects use the new SDK-style project format.</span></span> <span data-ttu-id="95346-112">Vytvořte nový soubor projektu s tímto formátem, nebo aktualizujte ten, který budete muset použít ve stylu sady SDK.</span><span class="sxs-lookup"><span data-stu-id="95346-112">Create a new project file with this format or update the one you have to use the SDK style.</span></span>

3. <span data-ttu-id="95346-113">**Opravit kód a sestavit:** Sestavte kód v části .NET Core Addressing – rozdíly na úrovni rozhraní API mezi .NET Framework a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="95346-113">**Fix code and build:** Build the code in .NET Core addressing API-level differences between .NET Framework and .NET Core.</span></span> <span data-ttu-id="95346-114">V případě potřeby aktualizujte balíčky třetích stran na ty, které podporují .NET Core.</span><span class="sxs-lookup"><span data-stu-id="95346-114">If needed, update third-party packages to the ones that support .NET Core.</span></span>

4. <span data-ttu-id="95346-115">**Spustit a otestovat:** Mohou existovat rozdíly, které se nezobrazí až do doby běhu.</span><span class="sxs-lookup"><span data-stu-id="95346-115">**Run and test:** There might be differences that don't show up until run time.</span></span> <span data-ttu-id="95346-116">Nezapomeňte ale aplikaci spustit a otestovat, jestli všechno funguje podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="95346-116">So, don't forget to run the application and test that everything works as expected.</span></span>

### <a name="preparation"></a><span data-ttu-id="95346-117">Příprava</span><span class="sxs-lookup"><span data-stu-id="95346-117">Preparation</span></span>

#### <a name="migrate-packagesconfig-file"></a><span data-ttu-id="95346-118">Migrovat soubor Packages. config</span><span class="sxs-lookup"><span data-stu-id="95346-118">Migrate packages.config file</span></span>

<span data-ttu-id="95346-119">V aplikaci .NET Framework jsou všechny odkazy na externí balíčky deklarovány v souboru *Packages. config* .</span><span class="sxs-lookup"><span data-stu-id="95346-119">In a .NET Framework application, all references to external packages are declared in the *packages.config* file.</span></span> <span data-ttu-id="95346-120">V rozhraní .NET Core již není nutné používat soubor *Packages. config* .</span><span class="sxs-lookup"><span data-stu-id="95346-120">In .NET Core, there's no longer the need to use the *packages.config* file.</span></span> <span data-ttu-id="95346-121">Místo toho použijte vlastnost [PackageReference](../../core/project-sdk/msbuild-props.md#packagereference) v souboru projektu k určení balíčků NuGet pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="95346-121">Instead, use the [PackageReference](../../core/project-sdk/msbuild-props.md#packagereference) property inside the project file to specify the NuGet packages for your app.</span></span>

<span data-ttu-id="95346-122">Takže je potřeba přejít z jednoho formátu do druhého.</span><span class="sxs-lookup"><span data-stu-id="95346-122">So, you need to transition from one format to another.</span></span> <span data-ttu-id="95346-123">Aktualizaci můžete provést ručně a přebírat závislosti obsažené v souboru *Packages. config* a migrovat je do souboru projektu ve `PackageReference` formátu.</span><span class="sxs-lookup"><span data-stu-id="95346-123">You can do the update manually, taking the dependencies contained in the *packages.config* file and migrating them to the project file with the `PackageReference` format.</span></span> <span data-ttu-id="95346-124">Nebo můžete nechat aplikaci Visual Studio pracovat za vás: klikněte pravým tlačítkem na soubor *Packages. config* a vyberte možnost **migrovat balíčky. config na PackageReference** .</span><span class="sxs-lookup"><span data-stu-id="95346-124">Or, you can let Visual Studio do the work for you: right-click on the *packages.config* file and select the **Migrate packages.config to PackageReference** option.</span></span>

#### <a name="verify-every-dependency-compatibility-in-net-core"></a><span data-ttu-id="95346-125">Ověřit všechny kompatibility závislostí v .NET Core</span><span class="sxs-lookup"><span data-stu-id="95346-125">Verify every dependency compatibility in .NET Core</span></span>

<span data-ttu-id="95346-126">Po dokončení migrace odkazů na balíčky je nutné ověřit všechny reference z hlediska kompatibility.</span><span class="sxs-lookup"><span data-stu-id="95346-126">Once you've migrated the package references, you must check each reference for compatibility.</span></span> <span data-ttu-id="95346-127">Můžete prozkoumat závislosti jednotlivých balíčků NuGet, které vaše aplikace používá v [NuGet.org](https://www.nuget.org/). Pokud balíček obsahuje .NET Standard závislosti, pak bude fungovat na .NET Core, protože .NET Core 3,1 [podporuje](../../standard/net-standard.md#net-implementation-support) všechny verze .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="95346-127">You can explore the dependencies of each NuGet package your application is using on [nuget.org](https://www.nuget.org/). If the package has .NET Standard dependencies, then it's going to work on .NET Core because .NET Core 3.1 [supports](../../standard/net-standard.md#net-implementation-support) all versions of .NET Standard.</span></span> <span data-ttu-id="95346-128">Následující obrázek ukazuje závislosti `Castle.Windsor` balíčku:</span><span class="sxs-lookup"><span data-stu-id="95346-128">The following image shows the dependencies for the `Castle.Windsor` package:</span></span>

![Snímek obrazovky se závislostmi NuGet pro balíček Castle. Windsor](./media/example-migration-core/nuget-dependencies.png)

<span data-ttu-id="95346-130">Chcete-li ověřit kompatibilitu balíčku, můžete použít nástroj <https://fuget.org> , který nabízí podrobnější informace o verzích a závislostech.</span><span class="sxs-lookup"><span data-stu-id="95346-130">To check the package compatibility, you can use the tool <https://fuget.org> that offers a more detailed information about versions and dependencies.</span></span>

<span data-ttu-id="95346-131">Projekt je pravděpodobně odkazován na starší verze balíčků, které nepodporují .NET Core, ale můžete najít novější verze, které ji podporují.</span><span class="sxs-lookup"><span data-stu-id="95346-131">Maybe the project is referencing older package versions that don't support .NET Core, but you might find newer versions that do support it.</span></span> <span data-ttu-id="95346-132">Aktualizace balíčků do novějších verzí proto obecně představuje dobrou doporučení.</span><span class="sxs-lookup"><span data-stu-id="95346-132">So, updating packages to newer versions is generally a good recommendation.</span></span> <span data-ttu-id="95346-133">Měli byste však vzít v úvahu, že aktualizace verze balíčku může vést k nějakým změnám, které by vynutily aktualizaci kódu.</span><span class="sxs-lookup"><span data-stu-id="95346-133">However, you should consider that updating the package version can introduce some breaking changes that would force you to update your code.</span></span>

<span data-ttu-id="95346-134">Co se stane, když nenajdete kompatibilní verzi?</span><span class="sxs-lookup"><span data-stu-id="95346-134">What happens if you don't find a compatible version?</span></span> <span data-ttu-id="95346-135">Co když ale nechcete aktualizovat verzi balíčku z důvodu těchto nejnovějších změn?</span><span class="sxs-lookup"><span data-stu-id="95346-135">What if you just don't want to update the version of a package because of these breaking changes?</span></span> <span data-ttu-id="95346-136">Nedělejte si starosti, protože je možné záviset na .NET Framework balíčky z aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="95346-136">Don't worry because it's possible to depend on .NET Framework packages from a .NET Core application.</span></span> <span data-ttu-id="95346-137">Nezapomeňte ho testovat v rozsáhlých případech, protože může způsobit chyby za běhu, pokud externí balíček volá rozhraní API, které není k dispozici v rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="95346-137">Don't forget to test it extensively because it can cause run-time errors if the external package calls an API that isn't available on .NET Core.</span></span> <span data-ttu-id="95346-138">To je skvělé, když používáte starý balíček, který se nebude aktualizovat, a vy můžete změnit cílení na práci v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="95346-138">This is great for when you're using an old package that isn't going to be updated and you can just retarget to work on the .NET Core.</span></span>

#### <a name="check-for-api-compatibility"></a><span data-ttu-id="95346-139">Ověřit kompatibilitu rozhraní API</span><span class="sxs-lookup"><span data-stu-id="95346-139">Check for API compatibility</span></span>

<span data-ttu-id="95346-140">Vzhledem k tomu, že je plocha rozhraní API v .NET Framework a .NET Core podobná, ale není identická, musíte ověřit, která rozhraní API jsou k dispozici v rozhraní .NET Core a nikoli.</span><span class="sxs-lookup"><span data-stu-id="95346-140">Since the API surface in .NET Framework and .NET Core is similar but not identical, you must check which APIs are available on .NET Core and which aren't.</span></span> <span data-ttu-id="95346-141">Nástroj Analyzátor přenositelnosti .NET můžete použít k Surface používaných rozhraní API, která nejsou přítomna v rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="95346-141">You can use the .NET Portability Analyzer tool to surface APIs used that aren't present on .NET Core.</span></span> <span data-ttu-id="95346-142">Vypadá na binární úrovni vaší aplikace, extrahuje všechna rozhraní API, která jsou volána, a pak zobrazí seznam rozhraní API, která nejsou k dispozici v cílové verzi rozhraní (v tomto případě .NET Core 3,1).</span><span class="sxs-lookup"><span data-stu-id="95346-142">It looks at the binary level of your app, extracts all the APIs that are called, and then lists which APIs aren't available on your target framework (.NET Core 3.1 in this case).</span></span>

<span data-ttu-id="95346-143">Další informace o tomto nástroji najdete na adrese:</span><span class="sxs-lookup"><span data-stu-id="95346-143">You can find more information about this tool at:</span></span>

<https://docs.microsoft.com/dotnet/standard/analyzers/portability-analyzer>

<span data-ttu-id="95346-144">Zajímavým aspektem tohoto nástroje je, že pouze rozsvítí rozdíly z vlastního kódu a nikoli z externích balíčků, které nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="95346-144">An interesting aspect of this tool is that it only surfaces the differences from your own code and not code from external packages, which you can't change.</span></span> <span data-ttu-id="95346-145">Nezapomeňte, že byste měli aktualizovat většinu těchto balíčků, abyste je mohli pracovat s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="95346-145">Remember you should have updated most of these packages to make them work with .NET Core.</span></span>

### <a name="migrate-project-file"></a><span data-ttu-id="95346-146">Migrovat soubor projektu</span><span class="sxs-lookup"><span data-stu-id="95346-146">Migrate project file</span></span>

#### <a name="create-the-new-net-core-project"></a><span data-ttu-id="95346-147">Vytvoření nového projektu .NET Core</span><span class="sxs-lookup"><span data-stu-id="95346-147">Create the new .NET Core project</span></span>

<span data-ttu-id="95346-148">Ve většině případů budete chtít aktualizovat existující projekt na nový formát .NET Core.</span><span class="sxs-lookup"><span data-stu-id="95346-148">In most of the cases, you'll want to update your existing project to the new .NET Core format.</span></span> <span data-ttu-id="95346-149">Můžete ale také vytvořit nový projekt a zachovávat si ho starý.</span><span class="sxs-lookup"><span data-stu-id="95346-149">However, you can also create a new project while maintaining the old one.</span></span> <span data-ttu-id="95346-150">Hlavní nevýhodou aktualizace původního projektu je, že ztratíte podporu návrháře, což může být pro vás důležité.</span><span class="sxs-lookup"><span data-stu-id="95346-150">The main drawback from updating the old project is that you lose designer support, which may be important for you.</span></span> <span data-ttu-id="95346-151">Chcete-li pokračovat v používání návrháře, je nutné vytvořit nový projekt .NET Core paralelně se starým a sdílet prostředky.</span><span class="sxs-lookup"><span data-stu-id="95346-151">If you want to keep using the designer, you must create a new .NET Core project in parallel with the old one and share assets.</span></span> <span data-ttu-id="95346-152">Pokud potřebujete upravit prvky uživatelského rozhraní v návrháři, můžete k tomu přejít na původní projekt.</span><span class="sxs-lookup"><span data-stu-id="95346-152">If you need to modify UI elements in the designer, you can switch to the old project to do that.</span></span> <span data-ttu-id="95346-153">A vzhledem k tomu, že prostředky jsou propojeny, budou aktualizovány také v projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="95346-153">And since assets are linked, they'll be updated in the .NET Core project as well.</span></span>

<span data-ttu-id="95346-154">[Projekt ve stylu sady SDK](../../core/project-sdk/msbuild-props.md) pro .NET Core je mnohem jednodušší než formát projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="95346-154">The [SDK-style project](../../core/project-sdk/msbuild-props.md) for .NET Core is a lot simpler than .NET Framework's project format.</span></span> <span data-ttu-id="95346-155">Kromě výše uvedených `PackageReference` položek nemusíte dělat spoustu dalších věcí.</span><span class="sxs-lookup"><span data-stu-id="95346-155">And apart from the previously mentioned `PackageReference` entries, you won't need to do much more.</span></span> <span data-ttu-id="95346-156">Nový formát projektu zahrnuje určité přípony souborů [ve výchozím nastavení](../../core/tools/csproj.md#default-compilation-includes-in-net-core-projects), například `.cs` soubory a `.xaml` , aniž by bylo nutné je explicitně zahrnout do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="95346-156">The new project format includes certain file extensions [by default](../../core/tools/csproj.md#default-compilation-includes-in-net-core-projects), such as `.cs` and `.xaml` files, without the need to explicitly include them in the project file.</span></span>

#### <a name="assemblyinfo-considerations"></a><span data-ttu-id="95346-157">Assembly.info požadavky</span><span class="sxs-lookup"><span data-stu-id="95346-157">Assembly.info considerations</span></span>

<span data-ttu-id="95346-158">Atributy se generují automaticky v projektech .NET Core.</span><span class="sxs-lookup"><span data-stu-id="95346-158">Attributes are autogenerated on .NET Core projects.</span></span> <span data-ttu-id="95346-159">Pokud projekt obsahuje soubor *AssemblyInfo.cs* , definice budou duplikovány, což způsobí konflikty při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="95346-159">If the project contains an *AssemblyInfo.cs* file, the definitions will be duplicated, which will cause compilation conflicts.</span></span> <span data-ttu-id="95346-160">Můžete odstranit starší soubor *AssemblyInfo.cs* nebo zakázat Autogeneration přidáním následujícího záznamu do souboru projektu .NET Core:</span><span class="sxs-lookup"><span data-stu-id="95346-160">You can delete the older *AssemblyInfo.cs* file or disable autogeneration by adding the following entry to the .NET Core project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

#### <a name="resources"></a><span data-ttu-id="95346-161">Prostředky</span><span class="sxs-lookup"><span data-stu-id="95346-161">Resources</span></span>

<span data-ttu-id="95346-162">Integrované prostředky jsou zahrnuté automaticky, ale prostředky nejsou, takže je potřeba migrovat prostředky do nového souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="95346-162">Embedded resources are included automatically but resources aren't, so you need to migrate the resources to the new project file.</span></span>

#### <a name="package-references"></a><span data-ttu-id="95346-163">Odkazy na balíčky</span><span class="sxs-lookup"><span data-stu-id="95346-163">Package references</span></span>

<span data-ttu-id="95346-164">Pomocí možnosti **migrovat balíčky. config na PackageReference** můžete snadno přesunout odkazy na externí balíčky do nového formátu, jak je uvedeno výše.</span><span class="sxs-lookup"><span data-stu-id="95346-164">With the **Migrate packages.config to PackageReference** option, you can easily move your external package references to the new format as previously mentioned.</span></span>

#### <a name="update-package-references"></a><span data-ttu-id="95346-165">Aktualizovat odkazy na balíček</span><span class="sxs-lookup"><span data-stu-id="95346-165">Update package references</span></span>

<span data-ttu-id="95346-166">Aktualizujte verze balíčků, které byly zjištěny jako kompatibilní, jak je znázorněno v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="95346-166">Update the versions of the packages you've found to be compatible, as shown in the previous section.</span></span>

### <a name="fix-the-code-and-build"></a><span data-ttu-id="95346-167">Opravit kód a sestavit</span><span class="sxs-lookup"><span data-stu-id="95346-167">Fix the code and build</span></span>

#### <a name="microsoftwindowscompatibility"></a><span data-ttu-id="95346-168">Microsoft. Windows. Compatibility</span><span class="sxs-lookup"><span data-stu-id="95346-168">Microsoft.Windows.Compatibility</span></span>

<span data-ttu-id="95346-169">Pokud vaše aplikace závisí na rozhraních API, která nejsou k dispozici v rozhraní .NET Core, jako je například registr, seznamy ACL nebo WCF, musíte do `Microsoft.Windows.Compatibility` balíčku přidat odkaz na tyto rozhraní API specifická pro systém Windows.</span><span class="sxs-lookup"><span data-stu-id="95346-169">If your application depends on APIs that aren't available on .NET Core, such as Registry, ACLs, or WCF, you have to include a reference to the `Microsoft.Windows.Compatibility` package to add these Windows-specific APIs.</span></span> <span data-ttu-id="95346-170">Pracují v .NET Core, ale nejsou zahrnuté, protože nejsou součástí různých platforem.</span><span class="sxs-lookup"><span data-stu-id="95346-170">They work on .NET Core but aren't included as they aren't cross-platform.</span></span>

<span data-ttu-id="95346-171">K dispozici je nástroj, který se nazývá API Analyzer ( <https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer> ), který vám pomůže identifikovat rozhraní API, která nejsou kompatibilní s vaším kódem.</span><span class="sxs-lookup"><span data-stu-id="95346-171">There's a tool called API Analyzer (<https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer>) that helps you identify APIs that aren't compatible with your code.</span></span>

#### <a name="use-if-directives"></a><span data-ttu-id="95346-172">Použít \# direktivy if</span><span class="sxs-lookup"><span data-stu-id="95346-172">Use \#if directives</span></span>

<span data-ttu-id="95346-173">Pokud při .NET Framework a .NET Core potřebujete jiné cesty spuštění, měli byste použít konstanty kompilace.</span><span class="sxs-lookup"><span data-stu-id="95346-173">If you need different execution paths when targeting .NET Framework and .NET Core, you should use compilation constants.</span></span> <span data-ttu-id="95346-174">Přidejte některé \# direktivy IF do kódu pro zachování stejné základny kódu pro oba cíle.</span><span class="sxs-lookup"><span data-stu-id="95346-174">Add some \#if directives to your code to keep the same code base for both targets.</span></span>

#### <a name="technologies-not-available-on-net-core"></a><span data-ttu-id="95346-175">Technologie, které nejsou dostupné v .NET Core</span><span class="sxs-lookup"><span data-stu-id="95346-175">Technologies not available on .NET Core</span></span>

<span data-ttu-id="95346-176">Některé technologie nejsou k dispozici v rozhraní .NET Core, například:</span><span class="sxs-lookup"><span data-stu-id="95346-176">Some technologies aren't available on .NET Core, such as:</span></span>

* <span data-ttu-id="95346-177">Objektů třídy AppDomains</span><span class="sxs-lookup"><span data-stu-id="95346-177">AppDomains</span></span>
* <span data-ttu-id="95346-178">Vzdálenou</span><span class="sxs-lookup"><span data-stu-id="95346-178">Remoting</span></span>
* <span data-ttu-id="95346-179">Zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="95346-179">Code Access Security</span></span>
* <span data-ttu-id="95346-180">Server WCF</span><span class="sxs-lookup"><span data-stu-id="95346-180">WCF Server</span></span>
* <span data-ttu-id="95346-181">Pracovní postup Windows</span><span class="sxs-lookup"><span data-stu-id="95346-181">Windows Workflow</span></span>

<span data-ttu-id="95346-182">To je důvod, proč potřebujete najít náhradu za tyto technologie, pokud je používáte ve své aplikaci.</span><span class="sxs-lookup"><span data-stu-id="95346-182">That's why you need to find a replacement for these technologies if you're using them in your application.</span></span> <span data-ttu-id="95346-183">Další informace najdete v článku [věnovaném technologii .NET Framework nedostupné v rozhraní .NET Core](../../core/porting/net-framework-tech-unavailable.md) .</span><span class="sxs-lookup"><span data-stu-id="95346-183">For more information, see the [.NET Framework technologies unavailable on .NET Core](../../core/porting/net-framework-tech-unavailable.md) article.</span></span>

#### <a name="regenerate-autogenerated-clients"></a><span data-ttu-id="95346-184">Znovu vygenerovat automaticky generované klienty</span><span class="sxs-lookup"><span data-stu-id="95346-184">Regenerate autogenerated clients</span></span>

<span data-ttu-id="95346-185">Pokud vaše aplikace používá automaticky generovaný kód, jako je například klient WCF, bude pravděpodobně nutné znovu vygenerovat tento kód pro cílový .NET Core.</span><span class="sxs-lookup"><span data-stu-id="95346-185">If your application uses autogenerated code, such as a WCF client, you may need to regenerate this code to target .NET Core.</span></span> <span data-ttu-id="95346-186">Někdy můžete najít některé chybějící odkazy, protože nemusí být zahrnuty jako součást výchozích sad sestavení .NET Core.</span><span class="sxs-lookup"><span data-stu-id="95346-186">Sometimes, you can find some missing references since they may not be included as part of the default .NET Core assemblies set.</span></span> <span data-ttu-id="95346-187">Pomocí nástroje, jako <https://apisof.net/> je, můžete snadno najít sestavení chybějící odkaz v a přidat ho z NuGet.</span><span class="sxs-lookup"><span data-stu-id="95346-187">Using a tool like <https://apisof.net/>, you can easily locate the assembly the missing reference lives in and add it from NuGet.</span></span>

#### <a name="rolling-back-package-versions"></a><span data-ttu-id="95346-188">Vracení verzí balíčku zpět</span><span class="sxs-lookup"><span data-stu-id="95346-188">Rolling back package versions</span></span>

<span data-ttu-id="95346-189">Jako obecné pravidlo jsme dřív uvedli, že byste měli lépe aktualizovat všechny verze jednoho balíčku tak, aby byly kompatibilní s .NET Core.</span><span class="sxs-lookup"><span data-stu-id="95346-189">As a general rule, we've previously stated that you better update every single package version to be compatible with .NET Core.</span></span> <span data-ttu-id="95346-190">Můžete ale najít, že cílení na aktualizovanou a kompatibilní verzi sestavení pouze neplatí.</span><span class="sxs-lookup"><span data-stu-id="95346-190">However, you can find that targeting an updated and compatible version of an assembly just doesn't pay off.</span></span> <span data-ttu-id="95346-191">Pokud náklady na změnu nejsou přijatelné, můžete uvažovat o vracení verzí balíčků, které budou používat .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="95346-191">If the cost of change isn't acceptable, you can consider rolling back package versions keeping the ones you use on .NET Framework.</span></span> <span data-ttu-id="95346-192">I když nemusí být cíleny na rozhraní .NET Core, měly by fungovat dobře, pokud nevolají některá nepodporovaná rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="95346-192">Although they may not be targeting .NET Core, they should work well unless they call some unsupported APIs.</span></span>

### <a name="run-and-test"></a><span data-ttu-id="95346-193">Spuštění a testování</span><span class="sxs-lookup"><span data-stu-id="95346-193">Run and test</span></span>

<span data-ttu-id="95346-194">Po sestavení vaší aplikace bez chyb můžete spustit poslední krok migrace otestováním všech funkcí.</span><span class="sxs-lookup"><span data-stu-id="95346-194">Once you have your application building with no errors, you can start the last step of the migration by testing every functionality.</span></span>

<span data-ttu-id="95346-195">V tomto posledním kroku můžete najít několik různých problémů v závislosti na složitosti vaší aplikace a závislostech a rozhraních API, které používáte.</span><span class="sxs-lookup"><span data-stu-id="95346-195">In this final step, you can find several different issues depending on the complexity of your application and the dependencies and APIs you're using.</span></span>

<span data-ttu-id="95346-196">Pokud například použijete konfigurační soubory (*App. config*), může dojít k chybám v době běhu, jako jsou konfigurační oddíly, které nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="95346-196">For example, if you use configuration files (*app.config*), you may find some errors at run time like Configuration Sections not present.</span></span> <span data-ttu-id="95346-197">`Microsoft.Extensions.Configuration`Tato chyba by se měla opravit pomocí balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="95346-197">Using the `Microsoft.Extensions.Configuration` NuGet package should fix that error.</span></span>

<span data-ttu-id="95346-198">Dalším důvodem pro chyby je použití `BeginInvoke` metod a, `EndInvoke` protože nejsou podporované v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="95346-198">Another reason for errors is the use of the `BeginInvoke` and `EndInvoke` methods because they aren't supported on .NET Core.</span></span> <span data-ttu-id="95346-199">Nepodporují se v .NET Core, protože mají závislost na vzdálené komunikaci, která v .NET Core neexistuje.</span><span class="sxs-lookup"><span data-stu-id="95346-199">They aren't supported on .NET Core because they have a dependency on Remoting, which doesn't exist on .NET Core.</span></span> <span data-ttu-id="95346-200">Chcete-li tento problém vyřešit, zkuste použít `await` klíčové slovo (je-li k dispozici) nebo <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="95346-200">To solve this issue, try to use the `await` keyword (when available) or the <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="95346-201">Pomocí analyzátorů kompatibility můžete identifikovat rozhraní API a vzory kódu v kódu, které mohou potenciálně způsobovat problémy v době běhu pomocí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="95346-201">You can use compatibility analyzers to let you identify APIs and code patterns in your code that can potentially cause problems at run time with .NET Core.</span></span> <span data-ttu-id="95346-202">Přejít na <https://github.com/dotnet/platform-compat> a použít analyzátor rozhraní .NET API pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="95346-202">Go to <https://github.com/dotnet/platform-compat> and use the .NET API analyzer on your project.</span></span>

## <a name="migrating-a-windows-forms-application"></a><span data-ttu-id="95346-203">Migrace aplikace model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95346-203">Migrating a Windows Forms application</span></span>

<span data-ttu-id="95346-204">Aby se dokončil proces migrace model Windows Forms aplikace, rozhodli jsme se migrovat ukázkovou aplikaci eShop, která je dostupná na adrese <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms> .</span><span class="sxs-lookup"><span data-stu-id="95346-204">To showcase a complete migration process of a Windows Forms application, we've chosen to migrate the eShop sample application available at <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms>.</span></span> <span data-ttu-id="95346-205">Úplný výsledek migrace můžete najít na adrese <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms> .</span><span class="sxs-lookup"><span data-stu-id="95346-205">You can find the complete result of the migration at <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms>.</span></span>

<span data-ttu-id="95346-206">Tato aplikace zobrazuje katalog produktů a umožňuje uživateli navigaci, filtrování a hledání produktů.</span><span class="sxs-lookup"><span data-stu-id="95346-206">This application shows a product catalog and allows the user to navigate, filter, and search for products.</span></span> <span data-ttu-id="95346-207">Z hlediska architektury se aplikace spoléhá na externí službu WCF, která slouží jako fasáda do back-endové databáze.</span><span class="sxs-lookup"><span data-stu-id="95346-207">From an architecture point of view, the app relies on an external WCF service that serves as a façade to a back-end database.</span></span>

<span data-ttu-id="95346-208">Hlavní okno aplikace můžete zobrazit na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="95346-208">You can see the main application window in the following picture:</span></span>

![Hlavní okno aplikace](./media/example-migration-core/main-application-window.png)

<span data-ttu-id="95346-210">Pokud otevřete soubor projektu *. csproj* , vidíte to přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="95346-210">If you open the *.csproj* project file, you can see something like this:</span></span>

![Snímek obrazovky s obsahem souboru csproj](./media/example-migration-core/csproj-file.png)

<span data-ttu-id="95346-212">Jak už jsme uvedli, projekt .NET Core má kompaktnější styl a potřebujete migrovat strukturu projektu na nový styl .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="95346-212">As previously mentioned, .NET Core project has a more compact style and you need to migrate the project structure to the new .NET Core SDK style.</span></span>

<span data-ttu-id="95346-213">V Průzkumník řešení klikněte pravým tlačítkem na projekt model Windows Forms a vyberte **Uvolnit projekt**  >  **Úpravy**.</span><span class="sxs-lookup"><span data-stu-id="95346-213">In the Solution Explorer, right click on the Windows Forms project and select **Unload Project** > **Edit**.</span></span>

<span data-ttu-id="95346-214">Nyní můžete aktualizovat soubor. csproj.</span><span class="sxs-lookup"><span data-stu-id="95346-214">Now you can update the .csproj file.</span></span> <span data-ttu-id="95346-215">Odstraníte celý obsah a nahradíte ho následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="95346-215">You'll delete the entire content and replace it with the following code:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
    <PropertyGroup>
        <OutputType>WinExe</OutputType>
        <TargetFramework>netcoreapp3.1</TargetFramework>
        <UseWindowsForms>true</UseWindowsForms>
        <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    </PropertyGroup>
</Project>
```

<span data-ttu-id="95346-216">Uložte a znovu načtěte projekt.</span><span class="sxs-lookup"><span data-stu-id="95346-216">Save and reload the project.</span></span> <span data-ttu-id="95346-217">Nyní jste dokončili aktualizaci souboru projektu a projekt cílí na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="95346-217">You're now done updating the project file and the project is targeting the .NET Core.</span></span>

<span data-ttu-id="95346-218">Pokud v tomto okamžiku zkompilujete projekt, zjistíte chyby související s odkazem na klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="95346-218">If you compile the project at this point, you'll find some errors related to the WCF client reference.</span></span> <span data-ttu-id="95346-219">Vzhledem k tomu, že se tento kód generuje automaticky, musíte ho znovu vygenerovat pro cílový .NET Core.</span><span class="sxs-lookup"><span data-stu-id="95346-219">Since this code is autogenerated, you must regenerate it to target .NET Core.</span></span>

![Snímek obrazovky s chybami kompilace v aplikaci Visual Studio](./media/example-migration-core/winforms-compilation-errors.png)

<span data-ttu-id="95346-221">Odstraňte soubor *reference.cs* a vygenerujte nového klienta služby.</span><span class="sxs-lookup"><span data-stu-id="95346-221">Delete the *Reference.cs* file and generate a new Service Client.</span></span>

<span data-ttu-id="95346-222">Klikněte pravým tlačítkem na **připojené služby** a vyberte možnost **Přidat připojenou službu** .</span><span class="sxs-lookup"><span data-stu-id="95346-222">Right-click on **Connected Services** and select the **Add Connected Service** option.</span></span>

![Snímek obrazovky s vybranou možností přidat připojenou službu v nabídce připojených služeb](./media/example-migration-core/add-connected-service.png)

<span data-ttu-id="95346-224">Otevře se okno připojené služby.</span><span class="sxs-lookup"><span data-stu-id="95346-224">The Connected Services window opens.</span></span> <span data-ttu-id="95346-225">Vyberte možnost **webové služby Microsoft WCF** .</span><span class="sxs-lookup"><span data-stu-id="95346-225">Select the **Microsoft WCF Web Service** option.</span></span>

![Snímek obrazovky okna připojené služby](./media/example-migration-core/connected-services-window.png)

<span data-ttu-id="95346-227">Pokud máte službu WCF ve stejném řešení jako v tomto příkladu, můžete místo zadání adresy URL služby vybrat možnost **zjišťování** .</span><span class="sxs-lookup"><span data-stu-id="95346-227">If you have the WCF Service in the same solution as we have in this example, you can select the **Discover** option instead of specifying a service URL.</span></span>

![Snímek obrazovky s referenčním oknem konfigurace WCF webové služby](./media/example-migration-core/configure-wcf-reference.png)

<span data-ttu-id="95346-229">Po umístění služby nástroj odráží kontrakt rozhraní API implementovaný službou.</span><span class="sxs-lookup"><span data-stu-id="95346-229">Once the service is located, the tool reflects the API contract implemented by the service.</span></span> <span data-ttu-id="95346-230">Změňte název oboru názvů tak `eShopServiceReference` , jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="95346-230">Change the name of the namespace to be `eShopServiceReference` as shown in the following image:</span></span>

![Snímek obrazovky se smlouvou API a oborem názvů se změnil](./media/example-migration-core/api-contract-namespace.png)

<span data-ttu-id="95346-232">Vyberte tlačítko **Dokončit** .</span><span class="sxs-lookup"><span data-stu-id="95346-232">Select the **Finish** button.</span></span> <span data-ttu-id="95346-233">Po chvíli se zobrazí generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="95346-233">After a while, you'll see the generated code.</span></span>

<span data-ttu-id="95346-234">Měli byste vidět tři automaticky generované soubory:</span><span class="sxs-lookup"><span data-stu-id="95346-234">You should see three autogenerated files:</span></span>

1. <span data-ttu-id="95346-235">*Začínáme*: odkaz na GitHub, který poskytuje některé informace o WCF.</span><span class="sxs-lookup"><span data-stu-id="95346-235">*Getting Started*: a link to GitHub to provide some information on WCF.</span></span>
2. <span data-ttu-id="95346-236">*Připojenou službu. JSON*: parametry konfigurace pro připojení ke službě.</span><span class="sxs-lookup"><span data-stu-id="95346-236">*ConnectedService.json*: configuration parameters to connect to the service.</span></span>
3. <span data-ttu-id="95346-237">*Reference.cs*: skutečný kód klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="95346-237">*Reference.cs*: the actual WCF client code.</span></span>

![Snímek obrazovky okna Průzkumník řešení se třemi automaticky generovanými soubory](./media/example-migration-core/autogenerated-files.png)

<span data-ttu-id="95346-239">Pokud znovu zkompilujete, zobrazí se mnoho chyb ze souborů *. cs* ve složce *pomocníka* .</span><span class="sxs-lookup"><span data-stu-id="95346-239">If you compile again, you'll see many errors coming from *.cs* files inside the *Helper* folder.</span></span> <span data-ttu-id="95346-240">Tato složka se objevila ve verzi .NET Framework, ale není zahrnutá v Old *. csproj*.</span><span class="sxs-lookup"><span data-stu-id="95346-240">This folder was present in the .NET Framework version but not included in the old *.csproj*.</span></span> <span data-ttu-id="95346-241">Ale v novém projektu ve stylu sady SDK je každý soubor s kódem, který je přítomen pod umístěním souboru projektu, ve výchozím nastavení zahrnut.</span><span class="sxs-lookup"><span data-stu-id="95346-241">But with the new SDK-style project, every code file present underneath the project file location is included by default.</span></span> <span data-ttu-id="95346-242">To znamená, že nový projekt .NET Core se pokusí kompilovat soubory uvnitř složky *pomocníka* .</span><span class="sxs-lookup"><span data-stu-id="95346-242">That is, the new .NET Core project tries to compile the files inside the *Helper* folder.</span></span> <span data-ttu-id="95346-243">Vzhledem k tomu, že tato složka není potřeba, můžete ji bezpečně odstranit.</span><span class="sxs-lookup"><span data-stu-id="95346-243">Since that folder isn't needed, you can safely delete it.</span></span>

<span data-ttu-id="95346-244">Pokud projekt zkompilujete znovu a spustíte, neuvidíte image produktu.</span><span class="sxs-lookup"><span data-stu-id="95346-244">If you compile the project again and execute it, you won't see the product images.</span></span> <span data-ttu-id="95346-245">Problémem je to, že se teď cesta k souborům mírně změnila.</span><span class="sxs-lookup"><span data-stu-id="95346-245">The problem is that now the path to the files has slightly changed.</span></span> <span data-ttu-id="95346-246">Chcete-li tento problém vyřešit, je třeba v cestě přidat další úroveň hloubky, aktualizovat v souboru `CatalogView.cs` řádek:</span><span class="sxs-lookup"><span data-stu-id="95346-246">To fix this issue, you need to add another level of depth in the path, updating in the file `CatalogView.cs` the line:</span></span>

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

<span data-ttu-id="95346-247">na</span><span class="sxs-lookup"><span data-stu-id="95346-247">to</span></span>

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

<span data-ttu-id="95346-248">Po této změně můžete ověřit, že se aplikace spouští a běží podle očekávání v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="95346-248">After this change, you can check that the application launches and runs as expected on .NET Core.</span></span>

## <a name="migrating-a-wpf-application"></a><span data-ttu-id="95346-249">Migrace aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="95346-249">Migrating a WPF application</span></span>

<span data-ttu-id="95346-250">`Shop.ClassicWPF`K provedení migrace použijeme ukázkovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="95346-250">We'll use the `Shop.ClassicWPF` sample application to perform the migration.</span></span> <span data-ttu-id="95346-251">Následující obrázek ukazuje snímek obrazovky aplikace před migrací:</span><span class="sxs-lookup"><span data-stu-id="95346-251">The following image shows a screenshot of the app before migration:</span></span>

![Ukázková aplikace před migrací](./media/example-migration-core/app-before-migration.png)

<span data-ttu-id="95346-253">Tato aplikace používá k ukládání informací katalogu produktů místní databázi SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="95346-253">This application uses a local SQL Server Express database to hold the product catalog information.</span></span> <span data-ttu-id="95346-254">K této databázi se dostanete přímo z aplikace WPF.</span><span class="sxs-lookup"><span data-stu-id="95346-254">This database is accessed directly from the WPF application.</span></span>

<span data-ttu-id="95346-255">Nejprve je třeba aktualizovat soubor *. csproj* na nový styl sady SDK používaný aplikacemi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="95346-255">First, you must update the *.csproj* file to the new SDK style used by .NET Core applications.</span></span> <span data-ttu-id="95346-256">Budete postupovat podle stejných kroků popsaných v tématu Migrace model Windows Forms: projekt zrušíte, otevřete soubor *. csproj* , aktualizujete jeho obsah a znovu načtete projekt.</span><span class="sxs-lookup"><span data-stu-id="95346-256">You'll follow the same steps described in the Windows Forms migration: you'll unload the project, open the *.csproj* file, update its contents, and reload the project.</span></span>

<span data-ttu-id="95346-257">V takovém případě odstraňte veškerý obsah souboru *. csproj* a nahraďte ho následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="95346-257">In this case, delete all the content of the *.csproj* file and replace it with the following code:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
    <PropertyGroup>
        <OutputType>WinExe</OutputType>
        <TargetFramework>netcoreapp3.1</TargetFramework>
        <UseWPF>true</UseWPF>
        <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    </PropertyGroup>
</Project>
```

<span data-ttu-id="95346-258">Pokud projekt znovu načtete a zkompilujete, zobrazí se následující chyba:</span><span class="sxs-lookup"><span data-stu-id="95346-258">If you reload the project and compile it, you'll get the following error:</span></span>

![Snímek obrazovky s chybami kompilace v aplikaci Visual Studio](./media/example-migration-core/wpf-compilation-error.png)

<span data-ttu-id="95346-260">Vzhledem k tomu, že jste odstranili všechen obsah *. csproj* , ztratili jste ve starém projektu specifikaci odkazů na projekt.</span><span class="sxs-lookup"><span data-stu-id="95346-260">Since you've deleted all the *.csproj* contents, you've lost a project reference specification present in the old project.</span></span> <span data-ttu-id="95346-261">Pouze potřebujete přidat tento řádek do souboru *. csproj* pro zahrnutí odkazu na projekt:</span><span class="sxs-lookup"><span data-stu-id="95346-261">You just need to add this line to the *.csproj* file to include the project reference back:</span></span>

```xml
<ItemGroup>
    <ProjectReference Include="..\\eShop.SqlProvider\\eShop.SqlProvider.csproj" />
<ItemGroup>
```

<span data-ttu-id="95346-262">Aplikaci Visual Studio můžete také nechat pomáhat kliknutím pravým tlačítkem na uzel **závislosti** a výběrem možnosti **Přidat odkaz na projekt**.</span><span class="sxs-lookup"><span data-stu-id="95346-262">You can also let Visual Studio help you by right-clicking on the **Dependencies** node and selecting **Add Project Reference**.</span></span> <span data-ttu-id="95346-263">Vyberte projekt z řešení a klikněte na **OK**:</span><span class="sxs-lookup"><span data-stu-id="95346-263">Select the project from the solution and click **OK**:</span></span>

![Snímek obrazovky dialogového okna Správce odkazů s vybraným projektem eShop. SqlProvider](./media/example-migration-core/reference-manager.png)

<span data-ttu-id="95346-265">Po přidání chybějícího odkazu na projekt se aplikace zkompiluje a spustí podle očekávání v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="95346-265">Once you add the missing project reference, the application compiles and runs as expected on .NET Core.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="95346-266">[Předchozí](windows-migration.md) 
> [Další](deploy-modern-applications.md)</span><span class="sxs-lookup"><span data-stu-id="95346-266">[Previous](windows-migration.md)
[Next](deploy-modern-applications.md)</span></span>
