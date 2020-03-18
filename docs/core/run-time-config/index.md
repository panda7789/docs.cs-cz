---
title: Možnosti konfigurace za běhu
description: Zjistěte, jak nakonfigurovat aplikace .NET Core pomocí nastavení konfigurace za běhu.
ms.date: 01/21/2020
ms.openlocfilehash: ddf68c30e620a06856f65e71bd050e1b77618f20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399159"
---
# <a name="net-core-run-time-configuration-settings"></a><span data-ttu-id="a608d-103">Nastavení konfigurace jádra .NET</span><span class="sxs-lookup"><span data-stu-id="a608d-103">.NET Core run-time configuration settings</span></span>

<span data-ttu-id="a608d-104">Rozhraní .NET Core podporuje použití konfiguračních souborů a proměnných prostředí ke konfiguraci chování aplikací .NET Core za běhu.</span><span class="sxs-lookup"><span data-stu-id="a608d-104">.NET Core supports the use of configuration files and environment variables to configure the behavior of .NET Core applications at run time.</span></span> <span data-ttu-id="a608d-105">Konfigurace za běhu je atraktivní volbou, pokud:</span><span class="sxs-lookup"><span data-stu-id="a608d-105">Run-time configuration is an attractive option if:</span></span>

- <span data-ttu-id="a608d-106">Nevlastníte ani neřídíte zdrojový kód aplikace, a proto jej nelze programově konfigurovat.</span><span class="sxs-lookup"><span data-stu-id="a608d-106">You don't own or control the source code for an application and therefore are unable to configure it programmatically.</span></span>

- <span data-ttu-id="a608d-107">Více instancí aplikace spustit současně v jednom systému a chcete nakonfigurovat každý pro optimální výkon.</span><span class="sxs-lookup"><span data-stu-id="a608d-107">Multiple instances of your application run at the same time on a single system, and you want to configure each for optimum performance.</span></span>

