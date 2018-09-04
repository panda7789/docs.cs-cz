---
title: Telemetrická data sady SDK .NET core
description: Seznamte se s funkcemi telemetrie .NET Core SDK, které shromažďují informace o využití pro analýzy, která data se shromažďují a jak ji zakázat.
author: richlander
ms.author: mairaw
ms.date: 06/20/2018
ms.openlocfilehash: b60fc9d9d619334269343fd858a782cdfeb09ba4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43513337"
---
# <a name="net-core-sdk-telemetry"></a><span data-ttu-id="654da-103">Telemetrická data sady SDK .NET core</span><span class="sxs-lookup"><span data-stu-id="654da-103">.NET Core SDK telemetry</span></span>

<span data-ttu-id="654da-104">[.NET Core SDK](index.md) zahrnuje [funkce telemetrie](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry) , který shromažďuje informace o využití.</span><span class="sxs-lookup"><span data-stu-id="654da-104">The [.NET Core SDK](index.md) includes a [telemetry feature](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry) that collects usage information.</span></span> <span data-ttu-id="654da-105">Je důležité, že tým rozhraní .NET rozumí použití nástroje tak může zlepšit.</span><span class="sxs-lookup"><span data-stu-id="654da-105">It's important that the .NET Team understands how the tools are used so they can be improved.</span></span> <span data-ttu-id="654da-106">Další informace najdete v tématu [co jsme se naučili v .NET Core SDK Telemetrie](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).</span><span class="sxs-lookup"><span data-stu-id="654da-106">For more information, see [What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).</span></span>

