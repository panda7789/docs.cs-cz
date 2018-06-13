---
title: .NET core rozhraní příkazového řádku nástroje telemetrie
description: Seznamte se s funkcemi telemetrie nástroje .NET Core, která shromažďují informace o využití za účelem analýzy, která data se shromažďují a jak ji zakázat.
author: richlander
ms.author: mairaw
ms.date: 08/04/2017
ms.openlocfilehash: 4c04867f5db512ef53c23ec41ea66db570a82021
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216080"
---
# <a name="net-core-cli-tools-telemetry"></a><span data-ttu-id="957da-103">.NET core rozhraní příkazového řádku nástroje telemetrie</span><span class="sxs-lookup"><span data-stu-id="957da-103">.NET Core CLI Tools telemetry</span></span>

<span data-ttu-id="957da-104">[.NET Core SDK](index.md) zahrnuje [telemetrie funkce](https://github.com/dotnet/cli/pull/2145) který shromažďuje informace o využití.</span><span class="sxs-lookup"><span data-stu-id="957da-104">The [.NET Core SDK](index.md) includes a [telemetry feature](https://github.com/dotnet/cli/pull/2145) that collects usage information.</span></span> <span data-ttu-id="957da-105">Je důležité, aby týmem rozhraní .NET znali použití nástroje tak, aby můžeme vylepšit je.</span><span class="sxs-lookup"><span data-stu-id="957da-105">It's important that the .NET Team understands how the tools are used so that we can improve them.</span></span> <span data-ttu-id="957da-106">Další informace najdete v tématu [co jsme jste se naučili z .NET Core SDK Telemetrie](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).</span><span class="sxs-lookup"><span data-stu-id="957da-106">For more information, see [What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/).</span></span>

<span data-ttu-id="957da-107">Shromážděná data je anonymní a publikované v souhrnné podobě k použití společností Microsoft a komunitou pod [Creative Commons porušení licence](https://creativecommons.org/licenses/by/4.0/).</span><span class="sxs-lookup"><span data-stu-id="957da-107">The collected data is anonymous and published in an aggregated form for use by both Microsoft and the community under the [Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).</span></span> 

## <a name="scope"></a><span data-ttu-id="957da-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="957da-108">Scope</span></span>

<span data-ttu-id="957da-109">`dotnet` Je příkaz použitý ke spuštění aplikace a rozhraní příkazového řádku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="957da-109">The `dotnet` command is used to launch both apps and the .NET Core CLI.</span></span> <span data-ttu-id="957da-110">`dotnet` Samotný příkaz nebude shromažďovat telemetrická data.</span><span class="sxs-lookup"><span data-stu-id="957da-110">The `dotnet` command itself doesn't collect telemetry.</span></span> <span data-ttu-id="957da-111">Rozhraní .NET Core příkazového řádku spustit `dotnet` příkaz shromažďovat telemetrii.</span><span class="sxs-lookup"><span data-stu-id="957da-111">The .NET Core CLI commands run by the `dotnet` command collect the telemetry.</span></span>

<span data-ttu-id="957da-112">Telemetrie *není povoleno* při použití `dotnet` samostatně, příkaz se žádný příkaz není připojen:</span><span class="sxs-lookup"><span data-stu-id="957da-112">Telemetry *isn't enabled* when using the `dotnet` command itself, with no command attached:</span></span>

- `dotnet`
- `dotnet [path-to-app]`

<span data-ttu-id="957da-113">Telemetrie *je povoleno* při použití [.NET Core rozhraní příkazového řádku](index.md), jako například:</span><span class="sxs-lookup"><span data-stu-id="957da-113">Telemetry *is enabled* when using the [.NET Core CLI commands](index.md), such as:</span></span>

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`


## <a name="behavior"></a><span data-ttu-id="957da-114">Chování</span><span class="sxs-lookup"><span data-stu-id="957da-114">Behavior</span></span>

<span data-ttu-id="957da-115">Ve výchozím nastavení je povolena funkce telemetrie nástrojů příkazového řádku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="957da-115">The .NET Core CLI Tools telemetry feature is enabled by default.</span></span> <span data-ttu-id="957da-116">Výslovný nesouhlas funkci telemetrie nastavením `DOTNET_CLI_TELEMETRY_OPTOUT` proměnnou prostředí `1` nebo `true`.</span><span class="sxs-lookup"><span data-stu-id="957da-116">Opt-out of the telemetry feature by setting the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span>

## <a name="data-points"></a><span data-ttu-id="957da-117">Datové body</span><span class="sxs-lookup"><span data-stu-id="957da-117">Data points</span></span>

<span data-ttu-id="957da-118">Funkci shromažďuje následující data:</span><span class="sxs-lookup"><span data-stu-id="957da-118">The feature collects the following data:</span></span>

- <span data-ttu-id="957da-119">Časové razítko volání&#8224;</span><span class="sxs-lookup"><span data-stu-id="957da-119">Timestamp of invocation&#8224;</span></span>
- <span data-ttu-id="957da-120">Příkaz vyvolat (například "sestavení")&#8224;</span><span class="sxs-lookup"><span data-stu-id="957da-120">Command invoked (for example, "build")&#8224;</span></span>
- <span data-ttu-id="957da-121">Tři octet adresa IP použitá k určení zeměpisné umístění&#8224;</span><span class="sxs-lookup"><span data-stu-id="957da-121">Three octet IP address used to determine geographical location&#8224;</span></span>
- <span data-ttu-id="957da-122">`ExitCode` příkaz</span><span class="sxs-lookup"><span data-stu-id="957da-122">`ExitCode` of the command</span></span>
- <span data-ttu-id="957da-123">Spuštění testu (pro testovací projekty)</span><span class="sxs-lookup"><span data-stu-id="957da-123">Test runner (for test projects)</span></span>
- <span data-ttu-id="957da-124">Operační systém a verze&#8224;</span><span class="sxs-lookup"><span data-stu-id="957da-124">Operating system and version&#8224;</span></span>
- <span data-ttu-id="957da-125">Jestli se nacházejí v uzlu moduly runtime ID modulu runtime</span><span class="sxs-lookup"><span data-stu-id="957da-125">Whether runtime IDs are present in the runtimes node</span></span>
- <span data-ttu-id="957da-126">Verze rozhraní .NET core SDK&#8224;</span><span class="sxs-lookup"><span data-stu-id="957da-126">.NET Core SDK version&#8224;</span></span>

<span data-ttu-id="957da-127">&#8224;Tato metrika je publikován.</span><span class="sxs-lookup"><span data-stu-id="957da-127">&#8224;This metric is published.</span></span>

<span data-ttu-id="957da-128">Od verze rozhraní .NET Core SDK 2.0, se shromažďují nové datové body:</span><span class="sxs-lookup"><span data-stu-id="957da-128">Starting with .NET Core SDK 2.0, new data points are collected:</span></span>

- <span data-ttu-id="957da-129">`dotnet` příkaz Možnosti a argumenty: pouze známé argumenty a možnosti jsou shromážděná (ne libovolný řetězce).</span><span class="sxs-lookup"><span data-stu-id="957da-129">`dotnet` command arguments and options: only known arguments and options are collected (not arbitrary strings).</span></span>
- <span data-ttu-id="957da-130">Zda je spuštěna sada SDK v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="957da-130">Whether the SDK is running in a container.</span></span>
- <span data-ttu-id="957da-131">Cílové architektury.</span><span class="sxs-lookup"><span data-stu-id="957da-131">Target frameworks.</span></span>
- <span data-ttu-id="957da-132">Adresu MAC s použitím algoritmu hash: kryptograficky (SHA256) anonymní a jedinečné ID pro počítač.</span><span class="sxs-lookup"><span data-stu-id="957da-132">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine.</span></span> <span data-ttu-id="957da-133">Tato metrika není publikována.</span><span class="sxs-lookup"><span data-stu-id="957da-133">This metric is not published.</span></span>
- <span data-ttu-id="957da-134">Hash aktuální pracovní adresář.</span><span class="sxs-lookup"><span data-stu-id="957da-134">Hashed current working directory.</span></span>

<span data-ttu-id="957da-135">Tato funkce nebude shromažďovat osobní údaje, jako jsou uživatelská jména nebo e-mailové adresy.</span><span class="sxs-lookup"><span data-stu-id="957da-135">The feature doesn't collect personal data, such as usernames or email addresses.</span></span> <span data-ttu-id="957da-136">Ji nelze kontrolovat kódu a není pro extrahování citlivých dat úrovni projektu, například název, úložišti nebo autora.</span><span class="sxs-lookup"><span data-stu-id="957da-136">It doesn't scan your code and doesn't extract sensitive project-level data, such as name, repo, or author.</span></span> <span data-ttu-id="957da-137">Data se odesílají bezpečně servery Microsoftu pomocí [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technologie, uchovávat v části s omezeným přístupem a publikovat v části ovládací prvky přísných bezpečnostních ze zabezpečeného [Azure Storage](https://azure.microsoft.com/services/storage/) systémy.</span><span class="sxs-lookup"><span data-stu-id="957da-137">The data is sent securely to Microsoft servers using [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and published under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

<span data-ttu-id="957da-138">Chceme vědět, jak se používají nástroje a pokud pracují dobře, co nejsou s nástroji pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="957da-138">We want to know how the tools are used and if they're working well, not what you're building with the tools.</span></span> <span data-ttu-id="957da-139">Pokud máte podezření, že je telemetrii shromažďování citlivá data nebo že nám nezabezpečeným nebo nesprávně zpracování dat, [souboru problém v úložišti dotnet/cli problémy](https://github.com/dotnet/cli/issues) pro šetření.</span><span class="sxs-lookup"><span data-stu-id="957da-139">If you suspect that the telemetry is collecting sensitive data or that we're insecurely or inappropriately handling data, [file an issue in the dotnet/cli repo issues](https://github.com/dotnet/cli/issues) for investigation.</span></span>

## <a name="published-data"></a><span data-ttu-id="957da-140">Publikovaná data</span><span class="sxs-lookup"><span data-stu-id="957da-140">Published data</span></span>

<span data-ttu-id="957da-141">Publikovaná data čtvrtletně je k dispozici a jsou uvedeny v [Data o využití .NET Core SDK](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span><span class="sxs-lookup"><span data-stu-id="957da-141">Published data is available quarterly and are listed at [.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md).</span></span> <span data-ttu-id="957da-142">Sloupce datového souboru jsou:</span><span class="sxs-lookup"><span data-stu-id="957da-142">The columns of a data file are:</span></span>
- <span data-ttu-id="957da-143">časové razítko</span><span class="sxs-lookup"><span data-stu-id="957da-143">Timestamp</span></span>
- <span data-ttu-id="957da-144">Occurrences&#8224;</span><span class="sxs-lookup"><span data-stu-id="957da-144">Occurrences&#8224;</span></span>
- <span data-ttu-id="957da-145">Příkaz</span><span class="sxs-lookup"><span data-stu-id="957da-145">Command</span></span>
- <span data-ttu-id="957da-146">Geography&#8225;</span><span class="sxs-lookup"><span data-stu-id="957da-146">Geography&#8225;</span></span>
- <span data-ttu-id="957da-147">Atribut OSFamily</span><span class="sxs-lookup"><span data-stu-id="957da-147">OSFamily</span></span>
- <span data-ttu-id="957da-148">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="957da-148">RuntimeID</span></span>
- <span data-ttu-id="957da-149">OSVersion</span><span class="sxs-lookup"><span data-stu-id="957da-149">OSVersion</span></span>
- <span data-ttu-id="957da-150">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="957da-150">SDKVersion</span></span>

<span data-ttu-id="957da-151">&#8224;*Výskytů* sloupec zobrazuje agregovaná počet tento příkaz použijte pro tento řádek metriky daný den.</span><span class="sxs-lookup"><span data-stu-id="957da-151">&#8224;The *Occurrences* column displays the aggregate count of that command's use for that row's metrics that day.</span></span> 

<span data-ttu-id="957da-152">&#8225;Obvykle *Geography* sloupec zobrazuje název země.</span><span class="sxs-lookup"><span data-stu-id="957da-152">&#8225;Typically, the *Geography* column displays the name of a country.</span></span> <span data-ttu-id="957da-153">V některých případech se zobrazí na kontinentě Antarktida v tomto sloupci, buď z důvodu výzkumných pracovníků pomocí .NET Core Antarktida nebo data nesprávné umístění.</span><span class="sxs-lookup"><span data-stu-id="957da-153">In some cases, the continent of Antarctica appears in this column, either due to researchers using .NET Core in Antarctica or incorrect location data.</span></span>

### <a name="example"></a><span data-ttu-id="957da-154">Příklad</span><span class="sxs-lookup"><span data-stu-id="957da-154">Example</span></span>

| <span data-ttu-id="957da-155">časové razítko</span><span class="sxs-lookup"><span data-stu-id="957da-155">Timestamp</span></span>      | <span data-ttu-id="957da-156">Výskytů</span><span class="sxs-lookup"><span data-stu-id="957da-156">Occurrences</span></span> | <span data-ttu-id="957da-157">Příkaz</span><span class="sxs-lookup"><span data-stu-id="957da-157">Command</span></span> | <span data-ttu-id="957da-158">Geography</span><span class="sxs-lookup"><span data-stu-id="957da-158">Geography</span></span> | <span data-ttu-id="957da-159">Atribut OSFamily</span><span class="sxs-lookup"><span data-stu-id="957da-159">OSFamily</span></span> | <span data-ttu-id="957da-160">RuntimeID</span><span class="sxs-lookup"><span data-stu-id="957da-160">RuntimeID</span></span>     | <span data-ttu-id="957da-161">OSVersion</span><span class="sxs-lookup"><span data-stu-id="957da-161">OSVersion</span></span> | <span data-ttu-id="957da-162">SDKVersion</span><span class="sxs-lookup"><span data-stu-id="957da-162">SDKVersion</span></span> |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| <span data-ttu-id="957da-163">4/16/2017 0:00</span><span class="sxs-lookup"><span data-stu-id="957da-163">4/16/2017 0:00</span></span> | <span data-ttu-id="957da-164">8</span><span class="sxs-lookup"><span data-stu-id="957da-164">8</span></span>           | <span data-ttu-id="957da-165">Spustit</span><span class="sxs-lookup"><span data-stu-id="957da-165">run</span></span>     | <span data-ttu-id="957da-166">Ugandy</span><span class="sxs-lookup"><span data-stu-id="957da-166">Uganda</span></span>    | <span data-ttu-id="957da-167">Darwin</span><span class="sxs-lookup"><span data-stu-id="957da-167">Darwin</span></span>   | <span data-ttu-id="957da-168">osx.10.12-x64</span><span class="sxs-lookup"><span data-stu-id="957da-168">osx.10.12-x64</span></span> | <span data-ttu-id="957da-169">10.12</span><span class="sxs-lookup"><span data-stu-id="957da-169">10.12</span></span>     | <span data-ttu-id="957da-170">1.0.1</span><span class="sxs-lookup"><span data-stu-id="957da-170">1.0.1</span></span>      |

### <a name="datasets"></a><span data-ttu-id="957da-171">Datové sady</span><span class="sxs-lookup"><span data-stu-id="957da-171">Datasets</span></span>

[<span data-ttu-id="957da-172">2016 - 3. ČTVRTLETÍ</span><span class="sxs-lookup"><span data-stu-id="957da-172">2016 - Q3</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)  
[<span data-ttu-id="957da-173">2016 - 4.</span><span class="sxs-lookup"><span data-stu-id="957da-173">2016 - Q4</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)  
[<span data-ttu-id="957da-174">2017 - 1.</span><span class="sxs-lookup"><span data-stu-id="957da-174">2017 - Q1</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)  
[<span data-ttu-id="957da-175">2017 - DOTAZ Č. 2</span><span class="sxs-lookup"><span data-stu-id="957da-175">2017 - Q2</span></span>](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)

<span data-ttu-id="957da-176">Další datové sady jsou odeslány standardní formátu adresy URL.</span><span class="sxs-lookup"><span data-stu-id="957da-176">Additional datasets are posted using a standard URL format.</span></span> <span data-ttu-id="957da-177">Nahraďte `<YEAR>` s za rok a nahraďte `<QUARTER>` s čtvrtletí v roce (použijte `1`, `2`, `3`, nebo `4`).</span><span class="sxs-lookup"><span data-stu-id="957da-177">Replace `<YEAR>` with the year and replace `<QUARTER>` with the quarter of the year (use `1`, `2`, `3`, or `4`).</span></span> <span data-ttu-id="957da-178">Soubory jsou v kartě s oddělovači (*TSV*) formátu.</span><span class="sxs-lookup"><span data-stu-id="957da-178">The files are in tab-separated values (*TSV*) format.</span></span> 

```
https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv
```

## <a name="license"></a><span data-ttu-id="957da-179">Licence</span><span class="sxs-lookup"><span data-stu-id="957da-179">License</span></span>

<span data-ttu-id="957da-180">Distribuce Microsoft .NET Core má licenci na [smlouvy EULA KNIHOVNY MICROSOFT .NET](https://aka.ms/dotnet-core-eula).</span><span class="sxs-lookup"><span data-stu-id="957da-180">The Microsoft distribution of .NET Core is licensed with the [MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="957da-181">Tuto licenci zahrnuje v části "DATA" Povolit telemetrii (zobrazené dole).</span><span class="sxs-lookup"><span data-stu-id="957da-181">This license includes the "DATA" section to enable telemetry (shown below).</span></span>

<span data-ttu-id="957da-182">[Balíčky NuGet pro rozhraní .NET](https://www.nuget.org/profiles/dotnetframework) použít licence, které jsou stejné, ale nepovolíte telemetrie (najdete v části [oboru](#scope)).</span><span class="sxs-lookup"><span data-stu-id="957da-182">[.NET NuGet packages](https://www.nuget.org/profiles/dotnetframework) use the same license but don't enable telemetry (see [Scope](#scope)).</span></span>

> 2. <span data-ttu-id="957da-183">DATA.</span><span class="sxs-lookup"><span data-stu-id="957da-183">DATA.</span></span> <span data-ttu-id="957da-184">Software může shromažďovat informace o vás a používání softwaru a který odesílat společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="957da-184">The software may collect information about you and your use of the software, and send that to Microsoft.</span></span> <span data-ttu-id="957da-185">Microsoft může tyto informace využívat ke zlepšování našich produktů a služeb.</span><span class="sxs-lookup"><span data-stu-id="957da-185">Microsoft may use this information to improve our products and services.</span></span> <span data-ttu-id="957da-186">Můžete získat další informace o shromažďování dat a použít v dokumentaci nápovědy a prohlášení o ochraně osobních údajů na adrese http://go.microsoft.com/fwlink/?LinkId=528096.</span><span class="sxs-lookup"><span data-stu-id="957da-186">You can learn more about data collection and use in the help documentation and the privacy statement at http://go.microsoft.com/fwlink/?LinkId=528096.</span></span> <span data-ttu-id="957da-187">Používání softwaru funguje jako svůj souhlas s tyto postupy.</span><span class="sxs-lookup"><span data-stu-id="957da-187">Your use of the software operates as your consent to these practices.</span></span>

## <a name="disclosure"></a><span data-ttu-id="957da-188">Zpřístupnění</span><span class="sxs-lookup"><span data-stu-id="957da-188">Disclosure</span></span>

<span data-ttu-id="957da-189">.NET Core rozhraní příkazového řádku nástroje zobrazit následující text při prvním spuštění příkazy (například `dotnet restore`).</span><span class="sxs-lookup"><span data-stu-id="957da-189">The .NET Core CLI Tools display the following text when you first run one of the commands (for example, `dotnet restore`).</span></span> <span data-ttu-id="957da-190">Text se může mírně lišit v závislosti na verzi sady SDK, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="957da-190">Text may vary slightly depending on the version of the SDK you're running.</span></span> <span data-ttu-id="957da-191">Toto prostředí "nejprve spustit" je, jak Microsoft upozorní vás na shromažďování dat.</span><span class="sxs-lookup"><span data-stu-id="957da-191">This "first run" experience is how Microsoft notifies you about data collection.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="957da-192">Viz také</span><span class="sxs-lookup"><span data-stu-id="957da-192">See also</span></span>

[<span data-ttu-id="957da-193">Co jsme jste se naučili z .NET Core SDK Telemetrie</span><span class="sxs-lookup"><span data-stu-id="957da-193">What we've learned from .NET Core SDK Telemetry</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/)  
<span data-ttu-id="957da-194">[Odkaz na zdroj telemetrie (dotnet/cli úložišti; release/2.0.0 větve)](https://github.com/dotnet/cli/tree/release/2.0.0/src/dotnet/Telemetry) </span><span class="sxs-lookup"><span data-stu-id="957da-194">[Telemetry reference source (dotnet/cli repo; release/2.0.0 branch)](https://github.com/dotnet/cli/tree/release/2.0.0/src/dotnet/Telemetry) </span></span>  
[<span data-ttu-id="957da-195">Data o využití .NET core SDK</span><span class="sxs-lookup"><span data-stu-id="957da-195">.NET Core SDK Usage Data</span></span>](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)