> [!NOTE]
> <span data-ttu-id="a608d-108">Tato dokumentace je nedokončená práce.</span><span class="sxs-lookup"><span data-stu-id="a608d-108">This documentation is a work in progress.</span></span> <span data-ttu-id="a608d-109">Pokud zjistíte, že zde uvedené informace jsou neúplné nebo nepřesné, [otevřete problém,](https://github.com/dotnet/docs/issues) abyste nám o tom měli vědět, nebo [odešlete žádost o přijetí informací](https://github.com/dotnet/docs/pulls) k řešení problému.</span><span class="sxs-lookup"><span data-stu-id="a608d-109">If you notice that the information presented here is either incomplete or inaccurate, either [open an issue](https://github.com/dotnet/docs/issues) to let us know about it, or [submit a pull request](https://github.com/dotnet/docs/pulls) to address the issue.</span></span> <span data-ttu-id="a608d-110">Informace o odesílání žádostí o přijetí vyžádat pro úložiště dotnet/docs naleznete v [příručce přispěvatele](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span><span class="sxs-lookup"><span data-stu-id="a608d-110">For information about submitting pull requests for the dotnet/docs repository, see the [contributor's guide](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span></span>

<span data-ttu-id="a608d-111">Jádro .NET poskytuje následující mechanismy pro konfiguraci chování aplikací za běhu:</span><span class="sxs-lookup"><span data-stu-id="a608d-111">.NET Core provides the following mechanisms for configuring run-time application behavior:</span></span>

- <span data-ttu-id="a608d-112">[Soubor runtimeconfig.json](#runtimeconfigjson)</span><span class="sxs-lookup"><span data-stu-id="a608d-112">The [runtimeconfig.json file](#runtimeconfigjson)</span></span>

- [<span data-ttu-id="a608d-113">Vlastnosti MSBuild</span><span class="sxs-lookup"><span data-stu-id="a608d-113">MSBuild properties</span></span>](#msbuild-properties)

- [<span data-ttu-id="a608d-114">Proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="a608d-114">Environment variables</span></span>](#environment-variables)

<span data-ttu-id="a608d-115">Některé hodnoty konfigurace lze také nastavit programově voláním <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="a608d-115">Some configuration values can also be set programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="a608d-116">Články v této části dokumentace jsou uspořádány podle kategorie, například [ladění](debugging-profiling.md) a [uvolňování paměti](garbage-collector.md).</span><span class="sxs-lookup"><span data-stu-id="a608d-116">The articles in this section of the documentation are organized by category, for example, [debugging](debugging-profiling.md) and [garbage collection](garbage-collector.md).</span></span> <span data-ttu-id="a608d-117">V příslušných případech jsou zobrazeny možnosti konfigurace pro soubory *runtimeconfig.json,* vlastnosti MSBuild, proměnné prostředí a pro křížový odkaz soubory *app.config* pro projekty rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a608d-117">Where applicable, configuration options are shown for *runtimeconfig.json* files, MSBuild properties, environment variables, and, for cross-reference, *app.config* files for .NET Framework projects.</span></span>

## <a name="runtimeconfigjson"></a><span data-ttu-id="a608d-118">runtimeconfig.json</span><span class="sxs-lookup"><span data-stu-id="a608d-118">runtimeconfig.json</span></span>

<span data-ttu-id="a608d-119">Při [vytváření](../tools/dotnet-build.md)projektu je ve výstupním adresáři generován soubor *[appname].runtimeconfig.json.*</span><span class="sxs-lookup"><span data-stu-id="a608d-119">When a project is [built](../tools/dotnet-build.md), an *[appname].runtimeconfig.json* file is generated in the output directory.</span></span> <span data-ttu-id="a608d-120">Pokud soubor *runtimeconfig.template.json* existuje ve stejné složce jako soubor projektu, všechny možnosti konfigurace, které obsahuje, jsou sloučeny do souboru *[appname].runtimeconfig.json.*</span><span class="sxs-lookup"><span data-stu-id="a608d-120">If a *runtimeconfig.template.json* file exists in the same folder as the project file, any configuration options it contains are merged into the *[appname].runtimeconfig.json* file.</span></span> <span data-ttu-id="a608d-121">Pokud vytváříte aplikaci sami, vložte všechny možnosti konfigurace do souboru *runtimeconconfig.template.json.*</span><span class="sxs-lookup"><span data-stu-id="a608d-121">If you're building the app yourself, put any configuration options in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="a608d-122">Pokud právě spouštěte aplikaci, vložte je přímo do souboru *[appname].runtimeconfig.json.*</span><span class="sxs-lookup"><span data-stu-id="a608d-122">If you're just running the app, insert them directly into the *[appname].runtimeconfig.json* file.</span></span>

> [!NOTE]
> <span data-ttu-id="a608d-123">Soubor *[appname].runtimeconfig.json* bude přepsán na následujícísestavení.</span><span class="sxs-lookup"><span data-stu-id="a608d-123">The *[appname].runtimeconfig.json* file will get overwritten on subsequent builds.</span></span>

<span data-ttu-id="a608d-124">V části **configProperties** souborů *runtimeconfig.json* určete možnosti konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a608d-124">Specify run-time configuration options in the **configProperties** section of the *runtimeconfig.json* files.</span></span> <span data-ttu-id="a608d-125">Tato část má formulář:</span><span class="sxs-lookup"><span data-stu-id="a608d-125">This section has the form:</span></span>

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a><span data-ttu-id="a608d-126">Příklad souboru [appname].runtimeconfig.json</span><span class="sxs-lookup"><span data-stu-id="a608d-126">Example [appname].runtimeconfig.json file</span></span>

<span data-ttu-id="a608d-127">Pokud umisťujete možnosti do výstupního souboru JSON, vnořte je pod `runtimeOptions` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a608d-127">If you're placing the options in the output JSON file, nest them under the `runtimeOptions` property.</span></span>

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

### <a name="example-runtimeconfigtemplatejson-file"></a><span data-ttu-id="a608d-128">Příklad souboru runtimeconfig.template.json</span><span class="sxs-lookup"><span data-stu-id="a608d-128">Example runtimeconfig.template.json file</span></span>

<span data-ttu-id="a608d-129">Pokud umisťujete možnosti do souboru Šablony `runtimeOptions` JSON, vyneche vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a608d-129">If you're placing the options in the template JSON file, omit the `runtimeOptions` property.</span></span>

```json
{
  "configProperties": {
    "System.GC.Concurrent": false,
    "System.Threading.ThreadPool.MinThreads": "4",
    "System.Threading.ThreadPool.MaxThreads": "25"
  }
}
```

## <a name="msbuild-properties"></a><span data-ttu-id="a608d-130">vlastnosti nástroje MSBuild</span><span class="sxs-lookup"><span data-stu-id="a608d-130">MSBuild properties</span></span>

<span data-ttu-id="a608d-131">Některé možnosti konfigurace za běhu lze nastavit pomocí vlastností MSBuild v souboru *.csproj* nebo *.vbproj* projektů .NET Core ve stylu sady SDK.</span><span class="sxs-lookup"><span data-stu-id="a608d-131">Some run-time configuration options can be set using MSBuild properties in the *.csproj* or *.vbproj* file of SDK-style .NET Core projects.</span></span> <span data-ttu-id="a608d-132">Vlastnosti MSBuild mají přednost před možnostmi nastaveným v souboru *runtimeconfig.template.json.*</span><span class="sxs-lookup"><span data-stu-id="a608d-132">MSBuild properties take precedence over options set in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="a608d-133">Také přepsat všechny možnosti, které nastavíte v souboru *[appname].runtimeconfig.json* v době sestavení.</span><span class="sxs-lookup"><span data-stu-id="a608d-133">They also overwrite any options you set in the *[appname].runtimeconfig.json* file at build time.</span></span>

<span data-ttu-id="a608d-134">Zde je příklad souboru projektu ve stylu sady SDK s vlastnostmi msbuild pro konfiguraci chování za běhu:</span><span class="sxs-lookup"><span data-stu-id="a608d-134">Here is an example SDK-style project file with MSBuild properties for configuring run-time behavior:</span></span>

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

<span data-ttu-id="a608d-135">Vlastnosti MSBuild pro konfiguraci chování za běhu jsou uvedeny v jednotlivých článcích pro každou oblast, například [uvolňování paměti](garbage-collector.md).</span><span class="sxs-lookup"><span data-stu-id="a608d-135">MSBuild properties for configuring run-time behavior are noted in the individual articles for each area, for example, [garbage collection](garbage-collector.md).</span></span>

## <a name="environment-variables"></a><span data-ttu-id="a608d-136">Proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="a608d-136">Environment variables</span></span>

<span data-ttu-id="a608d-137">Proměnné prostředí lze použít k zadání některých informací o konfiguraci za běhu.</span><span class="sxs-lookup"><span data-stu-id="a608d-137">Environment variables can be used to supply some run-time configuration information.</span></span> <span data-ttu-id="a608d-138">Konfigurační knoflíky určené jako proměnné prostředí mají obecně předponu **COMPlus_**.</span><span class="sxs-lookup"><span data-stu-id="a608d-138">Configuration knobs specified as environment variables generally have the prefix **COMPlus_**.</span></span>

<span data-ttu-id="a608d-139">Proměnné prostředí můžete definovat z Ovládacích panelů systému Windows na příkazovém řádku nebo programově voláním <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> metody v systémech Windows i Unix.</span><span class="sxs-lookup"><span data-stu-id="a608d-139">You can define environment variables from the Windows Control Panel, at the command line, or programmatically by calling the <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> method on both Windows and Unix-based systems.</span></span>

<span data-ttu-id="a608d-140">Následující příklady ukazují, jak nastavit proměnnou prostředí na příkazovém řádku:</span><span class="sxs-lookup"><span data-stu-id="a608d-140">The following examples show how to set an environment variable at the command line:</span></span>

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
