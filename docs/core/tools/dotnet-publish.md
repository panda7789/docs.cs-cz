---
title: dotnet publish – příkaz
description: Příkaz dotnet publish publikuje projekt nebo řešení .NET Core do adresáře.
ms.date: 02/24/2020
ms.openlocfilehash: cf41ee09244faad03feb8ccda19135b8c7780106
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156995"
---
# <a name="dotnet-publish"></a><span data-ttu-id="40025-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="40025-103">dotnet publish</span></span>

<span data-ttu-id="40025-104">**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="40025-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="40025-105">Název</span><span class="sxs-lookup"><span data-stu-id="40025-105">Name</span></span>

<span data-ttu-id="40025-106">`dotnet publish` – publikuje aplikaci a její závislosti do složky pro nasazení do hostitelského systému.</span><span class="sxs-lookup"><span data-stu-id="40025-106">`dotnet publish` - Publishes the application and its dependencies to a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="40025-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="40025-107">Synopsis</span></span>

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration] 
    [-f|--framework] [--force] [--interactive] [--manifest]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [--self-contained]
    [--no-self-contained] [-v|--verbosity] [--version-suffix]

dotnet publish [-h|--help]
```

## <a name="description"></a><span data-ttu-id="40025-108">Popis</span><span class="sxs-lookup"><span data-stu-id="40025-108">Description</span></span>

<span data-ttu-id="40025-109">`dotnet publish` zkompiluje aplikaci, přečte jejich závislosti zadané v souboru projektu a publikuje výslednou sadu souborů do adresáře.</span><span class="sxs-lookup"><span data-stu-id="40025-109">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="40025-110">Výstup obsahuje následující prostředky:</span><span class="sxs-lookup"><span data-stu-id="40025-110">The output includes the following assets:</span></span>

- <span data-ttu-id="40025-111">Kód zprostředkujícího jazyka (IL) v sestavení s příponou *DLL* .</span><span class="sxs-lookup"><span data-stu-id="40025-111">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="40025-112">Soubor *. DEPS. JSON* , který obsahuje všechny závislosti projektu.</span><span class="sxs-lookup"><span data-stu-id="40025-112">A *.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="40025-113">Soubor *. runtimeconfig. JSON* , který určuje sdílený modul runtime, který aplikace očekává, a další možnosti konfigurace pro modul runtime (například typ uvolňování paměti).</span><span class="sxs-lookup"><span data-stu-id="40025-113">A *.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="40025-114">Závislosti aplikace, které jsou zkopírovány z mezipaměti NuGet do výstupní složky.</span><span class="sxs-lookup"><span data-stu-id="40025-114">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="40025-115">Výstup příkazu `dotnet publish` je připravený k nasazení do hostitelského systému (například server, počítač, Mac, notebook) k provedení.</span><span class="sxs-lookup"><span data-stu-id="40025-115">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="40025-116">Jedná se o jediný oficiálně podporovaný způsob, jak připravit aplikaci pro nasazení.</span><span class="sxs-lookup"><span data-stu-id="40025-116">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="40025-117">V závislosti na typu nasazení, které projekt určuje, hostující systém může nebo nemusí mít nainstalovaný modul .NET Core Shared runtime.</span><span class="sxs-lookup"><span data-stu-id="40025-117">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span>

## <a name="arguments"></a><span data-ttu-id="40025-118">Argumenty</span><span class="sxs-lookup"><span data-stu-id="40025-118">Arguments</span></span>

- **`PROJECT|SOLUTION`**

  <span data-ttu-id="40025-119">Projekt nebo řešení, které se má publikovat</span><span class="sxs-lookup"><span data-stu-id="40025-119">The project or solution to publish.</span></span>
  
  * <span data-ttu-id="40025-120">`PROJECT` je cesta a název souboru [C#](csproj.md)projektu, F#nebo Visual Basic nebo cesta k adresáři, který obsahuje soubor projektu C#, F#nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="40025-120">`PROJECT` is the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="40025-121">Pokud adresář není zadaný, použije se ve výchozím nastavení aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="40025-121">If the directory is not specified, it defaults to the current directory.</span></span>

  * <span data-ttu-id="40025-122">`SOLUTION` je cesta a název souboru řešení ( *. sln* rozšíření) nebo cesta k adresáři, který obsahuje soubor řešení.</span><span class="sxs-lookup"><span data-stu-id="40025-122">`SOLUTION` is the path and filename of a solution file (*.sln* extension), or the path to a directory that contains a solution file.</span></span> <span data-ttu-id="40025-123">Pokud adresář není zadaný, použije se ve výchozím nastavení aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="40025-123">If the directory is not specified, it defaults to the current directory.</span></span> <span data-ttu-id="40025-124">**K dispozici od sady .NET Core 3,0 SDK.**</span><span class="sxs-lookup"><span data-stu-id="40025-124">**Available starting with .NET Core 3.0 SDK.**</span></span> 

## <a name="options"></a><span data-ttu-id="40025-125">Možnosti</span><span class="sxs-lookup"><span data-stu-id="40025-125">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="40025-126">Definuje konfiguraci sestavení.</span><span class="sxs-lookup"><span data-stu-id="40025-126">Defines the build configuration.</span></span> <span data-ttu-id="40025-127">Výchozí hodnota pro většinu projektů je `Debug`, ale můžete přepsat nastavení konfigurace sestavení v projektu.</span><span class="sxs-lookup"><span data-stu-id="40025-127">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="40025-128">Publikuje aplikaci pro zadanou [cílovou architekturu](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="40025-128">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="40025-129">V souboru projektu je nutné zadat cílovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="40025-129">You must specify the target framework in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="40025-130">Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné.</span><span class="sxs-lookup"><span data-stu-id="40025-130">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="40025-131">Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="40025-131">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="40025-132">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="40025-132">Prints out a short help for the command.</span></span>

- <span data-ttu-id="40025-133">**`--interactive`** **k dispozici počínaje verzí .NET Core 3,0 SDK.**</span><span class="sxs-lookup"><span data-stu-id="40025-133">**`--interactive`** **Available starting with .NET Core 3.0 SDK.**</span></span>

  <span data-ttu-id="40025-134">Umožňuje zastavení příkazu zastavit a počkat na vstup nebo akci uživatele.</span><span class="sxs-lookup"><span data-stu-id="40025-134">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="40025-135">Například k dokončení ověřování.</span><span class="sxs-lookup"><span data-stu-id="40025-135">For example, to complete authentication.</span></span> 

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="40025-136">Určuje jeden nebo několik [cílových manifestů](../deploying/runtime-store.md) , které se použijí ke zkrácení sady balíčků publikovaných s aplikací.</span><span class="sxs-lookup"><span data-stu-id="40025-136">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="40025-137">Soubor manifestu je součástí výstupu [příkazu`dotnet store`](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="40025-137">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="40025-138">Chcete-li zadat více manifestů, přidejte možnost `--manifest` pro každý manifest.</span><span class="sxs-lookup"><span data-stu-id="40025-138">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span>

- **`--no-build`**

  <span data-ttu-id="40025-139">Nevytvoří projekt před publikováním.</span><span class="sxs-lookup"><span data-stu-id="40025-139">Doesn't build the project before publishing.</span></span> <span data-ttu-id="40025-140">Také implicitně nastaví příznak `--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="40025-140">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="40025-141">Ignoruje odkazy z projektu na projekt a obnoví pouze kořenový projekt.</span><span class="sxs-lookup"><span data-stu-id="40025-141">Ignores project-to-project references and only restores the root project.</span></span>

