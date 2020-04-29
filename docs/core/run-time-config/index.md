---
title: Možnosti konfigurace běhového běhu
description: Naučte se konfigurovat aplikace .NET Core pomocí nastavení konfigurace za běhu.
ms.date: 01/21/2020
ms.openlocfilehash: d49707b93e272f0e527ff536a80140ec98e5c1a8
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506777"
---
# <a name="net-core-run-time-configuration-settings"></a><span data-ttu-id="5b5d7-103">Nastavení konfigurace runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="5b5d7-103">.NET Core run-time configuration settings</span></span>

<span data-ttu-id="5b5d7-104">.NET Core podporuje použití konfiguračních souborů a proměnných prostředí ke konfiguraci chování aplikací .NET Core v době běhu.</span><span class="sxs-lookup"><span data-stu-id="5b5d7-104">.NET Core supports the use of configuration files and environment variables to configure the behavior of .NET Core applications at run time.</span></span> <span data-ttu-id="5b5d7-105">Konfigurace běhového běhu je atraktivní možnost, pokud:</span><span class="sxs-lookup"><span data-stu-id="5b5d7-105">Run-time configuration is an attractive option if:</span></span>

- <span data-ttu-id="5b5d7-106">Zdrojový kód aplikace nevlastníte nebo neovládáte, a proto ji nelze programově nakonfigurovat.</span><span class="sxs-lookup"><span data-stu-id="5b5d7-106">You don't own or control the source code for an application and therefore are unable to configure it programmatically.</span></span>

- <span data-ttu-id="5b5d7-107">V jednom systému se spouští více instancí aplikace současně a chcete je nakonfigurovat pro optimální výkon.</span><span class="sxs-lookup"><span data-stu-id="5b5d7-107">Multiple instances of your application run at the same time on a single system, and you want to configure each for optimum performance.</span></span>

