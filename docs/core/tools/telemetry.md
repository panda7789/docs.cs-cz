---
title: Telemetrie .NET Core SDK
description: Objevte funkce telemetrie .NET Core SDK, které shromažďují informace o využití pro analýzu, shromažďovaná data a jejich zakázání.
author: KathleenDollard
ms.date: 08/27/2019
ms.openlocfilehash: abc9f8e1ef134ebfb5ec9acacb629d5180aaf83b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77625914"
---
# <a name="net-core-sdk-telemetry"></a><span data-ttu-id="a6546-103">Telemetrie .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="a6546-103">.NET Core SDK telemetry</span></span>

<span data-ttu-id="a6546-104">[.NET Core SDK](index.md) obsahuje funkci telemetrie, která shromažďuje data o využití a informace o výjimkách při selhání .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="a6546-104">The [.NET Core SDK](index.md) includes a telemetry feature that collects usage data and exception information when the .NET Core CLI crashes.</span></span> <span data-ttu-id="a6546-105">.NET Core CLI se dodává s .NET Core SDK a je to sada operací, které umožňují sestavovat, testovat a publikovat aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a6546-105">The .NET Core CLI comes with the .NET Core SDK and is the set of verbs that enable you to build, test, and publish your .NET Core apps.</span></span> <span data-ttu-id="a6546-106">Je důležité, aby tým .NET pochopil, jak se nástroje používají, aby bylo možné je zlepšit.</span><span class="sxs-lookup"><span data-stu-id="a6546-106">It's important that the .NET team understands how the tools are used so they can be improved.</span></span> <span data-ttu-id="a6546-107">Informace o selháních pomáhají týmu vyřešit problémy a opravovat chyby.</span><span class="sxs-lookup"><span data-stu-id="a6546-107">Information on failures helps the team resolve problems and fix bugs.</span></span>

