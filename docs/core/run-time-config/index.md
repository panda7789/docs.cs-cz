---
title: Konfigurace run-time
description: Naučte se konfigurovat aplikace .NET Core pomocí nastavení konfigurace za běhu.
ms.date: 11/13/2019
ms.openlocfilehash: e3922f6df81198b5e122f16d5cfc4b6d15cbb4ae
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567381"
---
# <a name="net-core-run-time-configuration-settings"></a><span data-ttu-id="4ad58-103">Nastavení konfigurace runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="4ad58-103">.NET Core run-time configuration settings</span></span>

<span data-ttu-id="4ad58-104">.NET Core podporuje použití konfiguračních souborů a proměnných prostředí ke konfiguraci chování aplikací .NET Core v době běhu.</span><span class="sxs-lookup"><span data-stu-id="4ad58-104">.NET Core supports the use of configuration files and environment variables to configure the behavior of .NET Core applications at run time.</span></span> <span data-ttu-id="4ad58-105">Konfigurace běhového běhu je atraktivní možnost, pokud:</span><span class="sxs-lookup"><span data-stu-id="4ad58-105">Run-time configuration is an attractive option if:</span></span>

- <span data-ttu-id="4ad58-106">Zdrojový kód aplikace nevlastníte nebo neovládáte, a proto ji nelze programově nakonfigurovat.</span><span class="sxs-lookup"><span data-stu-id="4ad58-106">You don't own or control the source code for an application and therefore are unable to configure it programmatically.</span></span>

- <span data-ttu-id="4ad58-107">V jednom systému se spouští více instancí aplikace současně a chcete je nakonfigurovat pro optimální výkon.</span><span class="sxs-lookup"><span data-stu-id="4ad58-107">Multiple instances of your application run at the same time on a single system, and you want to configure each for optimum performance.</span></span>

> [!NOTE]
> <span data-ttu-id="4ad58-108">Tato dokumentace je probíhající práce.</span><span class="sxs-lookup"><span data-stu-id="4ad58-108">This documentation is a work in progress.</span></span> <span data-ttu-id="4ad58-109">Pokud si všimnete, že zde uvedené informace jsou buď neúplné, nebo nepřesné, buď [otevřete problém](https://github.com/dotnet/docs/issues) , abychom nás věděli, nebo [odešlete žádost](https://github.com/dotnet/docs/pulls) o přijetí změn k vyřešení problému.</span><span class="sxs-lookup"><span data-stu-id="4ad58-109">If you notice that the information presented here is either incomplete or inaccurate, either [open an issue](https://github.com/dotnet/docs/issues) to let us know about it, or [submit a pull request](https://github.com/dotnet/docs/pulls) to address the issue.</span></span> <span data-ttu-id="4ad58-110">Informace o odesílání žádostí o přijetí změn pro úložiště dotnet/docs najdete v [příručce pro přispěvatele](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span><span class="sxs-lookup"><span data-stu-id="4ad58-110">For information on submitting pull requests for the dotnet/docs repository, see the [contributor's guide](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span></span>

<span data-ttu-id="4ad58-111">.NET Core poskytuje následující mechanismy pro konfiguraci aplikací v době běhu:</span><span class="sxs-lookup"><span data-stu-id="4ad58-111">.NET Core provides the following mechanisms for configuring applications at run time:</span></span>

- <span data-ttu-id="4ad58-112">[Soubor runtimeconfig. JSON](#runtimeconfigjson)</span><span class="sxs-lookup"><span data-stu-id="4ad58-112">The [runtimeconfig.json file](#runtimeconfigjson)</span></span>

- [<span data-ttu-id="4ad58-113">Proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="4ad58-113">Environment variables</span></span>](#environment-variables)

<span data-ttu-id="4ad58-114">Články v této části dokumentace jsou uspořádány podle kategorie, například ladění a uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="4ad58-114">The articles in this section of the documentation include are organized by category, for example, debugging and garbage collection.</span></span> <span data-ttu-id="4ad58-115">Pro *runtimeconfig. JSON* se zobrazí dostupné možnosti konfigurace (jenom .NET Core), *App. config* (jenom .NET Framework) a proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="4ad58-115">Available configuration options are shown for *runtimeconfig.json* (.NET Core only), *app.config* (.NET Framework only), and environment variables.</span></span>

## <a name="runtimeconfigjson"></a><span data-ttu-id="4ad58-116">runtimeconfig. JSON</span><span class="sxs-lookup"><span data-stu-id="4ad58-116">runtimeconfig.json</span></span>

<span data-ttu-id="4ad58-117">Zadejte možnosti konfigurace modulu runtime v části **configProperties** souboru *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="4ad58-117">Specify run-time configuration options in the **configProperties** section of the *runtimeconfig.json* file.</span></span> <span data-ttu-id="4ad58-118">Tato část obsahuje formulář:</span><span class="sxs-lookup"><span data-stu-id="4ad58-118">This section has the form:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "config-property-name1": "config-value1",
         "config-property-name2": "config-value2"
      }
   }
}
```

<span data-ttu-id="4ad58-119">Tady je příklad souboru:</span><span class="sxs-lookup"><span data-stu-id="4ad58-119">Here is an example file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": true,
         "System.GC.RetainVM": true,
         "System.Threading.ThreadPool.MinThreads": "4",
         "System.Threading.ThreadPool.MaxThreads": "25"
      }
   }
}
```

