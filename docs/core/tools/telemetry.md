---
title: ".NET core rozhraní příkazového řádku nástroje telemetrie"
description: "Seznamte se s funkcemi telemetrie nástroje .NET Core, která shromažďují informace o využití za účelem analýzy, která data se shromažďují a jak ji zakázat."
keywords: "Rozhraní .NET, .NET core telemetrie"
author: richlander
ms.author: mairaw
ms.date: 08/04/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 480df976-7568-4df4-9d26-9911357b5a31
ms.workload: dotnetcore
ms.openlocfilehash: 66ad63f0b2a2f62f34f0784b236d242f1d92066a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="net-core-cli-tools-telemetry"></a><span data-ttu-id="89b89-104">.NET core rozhraní příkazového řádku nástroje telemetrie</span><span class="sxs-lookup"><span data-stu-id="89b89-104">.NET Core CLI Tools telemetry</span></span>

<span data-ttu-id="89b89-105">[.NET Core SDK](index.md) zahrnuje [telemetrie funkce](https://github.com/dotnet/cli/pull/2145) který shromažďuje informace o využití.</span><span class="sxs-lookup"><span data-stu-id="89b89-105">The [.NET Core SDK](index.md) includes a [telemetry feature](https://github.com/dotnet/cli/pull/2145) that collects usage information.</span></span> <span data-ttu-id="89b89-106">Je důležité, aby týmem rozhraní .NET znali použití nástroje tak, aby můžeme vylepšit je.</span><span class="sxs-lookup"><span data-stu-id="89b89-106">It's important that the .NET Team understands how the tools are used so that we can improve them.</span></span> <span data-ttu-id="89b89-107">Další informace najdete v tématu [co jsme jste se naučili z .NET Core SDK Telemetrie](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).</span><span class="sxs-lookup"><span data-stu-id="89b89-107">For more information, see [What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).</span></span>

<span data-ttu-id="89b89-108">Shromážděná data je anonymní a publikované v souhrnné podobě k použití společností Microsoft a komunitou pod [Creative Commons porušení licence](https://creativecommons.org/licenses/by/4.0/).</span><span class="sxs-lookup"><span data-stu-id="89b89-108">The collected data is anonymous and published in an aggregated form for use by both Microsoft and the community under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span> 

## <a name="scope"></a><span data-ttu-id="89b89-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="89b89-109">Scope</span></span>

<span data-ttu-id="89b89-110">`dotnet` Je příkaz použitý ke spuštění aplikace a rozhraní příkazového řádku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="89b89-110">The `dotnet` command is used to launch both apps and the .NET Core CLI.</span></span> <span data-ttu-id="89b89-111">`dotnet` Samotný příkaz nebude shromažďovat telemetrická data.</span><span class="sxs-lookup"><span data-stu-id="89b89-111">The `dotnet` command itself doesn't collect telemetry.</span></span> <span data-ttu-id="89b89-112">Rozhraní .NET Core příkazového řádku spustit `dotnet` příkaz shromažďovat telemetrii.</span><span class="sxs-lookup"><span data-stu-id="89b89-112">The .NET Core CLI commands run by the `dotnet` command collect the telemetry.</span></span>

<span data-ttu-id="89b89-113">Telemetrie *není povoleno* při použití `dotnet` samostatně, příkaz se žádný příkaz není připojen:</span><span class="sxs-lookup"><span data-stu-id="89b89-113">Telemetry *isn't enabled* when using the `dotnet` command itself, with no command attached:</span></span>

- `dotnet`
- `dotnet [path-to-app]`

<span data-ttu-id="89b89-114">Telemetrie *je povoleno* při použití [.NET Core rozhraní příkazového řádku](index.md), jako například:</span><span class="sxs-lookup"><span data-stu-id="89b89-114">Telemetry *is enabled* when using the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`


## <a name="behavior"></a><span data-ttu-id="89b89-115">Chování</span><span class="sxs-lookup"><span data-stu-id="89b89-115">Behavior</span></span>

<span data-ttu-id="89b89-116">Ve výchozím nastavení je povolena funkce telemetrie nástrojů příkazového řádku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="89b89-116">The .NET Core CLI Tools telemetry feature is enabled by default.</span></span> <span data-ttu-id="89b89-117">Výslovný nesouhlas funkci telemetrie nastavením `DOTNET_CLI_TELEMETRY_OPTOUT` proměnnou prostředí `1` nebo `true`.</span><span class="sxs-lookup"><span data-stu-id="89b89-117">Opt-out of the telemetry feature by setting the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

## <a name="data-points"></a><span data-ttu-id="89b89-118">Datové body</span><span class="sxs-lookup"><span data-stu-id="89b89-118">Data points</span></span>

<span data-ttu-id="89b89-119">Funkci shromažďuje následující data:</span><span class="sxs-lookup"><span data-stu-id="89b89-119">The feature collects the following data:</span></span>

- <span data-ttu-id="89b89-120">Časové razítko volání &#8224;</span><span class="sxs-lookup"><span data-stu-id="89b89-120">Timestamp of invocation&#8224;</span></span>
- <span data-ttu-id="89b89-121">Příkaz vyvolat (například "sestavení") &#8224;</span><span class="sxs-lookup"><span data-stu-id="89b89-121">Command invoked (for example, "build")&#8224;</span></span>
- <span data-ttu-id="89b89-122">Tři octet adresa IP použitá k určení zeměpisné umístění &#8224;</span><span class="sxs-lookup"><span data-stu-id="89b89-122">Three octet IP address used to determine geographical location&#8224;</span></span>
- <span data-ttu-id="89b89-123">`ExitCode`příkaz</span><span class="sxs-lookup"><span data-stu-id="89b89-123">`ExitCode` of the command</span></span>
- <span data-ttu-id="89b89-124">Spuštění testu (pro testovací projekty)</span><span class="sxs-lookup"><span data-stu-id="89b89-124">Test runner (for test projects)</span></span>
- <span data-ttu-id="89b89-125">Operační systém a verze &#8224;</span><span class="sxs-lookup"><span data-stu-id="89b89-125">Operating system and version&#8224;</span></span>
- <span data-ttu-id="89b89-126">Jestli se nacházejí v uzlu moduly runtime ID modulu runtime</span><span class="sxs-lookup"><span data-stu-id="89b89-126">Whether runtime IDs are present in the runtimes node</span></span>
- <span data-ttu-id="89b89-127">Verze rozhraní .NET core SDK &#8224;</span><span class="sxs-lookup"><span data-stu-id="89b89-127">.NET Core SDK version&#8224;</span></span>

<span data-ttu-id="89b89-128">&#8224; Tato metrika je publikován.</span><span class="sxs-lookup"><span data-stu-id="89b89-128">&#8224;This metric is published.</span></span>

<span data-ttu-id="89b89-129">Od verze rozhraní .NET Core SDK 2.0, se shromažďují nové datové body:</span><span class="sxs-lookup"><span data-stu-id="89b89-129">Starting with .NET Core SDK 2.0, new data points are collected:</span></span>

- <span data-ttu-id="89b89-130">`dotnet`příkaz Možnosti a argumenty: pouze známé argumenty a možnosti jsou shromážděná (ne libovolný řetězce).</span><span class="sxs-lookup"><span data-stu-id="89b89-130">`dotnet` command arguments and options: only known arguments and options are collected (not arbitrary strings).</span></span>
- <span data-ttu-id="89b89-131">Zda je spuštěna sada SDK v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="89b89-131">Whether the SDK is running in a container.</span></span>
- <span data-ttu-id="89b89-132">Cílové architektury.</span><span class="sxs-lookup"><span data-stu-id="89b89-132">Target frameworks.</span></span>
- <span data-ttu-id="89b89-133">Adresu MAC s použitím algoritmu hash: kryptograficky (SHA256) anonymní a jedinečné ID pro počítač.</span><span class="sxs-lookup"><span data-stu-id="89b89-133">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> <span data-ttu-id="89b89-134">Tato metrika není publikována.</span><span class="sxs-lookup"><span data-stu-id="89b89-134">This metric is not published.</span></span>
- <span data-ttu-id="89b89-135">Hash aktuální pracovní adresář.</span><span class="sxs-lookup"><span data-stu-id="89b89-135">Hashed current working directory.</span></span>

<span data-ttu-id="89b89-136">Tato funkce nebude shromažďovat osobní údaje, jako jsou uživatelská jména nebo e-mailové adresy.</span><span class="sxs-lookup"><span data-stu-id="89b89-136">The feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="89b89-137">Ji nelze kontrolovat kódu a není pro extrahování citlivých dat úrovni projektu, například název, úložišti nebo autora.</span><span class="sxs-lookup"><span data-stu-id="89b89-137">It doesn't scan your code and doesn't extract sensitive project-level data, such as name, repo, or author.</span></span> <span data-ttu-id="89b89-138">Data se odesílají bezpečně servery Microsoftu pomocí [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technologie, uchovávat v části s omezeným přístupem a publikovat v části ovládací prvky přísných bezpečnostních ze zabezpečeného [Azure Storage](https://azure.microsoft.com/services/storage/) systémy.</span><span class="sxs-lookup"><span data-stu-id="89b89-138">The data is sent securely to Microsoft servers using [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="89b89-139">Chceme vědět, jak se používají nástroje a pokud pracují dobře, co nejsou s nástroji pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="89b89-139">We want to know how the tools are used and if they're working well, not what you're building with the tools.</span></span> <span data-ttu-id="89b89-140">Pokud máte podezření, že je telemetrii shromažďování citlivá data nebo že nám nezabezpečeným nebo nesprávně zpracování dat, [souboru problém v úložišti dotnet/cli problémy](https://github.com/dotnet/cli/issues) pro šetření.</span><span class="sxs-lookup"><span data-stu-id="89b89-140">If you suspect that the telemetry is collecting sensitive data or that we're insecurely or inappropriately handling data, [file an issue in the dotnet/cli repo issues](https://github.com/dotnet/cli/issues) for investigation.</span></span>

## <a name="published-data"></a><span data-ttu-id="89b89-141">Publikovaná data</span><span class="sxs-lookup"><span data-stu-id="89b89-141">Published data</span></span>

<span data-ttu-id="89b89-142">Publikovaná data čtvrtletně je k dispozici a jsou uvedeny v [Data o využití .NET Core SDK](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span><span class="sxs-lookup"><span data-stu-id="89b89-142">Published data is available quarterly and are listed at [.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span></span> <span data-ttu-id="89b89-143">Sloupce datového souboru jsou:</span><span class="sxs-lookup"><span data-stu-id="89b89-143">The columns of a data file are:</span></span>
- <span data-ttu-id="89b89-144">časové razítko</span><span class="sxs-lookup"><span data-stu-id="89b89-144">Timestamp</span></span>
- <span data-ttu-id="89b89-145">Výskytů &#8224;</span><span class="sxs-lookup"><span data-stu-id="89b89-145">Occurrences&#8224;</span></span>
- <span data-ttu-id="89b89-146">Příkaz</span><span class="sxs-lookup"><span data-stu-id="89b89-146">Command</span></span>
- <span data-ttu-id="89b89-147">Geography &#8225;</span><span class="sxs-lookup"><span data-stu-id="89b89-147">Geography&#8225;</span></span>
- <span data-ttu-id="89b89-148">Atribut OSFamily</span><span class="sxs-lookup"><span data-stu-id="89b89-148">OSFamily</span></span>
- <span data-ttu-id="89b89-149">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="89b89-149">RuntimeID</span></span>
- <span data-ttu-id="89b89-150">OSVersion</span><span class="sxs-lookup"><span data-stu-id="89b89-150">OSVersion</span></span>
- <span data-ttu-id="89b89-151">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="89b89-151">SDKVersion</span></span>

<span data-ttu-id="89b89-152">&#8224; *Výskytů* sloupec zobrazuje agregovaná počet tento příkaz použijte pro tento řádek metriky daný den.</span><span class="sxs-lookup"><span data-stu-id="89b89-152">&#8224;The *Occurrences* column displays the aggregate count of that command's use for that row's metrics that day.</span></span> 

<span data-ttu-id="89b89-153">&#8225; Obvykle *Geography* sloupec zobrazuje název země.</span><span class="sxs-lookup"><span data-stu-id="89b89-153">&#8225;Typically, the *Geography* column displays the name of a country.</span></span> <span data-ttu-id="89b89-154">V některých případech se zobrazí na kontinentě Antarktida v tomto sloupci, buď z důvodu výzkumných pracovníků pomocí .NET Core Antarktida nebo data nesprávné umístění.</span><span class="sxs-lookup"><span data-stu-id="89b89-154">In some cases, the continent of Antarctica appears in this column, either due to researchers using .NET Core in Antarctica or incorrect location data.</span></span>

### <a name="example"></a><span data-ttu-id="89b89-155">Příklad</span><span class="sxs-lookup"><span data-stu-id="89b89-155">Example</span></span>

| <span data-ttu-id="89b89-156">časové razítko</span><span class="sxs-lookup"><span data-stu-id="89b89-156">Timestamp</span></span>      | <span data-ttu-id="89b89-157">Výskytů</span><span class="sxs-lookup"><span data-stu-id="89b89-157">Occurrences</span></span> | <span data-ttu-id="89b89-158">Příkaz</span><span class="sxs-lookup"><span data-stu-id="89b89-158">Command</span></span> | <span data-ttu-id="89b89-159">Geography</span><span class="sxs-lookup"><span data-stu-id="89b89-159">Geography</span></span> | <span data-ttu-id="89b89-160">Atribut OSFamily</span><span class="sxs-lookup"><span data-stu-id="89b89-160">OSFamily</span></span> | <span data-ttu-id="89b89-161">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="89b89-161">RuntimeID</span></span>     | <span data-ttu-id="89b89-162">OSVersion</span><span class="sxs-lookup"><span data-stu-id="89b89-162">OSVersion</span></span> | <span data-ttu-id="89b89-163">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="89b89-163">SDKVersion</span></span> |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| <span data-ttu-id="89b89-164">4/16/2017 0:00</span><span class="sxs-lookup"><span data-stu-id="89b89-164">4/16/2017 0:00</span></span> | <span data-ttu-id="89b89-165">8</span><span class="sxs-lookup"><span data-stu-id="89b89-165">8</span></span>           | <span data-ttu-id="89b89-166">Spustit</span><span class="sxs-lookup"><span data-stu-id="89b89-166">run</span></span>     | <span data-ttu-id="89b89-167">Ugandy</span><span class="sxs-lookup"><span data-stu-id="89b89-167">Uganda</span></span>    | <span data-ttu-id="89b89-168">Darwin</span><span class="sxs-lookup"><span data-stu-id="89b89-168">Darwin</span></span>   | <span data-ttu-id="89b89-169">OSX.10.12 x64</span><span class="sxs-lookup"><span data-stu-id="89b89-169">osx.10.12-x64</span></span> | <span data-ttu-id="89b89-170">10.12</span><span class="sxs-lookup"><span data-stu-id="89b89-170">10.12</span></span>     | <span data-ttu-id="89b89-171">1.0.1</span><span class="sxs-lookup"><span data-stu-id="89b89-171">1.0.1</span></span>      |

### <a name="datasets"></a><span data-ttu-id="89b89-172">Datové sady</span><span class="sxs-lookup"><span data-stu-id="89b89-172">Datasets</span></span>

[<span data-ttu-id="89b89-173">2016 - 3. ČTVRTLETÍ</span><span class="sxs-lookup"><span data-stu-id="89b89-173">2016 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)  
[<span data-ttu-id="89b89-174">2016 - 4.</span><span class="sxs-lookup"><span data-stu-id="89b89-174">2016 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)  
[<span data-ttu-id="89b89-175">2017 - 1.</span><span class="sxs-lookup"><span data-stu-id="89b89-175">2017 - Q1</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)  
[<span data-ttu-id="89b89-176">2017 - DOTAZ Č. 2</span><span class="sxs-lookup"><span data-stu-id="89b89-176">2017 - Q2</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)

<span data-ttu-id="89b89-177">Další datové sady jsou odeslány standardní formátu adresy URL.</span><span class="sxs-lookup"><span data-stu-id="89b89-177">Additional datasets are posted using a standard URL format.</span></span> <span data-ttu-id="89b89-178">Nahraďte `<YEAR>` s za rok a nahraďte `<QUARTER>` s čtvrtletí v roce (použijte `1`, `2`, `3`, nebo `4`).</span><span class="sxs-lookup"><span data-stu-id="89b89-178">Replace `<YEAR>` with the year and replace `<QUARTER>` with the quarter of the year (use `1`, `2`, `3`, or `4`).</span></span> <span data-ttu-id="89b89-179">Soubory jsou v kartě s oddělovači (*TSV*) formátu.</span><span class="sxs-lookup"><span data-stu-id="89b89-179">The files are in tab-separated values (*TSV*) format.</span></span> 

```
https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv
```

## <a name="license"></a><span data-ttu-id="89b89-180">Licence</span><span class="sxs-lookup"><span data-stu-id="89b89-180">License</span></span>

<span data-ttu-id="89b89-181">Distribuce Microsoft .NET Core má licenci na [smlouvy EULA KNIHOVNY MICROSOFT .NET](https://aka.ms/dotnet-core-eula).</span><span class="sxs-lookup"><span data-stu-id="89b89-181">The Microsoft distribution of .NET Core is licensed with the [MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="89b89-182">Tuto licenci zahrnuje v části "DATA" Povolit telemetrii (zobrazené dole).</span><span class="sxs-lookup"><span data-stu-id="89b89-182">This license includes the "DATA" section to enable telemetry (shown below).</span></span>

<span data-ttu-id="89b89-183">[Balíčky NuGet pro rozhraní .NET](https://www.nuget.org/profiles/dotnetframework) použít licence, které jsou stejné, ale nepovolíte telemetrie (najdete v části [oboru](#scope)).</span><span class="sxs-lookup"><span data-stu-id="89b89-183">[.NET NuGet packages](https://www.nuget.org/profiles/dotnetframework) use the same license but don't enable telemetry (see [Scope](#scope)).</span></span>

> 2. <span data-ttu-id="89b89-184">DATA.</span><span class="sxs-lookup"><span data-stu-id="89b89-184">DATA.</span></span> <span data-ttu-id="89b89-185">Software může shromažďovat informace o vás a používání softwaru a který odesílat společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="89b89-185">The software may collect information about you and your use of the software, and send that to Microsoft.</span></span> <span data-ttu-id="89b89-186">Microsoft může tyto informace využívat ke zlepšování našich produktů a služeb.</span><span class="sxs-lookup"><span data-stu-id="89b89-186">Microsoft may use this information to improve our products and services.</span></span> <span data-ttu-id="89b89-187">Můžete získat další informace o shromažďování dat a použít v prohlášení o ochraně osobních údajů v http://go.microsoft.com/fwlink/?LinkId=528096 a v nápovědě.</span><span class="sxs-lookup"><span data-stu-id="89b89-187">You can learn more about data collection and use in the help documentation and the privacy statement at http://go.microsoft.com/fwlink/?LinkId=528096.</span></span> <span data-ttu-id="89b89-188">Používání softwaru funguje jako svůj souhlas s tyto postupy.</span><span class="sxs-lookup"><span data-stu-id="89b89-188">Your use of the software operates as your consent to these practices.</span></span>

## <a name="disclosure"></a><span data-ttu-id="89b89-189">Zpřístupnění</span><span class="sxs-lookup"><span data-stu-id="89b89-189">Disclosure</span></span>

<span data-ttu-id="89b89-190">.NET Core rozhraní příkazového řádku nástroje zobrazit následující text při prvním spuštění příkazy (například `dotnet restore`).</span><span class="sxs-lookup"><span data-stu-id="89b89-190">The .NET Core CLI Tools display the following text when you first run one of the commands (for example, `dotnet restore`).</span></span> <span data-ttu-id="89b89-191">Text se může mírně lišit v závislosti na verzi sady SDK, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="89b89-191">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="89b89-192">Toto prostředí "nejprve spustit" je, jak Microsoft upozorní vás na shromažďování dat.</span><span class="sxs-lookup"><span data-stu-id="89b89-192">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

```console
Welcome to .NET Core!
---------------------
Learn more about .NET Core @ https://aka.ms/dotnet-docs. Use dotnet --help to see available commands or go to https://aka.ms/dotnet-cli-docs.
 
Telemetry
--------------
The .NET Core tools collect usage data in order to improve your experience. The data is anonymous and does not include command-line arguments. The data is collected by Microsoft and shared with the community.
You can opt out of telemetry by setting a DOTNET_CLI_TELEMETRY_OPTOUT environment variable to 1 using your favorite shell.
You can read more about .NET Core tools telemetry @ https://aka.ms/dotnet-cli-telemetry.
```

## <a name="see-also"></a><span data-ttu-id="89b89-193">Viz také</span><span class="sxs-lookup"><span data-stu-id="89b89-193">See also</span></span>

[<span data-ttu-id="89b89-194">Co jsme jste se naučili z .NET Core SDK Telemetrie</span><span class="sxs-lookup"><span data-stu-id="89b89-194">What we've learned from .NET Core SDK Telemetry</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/)  
<span data-ttu-id="89b89-195">[Odkaz na zdroj telemetrie (dotnet/cli úložišti; release/2.0.0 větve)](https://github.com/dotnet/cli/blob/release/2.0.0/src/dotnet/Telemetry.cs) </span><span class="sxs-lookup"><span data-stu-id="89b89-195">[Telemetry reference source (dotnet/cli repo; release/2.0.0 branch)](https://github.com/dotnet/cli/blob/release/2.0.0/src/dotnet/Telemetry.cs) </span></span>  
[<span data-ttu-id="89b89-196">Data o využití .NET core SDK</span><span class="sxs-lookup"><span data-stu-id="89b89-196">.NET Core SDK Usage Data</span></span>](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)