> [!NOTE]
> <span data-ttu-id="5b5d7-108">Tato dokumentace je probíhající práce.</span><span class="sxs-lookup"><span data-stu-id="5b5d7-108">This documentation is a work in progress.</span></span> <span data-ttu-id="5b5d7-109">Pokud si všimnete, že zde uvedené informace jsou buď neúplné, nebo nepřesné, buď [otevřete problém](https://github.com/dotnet/docs/issues) , abychom nás věděli, nebo [odešlete žádost](https://github.com/dotnet/docs/pulls) o přijetí změn k vyřešení problému.</span><span class="sxs-lookup"><span data-stu-id="5b5d7-109">If you notice that the information presented here is either incomplete or inaccurate, either [open an issue](https://github.com/dotnet/docs/issues) to let us know about it, or [submit a pull request](https://github.com/dotnet/docs/pulls) to address the issue.</span></span> <span data-ttu-id="5b5d7-110">Informace o odesílání žádostí o přijetí změn pro úložiště dotnet/docs najdete v [příručce pro přispěvatele](https://docs.microsoft.com/contribute/dotnet/dotnet-contribute).</span><span class="sxs-lookup"><span data-stu-id="5b5d7-110">For information about submitting pull requests for the dotnet/docs repository, see the [contributor's guide](https://docs.microsoft.com/contribute/dotnet/dotnet-contribute).</span></span>

<span data-ttu-id="5b5d7-111">.NET Core poskytuje následující mechanismy pro konfiguraci chování aplikace za běhu:</span><span class="sxs-lookup"><span data-stu-id="5b5d7-111">.NET Core provides the following mechanisms for configuring run-time application behavior:</span></span>

- <span data-ttu-id="5b5d7-112">[Soubor runtimeconfig. JSON](#runtimeconfigjson)</span><span class="sxs-lookup"><span data-stu-id="5b5d7-112">The [runtimeconfig.json file](#runtimeconfigjson)</span></span>

- [<span data-ttu-id="5b5d7-113">Vlastnosti nástroje MSBuild</span><span class="sxs-lookup"><span data-stu-id="5b5d7-113">MSBuild properties</span></span>](#msbuild-properties)

- [<span data-ttu-id="5b5d7-114">Proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="5b5d7-114">Environment variables</span></span>](#environment-variables)

<span data-ttu-id="5b5d7-115">Některé hodnoty konfigurace lze také nastavit programově voláním <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="5b5d7-115">Some configuration values can also be set programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="5b5d7-116">Články v této části dokumentace jsou uspořádány podle kategorie, například [ladění](debugging-profiling.md) a [uvolňování paměti](garbage-collector.md).</span><span class="sxs-lookup"><span data-stu-id="5b5d7-116">The articles in this section of the documentation are organized by category, for example, [debugging](debugging-profiling.md) and [garbage collection](garbage-collector.md).</span></span> <span data-ttu-id="5b5d7-117">Pokud je to možné, zobrazí se možnosti konfigurace pro soubory *runtimeconfig. JSON* , vlastnosti MSBuild, proměnné prostředí a, pro křížové odkazy, soubory *App. config* pro .NET Framework projekty.</span><span class="sxs-lookup"><span data-stu-id="5b5d7-117">Where applicable, configuration options are shown for *runtimeconfig.json* files, MSBuild properties, environment variables, and, for cross-reference, *app.config* files for .NET Framework projects.</span></span>

## <a name="runtimeconfigjson"></a><span data-ttu-id="5b5d7-118">runtimeconfig. JSON</span><span class="sxs-lookup"><span data-stu-id="5b5d7-118">runtimeconfig.json</span></span>

<span data-ttu-id="5b5d7-119">Při [sestavení](../tools/dotnet-build.md)projektu se ve výstupním adresáři vygeneruje soubor *[AppName]. runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="5b5d7-119">When a project is [built](../tools/dotnet-build.md), an *[appname].runtimeconfig.json* file is generated in the output directory.</span></span> <span data-ttu-id="5b5d7-120">Pokud soubor *runtimeconfig. template. JSON* existuje ve stejné složce jako soubor projektu, všechny možnosti konfigurace, které obsahuje, jsou sloučeny do souboru *[název_aplikace]. runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="5b5d7-120">If a *runtimeconfig.template.json* file exists in the same folder as the project file, any configuration options it contains are merged into the *[appname].runtimeconfig.json* file.</span></span> <span data-ttu-id="5b5d7-121">Pokud vytváříte aplikaci sami, vložte do souboru *runtimeconfig. template. JSON* všechny možnosti konfigurace.</span><span class="sxs-lookup"><span data-stu-id="5b5d7-121">If you're building the app yourself, put any configuration options in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="5b5d7-122">Pokud jste právě spustili aplikaci, vložte ji přímo do souboru *[název_aplikace]. runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="5b5d7-122">If you're just running the app, insert them directly into the *[appname].runtimeconfig.json* file.</span></span>

> [!NOTE]
> <span data-ttu-id="5b5d7-123">Soubor *[AppName]. runtimeconfig. JSON* se přepíše v následných sestaveních.</span><span class="sxs-lookup"><span data-stu-id="5b5d7-123">The *[appname].runtimeconfig.json* file will get overwritten on subsequent builds.</span></span>

<span data-ttu-id="5b5d7-124">Zadejte možnosti konfigurace modulu runtime v části **configProperties** souborů *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="5b5d7-124">Specify run-time configuration options in the **configProperties** section of the *runtimeconfig.json* files.</span></span> <span data-ttu-id="5b5d7-125">Tato část obsahuje formulář:</span><span class="sxs-lookup"><span data-stu-id="5b5d7-125">This section has the form:</span></span>

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a><span data-ttu-id="5b5d7-126">Příklad souboru [AppName]. runtimeconfig. JSON</span><span class="sxs-lookup"><span data-stu-id="5b5d7-126">Example [appname].runtimeconfig.json file</span></span>

<span data-ttu-id="5b5d7-127">Pokud umístíte možnosti do výstupního souboru JSON, zanořit je do `runtimeOptions` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5b5d7-127">If you're placing the options in the output JSON file, nest them under the `runtimeOptions` property.</span></span>

```json
{
  "runtimeOptions": {
    "tfm": "netcoreapp3.1",
    "framework": {
      "name": "Microsoft.NETCore.App",
      "version": "3.1.0"
    },
    "configProperties": {
      "System.GC.Concurrent": false,
      "System.Threading.ThreadPool.MinThreads": 4,
      "System.Threading.ThreadPool.MaxThreads": 25
    }
  }
}
```

### <a name="example-runtimeconfigtemplatejson-file"></a><span data-ttu-id="5b5d7-128">Příklad souboru runtimeconfig. template. JSON</span><span class="sxs-lookup"><span data-stu-id="5b5d7-128">Example runtimeconfig.template.json file</span></span>

<span data-ttu-id="5b5d7-129">Pokud umístíte možnosti do souboru JSON šablony, vynechejte `runtimeOptions` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5b5d7-129">If you're placing the options in the template JSON file, omit the `runtimeOptions` property.</span></span>

```json
{
  "configProperties": {
    "System.GC.Concurrent": false,
    "System.Threading.ThreadPool.MinThreads": "4",
    "System.Threading.ThreadPool.MaxThreads": "25"
  }
}
```

## <a name="msbuild-properties"></a><span data-ttu-id="5b5d7-130">vlastnosti nástroje MSBuild</span><span class="sxs-lookup"><span data-stu-id="5b5d7-130">MSBuild properties</span></span>

<span data-ttu-id="5b5d7-131">Některé možnosti konfigurace modulu runtime lze nastavit pomocí vlastností nástroje MSBuild v souboru *. csproj* nebo *. vbproj* v projektech .NET Core ve stylu sady SDK.</span><span class="sxs-lookup"><span data-stu-id="5b5d7-131">Some run-time configuration options can be set using MSBuild properties in the *.csproj* or *.vbproj* file of SDK-style .NET Core projects.</span></span> <span data-ttu-id="5b5d7-132">Vlastnosti nástroje MSBuild mají přednost před možnostmi nastavenými v souboru *runtimeconfig. template. JSON* .</span><span class="sxs-lookup"><span data-stu-id="5b5d7-132">MSBuild properties take precedence over options set in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="5b5d7-133">Přepíší také všechny možnosti, které jste nastavili v souboru *[název_aplikace]. runtimeconfig. JSON* v době sestavení.</span><span class="sxs-lookup"><span data-stu-id="5b5d7-133">They also overwrite any options you set in the *[appname].runtimeconfig.json* file at build time.</span></span>

<span data-ttu-id="5b5d7-134">Zde je příklad souboru projektu ve stylu sady SDK s vlastnostmi MSBuild pro konfiguraci chování za běhu:</span><span class="sxs-lookup"><span data-stu-id="5b5d7-134">Here is an example SDK-style project file with MSBuild properties for configuring run-time behavior:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
    <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="5b5d7-135">Vlastnosti nástroje MSBuild pro konfiguraci chování za běhu jsou uvedeny v jednotlivých článcích pro každou oblast, například [uvolňování paměti](garbage-collector.md).</span><span class="sxs-lookup"><span data-stu-id="5b5d7-135">MSBuild properties for configuring run-time behavior are noted in the individual articles for each area, for example, [garbage collection](garbage-collector.md).</span></span>

## <a name="environment-variables"></a><span data-ttu-id="5b5d7-136">Proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="5b5d7-136">Environment variables</span></span>

<span data-ttu-id="5b5d7-137">Proměnné prostředí lze použít k poskytnutí některých informací o konfiguraci run-time.</span><span class="sxs-lookup"><span data-stu-id="5b5d7-137">Environment variables can be used to supply some run-time configuration information.</span></span> <span data-ttu-id="5b5d7-138">Konfigurační ovladače zadané jako proměnné prostředí mají obecně předponu **COMPlus_**.</span><span class="sxs-lookup"><span data-stu-id="5b5d7-138">Configuration knobs specified as environment variables generally have the prefix **COMPlus_**.</span></span>

<span data-ttu-id="5b5d7-139">Můžete definovat proměnné prostředí z ovládacích panelů systému Windows, na příkazovém řádku nebo programově voláním <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> metody v systémech Windows i UNIX.</span><span class="sxs-lookup"><span data-stu-id="5b5d7-139">You can define environment variables from the Windows Control Panel, at the command line, or programmatically by calling the <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> method on both Windows and Unix-based systems.</span></span>

<span data-ttu-id="5b5d7-140">Následující příklady ukazují, jak nastavit proměnnou prostředí na příkazovém řádku:</span><span class="sxs-lookup"><span data-stu-id="5b5d7-140">The following examples show how to set an environment variable at the command line:</span></span>

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
