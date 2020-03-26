---
title: dotnet publikovat, příkaz
description: Příkaz publikování dotnet publikuje projekt nebo řešení .NET Core do adresáře.
ms.date: 02/24/2020
ms.openlocfilehash: ed5b87b3343210ca81486ef4b9a9d70d1b534464
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80110968"
---
# <a name="dotnet-publish"></a><span data-ttu-id="f5601-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="f5601-103">dotnet publish</span></span>

<span data-ttu-id="f5601-104">**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="f5601-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f5601-105">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="f5601-105">Name</span></span>

<span data-ttu-id="f5601-106">`dotnet publish`- Publikuje aplikaci a její závislosti do složky pro nasazení do hostitelského systému.</span><span class="sxs-lookup"><span data-stu-id="f5601-106">`dotnet publish` - Publishes the application and its dependencies to a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f5601-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="f5601-107">Synopsis</span></span>

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration]
    [-f|--framework] [--force] [--interactive] [--manifest]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [--self-contained]
    [--no-self-contained] [-v|--verbosity] [--version-suffix]

dotnet publish [-h|--help]
```

## <a name="description"></a><span data-ttu-id="f5601-108">Popis</span><span class="sxs-lookup"><span data-stu-id="f5601-108">Description</span></span>

<span data-ttu-id="f5601-109">`dotnet publish`zkompiluje aplikaci, pročte její závislosti zadané v souboru projektu a publikuje výslednou sadu souborů do adresáře.</span><span class="sxs-lookup"><span data-stu-id="f5601-109">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="f5601-110">Výstup zahrnuje následující aktiva:</span><span class="sxs-lookup"><span data-stu-id="f5601-110">The output includes the following assets:</span></span>

- <span data-ttu-id="f5601-111">Kód zprostředkujícího jazyka (IL) v sestavení s rozšířením *dll.*</span><span class="sxs-lookup"><span data-stu-id="f5601-111">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="f5601-112">Soubor *.deps.json,* který obsahuje všechny závislosti projektu.</span><span class="sxs-lookup"><span data-stu-id="f5601-112">A *.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="f5601-113">Soubor *.runtimeconfig.json,* který určuje sdílený runtime, který aplikace očekává, stejně jako další možnosti konfigurace pro runtime (například typ uvolňování paměti).</span><span class="sxs-lookup"><span data-stu-id="f5601-113">A *.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="f5601-114">Závislosti aplikace, které jsou zkopírovány z mezipaměti NuGet do výstupní složky.</span><span class="sxs-lookup"><span data-stu-id="f5601-114">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="f5601-115">Výstup `dotnet publish` příkazu je připraven k nasazení do hostitelského systému (například server, PC, Mac, notebook) pro spuštění.</span><span class="sxs-lookup"><span data-stu-id="f5601-115">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="f5601-116">Je to jediný oficiálně podporovaný způsob, jak připravit aplikaci pro nasazení.</span><span class="sxs-lookup"><span data-stu-id="f5601-116">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="f5601-117">V závislosti na typu nasazení, který projekt určuje, může nebo nemusí mít hostitelský systém na něm nainstalovanou sdílenou runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f5601-117">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span>

## <a name="arguments"></a><span data-ttu-id="f5601-118">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f5601-118">Arguments</span></span>

- **`PROJECT|SOLUTION`**

  <span data-ttu-id="f5601-119">Projekt nebo řešení publikovat.</span><span class="sxs-lookup"><span data-stu-id="f5601-119">The project or solution to publish.</span></span>
  
  * <span data-ttu-id="f5601-120">`PROJECT`je cesta a název souboru projektu [jazyka C#](csproj.md), F# nebo Visual Basic nebo cesta k adresáři, který obsahuje soubor projektu Jazyka C#, F# nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f5601-120">`PROJECT` is the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="f5601-121">Pokud adresář není zadán, je výchozí pro aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="f5601-121">If the directory is not specified, it defaults to the current directory.</span></span>

  * <span data-ttu-id="f5601-122">`SOLUTION`je cesta a název souboru řešení (*přípona .sln)* nebo cesta k adresáři, který obsahuje soubor řešení.</span><span class="sxs-lookup"><span data-stu-id="f5601-122">`SOLUTION` is the path and filename of a solution file (*.sln* extension), or the path to a directory that contains a solution file.</span></span> <span data-ttu-id="f5601-123">Pokud adresář není zadán, je výchozí pro aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="f5601-123">If the directory is not specified, it defaults to the current directory.</span></span> <span data-ttu-id="f5601-124">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="f5601-124">Available since .NET Core 3.0 SDK.</span></span>

## <a name="options"></a><span data-ttu-id="f5601-125">Možnosti</span><span class="sxs-lookup"><span data-stu-id="f5601-125">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="f5601-126">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="f5601-126">Defines the build configuration.</span></span> <span data-ttu-id="f5601-127">Výchozí hodnota pro `Debug`většinu projektů je , ale můžete přepsat nastavení konfigurace sestavení v projektu.</span><span class="sxs-lookup"><span data-stu-id="f5601-127">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f5601-128">Publikuje aplikaci pro zadaný [cílový rámec](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="f5601-128">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="f5601-129">Je nutné zadat cílovou architekturu v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="f5601-129">You must specify the target framework in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="f5601-130">Vynutí vyřešení všech závislostí, i když bylo poslední obnovení úspěšné.</span><span class="sxs-lookup"><span data-stu-id="f5601-130">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="f5601-131">Zadání tohoto příznaku je stejné jako odstranění souboru *project.assets.json.*</span><span class="sxs-lookup"><span data-stu-id="f5601-131">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="f5601-132">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="f5601-132">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="f5601-133">Umožňuje příkazu zastavit a čekat na vstup uživatele nebo akci.</span><span class="sxs-lookup"><span data-stu-id="f5601-133">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="f5601-134">Například k dokončení ověřování.</span><span class="sxs-lookup"><span data-stu-id="f5601-134">For example, to complete authentication.</span></span> <span data-ttu-id="f5601-135">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="f5601-135">Available since .NET Core 3.0 SDK.</span></span>

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="f5601-136">Určuje jeden nebo více [cílových manifestů,](../deploying/runtime-store.md) které se mají použít k oříznutí sady balíčků publikovaných s aplikací.</span><span class="sxs-lookup"><span data-stu-id="f5601-136">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="f5601-137">Soubor manifestu je součástí výstupu [ `dotnet store` příkazu](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="f5601-137">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="f5601-138">Chcete-li zadat více `--manifest` manifestů, přidejte možnost pro každý manifest.</span><span class="sxs-lookup"><span data-stu-id="f5601-138">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span>

- **`--no-build`**

  <span data-ttu-id="f5601-139">Nesestavuje projekt před publikováním.</span><span class="sxs-lookup"><span data-stu-id="f5601-139">Doesn't build the project before publishing.</span></span> <span data-ttu-id="f5601-140">Také implicitně nastaví příznak. `--no-restore`</span><span class="sxs-lookup"><span data-stu-id="f5601-140">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="f5601-141">Ignoruje odkazy projektu na projekt a obnoví pouze kořenový projekt.</span><span class="sxs-lookup"><span data-stu-id="f5601-141">Ignores project-to-project references and only restores the root project.</span></span>

- **`--nologo`**

  <span data-ttu-id="f5601-142">Nezobrazuje spouštěcí banner ani zprávu o autorských právech.</span><span class="sxs-lookup"><span data-stu-id="f5601-142">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="f5601-143">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="f5601-143">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="f5601-144">Nespustí implicitní obnovení při spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="f5601-144">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="f5601-145">Určuje cestu pro výstupní adresář.</span><span class="sxs-lookup"><span data-stu-id="f5601-145">Specifies the path for the output directory.</span></span> <span data-ttu-id="f5601-146">Pokud není zadán, výchozí hodnota *./bin/[configuration]/[framework]/publish/* pro spustitelný soubor ový soubor a binární soubory mezi platformami.</span><span class="sxs-lookup"><span data-stu-id="f5601-146">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a runtime-dependent executable and cross-platform binaries.</span></span> <span data-ttu-id="f5601-147">Výchozí hodnota je *./bin/[configuration]/[framework]/[runtime]/publish/* pro samostatný spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="f5601-147">It defaults to *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained executable.</span></span>

  <span data-ttu-id="f5601-148">Pokud je cesta relativní, je vygenerovaný výstupní adresář relativní k umístění souboru projektu, nikoli k aktuálnímu pracovnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="f5601-148">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

- **`--self-contained [true|false]`**

  <span data-ttu-id="f5601-149">Publikuje zaběhu .NET Core s vaší aplikací, takže runtime nemusí být nainstalován v cílovém počítači.</span><span class="sxs-lookup"><span data-stu-id="f5601-149">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="f5601-150">Ve `true` výchozím nastavení je zadán identifikátor za běhu.</span><span class="sxs-lookup"><span data-stu-id="f5601-150">Default is `true` if a runtime identifier is specified.</span></span> <span data-ttu-id="f5601-151">Další informace naleznete v tématu [publikování a](../deploying/index.md) publikování [aplikací .NET Core pomocí rozhraní .NET Core .](../deploying/deploy-with-cli.md)</span><span class="sxs-lookup"><span data-stu-id="f5601-151">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`--no-self-contained`**

  <span data-ttu-id="f5601-152">Odpovídá `--self-contained false`.</span><span class="sxs-lookup"><span data-stu-id="f5601-152">Equivalent to `--self-contained false`.</span></span> <span data-ttu-id="f5601-153">K dispozici od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="f5601-153">Available since .NET Core 3.0 SDK.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="f5601-154">Publikuje aplikaci pro daný běhový čas.</span><span class="sxs-lookup"><span data-stu-id="f5601-154">Publishes the application for a given runtime.</span></span> <span data-ttu-id="f5601-155">Seznam identifikátorů modulu Runtime (RID) naleznete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="f5601-155">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="f5601-156">Další informace naleznete v tématu [publikování a](../deploying/index.md) publikování [aplikací .NET Core pomocí rozhraní .NET Core .](../deploying/deploy-with-cli.md)</span><span class="sxs-lookup"><span data-stu-id="f5601-156">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="f5601-157">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="f5601-157">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f5601-158">Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a .</span><span class="sxs-lookup"><span data-stu-id="f5601-158">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="f5601-159">Výchozí hodnota `minimal`je .</span><span class="sxs-lookup"><span data-stu-id="f5601-159">Default value is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="f5601-160">Definuje příponu verze, která nahradí hvězdičku (`*`) v poli verze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="f5601-160">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

## <a name="examples"></a><span data-ttu-id="f5601-161">Příklady</span><span class="sxs-lookup"><span data-stu-id="f5601-161">Examples</span></span>

- <span data-ttu-id="f5601-162">Vytvořte [binární soubor pro běhový čas závislý na více platformách](../deploying/index.md#produce-a-cross-platform-binary) pro projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="f5601-162">Create a [runtime-dependent cross-platform binary](../deploying/index.md#produce-a-cross-platform-binary) for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet publish
  ```

  <span data-ttu-id="f5601-163">Počínaje .NET Core 3.0 SDK, tento příklad také vytvoří [spustitelný soubor závislý na modulu runtime](../deploying/index.md#publish-runtime-dependent) pro aktuální platformu.</span><span class="sxs-lookup"><span data-stu-id="f5601-163">Starting with .NET Core 3.0 SDK, this example also creates a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the current platform.</span></span>

- <span data-ttu-id="f5601-164">Vytvořte [samostatný spustitelný soubor](../deploying/index.md#publish-self-contained) pro projekt v aktuálním adresáři pro konkrétní modul runtime:</span><span class="sxs-lookup"><span data-stu-id="f5601-164">Create a [self-contained executable](../deploying/index.md#publish-self-contained) for the project in the current directory, for a specific runtime:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  <span data-ttu-id="f5601-165">Rid musí být v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="f5601-165">The RID must be in the project file.</span></span>

- <span data-ttu-id="f5601-166">Vytvořte [spustitelný soubor závislý na modulu runtime](../deploying/index.md#publish-runtime-dependent) pro projekt v aktuálním adresáři pro konkrétní platformu:</span><span class="sxs-lookup"><span data-stu-id="f5601-166">Create a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the project in the current directory, for a specific platform:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  <span data-ttu-id="f5601-167">Rid musí být v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="f5601-167">The RID must be in the project file.</span></span> <span data-ttu-id="f5601-168">Tento příklad platí pro .NET Core 3.0 SDK a novější verze.</span><span class="sxs-lookup"><span data-stu-id="f5601-168">This example applies to .NET Core 3.0 SDK and later versions.</span></span>

- <span data-ttu-id="f5601-169">Publikujte projekt v aktuálním adresáři pro konkrétní rozhraní runtime a cílový rámec:</span><span class="sxs-lookup"><span data-stu-id="f5601-169">Publish the project in the current directory, for a specific runtime and target framework:</span></span>

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- <span data-ttu-id="f5601-170">Publikování zadaného souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="f5601-170">Publish the specified project file:</span></span>

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="f5601-171">Publikujte aktuální aplikaci, ale neobnovte odkazy projektu na projekt (P2P), pouze kořenový projekt během operace obnovení:</span><span class="sxs-lookup"><span data-stu-id="f5601-171">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation:</span></span>

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a><span data-ttu-id="f5601-172">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5601-172">See also</span></span>

- [<span data-ttu-id="f5601-173">Přehled publikování aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="f5601-173">.NET Core application publishing overview</span></span>](../deploying/index.md)
- [<span data-ttu-id="f5601-174">Publikování aplikací .NET Core pomocí rozhraní CLI jádra ROZHRANÍ .NET</span><span class="sxs-lookup"><span data-stu-id="f5601-174">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="f5601-175">Cílové architektury</span><span class="sxs-lookup"><span data-stu-id="f5601-175">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="f5601-176">Katalog IDentifier (RID) modulu runtime</span><span class="sxs-lookup"><span data-stu-id="f5601-176">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="f5601-177">Práce s macOS Catalina Notarization</span><span class="sxs-lookup"><span data-stu-id="f5601-177">Working with macOS Catalina Notarization</span></span>](../install/macos-notarization-issues.md)
- [<span data-ttu-id="f5601-178">Adresářová struktura publikované aplikace</span><span class="sxs-lookup"><span data-stu-id="f5601-178">Directory structure of a published application</span></span>](/aspnet/core/hosting/directory-structure)