- <span data-ttu-id="40025-142">**`--nologo`** **k dispozici počínaje verzí .NET Core 3,0 SDK.**</span><span class="sxs-lookup"><span data-stu-id="40025-142">**`--nologo`** **Available starting with .NET Core 3.0 SDK.**</span></span>

  <span data-ttu-id="40025-143">Nezobrazuje úvodní nápis nebo zprávu o autorských právech.</span><span class="sxs-lookup"><span data-stu-id="40025-143">Doesn't display the startup banner or the copyright message.</span></span> 

- **`--no-restore`**

  <span data-ttu-id="40025-144">Při spuštění příkazu neprovede implicitní obnovení.</span><span class="sxs-lookup"><span data-stu-id="40025-144">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="40025-145">Určuje cestu k výstupnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="40025-145">Specifies the path for the output directory.</span></span> <span data-ttu-id="40025-146">Pokud není zadaný, použije se výchozí hodnota *./bin/[Configuration]/[Framework]/Publish/* pro spustitelný soubor závislý na modulu runtime a binární soubory pro více platforem.</span><span class="sxs-lookup"><span data-stu-id="40025-146">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a runtime-dependent executable and cross-platform binaries.</span></span> <span data-ttu-id="40025-147">Výchozí hodnota je *./bin/[Configuration]/[Framework]/[runtime]/Publish/* pro samostatně obsažený spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="40025-147">It defaults to *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained executable.</span></span>

  <span data-ttu-id="40025-148">Pokud je cesta relativní, vygenerovaný výstupní adresář je relativní vzhledem k umístění souboru projektu, nikoli k aktuálnímu pracovnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="40025-148">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

- **`--self-contained [true|false]`**

  <span data-ttu-id="40025-149">Publikuje modul runtime .NET Core ve vaší aplikaci, takže modul runtime nemusí být na cílovém počítači nainstalován.</span><span class="sxs-lookup"><span data-stu-id="40025-149">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="40025-150">Výchozí hodnota je `true`, pokud je zadán identifikátor modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="40025-150">Default is `true` if a runtime identifier is specified.</span></span> <span data-ttu-id="40025-151">Další informace najdete v tématu [aplikace .NET Core – publikování](../deploying/index.md) a [publikování aplikací .net Core pomocí .NET Core CLI](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="40025-151">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- <span data-ttu-id="40025-152">**`--no-self-contained`** **k dispozici počínaje verzí .NET Core 3,0 SDK.**</span><span class="sxs-lookup"><span data-stu-id="40025-152">**`--no-self-contained`**  **Available starting with .NET Core 3.0 SDK.**</span></span>

  <span data-ttu-id="40025-153">Ekvivalent `--self-contained false`.</span><span class="sxs-lookup"><span data-stu-id="40025-153">Equivalent to `--self-contained false`.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="40025-154">Publikuje aplikaci pro daný modul runtime.</span><span class="sxs-lookup"><span data-stu-id="40025-154">Publishes the application for a given runtime.</span></span> <span data-ttu-id="40025-155">Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="40025-155">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="40025-156">Další informace najdete v tématu [aplikace .NET Core – publikování](../deploying/index.md) a [publikování aplikací .net Core pomocí .NET Core CLI](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="40025-156">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="40025-157">Nastaví úroveň podrobností příkazu.</span><span class="sxs-lookup"><span data-stu-id="40025-157">Sets the verbosity level of the command.</span></span> <span data-ttu-id="40025-158">Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="40025-158">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="40025-159">Definuje příponu verze, která nahradí hvězdičku (`*`) v poli verze souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="40025-159">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

## <a name="examples"></a><span data-ttu-id="40025-160">Příklady</span><span class="sxs-lookup"><span data-stu-id="40025-160">Examples</span></span>

- <span data-ttu-id="40025-161">Vytvořte [binární soubor pro více platforem závislý na modulu runtime](../deploying/index.md#produce-a-cross-platform-binary) pro projekt v aktuálním adresáři:</span><span class="sxs-lookup"><span data-stu-id="40025-161">Create a [runtime-dependent cross-platform binary](../deploying/index.md#produce-a-cross-platform-binary) for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet publish
  ```

  <span data-ttu-id="40025-162">Od .NET Core 3,0 SDK tento příklad také vytvoří [spustitelný soubor závislý na modulu runtime](../deploying/index.md#publish-runtime-dependent) pro aktuální platformu.</span><span class="sxs-lookup"><span data-stu-id="40025-162">Starting with .NET Core 3.0 SDK, this example also creates a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the current platform.</span></span>

- <span data-ttu-id="40025-163">Vytvoření [samostatného spustitelného souboru](../deploying/index.md#publish-self-contained) pro projekt v aktuálním adresáři pro konkrétní modul runtime:</span><span class="sxs-lookup"><span data-stu-id="40025-163">Create a [self-contained executable](../deploying/index.md#publish-self-contained) for the project in the current directory, for a specific runtime:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  <span data-ttu-id="40025-164">Identifikátor RID musí být v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="40025-164">The RID must be in the project file.</span></span>

- <span data-ttu-id="40025-165">Vytvořte [spustitelný soubor závislý na modulu runtime](../deploying/index.md#publish-runtime-dependent) pro projekt v aktuálním adresáři pro konkrétní platformu:</span><span class="sxs-lookup"><span data-stu-id="40025-165">Create a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the project in the current directory, for a specific platform:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  <span data-ttu-id="40025-166">Identifikátor RID musí být v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="40025-166">The RID must be in the project file.</span></span> <span data-ttu-id="40025-167">Tento příklad platí pro .NET Core 3,0 SDK a novější verze.</span><span class="sxs-lookup"><span data-stu-id="40025-167">This example applies to .NET Core 3.0 SDK and later versions.</span></span>

- <span data-ttu-id="40025-168">Publikování projektu v aktuálním adresáři pro konkrétní modul runtime a cílové rozhraní:</span><span class="sxs-lookup"><span data-stu-id="40025-168">Publish the project in the current directory, for a specific runtime and target framework:</span></span>

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- <span data-ttu-id="40025-169">Publikovat zadaný soubor projektu:</span><span class="sxs-lookup"><span data-stu-id="40025-169">Publish the specified project file:</span></span>

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="40025-170">Publikování aktuální aplikace, ale neobnovujte odkazy na projekt na projekt (P2P), pouze kořenový projekt během operace obnovení:</span><span class="sxs-lookup"><span data-stu-id="40025-170">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation:</span></span>

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a><span data-ttu-id="40025-171">Viz také</span><span class="sxs-lookup"><span data-stu-id="40025-171">See also</span></span>

- [<span data-ttu-id="40025-172">Přehled publikování aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="40025-172">.NET Core application publishing overview</span></span>](../deploying/index.md)
- [<span data-ttu-id="40025-173">Publikování aplikací .NET Core pomocí .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="40025-173">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="40025-174">Cílové architektury</span><span class="sxs-lookup"><span data-stu-id="40025-174">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="40025-175">Katalog identifikátoru runtime (RID)</span><span class="sxs-lookup"><span data-stu-id="40025-175">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- <span data-ttu-id="40025-176">[Práce s MacOS Catalina notarization](../install/macos-notarization-issues.md) Další informace najdete v následujících zdrojích informací:</span><span class="sxs-lookup"><span data-stu-id="40025-176">[Working with macOS Catalina Notarization](../install/macos-notarization-issues.md) For more information, see he following resources:</span></span>
- [<span data-ttu-id="40025-177">Adresářová struktura publikované aplikace</span><span class="sxs-lookup"><span data-stu-id="40025-177">Directory structure of a published application</span></span>](/aspnet/core/hosting/directory-structure)