<span data-ttu-id="654da-107">Shromážděná data jsou anonymní a publikované v souhrnné podobě k použití Microsoftem a komunitou v části [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span><span class="sxs-lookup"><span data-stu-id="654da-107">The collected data is anonymous and published in an aggregated form for use by both Microsoft and the community under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span>

## <a name="scope"></a><span data-ttu-id="654da-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="654da-108">Scope</span></span>

<span data-ttu-id="654da-109">`dotnet` Příkaz se používá ke spuštění aplikace a rozhraní příkazového řádku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="654da-109">The `dotnet` command is used to launch both apps and the .NET Core CLI.</span></span> <span data-ttu-id="654da-110">`dotnet` Telemetrii neshromažďuje příkazu samého.</span><span class="sxs-lookup"><span data-stu-id="654da-110">The `dotnet` command itself doesn't collect telemetry.</span></span> <span data-ttu-id="654da-111">Příkazy rozhraní příkazového řádku .NET Core spuštěné `dotnet` příkaz shromažďovat telemetrická data.</span><span class="sxs-lookup"><span data-stu-id="654da-111">The .NET Core CLI commands run by the `dotnet` command collect the telemetry.</span></span>

<span data-ttu-id="654da-112">Telemetrie *není povoleno* při použití `dotnet` s příkazem pro samotného, není příkaz připojit:</span><span class="sxs-lookup"><span data-stu-id="654da-112">Telemetry *isn't enabled* when using the `dotnet` command itself, with no command attached:</span></span>

- `dotnet`
- `dotnet [path-to-app]`

<span data-ttu-id="654da-113">Telemetrie *je povoleno* při použití [příkazy rozhraní příkazového řádku .NET Core](index.md), jako například:</span><span class="sxs-lookup"><span data-stu-id="654da-113">Telemetry *is enabled* when using the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`

## <a name="how-to-opt-out"></a><span data-ttu-id="654da-114">Jak se chcete odhlásit</span><span class="sxs-lookup"><span data-stu-id="654da-114">How to opt out</span></span>

<span data-ttu-id="654da-115">Ve výchozím nastavení je povolena funkce telemetrická data sady SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="654da-115">The .NET Core SDK telemetry feature is enabled by default.</span></span> <span data-ttu-id="654da-116">Vyjádřit výslovný nesouhlas funkce telemetrie nastavením `DOTNET_CLI_TELEMETRY_OPTOUT` proměnnou prostředí, aby `1` nebo `true`.</span><span class="sxs-lookup"><span data-stu-id="654da-116">Opt out of the telemetry feature by setting the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

## <a name="data-points"></a><span data-ttu-id="654da-117">Datové body</span><span class="sxs-lookup"><span data-stu-id="654da-117">Data points</span></span>

<span data-ttu-id="654da-118">Funkci shromažďuje následující data:</span><span class="sxs-lookup"><span data-stu-id="654da-118">The feature collects the following data:</span></span>

- <span data-ttu-id="654da-119">Časové razítko volání&#8224;</span><span class="sxs-lookup"><span data-stu-id="654da-119">Timestamp of invocation&#8224;</span></span>
- <span data-ttu-id="654da-120">Příkaz vyvolána (například "sestavení")&#8224;</span><span class="sxs-lookup"><span data-stu-id="654da-120">Command invoked (for example, "build")&#8224;</span></span>
- <span data-ttu-id="654da-121">Tři octet IP adresy použité k určení zeměpisného umístění&#8224;</span><span class="sxs-lookup"><span data-stu-id="654da-121">Three octet IP address used to determine geographical location&#8224;</span></span>
- <span data-ttu-id="654da-122">`ExitCode` příkaz</span><span class="sxs-lookup"><span data-stu-id="654da-122">`ExitCode` of the command</span></span>
- <span data-ttu-id="654da-123">Nástroj test runner (pro projekty testů)</span><span class="sxs-lookup"><span data-stu-id="654da-123">Test runner (for test projects)</span></span>
- <span data-ttu-id="654da-124">Operační systém a verze&#8224;</span><span class="sxs-lookup"><span data-stu-id="654da-124">Operating system and version&#8224;</span></span>
- <span data-ttu-id="654da-125">Určuje, zda jsou k dispozici v uzlu moduly runtime ID modulu runtime</span><span class="sxs-lookup"><span data-stu-id="654da-125">Whether runtime IDs are present in the runtimes node</span></span>
- <span data-ttu-id="654da-126">Verze .NET core SDK&#8224;</span><span class="sxs-lookup"><span data-stu-id="654da-126">.NET Core SDK version&#8224;</span></span>

<span data-ttu-id="654da-127">&#8224;Tato metrika je publikována.</span><span class="sxs-lookup"><span data-stu-id="654da-127">&#8224;This metric is published.</span></span>

<span data-ttu-id="654da-128">Počínaje .NET Core SDK 2.0, jsou shromažďovány nové datové body:</span><span class="sxs-lookup"><span data-stu-id="654da-128">Starting with .NET Core SDK 2.0, new data points are collected:</span></span>

- <span data-ttu-id="654da-129">`dotnet` příkaz možností a argumentů: pouze známé možnosti a argumenty jsou shromážděná (ne libovolné řetězce).</span><span class="sxs-lookup"><span data-stu-id="654da-129">`dotnet` command arguments and options: only known arguments and options are collected (not arbitrary strings).</span></span>
- <span data-ttu-id="654da-130">Určuje, zda sada SDK je spuštěn v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="654da-130">Whether the SDK is running in a container.</span></span>
- <span data-ttu-id="654da-131">Cílové architektury.</span><span class="sxs-lookup"><span data-stu-id="654da-131">Target frameworks.</span></span>
- <span data-ttu-id="654da-132">Hodnoty hash adresy MAC: kryptograficky (SHA256) anonymní a jedinečné ID pro počítač.</span><span class="sxs-lookup"><span data-stu-id="654da-132">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> <span data-ttu-id="654da-133">Tato metrika není publikována.</span><span class="sxs-lookup"><span data-stu-id="654da-133">This metric isn't published.</span></span>
- <span data-ttu-id="654da-134">Hodnoty hash aktuálního pracovního adresáře.</span><span class="sxs-lookup"><span data-stu-id="654da-134">Hashed current working directory.</span></span>

<span data-ttu-id="654da-135">Funkci neshromažďuje osobní údaje, jako jsou uživatelská jména nebo e-mailové adresy.</span><span class="sxs-lookup"><span data-stu-id="654da-135">The feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="654da-136">Nebude Kontrola kódu a nebude extrahovat citlivých dat na úrovni projektu, jako je například název, úložiště nebo autora.</span><span class="sxs-lookup"><span data-stu-id="654da-136">It doesn't scan your code and doesn't extract sensitive project-level data, such as name, repo, or author.</span></span> <span data-ttu-id="654da-137">Data se odesílají bezpečně na servery Microsoftu pomocí [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technologie, uchovávat v části s omezeným přístupem a publikování na základě striktní bezpečnostní opatření z zabezpečené [službyAzureStorage](https://azure.microsoft.com/services/storage/) systémy.</span><span class="sxs-lookup"><span data-stu-id="654da-137">The data is sent securely to Microsoft servers using [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="654da-138">Tým .NET chce vědět, jak se používají nástroje a pokud pracují dobře, nejsou sestavení pomocí nástrojů.</span><span class="sxs-lookup"><span data-stu-id="654da-138">The .NET team wants to know how the tools are used and if they're working well, not what you're building with the tools.</span></span> <span data-ttu-id="654da-139">Pokud máte podezření, že se citlivá data nebo, který sbírá telemetrických dat dat se nezabezpečeným způsobem nebo neoprávněně zpracována, založte problém v [dotnet/cli](https://github.com/dotnet/cli/issues) úložiště pro šetření.</span><span class="sxs-lookup"><span data-stu-id="654da-139">If you suspect that the telemetry is collecting sensitive data or that the data is being insecurely or inappropriately handled, file an issue in the [dotnet/cli](https://github.com/dotnet/cli/issues) repository for investigation.</span></span>

## <a name="published-data"></a><span data-ttu-id="654da-140">Publikovaná data</span><span class="sxs-lookup"><span data-stu-id="654da-140">Published data</span></span>

<span data-ttu-id="654da-141">Publikovaná data čtvrtletně je k dispozici a jsou uvedeny v tématu [Data o využití sady SDK .NET Core](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span><span class="sxs-lookup"><span data-stu-id="654da-141">Published data is available quarterly and are listed at [.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span></span> <span data-ttu-id="654da-142">Jsou sloupce datového souboru:</span><span class="sxs-lookup"><span data-stu-id="654da-142">The columns of a data file are:</span></span>

- <span data-ttu-id="654da-143">Časové razítko</span><span class="sxs-lookup"><span data-stu-id="654da-143">Timestamp</span></span>
- <span data-ttu-id="654da-144">Occurrences&#8224;</span><span class="sxs-lookup"><span data-stu-id="654da-144">Occurrences&#8224;</span></span>
- <span data-ttu-id="654da-145">Příkaz</span><span class="sxs-lookup"><span data-stu-id="654da-145">Command</span></span>
- <span data-ttu-id="654da-146">Zeměpisné oblasti&#8225;</span><span class="sxs-lookup"><span data-stu-id="654da-146">Geography&#8225;</span></span>
- <span data-ttu-id="654da-147">Atribut OSFamily</span><span class="sxs-lookup"><span data-stu-id="654da-147">OSFamily</span></span>
- <span data-ttu-id="654da-148">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="654da-148">RuntimeID</span></span>
- <span data-ttu-id="654da-149">OSVersion</span><span class="sxs-lookup"><span data-stu-id="654da-149">OSVersion</span></span>
- <span data-ttu-id="654da-150">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="654da-150">SDKVersion</span></span>

<span data-ttu-id="654da-151">&#8224;*Výskyty* sloupec zobrazuje agregace počet použití tohoto příkazu pro tento řádek metrik daný den.</span><span class="sxs-lookup"><span data-stu-id="654da-151">&#8224;The *Occurrences* column displays the aggregate count of that command's use for that row's metrics that day.</span></span>

<span data-ttu-id="654da-152">&#8225;Obvykle *zeměpisné oblasti* sloupec zobrazuje název země.</span><span class="sxs-lookup"><span data-stu-id="654da-152">&#8225;Typically, the *Geography* column displays the name of a country.</span></span> <span data-ttu-id="654da-153">V některých případech se v tomto sloupci, ať už z důvodu výzkumných pracovníků pomocí platformy .NET Core v Antarktida nebo nesprávné umístění dat zobrazí kontinent Antarktida.</span><span class="sxs-lookup"><span data-stu-id="654da-153">In some cases, the continent of Antarctica appears in this column, either due to researchers using .NET Core in Antarctica or incorrect location data.</span></span>

### <a name="example"></a><span data-ttu-id="654da-154">Příklad</span><span class="sxs-lookup"><span data-stu-id="654da-154">Example</span></span>

| <span data-ttu-id="654da-155">Časové razítko</span><span class="sxs-lookup"><span data-stu-id="654da-155">Timestamp</span></span>      | <span data-ttu-id="654da-156">Výskyty</span><span class="sxs-lookup"><span data-stu-id="654da-156">Occurrences</span></span> | <span data-ttu-id="654da-157">Příkaz</span><span class="sxs-lookup"><span data-stu-id="654da-157">Command</span></span> | <span data-ttu-id="654da-158">Zeměpisné oblasti</span><span class="sxs-lookup"><span data-stu-id="654da-158">Geography</span></span> | <span data-ttu-id="654da-159">Atribut OSFamily</span><span class="sxs-lookup"><span data-stu-id="654da-159">OSFamily</span></span> | <span data-ttu-id="654da-160">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="654da-160">RuntimeID</span></span>     | <span data-ttu-id="654da-161">OSVersion</span><span class="sxs-lookup"><span data-stu-id="654da-161">OSVersion</span></span> | <span data-ttu-id="654da-162">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="654da-162">SDKVersion</span></span> |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| <span data-ttu-id="654da-163">4/16/2017 0:00</span><span class="sxs-lookup"><span data-stu-id="654da-163">4/16/2017 0:00</span></span> | <span data-ttu-id="654da-164">8</span><span class="sxs-lookup"><span data-stu-id="654da-164">8</span></span>           | <span data-ttu-id="654da-165">Spuštění</span><span class="sxs-lookup"><span data-stu-id="654da-165">run</span></span>     | <span data-ttu-id="654da-166">Uganda</span><span class="sxs-lookup"><span data-stu-id="654da-166">Uganda</span></span>    | <span data-ttu-id="654da-167">Darwin</span><span class="sxs-lookup"><span data-stu-id="654da-167">Darwin</span></span>   | <span data-ttu-id="654da-168">osx.10.12-x64</span><span class="sxs-lookup"><span data-stu-id="654da-168">osx.10.12-x64</span></span> | <span data-ttu-id="654da-169">10.12</span><span class="sxs-lookup"><span data-stu-id="654da-169">10.12</span></span>     | <span data-ttu-id="654da-170">1.0.1</span><span class="sxs-lookup"><span data-stu-id="654da-170">1.0.1</span></span>      |

### <a name="datasets"></a><span data-ttu-id="654da-171">Datové sady</span><span class="sxs-lookup"><span data-stu-id="654da-171">Datasets</span></span>

[<span data-ttu-id="654da-172">2016 - 3. ČTVRTLETÍ</span><span class="sxs-lookup"><span data-stu-id="654da-172">2016 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)  
[<span data-ttu-id="654da-173">2016 – 4.</span><span class="sxs-lookup"><span data-stu-id="654da-173">2016 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)  
[<span data-ttu-id="654da-174">2017 – Q1</span><span class="sxs-lookup"><span data-stu-id="654da-174">2017 - Q1</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)  
[<span data-ttu-id="654da-175">2017 - 2. ČTVRTLETÍ</span><span class="sxs-lookup"><span data-stu-id="654da-175">2017 - Q2</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)  
[<span data-ttu-id="654da-176">2017 - 3. ČTVRTLETÍ</span><span class="sxs-lookup"><span data-stu-id="654da-176">2017 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q3.tsv)  
[<span data-ttu-id="654da-177">2017 - 4.</span><span class="sxs-lookup"><span data-stu-id="654da-177">2017 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q4.tsv)  

<span data-ttu-id="654da-178">Další datové sady jsou odeslány pomocí standardní formát adresy URL.</span><span class="sxs-lookup"><span data-stu-id="654da-178">Additional datasets are posted using a standard URL format.</span></span> <span data-ttu-id="654da-179">Nahraďte `<YEAR>` rokem a nahradit `<QUARTER>` s čtvrtletí v roce (použijte `1`, `2`, `3`, nebo `4`).</span><span class="sxs-lookup"><span data-stu-id="654da-179">Replace `<YEAR>` with the year and replace `<QUARTER>` with the quarter of the year (use `1`, `2`, `3`, or `4`).</span></span> <span data-ttu-id="654da-180">Soubory jsou v hodnoty oddělené tabulátorem (*TSV*) formát.</span><span class="sxs-lookup"><span data-stu-id="654da-180">The files are in tab-separated values (*TSV*) format.</span></span>

`https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv`

## <a name="license"></a><span data-ttu-id="654da-181">Licence</span><span class="sxs-lookup"><span data-stu-id="654da-181">License</span></span>

<span data-ttu-id="654da-182">Je distribuce Microsoftu .NET Core licenci [smlouva EULA KNIHOVNY MICROSOFT .NET](https://aka.ms/dotnet-core-eula).</span><span class="sxs-lookup"><span data-stu-id="654da-182">The Microsoft distribution of .NET Core is licensed with the [MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="654da-183">Platnost této licence obsahuje oddíl "DATA" Povolit telemetrii (viz dole).</span><span class="sxs-lookup"><span data-stu-id="654da-183">This license includes the "DATA" section to enable telemetry (shown below).</span></span>

<span data-ttu-id="654da-184">[Balíčky .NET NuGet](https://www.nuget.org/profiles/dotnetframework) používají stejné licence, ale nepovolí telemetrie (naleznete v tématu [oboru](#scope)).</span><span class="sxs-lookup"><span data-stu-id="654da-184">[.NET NuGet packages](https://www.nuget.org/profiles/dotnetframework) use the same license but don't enable telemetry (see [Scope](#scope)).</span></span>

> 2. <span data-ttu-id="654da-185">DATA.</span><span class="sxs-lookup"><span data-stu-id="654da-185">DATA.</span></span> <span data-ttu-id="654da-186">Software může shromažďovat informace o vás a vaše užívání tohoto softwaru a zasílat je společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="654da-186">The software may collect information about you and your use of the software, and send that to Microsoft.</span></span> <span data-ttu-id="654da-187">Microsoft může použít tyto informace k vylepšování našich produktů a služeb.</span><span class="sxs-lookup"><span data-stu-id="654da-187">Microsoft may use this information to improve our products and services.</span></span> <span data-ttu-id="654da-188">Můžete získat další informace o shromažďování dat a používat v dokumentaci nápovědy a v prohlášení o ochraně osobních údajů na adrese http://go.microsoft.com/fwlink/?LinkId=528096.</span><span class="sxs-lookup"><span data-stu-id="654da-188">You can learn more about data collection and use in the help documentation and the privacy statement at http://go.microsoft.com/fwlink/?LinkId=528096.</span></span> <span data-ttu-id="654da-189">Pracuje vaše užívání tohoto softwaru vyjadřujete souhlas s těmito postupy.</span><span class="sxs-lookup"><span data-stu-id="654da-189">Your use of the software operates as your consent to these practices.</span></span>

## <a name="disclosure"></a><span data-ttu-id="654da-190">Zpřístupnění</span><span class="sxs-lookup"><span data-stu-id="654da-190">Disclosure</span></span>

<span data-ttu-id="654da-191">.NET Core SDK zobrazí při prvním spuštění jednu z následující text [příkazy rozhraní příkazového řádku .NET Core](index.md) (například `dotnet restore`).</span><span class="sxs-lookup"><span data-stu-id="654da-191">The .NET Core SDK displays the following text when you first run one of the [.NET Core CLI commands](index.md) (for example, `dotnet restore`).</span></span> <span data-ttu-id="654da-192">Text může mírně lišit v závislosti na verzi sady SDK, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="654da-192">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="654da-193">Toto prostředí "prvního spuštění" je, jak Microsoft upozorní vás na shromažďování dat.</span><span class="sxs-lookup"><span data-stu-id="654da-193">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="654da-194">Viz také:</span><span class="sxs-lookup"><span data-stu-id="654da-194">See also</span></span>

- [<span data-ttu-id="654da-195">Co jsme se naučili z telemetrická data sady SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="654da-195">What we've learned from .NET Core SDK Telemetry</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/)
- [<span data-ttu-id="654da-196">Odkaz na zdroj telemetrie (úložišti dotnet/cli)</span><span class="sxs-lookup"><span data-stu-id="654da-196">Telemetry reference source (dotnet/cli repo)</span></span>](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)
- [<span data-ttu-id="654da-197">Data o využití sady SDK .NET core</span><span class="sxs-lookup"><span data-stu-id="654da-197">.NET Core SDK Usage Data</span></span>](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)