<span data-ttu-id="a6546-108">Shromážděná data jsou anonymní a publikovaná v rámci [licence Creative](https://creativecommons.org/licenses/by/4.0/)navýšení.</span><span class="sxs-lookup"><span data-stu-id="a6546-108">The collected data is anonymous and published in aggregate under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span> 

## <a name="scope"></a><span data-ttu-id="a6546-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="a6546-109">Scope</span></span>

<span data-ttu-id="a6546-110">`dotnet` má dvě funkce: ke spuštění aplikací a k provádění příkazů rozhraní příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a6546-110">`dotnet` has two functions: to run apps, and to execute CLI commands.</span></span> <span data-ttu-id="a6546-111">Při použití `dotnet` k spuštění aplikace v následujícím formátu *není shromažďována* telemetrie:</span><span class="sxs-lookup"><span data-stu-id="a6546-111">Telemetry *isn't collected* when using `dotnet` to start an application in the following format:</span></span>

- `dotnet [path-to-app].dll`

<span data-ttu-id="a6546-112">Telemetrie *se shromáždí* při použití některého z [.NET Core CLI příkazů](index.md), jako je například:</span><span class="sxs-lookup"><span data-stu-id="a6546-112">Telemetry *is collected* when using any of the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet run`

## <a name="how-to-opt-out"></a><span data-ttu-id="a6546-113">Jak odhlásit</span><span class="sxs-lookup"><span data-stu-id="a6546-113">How to opt out</span></span>

<span data-ttu-id="a6546-114">Funkce telemetrie .NET Core SDK je ve výchozím nastavení povolená.</span><span class="sxs-lookup"><span data-stu-id="a6546-114">The .NET Core SDK telemetry feature is enabled by default.</span></span> <span data-ttu-id="a6546-115">Pokud se chcete odhlásit od funkce telemetrie, nastavte proměnnou prostředí `DOTNET_CLI_TELEMETRY_OPTOUT` na `1` nebo `true`.</span><span class="sxs-lookup"><span data-stu-id="a6546-115">To opt out of the telemetry feature, set the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span> 

<span data-ttu-id="a6546-116">V případě, že dojde k úspěšné instalaci, posílá instalační program .NET Core SDK také jednu položku telemetrie.</span><span class="sxs-lookup"><span data-stu-id="a6546-116">A single telemetry entry is also sent by the .NET Core SDK installer when a successful installation happens.</span></span> <span data-ttu-id="a6546-117">Chcete-li se odhlásit, nastavte před instalací .NET Core SDK proměnnou prostředí `DOTNET_CLI_TELEMETRY_OPTOUT`.</span><span class="sxs-lookup"><span data-stu-id="a6546-117">To opt out, set the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable before you install the .NET Core SDK.</span></span>

## <a name="disclosure"></a><span data-ttu-id="a6546-118">Námitk</span><span class="sxs-lookup"><span data-stu-id="a6546-118">Disclosure</span></span>

<span data-ttu-id="a6546-119">Při prvním spuštění jednoho z [příkazů .NET Core CLI](index.md) (například `dotnet build`) zobrazí .NET Core SDK text podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="a6546-119">The .NET Core SDK displays text similar to the following when you first run one of the [.NET Core CLI commands](index.md) (for example, `dotnet build`).</span></span> <span data-ttu-id="a6546-120">Text se může v závislosti na verzi sady SDK, kterou používáte, mírně lišit.</span><span class="sxs-lookup"><span data-stu-id="a6546-120">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="a6546-121">Toto je postup "prvního spuštění", který vás Microsoft upozorní na shromažďování dat.</span><span class="sxs-lookup"><span data-stu-id="a6546-121">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

```console
Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience. The data is anonymous. It is collected by Microsoft and shared with the community. You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

## <a name="data-points"></a><span data-ttu-id="a6546-122">Datové body</span><span class="sxs-lookup"><span data-stu-id="a6546-122">Data points</span></span>

<span data-ttu-id="a6546-123">Funkce telemetrie neshromažďuje osobní údaje, jako jsou uživatelská jména nebo e-mailové adresy.</span><span class="sxs-lookup"><span data-stu-id="a6546-123">The telemetry feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="a6546-124">Nekontroluje váš kód a neextrahuje data na úrovni projektu, jako je název, úložiště nebo autor.</span><span class="sxs-lookup"><span data-stu-id="a6546-124">It doesn't scan your code and doesn't extract project-level data, such as name, repository, or author.</span></span> <span data-ttu-id="a6546-125">Data se odesílají zabezpečeně na servery Microsoftu pomocí [Azure monitor](https://azure.microsoft.com/services/monitor/) technologie, která se drží pod omezeným přístupem, a publikují se v rámci striktních bezpečnostních mechanismů pro [Azure Storage](https://azure.microsoft.com/services/storage/) systémy.</span><span class="sxs-lookup"><span data-stu-id="a6546-125">The data is sent securely to Microsoft servers using [Azure Monitor](https://azure.microsoft.com/services/monitor/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="a6546-126">Ochrana vašich osobních údajů je pro nás důležitá.</span><span class="sxs-lookup"><span data-stu-id="a6546-126">Protecting your privacy is important to us.</span></span> <span data-ttu-id="a6546-127">Pokud máte podezření, že telemetrie shromažďuje citlivá data, nebo jsou data nezabezpečená nebo nevhodně zpracovaná, zapište problém do úložiště [dotnet/CLI](https://github.com/dotnet/cli/issues) nebo odešlete e-mail [dotnet@microsoft.com](mailto:dotnet@microsoft.com) k šetření.</span><span class="sxs-lookup"><span data-stu-id="a6546-127">If you suspect the telemetry is collecting sensitive data or the data is being insecurely or inappropriately handled, file an issue in the [dotnet/cli](https://github.com/dotnet/cli/issues) repository or send an email to [dotnet@microsoft.com](mailto:dotnet@microsoft.com) for investigation.</span></span>

<span data-ttu-id="a6546-128">Funkce telemetrie shromažďuje následující data:</span><span class="sxs-lookup"><span data-stu-id="a6546-128">The telemetry feature collects the following data:</span></span>

| <span data-ttu-id="a6546-129">Verze sady SDK</span><span class="sxs-lookup"><span data-stu-id="a6546-129">SDK versions</span></span> | <span data-ttu-id="a6546-130">Data</span><span class="sxs-lookup"><span data-stu-id="a6546-130">Data</span></span> |
|--------------|------|
| <span data-ttu-id="a6546-131">Vše</span><span class="sxs-lookup"><span data-stu-id="a6546-131">All</span></span>          | <span data-ttu-id="a6546-132">Časové razítko vyvolání</span><span class="sxs-lookup"><span data-stu-id="a6546-132">Timestamp of invocation.</span></span> |
| <span data-ttu-id="a6546-133">Vše</span><span class="sxs-lookup"><span data-stu-id="a6546-133">All</span></span>          | <span data-ttu-id="a6546-134">Byl vyvolán příkaz (například "Build"), který začíná hodnotou hash 2,1.</span><span class="sxs-lookup"><span data-stu-id="a6546-134">Command invoked (for example, "build"), hashed starting in 2.1.</span></span> |
| <span data-ttu-id="a6546-135">Vše</span><span class="sxs-lookup"><span data-stu-id="a6546-135">All</span></span>          | <span data-ttu-id="a6546-136">Tři oktety, které se používají k určení geografického umístění.</span><span class="sxs-lookup"><span data-stu-id="a6546-136">Three octet IP address used to determine the geographical location.</span></span> |
| <span data-ttu-id="a6546-137">Vše</span><span class="sxs-lookup"><span data-stu-id="a6546-137">All</span></span>          | <span data-ttu-id="a6546-138">Operační systém a verze.</span><span class="sxs-lookup"><span data-stu-id="a6546-138">Operating system and version.</span></span> |
| <span data-ttu-id="a6546-139">Vše</span><span class="sxs-lookup"><span data-stu-id="a6546-139">All</span></span>          | <span data-ttu-id="a6546-140">ID modulu runtime (RID), na kterém je sada SDK spuštěná.</span><span class="sxs-lookup"><span data-stu-id="a6546-140">Runtime ID (RID) the SDK is running on.</span></span> |
| <span data-ttu-id="a6546-141">Vše</span><span class="sxs-lookup"><span data-stu-id="a6546-141">All</span></span>          | <span data-ttu-id="a6546-142">Verze .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="a6546-142">.NET Core SDK version.</span></span> |
| <span data-ttu-id="a6546-143">Vše</span><span class="sxs-lookup"><span data-stu-id="a6546-143">All</span></span>          | <span data-ttu-id="a6546-144">Profil telemetrie: volitelná hodnota se používá jenom s výslovným výslovným souhlasem uživatele a používá se interně v Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="a6546-144">Telemetry profile: an optional value only used with explicit user opt-in and used internally at Microsoft.</span></span> |
| <span data-ttu-id="a6546-145">> = 2.0</span><span class="sxs-lookup"><span data-stu-id="a6546-145">>=2.0</span></span>        | <span data-ttu-id="a6546-146">Argumenty a možnosti příkazu: několik argumentů a možností je shromažďováno (nejedná se o libovolný řetězec).</span><span class="sxs-lookup"><span data-stu-id="a6546-146">Command arguments and options: several arguments and options are collected (not arbitrary strings).</span></span> <span data-ttu-id="a6546-147">Viz [shromážděné možnosti](#collected-options).</span><span class="sxs-lookup"><span data-stu-id="a6546-147">See [collected options](#collected-options).</span></span> <span data-ttu-id="a6546-148">Hodnota hash po 2.1.300</span><span class="sxs-lookup"><span data-stu-id="a6546-148">Hashed after 2.1.300.</span></span> |
| <span data-ttu-id="a6546-149">> = 2.0</span><span class="sxs-lookup"><span data-stu-id="a6546-149">>=2.0</span></span>         | <span data-ttu-id="a6546-150">Určuje, jestli je sada SDK spuštěná v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="a6546-150">Whether the SDK is running in a container.</span></span> |
| <span data-ttu-id="a6546-151">> = 2.0</span><span class="sxs-lookup"><span data-stu-id="a6546-151">>=2.0</span></span>         | <span data-ttu-id="a6546-152">Cílové architektury (z události `TargetFramework`), které začínají algoritmem hash 2,1.</span><span class="sxs-lookup"><span data-stu-id="a6546-152">Target frameworks (from the `TargetFramework` event), hashed starting in 2.1.</span></span> |
| <span data-ttu-id="a6546-153">> = 2.0</span><span class="sxs-lookup"><span data-stu-id="a6546-153">>=2.0</span></span>         | <span data-ttu-id="a6546-154">Adresa MAC Access Control médií (MAC): kryptograficky (SHA256) anonymní a jedinečné ID pro počítač.</span><span class="sxs-lookup"><span data-stu-id="a6546-154">Hashed Media Access Control (MAC) address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> |
| <span data-ttu-id="a6546-155">> = 2.0</span><span class="sxs-lookup"><span data-stu-id="a6546-155">>=2.0</span></span>         | <span data-ttu-id="a6546-156">Aktuální pracovní adresář má hodnotu hash.</span><span class="sxs-lookup"><span data-stu-id="a6546-156">Hashed current working directory.</span></span> |
| <span data-ttu-id="a6546-157">> = 2.0</span><span class="sxs-lookup"><span data-stu-id="a6546-157">>=2.0</span></span>         | <span data-ttu-id="a6546-158">Sestava úspěšné instalace s názvem souboru EXE instalačního programu s algoritmem hash</span><span class="sxs-lookup"><span data-stu-id="a6546-158">Install success report, with hashed installer exe filename.</span></span> |
| <span data-ttu-id="a6546-159">> = 2.1.300</span><span class="sxs-lookup"><span data-stu-id="a6546-159">>=2.1.300</span></span>     | <span data-ttu-id="a6546-160">Verze jádra.</span><span class="sxs-lookup"><span data-stu-id="a6546-160">Kernel version.</span></span> |
| <span data-ttu-id="a6546-161">> = 2.1.300</span><span class="sxs-lookup"><span data-stu-id="a6546-161">>=2.1.300</span></span>     | <span data-ttu-id="a6546-162">Verze nebo verze LIBC.</span><span class="sxs-lookup"><span data-stu-id="a6546-162">Libc release/version.</span></span> |
| <span data-ttu-id="a6546-163">> = 3.0.100</span><span class="sxs-lookup"><span data-stu-id="a6546-163">>=3.0.100</span></span>     | <span data-ttu-id="a6546-164">Určuje, zda byl výstup přesměrován (true nebo false).</span><span class="sxs-lookup"><span data-stu-id="a6546-164">Whether the output was redirected (true or false).</span></span> |
| <span data-ttu-id="a6546-165">> = 3.0.100</span><span class="sxs-lookup"><span data-stu-id="a6546-165">>=3.0.100</span></span>     | <span data-ttu-id="a6546-166">V případě selhání CLI/SDK je typ výjimky a jeho trasování zásobníku (do odeslaného trasování zásobníku je zahrnut pouze kód CLI/SDK).</span><span class="sxs-lookup"><span data-stu-id="a6546-166">On a CLI/SDK crash, the exception type and its stack trace (only CLI/SDK code is included in the stack trace sent).</span></span> <span data-ttu-id="a6546-167">Další informace najdete v tématu [shromážděná telemetrie výjimek při selhání .NET Core CLI/SDK](#net-core-clisdk-crash-exception-telemetry-collected).</span><span class="sxs-lookup"><span data-stu-id="a6546-167">For more information, see [.NET Core CLI/SDK crash exception telemetry collected](#net-core-clisdk-crash-exception-telemetry-collected).</span></span> |

### <a name="collected-options"></a><span data-ttu-id="a6546-168">Shromážděné možnosti</span><span class="sxs-lookup"><span data-stu-id="a6546-168">Collected options</span></span>

<span data-ttu-id="a6546-169">Některé příkazy odesílají další data.</span><span class="sxs-lookup"><span data-stu-id="a6546-169">Certain commands send additional data.</span></span> <span data-ttu-id="a6546-170">Podmnožina příkazů odesílá první argument:</span><span class="sxs-lookup"><span data-stu-id="a6546-170">A subset of commands sends the first argument:</span></span>

| <span data-ttu-id="a6546-171">Příkaz</span><span class="sxs-lookup"><span data-stu-id="a6546-171">Command</span></span>               | <span data-ttu-id="a6546-172">Data prvního argumentu byla odeslána.</span><span class="sxs-lookup"><span data-stu-id="a6546-172">First argument data sent</span></span>                |
|-----------------------|-----------------------------------------|
| `dotnet help <arg>`   | <span data-ttu-id="a6546-173">Dotaz na příkaz se dotazuje na.</span><span class="sxs-lookup"><span data-stu-id="a6546-173">The command help is being queried for.</span></span>  |
| `dotnet new <arg>`    | <span data-ttu-id="a6546-174">Název šablony (s algoritmem hash)</span><span class="sxs-lookup"><span data-stu-id="a6546-174">The template name (hashed).</span></span>             |
| `dotnet add <arg>`    | <span data-ttu-id="a6546-175">Slovo `package` nebo `reference`.</span><span class="sxs-lookup"><span data-stu-id="a6546-175">The word `package` or `reference`.</span></span>      |
| `dotnet remove <arg>` | <span data-ttu-id="a6546-176">Slovo `package` nebo `reference`.</span><span class="sxs-lookup"><span data-stu-id="a6546-176">The word `package` or `reference`.</span></span>      |
| `dotnet list <arg>`   | <span data-ttu-id="a6546-177">Slovo `package` nebo `reference`.</span><span class="sxs-lookup"><span data-stu-id="a6546-177">The word `package` or `reference`.</span></span>      |
| `dotnet sln <arg>`    | <span data-ttu-id="a6546-178">Slovo `add`, `list`nebo `remove`.</span><span class="sxs-lookup"><span data-stu-id="a6546-178">The word `add`, `list`, or `remove`.</span></span>    |
| `dotnet nuget <arg>`  | <span data-ttu-id="a6546-179">Slovo `delete`, `locals`nebo `push`.</span><span class="sxs-lookup"><span data-stu-id="a6546-179">The word `delete`, `locals`, or `push`.</span></span> |

<span data-ttu-id="a6546-180">Podmnožina příkazů odesílá vybrané možnosti, pokud jsou použity, spolu s jejich hodnotami:</span><span class="sxs-lookup"><span data-stu-id="a6546-180">A subset of commands sends selected options if they're used, along with their values:</span></span>

| <span data-ttu-id="a6546-181">Možnost</span><span class="sxs-lookup"><span data-stu-id="a6546-181">Option</span></span>                  | <span data-ttu-id="a6546-182">Příkazy</span><span class="sxs-lookup"><span data-stu-id="a6546-182">Commands</span></span>                                                                                       |
|-------------------------|------------------------------------------------------------------------------------------------|
| `--verbosity`           | <span data-ttu-id="a6546-183">Všechny příkazy</span><span class="sxs-lookup"><span data-stu-id="a6546-183">All commands</span></span>                                                                                   |
| `--language`            | `dotnet new`                                                                                   |
| `--configuration`       | <span data-ttu-id="a6546-184">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run``dotnet test`</span><span class="sxs-lookup"><span data-stu-id="a6546-184">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`</span></span>                  |
| `--framework`           | <span data-ttu-id="a6546-185">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test``dotnet vstest`</span><span class="sxs-lookup"><span data-stu-id="a6546-185">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest`</span></span> |
| `--runtime`             | <span data-ttu-id="a6546-186">`dotnet build``dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="a6546-186">`dotnet build`,  `dotnet publish`</span></span>                                                              |
| `--platform`            | `dotnet vstest`                                                                                |
| `--logger`              | `dotnet vstest`                                                                                |
| `--sdk-package-version` | `dotnet migrate`                                                                               |

<span data-ttu-id="a6546-187">S výjimkou `--verbosity` a `--sdk-package-version`jsou všechny ostatní hodnoty hash od .NET Core 2.1.100 SDK.</span><span class="sxs-lookup"><span data-stu-id="a6546-187">Except for `--verbosity` and `--sdk-package-version`, all the other values are hashed starting with .NET Core 2.1.100 SDK.</span></span>

## <a name="net-core-clisdk-crash-exception-telemetry-collected"></a><span data-ttu-id="a6546-188">Shromážděná telemetrie výjimek při selhání .NET Core CLI/SDK</span><span class="sxs-lookup"><span data-stu-id="a6546-188">.NET Core CLI/SDK crash exception telemetry collected</span></span>

<span data-ttu-id="a6546-189">Pokud .NET Core CLI/SDK selže, shromažďuje název výjimky a trasování zásobníku kódu CLI/SDK.</span><span class="sxs-lookup"><span data-stu-id="a6546-189">If the .NET Core CLI/SDK crashes, it collects the name of the exception and stack trace of the CLI/SDK code.</span></span> <span data-ttu-id="a6546-190">Tyto informace jsou shromažďovány k vyhodnocení problémů a zlepšení kvality .NET Core SDK a CLI.</span><span class="sxs-lookup"><span data-stu-id="a6546-190">This information is collected to assess problems and improve the quality of the .NET Core SDK and CLI.</span></span> <span data-ttu-id="a6546-191">Tento článek poskytuje informace o datech, která shromažďujeme.</span><span class="sxs-lookup"><span data-stu-id="a6546-191">This article provides information about the data we collect.</span></span> <span data-ttu-id="a6546-192">Poskytuje také tipy k tomu, jak si uživatelé, kteří vytvářejí svou vlastní verzi .NET Core SDK, můžou zabránit nechtěnému zveřejnění osobních nebo citlivých informací.</span><span class="sxs-lookup"><span data-stu-id="a6546-192">It also provides tips on how users building their own version of the .NET Core SDK can avoid inadvertent disclosure of personal or sensitive information.</span></span>

### <a name="types-of-collected-data"></a><span data-ttu-id="a6546-193">Typy shromážděných dat</span><span class="sxs-lookup"><span data-stu-id="a6546-193">Types of collected data</span></span>

<span data-ttu-id="a6546-194">.NET Core CLI shromažďuje informace pouze o výjimkách CLI/SDK, nikoli výjimkách v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a6546-194">.NET Core CLI collects information for CLI/SDK exceptions only, not exceptions in your application.</span></span> <span data-ttu-id="a6546-195">Shromážděná data obsahují název výjimky a trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="a6546-195">The collected data contains the name of the exception and the stack trace.</span></span> <span data-ttu-id="a6546-196">Toto trasování zásobníku je kódu CLI/SDK.</span><span class="sxs-lookup"><span data-stu-id="a6546-196">This stack trace is of CLI/SDK code.</span></span>

<span data-ttu-id="a6546-197">Následující příklad znázorňuje druh shromažďovaných dat:</span><span class="sxs-lookup"><span data-stu-id="a6546-197">The following example shows the kind of data that is collected:</span></span>

```console
System.IO.IOException
at System.ConsolePal.WindowsConsoleStream.Write(Byte[] buffer, Int32 offset, Int32 count)
at System.IO.StreamWriter.Flush(Boolean flushStream, Boolean flushEncoder)
at System.IO.StreamWriter.Write(Char[] buffer)
at System.IO.TextWriter.WriteLine()
at System.IO.TextWriter.SyncTextWriter.WriteLine()
at Microsoft.DotNet.Cli.Utils.Reporter.WriteLine()
at Microsoft.DotNet.Tools.Run.RunCommand.EnsureProjectIsBuilt()
at Microsoft.DotNet.Tools.Run.RunCommand.Execute()
at Microsoft.DotNet.Tools.Run.RunCommand.Run(String[] args)
at Microsoft.DotNet.Cli.Program.ProcessArgs(String[] args, ITelemetry telemetryClient)
at Microsoft.DotNet.Cli.Program.Main(String[] args)
```

### <a name="avoid-inadvertent-disclosure-of-information"></a><span data-ttu-id="a6546-198">Vyhněte se nechtěnému zveřejňování informací</span><span class="sxs-lookup"><span data-stu-id="a6546-198">Avoid inadvertent disclosure of information</span></span>

<span data-ttu-id="a6546-199">Přispěvatelé .NET Core a všichni ostatní spouštějí verzi .NET Core SDK, kterou samy vytvořili, by měli zvážit cestu ke svému zdrojovému kódu sady SDK.</span><span class="sxs-lookup"><span data-stu-id="a6546-199">.NET Core contributors and anyone else running a version of the .NET Core SDK that they built themselves should consider the path to their SDK source code.</span></span> <span data-ttu-id="a6546-200">Pokud dojde k chybě při použití .NET Core SDK, které je vlastní sestavení ladění nebo nakonfigurováno pomocí vlastních souborů symbolů sestavení, bude cesta ke zdrojovému souboru sady SDK z sestavovacího počítače shromažďována jako součást trasování zásobníku a není použita hodnota hash.</span><span class="sxs-lookup"><span data-stu-id="a6546-200">If a crash occurs while using a .NET Core SDK that is a custom debug build or configured with custom build symbol files, the SDK source file path from the build machine is collected as part of the stack trace and isn't hashed.</span></span>

<span data-ttu-id="a6546-201">Z tohoto důvodu by se vlastní sestavení .NET Core SDK neměla nacházet v adresářích, jejichž názvy cest zveřejňují osobní nebo citlivé informace.</span><span class="sxs-lookup"><span data-stu-id="a6546-201">Because of this, custom builds of the .NET Core SDK shouldn't be located in directories whose path names expose personal or sensitive information.</span></span> 

## <a name="see-also"></a><span data-ttu-id="a6546-202">Viz také</span><span class="sxs-lookup"><span data-stu-id="a6546-202">See also</span></span>

- [<span data-ttu-id="a6546-203">Data telemetrie .NET Core CLI-2019 Q2</span><span class="sxs-lookup"><span data-stu-id="a6546-203">.NET Core CLI Telemetry - 2019 Q2 Data</span></span>](https://dotnet.microsoft.com/platform/telemetry/dotnet-core-cli-2019q2)
- [<span data-ttu-id="a6546-204">Zdroj odkazů telemetrie (úložiště dotnet/CLI)</span><span class="sxs-lookup"><span data-stu-id="a6546-204">Telemetry reference source (dotnet/cli repository)</span></span>](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)
