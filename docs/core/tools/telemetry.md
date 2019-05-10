---
title: Telemetrická data sady SDK .NET core
description: Seznamte se s funkcemi telemetrie .NET Core SDK, které shromažďují informace o využití pro analýzy, která data se shromažďují a jak ji zakázat.
author: richlander
ms.date: 06/20/2018
ms.custom: seodec18
ms.openlocfilehash: 82410863c81faa95edfb120c95ec6bc186ed1328
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64751675"
---
# <a name="net-core-sdk-telemetry"></a><span data-ttu-id="28b91-103">Telemetrická data sady SDK .NET core</span><span class="sxs-lookup"><span data-stu-id="28b91-103">.NET Core SDK telemetry</span></span>

<span data-ttu-id="28b91-104">[.NET Core SDK](index.md) zahrnuje [funkce telemetrie](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry) , který shromažďuje informace o využití.</span><span class="sxs-lookup"><span data-stu-id="28b91-104">The [.NET Core SDK](index.md) includes a [telemetry feature](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry) that collects usage information.</span></span> <span data-ttu-id="28b91-105">Je důležité, že tým rozhraní .NET rozumí použití nástroje tak může zlepšit.</span><span class="sxs-lookup"><span data-stu-id="28b91-105">It's important that the .NET Team understands how the tools are used so they can be improved.</span></span> <span data-ttu-id="28b91-106">Další informace najdete v tématu [co jsme se naučili v .NET Core SDK Telemetrie](https://devblogs.microsoft.com/dotnet/what-weve-learned-from-net-core-sdk-telemetry/).</span><span class="sxs-lookup"><span data-stu-id="28b91-106">For more information, see [What we've learned from .NET Core SDK Telemetry](https://devblogs.microsoft.com/dotnet/what-weve-learned-from-net-core-sdk-telemetry/).</span></span>

<span data-ttu-id="28b91-107">Shromážděná data jsou anonymní a publikované v souhrnné podobě k použití Microsoftem a komunitou v části [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span><span class="sxs-lookup"><span data-stu-id="28b91-107">The collected data is anonymous and published in an aggregated form for use by both Microsoft and the community under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span>

## <a name="scope"></a><span data-ttu-id="28b91-108">Scope</span><span class="sxs-lookup"><span data-stu-id="28b91-108">Scope</span></span>

<span data-ttu-id="28b91-109">`dotnet` Příkaz se používá ke spuštění aplikace a rozhraní příkazového řádku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="28b91-109">The `dotnet` command is used to launch both apps and the .NET Core CLI.</span></span> <span data-ttu-id="28b91-110">`dotnet` Telemetrii neshromažďuje příkazu samého.</span><span class="sxs-lookup"><span data-stu-id="28b91-110">The `dotnet` command itself doesn't collect telemetry.</span></span> <span data-ttu-id="28b91-111">Příkazy rozhraní příkazového řádku .NET Core spuštěné `dotnet` příkaz shromažďovat telemetrická data.</span><span class="sxs-lookup"><span data-stu-id="28b91-111">The .NET Core CLI commands run by the `dotnet` command collect the telemetry.</span></span>

<span data-ttu-id="28b91-112">Telemetrie *není povoleno* při použití `dotnet` s příkazem pro samotného, není příkaz připojit:</span><span class="sxs-lookup"><span data-stu-id="28b91-112">Telemetry *isn't enabled* when using the `dotnet` command itself, with no command attached:</span></span>

- `dotnet`
- `dotnet [path-to-app]`

<span data-ttu-id="28b91-113">Telemetrie *je povoleno* při použití [příkazy rozhraní příkazového řádku .NET Core](index.md), jako například:</span><span class="sxs-lookup"><span data-stu-id="28b91-113">Telemetry *is enabled* when using the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`

## <a name="how-to-opt-out"></a><span data-ttu-id="28b91-114">Jak se chcete odhlásit</span><span class="sxs-lookup"><span data-stu-id="28b91-114">How to opt out</span></span>

<span data-ttu-id="28b91-115">Ve výchozím nastavení je povolena funkce telemetrická data sady SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="28b91-115">The .NET Core SDK telemetry feature is enabled by default.</span></span> <span data-ttu-id="28b91-116">Vyjádřit výslovný nesouhlas funkce telemetrie nastavením `DOTNET_CLI_TELEMETRY_OPTOUT` proměnnou prostředí, aby `1` nebo `true`.</span><span class="sxs-lookup"><span data-stu-id="28b91-116">Opt out of the telemetry feature by setting the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

## <a name="data-points"></a><span data-ttu-id="28b91-117">Datové body</span><span class="sxs-lookup"><span data-stu-id="28b91-117">Data points</span></span>

<span data-ttu-id="28b91-118">Funkci shromažďuje následující data:</span><span class="sxs-lookup"><span data-stu-id="28b91-118">The feature collects the following data:</span></span>

- <span data-ttu-id="28b91-119">Časové razítko volání&#8224;</span><span class="sxs-lookup"><span data-stu-id="28b91-119">Timestamp of invocation&#8224;</span></span>
- <span data-ttu-id="28b91-120">Příkaz vyvolána (například "sestavení")&#8224;</span><span class="sxs-lookup"><span data-stu-id="28b91-120">Command invoked (for example, "build")&#8224;</span></span>
- <span data-ttu-id="28b91-121">Tři octet IP adresy použité k určení zeměpisného umístění&#8224;</span><span class="sxs-lookup"><span data-stu-id="28b91-121">Three octet IP address used to determine geographical location&#8224;</span></span>
- <span data-ttu-id="28b91-122">`ExitCode` příkaz</span><span class="sxs-lookup"><span data-stu-id="28b91-122">`ExitCode` of the command</span></span>
- <span data-ttu-id="28b91-123">Nástroj test runner (pro projekty testů)</span><span class="sxs-lookup"><span data-stu-id="28b91-123">Test runner (for test projects)</span></span>
- <span data-ttu-id="28b91-124">Operační systém a verze&#8224;</span><span class="sxs-lookup"><span data-stu-id="28b91-124">Operating system and version&#8224;</span></span>
- <span data-ttu-id="28b91-125">Určuje, zda jsou k dispozici v uzlu moduly runtime ID modulu runtime</span><span class="sxs-lookup"><span data-stu-id="28b91-125">Whether runtime IDs are present in the runtimes node</span></span>
- <span data-ttu-id="28b91-126">Verze .NET core SDK&#8224;</span><span class="sxs-lookup"><span data-stu-id="28b91-126">.NET Core SDK version&#8224;</span></span>

<span data-ttu-id="28b91-127">&#8224;Tato metrika je publikována.</span><span class="sxs-lookup"><span data-stu-id="28b91-127">&#8224;This metric is published.</span></span>

<span data-ttu-id="28b91-128">Počínaje .NET Core 2.0 SDK, jsou shromažďovány nové datové body:</span><span class="sxs-lookup"><span data-stu-id="28b91-128">Starting with .NET Core 2.0 SDK, new data points are collected:</span></span>

- <span data-ttu-id="28b91-129">`dotnet` příkaz možností a argumentů: pouze známé možnosti a argumenty jsou shromážděná (ne libovolné řetězce).</span><span class="sxs-lookup"><span data-stu-id="28b91-129">`dotnet` command arguments and options: only known arguments and options are collected (not arbitrary strings).</span></span>
- <span data-ttu-id="28b91-130">Určuje, zda sada SDK je spuštěn v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="28b91-130">Whether the SDK is running in a container.</span></span>
- <span data-ttu-id="28b91-131">Cílové architektury.</span><span class="sxs-lookup"><span data-stu-id="28b91-131">Target frameworks.</span></span>
- <span data-ttu-id="28b91-132">Hodnoty hash adresy MAC: kryptograficky (SHA256) anonymní a jedinečné ID pro počítač.</span><span class="sxs-lookup"><span data-stu-id="28b91-132">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> <span data-ttu-id="28b91-133">Tato metrika není publikována.</span><span class="sxs-lookup"><span data-stu-id="28b91-133">This metric isn't published.</span></span>
- <span data-ttu-id="28b91-134">Hodnoty hash aktuálního pracovního adresáře.</span><span class="sxs-lookup"><span data-stu-id="28b91-134">Hashed current working directory.</span></span>

<span data-ttu-id="28b91-135">Funkci neshromažďuje osobní údaje, jako jsou uživatelská jména nebo e-mailové adresy.</span><span class="sxs-lookup"><span data-stu-id="28b91-135">The feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="28b91-136">Nebude Kontrola kódu a nebude extrahovat citlivých dat na úrovni projektu, jako je například název, úložiště nebo autora.</span><span class="sxs-lookup"><span data-stu-id="28b91-136">It doesn't scan your code and doesn't extract sensitive project-level data, such as name, repo, or author.</span></span> <span data-ttu-id="28b91-137">Data se odesílají bezpečně na servery Microsoftu pomocí [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technologie, uchovávat v části s omezeným přístupem a publikování na základě striktní bezpečnostní opatření z zabezpečené [službyAzureStorage](https://azure.microsoft.com/services/storage/) systémy.</span><span class="sxs-lookup"><span data-stu-id="28b91-137">The data is sent securely to Microsoft servers using [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="28b91-138">Tým .NET chce vědět, jak se používají nástroje a pokud pracují dobře, nejsou sestavení pomocí nástrojů.</span><span class="sxs-lookup"><span data-stu-id="28b91-138">The .NET team wants to know how the tools are used and if they're working well, not what you're building with the tools.</span></span> <span data-ttu-id="28b91-139">Pokud máte podezření, že se citlivá data nebo, který sbírá telemetrických dat dat se nezabezpečeným způsobem nebo neoprávněně zpracována, založte problém v [dotnet/cli](https://github.com/dotnet/cli/issues) úložiště pro šetření.</span><span class="sxs-lookup"><span data-stu-id="28b91-139">If you suspect that the telemetry is collecting sensitive data or that the data is being insecurely or inappropriately handled, file an issue in the [dotnet/cli](https://github.com/dotnet/cli/issues) repository for investigation.</span></span>

## <a name="published-data"></a><span data-ttu-id="28b91-140">Publikovaná data</span><span class="sxs-lookup"><span data-stu-id="28b91-140">Published data</span></span>

<span data-ttu-id="28b91-141">Publikovaná data čtvrtletně je k dispozici a jsou uvedeny v tématu [Data o využití sady SDK .NET Core](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span><span class="sxs-lookup"><span data-stu-id="28b91-141">Published data is available quarterly and are listed at [.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span></span> <span data-ttu-id="28b91-142">Jsou sloupce datového souboru:</span><span class="sxs-lookup"><span data-stu-id="28b91-142">The columns of a data file are:</span></span>

- <span data-ttu-id="28b91-143">Timestamp</span><span class="sxs-lookup"><span data-stu-id="28b91-143">Timestamp</span></span>
- <span data-ttu-id="28b91-144">Occurrences&#8224;</span><span class="sxs-lookup"><span data-stu-id="28b91-144">Occurrences&#8224;</span></span>
- <span data-ttu-id="28b91-145">Příkaz</span><span class="sxs-lookup"><span data-stu-id="28b91-145">Command</span></span>
- <span data-ttu-id="28b91-146">Geography&#8225;</span><span class="sxs-lookup"><span data-stu-id="28b91-146">Geography&#8225;</span></span>
- <span data-ttu-id="28b91-147">OSFamily</span><span class="sxs-lookup"><span data-stu-id="28b91-147">OSFamily</span></span>
- <span data-ttu-id="28b91-148">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="28b91-148">RuntimeID</span></span>
- <span data-ttu-id="28b91-149">OSVersion</span><span class="sxs-lookup"><span data-stu-id="28b91-149">OSVersion</span></span>
- <span data-ttu-id="28b91-150">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="28b91-150">SDKVersion</span></span>

<span data-ttu-id="28b91-151">&#8224;*Výskyty* sloupec zobrazuje agregace počet použití tohoto příkazu pro tento řádek metrik daný den.</span><span class="sxs-lookup"><span data-stu-id="28b91-151">&#8224;The *Occurrences* column displays the aggregate count of that command's use for that row's metrics that day.</span></span>

<span data-ttu-id="28b91-152">&#8225;Obvykle *zeměpisné oblasti* sloupec zobrazuje název země.</span><span class="sxs-lookup"><span data-stu-id="28b91-152">&#8225;Typically, the *Geography* column displays the name of a country.</span></span> <span data-ttu-id="28b91-153">V některých případech se v tomto sloupci, ať už z důvodu výzkumných pracovníků pomocí platformy .NET Core v Antarktida nebo nesprávné umístění dat zobrazí kontinent Antarktida.</span><span class="sxs-lookup"><span data-stu-id="28b91-153">In some cases, the continent of Antarctica appears in this column, either due to researchers using .NET Core in Antarctica or incorrect location data.</span></span>

### <a name="example"></a><span data-ttu-id="28b91-154">Příklad</span><span class="sxs-lookup"><span data-stu-id="28b91-154">Example</span></span>

| <span data-ttu-id="28b91-155">Timestamp</span><span class="sxs-lookup"><span data-stu-id="28b91-155">Timestamp</span></span>      | <span data-ttu-id="28b91-156">Výskyty</span><span class="sxs-lookup"><span data-stu-id="28b91-156">Occurrences</span></span> | <span data-ttu-id="28b91-157">Příkaz</span><span class="sxs-lookup"><span data-stu-id="28b91-157">Command</span></span> | <span data-ttu-id="28b91-158">Zeměpisné oblasti</span><span class="sxs-lookup"><span data-stu-id="28b91-158">Geography</span></span> | <span data-ttu-id="28b91-159">OSFamily</span><span class="sxs-lookup"><span data-stu-id="28b91-159">OSFamily</span></span> | <span data-ttu-id="28b91-160">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="28b91-160">RuntimeID</span></span>     | <span data-ttu-id="28b91-161">OSVersion</span><span class="sxs-lookup"><span data-stu-id="28b91-161">OSVersion</span></span> | <span data-ttu-id="28b91-162">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="28b91-162">SDKVersion</span></span> |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| <span data-ttu-id="28b91-163">4/16/2017 0:00</span><span class="sxs-lookup"><span data-stu-id="28b91-163">4/16/2017 0:00</span></span> | <span data-ttu-id="28b91-164">8</span><span class="sxs-lookup"><span data-stu-id="28b91-164">8</span></span>           | <span data-ttu-id="28b91-165">Spuštění</span><span class="sxs-lookup"><span data-stu-id="28b91-165">run</span></span>     | <span data-ttu-id="28b91-166">Uganda</span><span class="sxs-lookup"><span data-stu-id="28b91-166">Uganda</span></span>    | <span data-ttu-id="28b91-167">Darwin</span><span class="sxs-lookup"><span data-stu-id="28b91-167">Darwin</span></span>   | <span data-ttu-id="28b91-168">osx.10.12-x64</span><span class="sxs-lookup"><span data-stu-id="28b91-168">osx.10.12-x64</span></span> | <span data-ttu-id="28b91-169">10.12</span><span class="sxs-lookup"><span data-stu-id="28b91-169">10.12</span></span>     | <span data-ttu-id="28b91-170">1.0.1</span><span class="sxs-lookup"><span data-stu-id="28b91-170">1.0.1</span></span>      |

### <a name="datasets"></a><span data-ttu-id="28b91-171">Datové sady</span><span class="sxs-lookup"><span data-stu-id="28b91-171">Datasets</span></span>

- [<span data-ttu-id="28b91-172">2016 - 3. ČTVRTLETÍ</span><span class="sxs-lookup"><span data-stu-id="28b91-172">2016 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)
- [<span data-ttu-id="28b91-173">2016 – 4.</span><span class="sxs-lookup"><span data-stu-id="28b91-173">2016 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)
- [<span data-ttu-id="28b91-174">2017 - Q1</span><span class="sxs-lookup"><span data-stu-id="28b91-174">2017 - Q1</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)
- [<span data-ttu-id="28b91-175">2017 - Q2</span><span class="sxs-lookup"><span data-stu-id="28b91-175">2017 - Q2</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)
- [<span data-ttu-id="28b91-176">2017 - Q3</span><span class="sxs-lookup"><span data-stu-id="28b91-176">2017 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q3.tsv)
- [<span data-ttu-id="28b91-177">2017 - 4.</span><span class="sxs-lookup"><span data-stu-id="28b91-177">2017 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q4.tsv)

<span data-ttu-id="28b91-178">Další datové sady jsou odeslány pomocí standardní formát adresy URL.</span><span class="sxs-lookup"><span data-stu-id="28b91-178">Additional datasets are posted using a standard URL format.</span></span> <span data-ttu-id="28b91-179">Nahraďte `<YEAR>` rokem a nahradit `<QUARTER>` s čtvrtletí v roce (použijte `1`, `2`, `3`, nebo `4`).</span><span class="sxs-lookup"><span data-stu-id="28b91-179">Replace `<YEAR>` with the year and replace `<QUARTER>` with the quarter of the year (use `1`, `2`, `3`, or `4`).</span></span> <span data-ttu-id="28b91-180">Soubory jsou v hodnoty oddělené tabulátorem (*TSV*) formát.</span><span class="sxs-lookup"><span data-stu-id="28b91-180">The files are in tab-separated values (*TSV*) format.</span></span>

`https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv`

## <a name="license"></a><span data-ttu-id="28b91-181">Licence</span><span class="sxs-lookup"><span data-stu-id="28b91-181">License</span></span>

<span data-ttu-id="28b91-182">Je distribuce Microsoftu .NET Core licenci [licenční podmínky pro Software společnosti Microsoft: Knihovna .NET Mirosoft](https://aka.ms/dotnet-core-eula).</span><span class="sxs-lookup"><span data-stu-id="28b91-182">The Microsoft distribution of .NET Core is licensed with the [Microsoft Software License Terms: Mirosoft .NET Library](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="28b91-183">Podrobnosti o shromažďování dat a zpracování najdete v části s názvem "Data".</span><span class="sxs-lookup"><span data-stu-id="28b91-183">For details on data collection and processing, see the section entitled "Data."</span></span>

<span data-ttu-id="28b91-184">[Balíčky .NET NuGet](https://www.nuget.org/profiles/dotnetframework) používají stejné licence, ale nepovolí telemetrie (naleznete v tématu [oboru](#scope)).</span><span class="sxs-lookup"><span data-stu-id="28b91-184">[.NET NuGet packages](https://www.nuget.org/profiles/dotnetframework) use the same license but don't enable telemetry (see [Scope](#scope)).</span></span>

## <a name="disclosure"></a><span data-ttu-id="28b91-185">Zpřístupnění</span><span class="sxs-lookup"><span data-stu-id="28b91-185">Disclosure</span></span>

<span data-ttu-id="28b91-186">.NET Core SDK zobrazí při prvním spuštění jednu z následující text [příkazy rozhraní příkazového řádku .NET Core](index.md) (například `dotnet restore`).</span><span class="sxs-lookup"><span data-stu-id="28b91-186">The .NET Core SDK displays the following text when you first run one of the [.NET Core CLI commands](index.md) (for example, `dotnet restore`).</span></span> <span data-ttu-id="28b91-187">Text může mírně lišit v závislosti na verzi sady SDK, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="28b91-187">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="28b91-188">Toto prostředí "prvního spuštění" je, jak Microsoft upozorní vás na shromažďování dat.</span><span class="sxs-lookup"><span data-stu-id="28b91-188">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

```console
Welcome to .NET Core!
---------------------
Learn more about .NET Core: https://aka.ms/dotnet-docs
Use 'dotnet --help' to see available commands or visit: https://aka.ms/dotnet-cli-docs

Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience.
The data is anonymous and doesn't include command-line arguments.
The data is collected by Microsoft and shared with the community.
You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

## <a name="see-also"></a><span data-ttu-id="28b91-189">Viz také:</span><span class="sxs-lookup"><span data-stu-id="28b91-189">See also</span></span>

- [<span data-ttu-id="28b91-190">Co jsme se naučili z telemetrická data sady SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="28b91-190">What we've learned from .NET Core SDK Telemetry</span></span>](https://devblogs.microsoft.com/dotnet/what-weve-learned-from-net-core-sdk-telemetry/)
- [<span data-ttu-id="28b91-191">Odkaz na zdroj telemetrie (úložišti dotnet/cli)</span><span class="sxs-lookup"><span data-stu-id="28b91-191">Telemetry reference source (dotnet/cli repo)</span></span>](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)
- [<span data-ttu-id="28b91-192">Data o využití sady SDK .NET core</span><span class="sxs-lookup"><span data-stu-id="28b91-192">.NET Core SDK Usage Data</span></span>](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)
