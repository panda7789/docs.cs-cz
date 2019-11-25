---
title: Kolekce telemetrie pomocí ML.NET CLI
description: Přečtěte si o funkcích telemetrie ML.NET CLI, které shromažďují informace o využití pro analýzu, shromažďovaná data a jejich zakázání. Vyhledejte také odkazy na licenční smlouvu .NET a informace o dodržování předpisů v Microsoft GDPRe.
ms.topic: conceptual
ms.date: 09/03/2019
ms.custom: ''
ms.openlocfilehash: edd74b6f3d3c50d5eff012629f0b1db6b62d9021
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977269"
---
# <a name="telemetry-collection-by-the-mlnet-cli"></a><span data-ttu-id="b66ec-104">Kolekce telemetrie pomocí rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="b66ec-104">Telemetry collection by the ML.NET CLI</span></span>

<span data-ttu-id="b66ec-105">[Ml.NET CLI](https://aka.ms/mlnet-cli) obsahuje funkci telemetrie, která shromažďuje anonymní data o využití, která jsou agregovaná pro použití Microsoftem.</span><span class="sxs-lookup"><span data-stu-id="b66ec-105">The [ML.NET CLI](https://aka.ms/mlnet-cli) includes a telemetry feature that collects anonymous usage data that is aggregated for use by Microsoft.</span></span>

## <a name="how-microsoft-uses-the-data"></a><span data-ttu-id="b66ec-106">Způsob, jakým společnost Microsoft používá data</span><span class="sxs-lookup"><span data-stu-id="b66ec-106">How Microsoft uses the data</span></span>

<span data-ttu-id="b66ec-107">Produktový tým používá data telemetrie ML.NET CLI, která vám pomůžou pochopit, jak tyto nástroje vylepšit.</span><span class="sxs-lookup"><span data-stu-id="b66ec-107">The product team uses ML.NET CLI telemetry data to help understand how to improve the tools.</span></span> <span data-ttu-id="b66ec-108">Pokud například zákazníci často používají konkrétní úlohu strojového učení, produktový tým prozkoumá důvody, proč a používá zjištění k určení priorit vývoje funkcí.</span><span class="sxs-lookup"><span data-stu-id="b66ec-108">For example, if customers infrequently use a particular machine learning task, the product team investigates why and uses findings to prioritize feature development.</span></span> <span data-ttu-id="b66ec-109">Telemetrie ML.NET CLI také pomáhá s laděním problémů, jako jsou havárie a anomálie v kódu.</span><span class="sxs-lookup"><span data-stu-id="b66ec-109">ML.NET CLI telemetry also helps with debugging of issues such as crashes and code anomalies.</span></span>

<span data-ttu-id="b66ec-110">I když se tento přehled oceňuje produktovým týmem, ví, že ne všichni chtějí posílat tato data.</span><span class="sxs-lookup"><span data-stu-id="b66ec-110">While the product team appreciates this insight, we also know that not everyone wants to send this data.</span></span> [<span data-ttu-id="b66ec-111">Zjistěte, jak zakázat telemetrii.</span><span class="sxs-lookup"><span data-stu-id="b66ec-111">Find out how to disable telemetry.</span></span>](#opt-out-of-data-collection)

## <a name="scope"></a><span data-ttu-id="b66ec-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="b66ec-112">Scope</span></span>

<span data-ttu-id="b66ec-113">Příkaz `mlnet` spustí rozhraní příkazového řádku ML.NET, ale samotný příkaz nebude shromažďovat telemetrii.</span><span class="sxs-lookup"><span data-stu-id="b66ec-113">The `mlnet` command launches the ML.NET CLI, but the command itself doesn't collect telemetry.</span></span>

<span data-ttu-id="b66ec-114">Telemetrie *není povolená* , když spustíte příkaz `mlnet` bez připojeného příkazu.</span><span class="sxs-lookup"><span data-stu-id="b66ec-114">Telemetry *isn't enabled* when you run the `mlnet` command with no other command attached.</span></span> <span data-ttu-id="b66ec-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b66ec-115">For example:</span></span>

- `mlnet`
- `mlnet --help`

<span data-ttu-id="b66ec-116">Telemetrii *je povolena* , když spustíte [příkaz ml.NET CLI](../reference/ml-net-cli-reference.md), například `mlnet auto-train`.</span><span class="sxs-lookup"><span data-stu-id="b66ec-116">Telemetry *is enabled* when you run an [ML.NET CLI command](../reference/ml-net-cli-reference.md), such as `mlnet auto-train`.</span></span>

## <a name="opt-out-of-data-collection"></a><span data-ttu-id="b66ec-117">Odhlásit se od shromažďování dat</span><span class="sxs-lookup"><span data-stu-id="b66ec-117">Opt out of data collection</span></span>

<span data-ttu-id="b66ec-118">Funkce telemetrie ML.NET CLI je ve výchozím nastavení povolená.</span><span class="sxs-lookup"><span data-stu-id="b66ec-118">The ML.NET CLI telemetry feature is enabled by default.</span></span>

<span data-ttu-id="b66ec-119">Odsouhlasit funkci telemetrie nastavením proměnné prostředí `MLDOTNET_CLI_TELEMETRY_OPTOUT` na `1` nebo `true`.</span><span class="sxs-lookup"><span data-stu-id="b66ec-119">Opt out of the telemetry feature by setting the `MLDOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span> <span data-ttu-id="b66ec-120">Tato proměnná prostředí se globálně aplikuje na nástroj ML.NET CLI.</span><span class="sxs-lookup"><span data-stu-id="b66ec-120">This environment variable applies globally to the ML.NET CLI tool.</span></span>

## <a name="data-points-collected"></a><span data-ttu-id="b66ec-121">Shromážděné datové body</span><span class="sxs-lookup"><span data-stu-id="b66ec-121">Data points collected</span></span>

<span data-ttu-id="b66ec-122">Tato funkce shromažďuje následující data:</span><span class="sxs-lookup"><span data-stu-id="b66ec-122">The feature collects the following data:</span></span>

- <span data-ttu-id="b66ec-123">Jaký příkaz byl vyvolán, například `auto-train`</span><span class="sxs-lookup"><span data-stu-id="b66ec-123">What command was invoked, such as `auto-train`</span></span>
- <span data-ttu-id="b66ec-124">Použité názvy parametrů příkazového řádku (to znamená "DataSet-Name; Label-column-name, ml-Task, Output-Path, Max-prozkoumává-Time, verbose")</span><span class="sxs-lookup"><span data-stu-id="b66ec-124">Command-line parameter names used (that is, "dataset-name, label-column-name, ml-task, output-path, max-exploration-time, verbosity")</span></span>
- <span data-ttu-id="b66ec-125">Adresa MAC s algoritmem hash: kryptograficky (SHA256) anonymní a jedinečné ID pro počítač</span><span class="sxs-lookup"><span data-stu-id="b66ec-125">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine</span></span>
- <span data-ttu-id="b66ec-126">Časové razítko vyvolání</span><span class="sxs-lookup"><span data-stu-id="b66ec-126">Timestamp of an invocation</span></span>
- <span data-ttu-id="b66ec-127">Tři oktety: IP adresa (nikoli plná IP adresa) se používá jenom k určení geografického umístění.</span><span class="sxs-lookup"><span data-stu-id="b66ec-127">Three octet IP address (not full IP address) used only to determine geographical location</span></span>
- <span data-ttu-id="b66ec-128">Název všech argumentů/parametrů použitých.</span><span class="sxs-lookup"><span data-stu-id="b66ec-128">Name of all arguments/parameters used.</span></span> <span data-ttu-id="b66ec-129">Nejedná se o hodnoty zákazníka, jako jsou například řetězce.</span><span class="sxs-lookup"><span data-stu-id="b66ec-129">Not the customer's values, such as strings</span></span>
- <span data-ttu-id="b66ec-130">Název souboru datové sady s algoritmem hash</span><span class="sxs-lookup"><span data-stu-id="b66ec-130">Hashed dataset filename</span></span>
- <span data-ttu-id="b66ec-131">Datová sada – interval velikosti souboru</span><span class="sxs-lookup"><span data-stu-id="b66ec-131">Dataset file-size bucket</span></span>
- <span data-ttu-id="b66ec-132">Operační systém a verze</span><span class="sxs-lookup"><span data-stu-id="b66ec-132">Operating system and version</span></span>
- <span data-ttu-id="b66ec-133">Hodnota parametru--Task: kategorií hodnoty, například `regression`, `binary-classification`a `multiclass-classification`</span><span class="sxs-lookup"><span data-stu-id="b66ec-133">Value of --task parameter: Categorical values, such as `regression`, `binary-classification`, and `multiclass-classification`</span></span>
- <span data-ttu-id="b66ec-134">Verze rozhraní příkazového řádku ML.NET (tj. 0.3.27703.4)</span><span class="sxs-lookup"><span data-stu-id="b66ec-134">ML.NET CLI version (that is, 0.3.27703.4)</span></span>

<span data-ttu-id="b66ec-135">Data se na servery Microsoftu odesílají zabezpečeně pomocí technologie [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) , která se drží pod omezeným přístupem, a používají se v rámci přísných bezpečnostních mechanismů pro systémy zabezpečení [Azure Storage](https://azure.microsoft.com/services/storage/) .</span><span class="sxs-lookup"><span data-stu-id="b66ec-135">The data is sent securely to Microsoft servers using [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and used under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

### <a name="data-points-not-collected"></a><span data-ttu-id="b66ec-136">Datové body nejsou shromažďovány.</span><span class="sxs-lookup"><span data-stu-id="b66ec-136">Data points not collected</span></span>

<span data-ttu-id="b66ec-137">*Funkce telemetrie* neshromažďuje:</span><span class="sxs-lookup"><span data-stu-id="b66ec-137">The telemetry feature *doesn't* collect:</span></span>

- <span data-ttu-id="b66ec-138">osobní údaje, jako jsou uživatelská jména</span><span class="sxs-lookup"><span data-stu-id="b66ec-138">personal data, such as usernames</span></span>
- <span data-ttu-id="b66ec-139">názvy souborů DataSet</span><span class="sxs-lookup"><span data-stu-id="b66ec-139">dataset filenames</span></span>
- <span data-ttu-id="b66ec-140">data ze souborů datové sady</span><span class="sxs-lookup"><span data-stu-id="b66ec-140">data from dataset files</span></span>

<span data-ttu-id="b66ec-141">Pokud máte podezření, že telemetrie ML.NET CLI shromažďuje citlivá data, nebo že data jsou nezabezpečená nebo nevhodně zpracovaná, zajistěte si problém v úložišti [ml.NET](https://github.com/dotnet/machinelearning) pro účely šetření.</span><span class="sxs-lookup"><span data-stu-id="b66ec-141">If you suspect that the ML.NET CLI telemetry is collecting sensitive data or that the data is being insecurely or inappropriately handled, file an issue in the [ML.NET](https://github.com/dotnet/machinelearning) repository for investigation.</span></span>

## <a name="license"></a><span data-ttu-id="b66ec-142">průkaz</span><span class="sxs-lookup"><span data-stu-id="b66ec-142">License</span></span>

<span data-ttu-id="b66ec-143">Distribuce rozhraní ML.NET CLI společnosti Microsoft je licencovaná s [licenčními podmínkami pro software společnosti Microsoft: Knihovna Microsoft .NET](https://aka.ms/dotnet-core-eula).</span><span class="sxs-lookup"><span data-stu-id="b66ec-143">The Microsoft distribution of ML.NET CLI is licensed with the [Microsoft Software License Terms: Microsoft .NET Library](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="b66ec-144">Podrobnosti o shromažďování a zpracování dat najdete v části s názvem "data".</span><span class="sxs-lookup"><span data-stu-id="b66ec-144">For details on data collection and processing, see the section entitled "Data."</span></span>

## <a name="disclosure"></a><span data-ttu-id="b66ec-145">Námitk</span><span class="sxs-lookup"><span data-stu-id="b66ec-145">Disclosure</span></span>

<span data-ttu-id="b66ec-146">Při prvním spuštění [příkazu cli ml.NET](../reference/ml-net-cli-reference.md) , jako je například `mlnet auto-train`, se v nástroji ml.NET CLI zobrazí text, který vám ukáže, jak se odhlásit z telemetrie.</span><span class="sxs-lookup"><span data-stu-id="b66ec-146">When you first run a [ML.NET CLI command](../reference/ml-net-cli-reference.md) such as `mlnet auto-train`, the ML.NET CLI tool displays disclosure text that tells you how to opt out of telemetry.</span></span> <span data-ttu-id="b66ec-147">Text se může mírně lišit v závislosti na verzi rozhraní příkazového řádku, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="b66ec-147">Text may vary slightly depending on the version of the CLI you're running.</span></span>

## <a name="see-also"></a><span data-ttu-id="b66ec-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b66ec-148">See also</span></span>

- [<span data-ttu-id="b66ec-149">Reference k rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="b66ec-149">ML.NET CLI reference</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="b66ec-150">Licenční smlouvy pro software společnosti Microsoft: Knihovna Microsoft .NET</span><span class="sxs-lookup"><span data-stu-id="b66ec-150">Microsoft Software License Terms: Microsoft .NET Library</span></span>](https://aka.ms/dotnet-core-eula)
- [<span data-ttu-id="b66ec-151">Ochrana osobních údajů v Microsoftu</span><span class="sxs-lookup"><span data-stu-id="b66ec-151">Privacy at Microsoft</span></span>](https://www.microsoft.com/trustcenter/privacy/)
- [<span data-ttu-id="b66ec-152">Prohlášení o zásadách ochrany osobních údajů společnosti Microsoft</span><span class="sxs-lookup"><span data-stu-id="b66ec-152">Microsoft Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
