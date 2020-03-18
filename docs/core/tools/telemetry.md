---
title: Telemetrie sady .NET Core SDK
description: Seznamte se s telemetrickými funkcemi sady .NET Core SDK, které shromažďují informace o využití pro analýzu, která data jsou shromažďována a jak je zakázat.
author: KathleenDollard
ms.date: 08/27/2019
ms.openlocfilehash: 9d5d7ff09ade89712f2fbbe35224851bb1c28b4c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156683"
---
# <a name="net-core-sdk-telemetry"></a><span data-ttu-id="cfdbd-103">Telemetrie sady .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="cfdbd-103">.NET Core SDK telemetry</span></span>

<span data-ttu-id="cfdbd-104">Sada [.NET Core SDK](index.md) obsahuje funkci telemetrie, která shromažďuje data o využití a informace o výjimkách při selhání rozhraní .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-104">The [.NET Core SDK](index.md) includes a telemetry feature that collects usage data and exception information when the .NET Core CLI crashes.</span></span> <span data-ttu-id="cfdbd-105">Rozhraní PŘÍKAZOVÉHO NASTAVENÍ .NET Core cli je dodáváno se sadou .NET Core SDK a je sadou sloves, která umožňují vytvářet, testovat a publikovat aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-105">The .NET Core CLI comes with the .NET Core SDK and is the set of verbs that enable you to build, test, and publish your .NET Core apps.</span></span> <span data-ttu-id="cfdbd-106">Je důležité, aby tým .NET pochopil, jak se nástroje používají, aby je bylo možné zlepšit.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-106">It's important that the .NET team understands how the tools are used so they can be improved.</span></span> <span data-ttu-id="cfdbd-107">Informace o selhání pomáhá týmu vyřešit problémy a opravit chyby.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-107">Information on failures helps the team resolve problems and fix bugs.</span></span>