<span data-ttu-id="4ad58-120">Soubor *runtimeconfig. JSON* se automaticky vytvoří v adresáři buildu pomocí příkazu [dotnet Build](../tools/dotnet-build.md) .</span><span class="sxs-lookup"><span data-stu-id="4ad58-120">The *runtimeconfig.json* file is automatically created in the build directory by the [dotnet build](../tools/dotnet-build.md) command.</span></span> <span data-ttu-id="4ad58-121">Vytvoří se také při výběru možnosti nabídky **sestavení** v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4ad58-121">It's also created when you select the **Build** menu option in Visual Studio.</span></span> <span data-ttu-id="4ad58-122">Po vytvoření můžete soubor upravit.</span><span class="sxs-lookup"><span data-stu-id="4ad58-122">You can then edit the file once it's created.</span></span>

<span data-ttu-id="4ad58-123">Některé hodnoty konfigurace lze také nastavit programově voláním metody <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4ad58-123">Some configuration values can also be set programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

## <a name="environment-variables"></a><span data-ttu-id="4ad58-124">Proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="4ad58-124">Environment variables</span></span>

<span data-ttu-id="4ad58-125">Proměnné prostředí lze použít k poskytnutí některých informací o konfiguraci run-time.</span><span class="sxs-lookup"><span data-stu-id="4ad58-125">Environment variables can be used to supply some run-time configuration information.</span></span> <span data-ttu-id="4ad58-126">Konfigurační ovladače zadané jako proměnné prostředí mají obecně předponu **COMPlus_** .</span><span class="sxs-lookup"><span data-stu-id="4ad58-126">Configuration knobs specified as environment variables generally have the prefix **COMPlus_**.</span></span>

<span data-ttu-id="4ad58-127">Můžete definovat proměnné prostředí z ovládacích panelů systému Windows, na příkazovém řádku nebo programově voláním metody <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> v systémech Windows a UNIX.</span><span class="sxs-lookup"><span data-stu-id="4ad58-127">You can define environment variables from the Windows Control Panel, at the command line, or programmatically by calling the <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> method on both Windows and Unix-based systems.</span></span>

<span data-ttu-id="4ad58-128">Následující příklady ukazují, jak nastavit proměnnou prostředí na příkazovém řádku:</span><span class="sxs-lookup"><span data-stu-id="4ad58-128">The following examples show how to set an environment variable at the command line:</span></span>

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