<span data-ttu-id="cfdbd-108">Shromážděné údaje jsou anonymní a jsou zveřejňovány souhrnně pod [licencí Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span><span class="sxs-lookup"><span data-stu-id="cfdbd-108">The collected data is anonymous and published in aggregate under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span>

## <a name="scope"></a><span data-ttu-id="cfdbd-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="cfdbd-109">Scope</span></span>

<span data-ttu-id="cfdbd-110">`dotnet`má dvě funkce: spouštět aplikace a spouštět příkazy příkazového příkazu.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-110">`dotnet` has two functions: to run apps, and to execute CLI commands.</span></span> <span data-ttu-id="cfdbd-111">Telemetrie *se neshromažďuje* při spuštění `dotnet` aplikace v následujícím formátu:</span><span class="sxs-lookup"><span data-stu-id="cfdbd-111">Telemetry *isn't collected* when using `dotnet` to start an application in the following format:</span></span>

- `dotnet [path-to-app].dll`

<span data-ttu-id="cfdbd-112">Telemetrie *se shromažďuje* při použití některého z [příkazů rozhraní PŘÍKAZOVÉHO PŘÍKAZU .NET Core](index.md), například:</span><span class="sxs-lookup"><span data-stu-id="cfdbd-112">Telemetry *is collected* when using any of the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet run`

## <a name="how-to-opt-out"></a><span data-ttu-id="cfdbd-113">Jak se odhlásit</span><span class="sxs-lookup"><span data-stu-id="cfdbd-113">How to opt out</span></span>

<span data-ttu-id="cfdbd-114">Funkce telemetrie sady .NET Core SDK je ve výchozím nastavení povolena.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-114">The .NET Core SDK telemetry feature is enabled by default.</span></span> <span data-ttu-id="cfdbd-115">Chcete-li odhlásit funkci telemetrie, `1` nastavte `true`proměnnou `DOTNET_CLI_TELEMETRY_OPTOUT` prostředí na nebo .</span><span class="sxs-lookup"><span data-stu-id="cfdbd-115">To opt out of the telemetry feature, set the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

<span data-ttu-id="cfdbd-116">Instalační program sady .NET Core SDK odesílá také jednu položku telemetrie, když dojde k úspěšné instalaci.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-116">A single telemetry entry is also sent by the .NET Core SDK installer when a successful installation happens.</span></span> <span data-ttu-id="cfdbd-117">Chcete-li se `DOTNET_CLI_TELEMETRY_OPTOUT` odhlásit, nastavte před instalací sady .NET Core SDK proměnnou prostředí.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-117">To opt out, set the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable before you install the .NET Core SDK.</span></span>

## <a name="disclosure"></a><span data-ttu-id="cfdbd-118">Zveřejnění</span><span class="sxs-lookup"><span data-stu-id="cfdbd-118">Disclosure</span></span>

<span data-ttu-id="cfdbd-119">Sada .NET Core SDK zobrazí text podobný následujícímu při prvním spuštění jednoho z příkazů `dotnet build`rozhraní [PŘÍKAZU .NET Core (například](index.md) ).</span><span class="sxs-lookup"><span data-stu-id="cfdbd-119">The .NET Core SDK displays text similar to the following when you first run one of the [.NET Core CLI commands](index.md) (for example, `dotnet build`).</span></span> <span data-ttu-id="cfdbd-120">Text se může mírně lišit v závislosti na verzi sady SDK, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-120">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="cfdbd-121">Toto "první spuštění" prostředí je, jak microsoft vás upozorní na shromažďování dat.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-121">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

```console
Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience. The data is anonymous. It is collected by Microsoft and shared with the community. You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

## <a name="data-points"></a><span data-ttu-id="cfdbd-122">Datové body</span><span class="sxs-lookup"><span data-stu-id="cfdbd-122">Data points</span></span>

<span data-ttu-id="cfdbd-123">Funkce telemetrie neshromažďuje osobní údaje, jako jsou uživatelská jména nebo e-mailové adresy.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-123">The telemetry feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="cfdbd-124">Neprohledá váš kód a neextrahuje data na úrovni projektu, jako je název, úložiště nebo autor.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-124">It doesn't scan your code and doesn't extract project-level data, such as name, repository, or author.</span></span> <span data-ttu-id="cfdbd-125">Data se bezpečně odesílají na servery Microsoftu pomocí technologie [Azure Monitor,](https://azure.microsoft.com/services/monitor/) která je držena pod omezeným přístupem a publikuje se pod přísnými bezpečnostními kontrolami ze zabezpečených systémů [Azure Storage.](https://azure.microsoft.com/services/storage/)</span><span class="sxs-lookup"><span data-stu-id="cfdbd-125">The data is sent securely to Microsoft servers using [Azure Monitor](https://azure.microsoft.com/services/monitor/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="cfdbd-126">Ochrana vašeho soukromí je pro nás důležitá.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-126">Protecting your privacy is important to us.</span></span> <span data-ttu-id="cfdbd-127">Pokud máte podezření, že telemetrie shromažďuje citlivá data nebo jsou nebezpečně nebo nevhodně zpracována, zasuzujte problém do úložiště [dotnet/cli](https://github.com/dotnet/cli/issues) nebo odešlete e-mail k [dotnet@microsoft.com](mailto:dotnet@microsoft.com) prošetření.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-127">If you suspect the telemetry is collecting sensitive data or the data is being insecurely or inappropriately handled, file an issue in the [dotnet/cli](https://github.com/dotnet/cli/issues) repository or send an email to [dotnet@microsoft.com](mailto:dotnet@microsoft.com) for investigation.</span></span>

<span data-ttu-id="cfdbd-128">Funkce telemetrie shromažďuje následující data:</span><span class="sxs-lookup"><span data-stu-id="cfdbd-128">The telemetry feature collects the following data:</span></span>

| <span data-ttu-id="cfdbd-129">Verze sady SDK</span><span class="sxs-lookup"><span data-stu-id="cfdbd-129">SDK versions</span></span> | <span data-ttu-id="cfdbd-130">Data</span><span class="sxs-lookup"><span data-stu-id="cfdbd-130">Data</span></span> |
|--------------|------|
| <span data-ttu-id="cfdbd-131">Všechny</span><span class="sxs-lookup"><span data-stu-id="cfdbd-131">All</span></span>          | <span data-ttu-id="cfdbd-132">Časové razítko vyvolání.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-132">Timestamp of invocation.</span></span> |
| <span data-ttu-id="cfdbd-133">Všechny</span><span class="sxs-lookup"><span data-stu-id="cfdbd-133">All</span></span>          | <span data-ttu-id="cfdbd-134">Příkaz vyvolán (například "sestavení"), zahashované počínaje 2.1.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-134">Command invoked (for example, "build"), hashed starting in 2.1.</span></span> |
| <span data-ttu-id="cfdbd-135">Všechny</span><span class="sxs-lookup"><span data-stu-id="cfdbd-135">All</span></span>          | <span data-ttu-id="cfdbd-136">Tři oktetové IP adresy používané k určení zeměpisné polohy.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-136">Three octet IP address used to determine the geographical location.</span></span> |
| <span data-ttu-id="cfdbd-137">Všechny</span><span class="sxs-lookup"><span data-stu-id="cfdbd-137">All</span></span>          | <span data-ttu-id="cfdbd-138">Operační systém a verze.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-138">Operating system and version.</span></span> |
| <span data-ttu-id="cfdbd-139">Všechny</span><span class="sxs-lookup"><span data-stu-id="cfdbd-139">All</span></span>          | <span data-ttu-id="cfdbd-140">Runtime ID (RID) sada SDK je spuštěna.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-140">Runtime ID (RID) the SDK is running on.</span></span> |
| <span data-ttu-id="cfdbd-141">Všechny</span><span class="sxs-lookup"><span data-stu-id="cfdbd-141">All</span></span>          | <span data-ttu-id="cfdbd-142">Verze sady .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-142">.NET Core SDK version.</span></span> |
| <span data-ttu-id="cfdbd-143">Všechny</span><span class="sxs-lookup"><span data-stu-id="cfdbd-143">All</span></span>          | <span data-ttu-id="cfdbd-144">Profil telemetrie: volitelná hodnota používaná pouze s explicitním přihlášením uživatele a interně používaná u společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-144">Telemetry profile: an optional value only used with explicit user opt-in and used internally at Microsoft.</span></span> |
| <span data-ttu-id="cfdbd-145">>=2,0</span><span class="sxs-lookup"><span data-stu-id="cfdbd-145">>=2.0</span></span>        | <span data-ttu-id="cfdbd-146">Příkaz argumenty a možnosti: několik argumentů a možností jsou shromažďovány (ne libovolné řetězce).</span><span class="sxs-lookup"><span data-stu-id="cfdbd-146">Command arguments and options: several arguments and options are collected (not arbitrary strings).</span></span> <span data-ttu-id="cfdbd-147">Viz [shromážděné možnosti](#collected-options).</span><span class="sxs-lookup"><span data-stu-id="cfdbd-147">See [collected options](#collected-options).</span></span> <span data-ttu-id="cfdbd-148">Hashed po 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-148">Hashed after 2.1.300.</span></span> |
| <span data-ttu-id="cfdbd-149">>=2,0</span><span class="sxs-lookup"><span data-stu-id="cfdbd-149">>=2.0</span></span>         | <span data-ttu-id="cfdbd-150">Zda je sada SDK spuštěna v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-150">Whether the SDK is running in a container.</span></span> |
| <span data-ttu-id="cfdbd-151">>=2,0</span><span class="sxs-lookup"><span data-stu-id="cfdbd-151">>=2.0</span></span>         | <span data-ttu-id="cfdbd-152">Cílové rámce (z `TargetFramework` události), hash začíná v 2.1.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-152">Target frameworks (from the `TargetFramework` event), hashed starting in 2.1.</span></span> |
| <span data-ttu-id="cfdbd-153">>=2,0</span><span class="sxs-lookup"><span data-stu-id="cfdbd-153">>=2.0</span></span>         | <span data-ttu-id="cfdbd-154">Hashed Media Access Control (MAC) adresa: kryptograficky (SHA256) anonymní a jedinečné ID pro počítač.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-154">Hashed Media Access Control (MAC) address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> |
| <span data-ttu-id="cfdbd-155">>=2,0</span><span class="sxs-lookup"><span data-stu-id="cfdbd-155">>=2.0</span></span>         | <span data-ttu-id="cfdbd-156">Zahashed aktuální pracovní adresář.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-156">Hashed current working directory.</span></span> |
| <span data-ttu-id="cfdbd-157">>=2,0</span><span class="sxs-lookup"><span data-stu-id="cfdbd-157">>=2.0</span></span>         | <span data-ttu-id="cfdbd-158">Nainstalujte zprávu o úspěchu s názvem souboru exe zahasovaného instalačního programu.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-158">Install success report, with hashed installer exe filename.</span></span> |
| <span data-ttu-id="cfdbd-159">>=2.1.300</span><span class="sxs-lookup"><span data-stu-id="cfdbd-159">>=2.1.300</span></span>     | <span data-ttu-id="cfdbd-160">Verze jádra.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-160">Kernel version.</span></span> |
| <span data-ttu-id="cfdbd-161">>=2.1.300</span><span class="sxs-lookup"><span data-stu-id="cfdbd-161">>=2.1.300</span></span>     | <span data-ttu-id="cfdbd-162">Libc vydání / verze.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-162">Libc release/version.</span></span> |
| <span data-ttu-id="cfdbd-163">>=3.0.100</span><span class="sxs-lookup"><span data-stu-id="cfdbd-163">>=3.0.100</span></span>     | <span data-ttu-id="cfdbd-164">Zda byl výstup přesměrován (true nebo false).</span><span class="sxs-lookup"><span data-stu-id="cfdbd-164">Whether the output was redirected (true or false).</span></span> |
| <span data-ttu-id="cfdbd-165">>=3.0.100</span><span class="sxs-lookup"><span data-stu-id="cfdbd-165">>=3.0.100</span></span>     | <span data-ttu-id="cfdbd-166">Při selhání cli/SDK typ výjimky a jeho trasování zásobníku (pouze CLI/SDK kód je součástí trasování zásobníku odeslána).</span><span class="sxs-lookup"><span data-stu-id="cfdbd-166">On a CLI/SDK crash, the exception type and its stack trace (only CLI/SDK code is included in the stack trace sent).</span></span> <span data-ttu-id="cfdbd-167">Další informace naleznete [v tématu .NET Core CLI/SDK výjimka výjimky telemetrie shromážděny](#net-core-clisdk-crash-exception-telemetry-collected).</span><span class="sxs-lookup"><span data-stu-id="cfdbd-167">For more information, see [.NET Core CLI/SDK crash exception telemetry collected](#net-core-clisdk-crash-exception-telemetry-collected).</span></span> |

### <a name="collected-options"></a><span data-ttu-id="cfdbd-168">Shromážděné možnosti</span><span class="sxs-lookup"><span data-stu-id="cfdbd-168">Collected options</span></span>

<span data-ttu-id="cfdbd-169">Některé příkazy odesílají další data.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-169">Certain commands send additional data.</span></span> <span data-ttu-id="cfdbd-170">Podmnožina příkazů odešle první argument:</span><span class="sxs-lookup"><span data-stu-id="cfdbd-170">A subset of commands sends the first argument:</span></span>

| <span data-ttu-id="cfdbd-171">Příkaz</span><span class="sxs-lookup"><span data-stu-id="cfdbd-171">Command</span></span>               | <span data-ttu-id="cfdbd-172">Odeslaná data prvního argumentu</span><span class="sxs-lookup"><span data-stu-id="cfdbd-172">First argument data sent</span></span>                |
|-----------------------|-----------------------------------------|
| `dotnet help <arg>`   | <span data-ttu-id="cfdbd-173">Nápověda příkazu je dotazován.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-173">The command help is being queried for.</span></span>  |
| `dotnet new <arg>`    | <span data-ttu-id="cfdbd-174">Název šablony (hash).</span><span class="sxs-lookup"><span data-stu-id="cfdbd-174">The template name (hashed).</span></span>             |
| `dotnet add <arg>`    | <span data-ttu-id="cfdbd-175">Slovo `package` nebo `reference`.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-175">The word `package` or `reference`.</span></span>      |
| `dotnet remove <arg>` | <span data-ttu-id="cfdbd-176">Slovo `package` nebo `reference`.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-176">The word `package` or `reference`.</span></span>      |
| `dotnet list <arg>`   | <span data-ttu-id="cfdbd-177">Slovo `package` nebo `reference`.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-177">The word `package` or `reference`.</span></span>      |
| `dotnet sln <arg>`    | <span data-ttu-id="cfdbd-178">Slovo `add`, `list`, `remove`nebo .</span><span class="sxs-lookup"><span data-stu-id="cfdbd-178">The word `add`, `list`, or `remove`.</span></span>    |
| `dotnet nuget <arg>`  | <span data-ttu-id="cfdbd-179">Slovo `delete`, `locals`, `push`nebo .</span><span class="sxs-lookup"><span data-stu-id="cfdbd-179">The word `delete`, `locals`, or `push`.</span></span> |

<span data-ttu-id="cfdbd-180">Podmnožina příkazů odešle vybrané volby, pokud jsou použity, spolu s jejich hodnotami:</span><span class="sxs-lookup"><span data-stu-id="cfdbd-180">A subset of commands sends selected options if they're used, along with their values:</span></span>

| <span data-ttu-id="cfdbd-181">Možnost</span><span class="sxs-lookup"><span data-stu-id="cfdbd-181">Option</span></span>                  | <span data-ttu-id="cfdbd-182">Příkazy</span><span class="sxs-lookup"><span data-stu-id="cfdbd-182">Commands</span></span>                                                                                       |
|-------------------------|------------------------------------------------------------------------------------------------|
| `--verbosity`           | <span data-ttu-id="cfdbd-183">Všechny příkazy</span><span class="sxs-lookup"><span data-stu-id="cfdbd-183">All commands</span></span>                                                                                   |
| `--language`            | `dotnet new`                                                                                   |
| `--configuration`       | <span data-ttu-id="cfdbd-184">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`</span><span class="sxs-lookup"><span data-stu-id="cfdbd-184">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`</span></span>                  |
| `--framework`           | <span data-ttu-id="cfdbd-185">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest`</span><span class="sxs-lookup"><span data-stu-id="cfdbd-185">`dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest`</span></span> |
| `--runtime`             | <span data-ttu-id="cfdbd-186">`dotnet build`,  `dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="cfdbd-186">`dotnet build`,  `dotnet publish`</span></span>                                                              |
| `--platform`            | `dotnet vstest`                                                                                |
| `--logger`              | `dotnet vstest`                                                                                |
| `--sdk-package-version` | `dotnet migrate`                                                                               |

<span data-ttu-id="cfdbd-187">S `--verbosity` výjimkou `--sdk-package-version`a , všechny ostatní hodnoty jsou zahashovat počínaje .NET Core 2.1.100 SDK.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-187">Except for `--verbosity` and `--sdk-package-version`, all the other values are hashed starting with .NET Core 2.1.100 SDK.</span></span>

## <a name="net-core-clisdk-crash-exception-telemetry-collected"></a><span data-ttu-id="cfdbd-188">Shromážděná telemetrie výjimky selhání rozhraní CLI jádra jádra nebo sady SDK</span><span class="sxs-lookup"><span data-stu-id="cfdbd-188">.NET Core CLI/SDK crash exception telemetry collected</span></span>

<span data-ttu-id="cfdbd-189">Pokud dojde k chybě rozhraní .NET Core CLI/SDK, shromažďuje název výjimky a trasování zásobníku kódu CLI/SDK.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-189">If the .NET Core CLI/SDK crashes, it collects the name of the exception and stack trace of the CLI/SDK code.</span></span> <span data-ttu-id="cfdbd-190">Tyto informace jsou shromažďovány k posouzení problémů a zlepšení kvality sady .NET Core SDK a CLI.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-190">This information is collected to assess problems and improve the quality of the .NET Core SDK and CLI.</span></span> <span data-ttu-id="cfdbd-191">Tento článek obsahuje informace o shromažďinách.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-191">This article provides information about the data we collect.</span></span> <span data-ttu-id="cfdbd-192">Poskytuje také tipy, jak uživatelé, kteří vytváří vlastní verzi sady .NET Core SDK, mohou zabránit neúmyslnému zveřejnění osobních nebo citlivých informací.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-192">It also provides tips on how users building their own version of the .NET Core SDK can avoid inadvertent disclosure of personal or sensitive information.</span></span>

### <a name="types-of-collected-data"></a><span data-ttu-id="cfdbd-193">Typy shromážděných údajů</span><span class="sxs-lookup"><span data-stu-id="cfdbd-193">Types of collected data</span></span>

<span data-ttu-id="cfdbd-194">Rozhraní .NET Core CLI shromažďuje informace pouze pro výjimky cli/SDK, nikoli výjimky ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-194">.NET Core CLI collects information for CLI/SDK exceptions only, not exceptions in your application.</span></span> <span data-ttu-id="cfdbd-195">Shromážděná data obsahuje název výjimky a trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-195">The collected data contains the name of the exception and the stack trace.</span></span> <span data-ttu-id="cfdbd-196">Toto trasování zásobníku je kódu CLI/SDK.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-196">This stack trace is of CLI/SDK code.</span></span>

<span data-ttu-id="cfdbd-197">Následující příklad ukazuje druh dat, která jsou shromažďována:</span><span class="sxs-lookup"><span data-stu-id="cfdbd-197">The following example shows the kind of data that is collected:</span></span>

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

### <a name="avoid-inadvertent-disclosure-of-information"></a><span data-ttu-id="cfdbd-198">Vyhněte se neúmyslnému zveřejnění informací</span><span class="sxs-lookup"><span data-stu-id="cfdbd-198">Avoid inadvertent disclosure of information</span></span>

<span data-ttu-id="cfdbd-199">Přispěvatelé .NET Core a kdokoli jiný, kdo používá verzi sady .NET Core SDK, kterou sami vytvořili, by měli zvážit cestu k jejich zdrojovému kódu sady SDK.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-199">.NET Core contributors and anyone else running a version of the .NET Core SDK that they built themselves should consider the path to their SDK source code.</span></span> <span data-ttu-id="cfdbd-200">Pokud dojde k chybě při použití sady .NET Core SDK, která je vlastní ladění sestavení nebo nakonfigurován s vlastní soubory symbolů sestavení, cesta zdrojového souboru Sady SDK z počítače sestavení se shromažďují jako součást trasování zásobníku a není zakódován.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-200">If a crash occurs while using a .NET Core SDK that is a custom debug build or configured with custom build symbol files, the SDK source file path from the build machine is collected as part of the stack trace and isn't hashed.</span></span>

<span data-ttu-id="cfdbd-201">Z tohoto důvodu vlastní sestavení sady .NET Core SDK by neměla být umístěna v adresářích, jejichž názvy cest zveřejňují osobní nebo citlivé informace.</span><span class="sxs-lookup"><span data-stu-id="cfdbd-201">Because of this, custom builds of the .NET Core SDK shouldn't be located in directories whose path names expose personal or sensitive information.</span></span>

## <a name="see-also"></a><span data-ttu-id="cfdbd-202">Viz také</span><span class="sxs-lookup"><span data-stu-id="cfdbd-202">See also</span></span>

- [<span data-ttu-id="cfdbd-203">Telemetrie rozhraní CLI .NET - data Q2 2 2 2 2</span><span class="sxs-lookup"><span data-stu-id="cfdbd-203">.NET Core CLI Telemetry - 2019 Q2 Data</span></span>](https://dotnet.microsoft.com/platform/telemetry/dotnet-core-cli-2019q2)
- [<span data-ttu-id="cfdbd-204">Referenční zdroj telemetrie (úložiště dotnet/cli)</span><span class="sxs-lookup"><span data-stu-id="cfdbd-204">Telemetry reference source (dotnet/cli repository)</span></span>](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)
