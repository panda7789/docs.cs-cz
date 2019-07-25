---
title: Kolekce telemetrie pomocí ML.NET CLI
description: Přečtěte si o funkcích telemetrie ML.NET CLI, které shromažďují informace o využití pro analýzu, shromažďovaná data a jejich zakázání. Vyhledejte také odkazy na licenční smlouvu .NET a informace o dodržování předpisů v Microsoft GDPRe.
ms.topic: conceptual
ms.date: 05/05/2019
ms.custom: ''
ms.openlocfilehash: eab1e37d7d0d47251c4f92422730b105cf2db265
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433797"
---
# <a name="telemetry-collection-by-the-mlnet-cli"></a><span data-ttu-id="35e80-104">Kolekce telemetrie pomocí rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="35e80-104">Telemetry collection by the ML.NET CLI</span></span>

<span data-ttu-id="35e80-105">[Ml.NET CLI](https://aka.ms/mlnet-cli) obsahuje funkci telemetrie, která shromažďuje anonymní data o využití, která jsou agregovaná pro použití Microsoftem.</span><span class="sxs-lookup"><span data-stu-id="35e80-105">The [ML.NET CLI](https://aka.ms/mlnet-cli) includes a telemetry feature that collects anonymous usage data that is aggregated for use by Microsoft.</span></span>

## <a name="how-microsoft-uses-the-data"></a><span data-ttu-id="35e80-106">Způsob, jakým společnost Microsoft používá data</span><span class="sxs-lookup"><span data-stu-id="35e80-106">How Microsoft uses the data</span></span>

<span data-ttu-id="35e80-107">Produktový tým používá data telemetrie ML.NET CLI, která vám pomůžou pochopit, jak tyto nástroje vylepšit.</span><span class="sxs-lookup"><span data-stu-id="35e80-107">The product team uses ML.NET CLI telemetry data to help understand how to improve the tools.</span></span> <span data-ttu-id="35e80-108">Pokud například zákazníci často používají konkrétní úlohu strojového učení, produktový tým prozkoumá důvody, proč a používá zjištění k určení priorit vývoje funkcí.</span><span class="sxs-lookup"><span data-stu-id="35e80-108">For example, if customers infrequently use a particular machine learning task, the product team investigates why and uses findings to prioritize feature development.</span></span> <span data-ttu-id="35e80-109">Telemetrie ML.NET CLI také pomáhá s laděním problémů, jako jsou havárie a anomálie v kódu.</span><span class="sxs-lookup"><span data-stu-id="35e80-109">ML.NET CLI telemetry also helps with debugging of issues such as crashes and code anomalies.</span></span> 

<span data-ttu-id="35e80-110">I když se tento přehled oceňuje produktovým týmem, ví, že ne všichni chtějí posílat tato data.</span><span class="sxs-lookup"><span data-stu-id="35e80-110">While the product team appreciates this insight, we also know that not everyone wants to send this data.</span></span> [<span data-ttu-id="35e80-111">Zjistěte, jak zakázat telemetrii.</span><span class="sxs-lookup"><span data-stu-id="35e80-111">Find out how to disable telemetry.</span></span>](#opt-out-of-data-collection)

## <a name="scope"></a><span data-ttu-id="35e80-112">Scope</span><span class="sxs-lookup"><span data-stu-id="35e80-112">Scope</span></span>

<span data-ttu-id="35e80-113">`mlnet` Příkaz spustí rozhraní příkazového řádku ml.NET, ale samotný příkaz nebude shromažďovat telemetrii.</span><span class="sxs-lookup"><span data-stu-id="35e80-113">The `mlnet` command launches the ML.NET CLI, but the command itself doesn't collect telemetry.</span></span>

<span data-ttu-id="35e80-114">Telemetrie *není povolená* , když `mlnet` příkaz spustíte bez dalšího příkazu.</span><span class="sxs-lookup"><span data-stu-id="35e80-114">Telemetry *isn't enabled* when you run the `mlnet` command with no other command attached.</span></span> <span data-ttu-id="35e80-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="35e80-115">For example:</span></span>

- `mlnet`
- `mlnet --help`

<span data-ttu-id="35e80-116">Telemetrii *je povolena* při spuštění [příkazu CLI ml.NET](../reference/ml-net-cli-reference.md) `mlnet auto-train`, například.</span><span class="sxs-lookup"><span data-stu-id="35e80-116">Telemetry *is enabled* when you run an [ML.NET CLI command](../reference/ml-net-cli-reference.md), such as `mlnet auto-train`.</span></span>

## <a name="opt-out-of-data-collection"></a><span data-ttu-id="35e80-117">Odhlásit se od shromažďování dat</span><span class="sxs-lookup"><span data-stu-id="35e80-117">Opt out of data collection</span></span>

<span data-ttu-id="35e80-118">Funkce telemetrie ML.NET CLI je ve výchozím nastavení povolená.</span><span class="sxs-lookup"><span data-stu-id="35e80-118">The ML.NET CLI telemetry feature is enabled by default.</span></span>

<span data-ttu-id="35e80-119">Odsouhlasit funkci `DOTNET_CLI_TELEMETRY_OPTOUT` telemetrie nastavením proměnné prostředí na `1` nebo `true`.</span><span class="sxs-lookup"><span data-stu-id="35e80-119">Opt out of the telemetry feature by setting the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span> <span data-ttu-id="35e80-120">Tato proměnná prostředí se globálně vztahuje k nástroji rozhraní .NET CLI.</span><span class="sxs-lookup"><span data-stu-id="35e80-120">This environment variable applies globally to the .NET CLI tool.</span></span>

## <a name="data-points-collected"></a><span data-ttu-id="35e80-121">Shromážděné datové body</span><span class="sxs-lookup"><span data-stu-id="35e80-121">Data points collected</span></span>

<span data-ttu-id="35e80-122">Tato funkce shromažďuje následující data:</span><span class="sxs-lookup"><span data-stu-id="35e80-122">The feature collects the following data:</span></span>

- <span data-ttu-id="35e80-123">Jaký příkaz byl vyvolán, například`auto-train`</span><span class="sxs-lookup"><span data-stu-id="35e80-123">What command was invoked, such as `auto-train`</span></span>
- <span data-ttu-id="35e80-124">Použité názvy parametrů příkazového řádku (tj. název sady dat, popisek-sloupec-název, ml-úloha, výstup-cesta, maximální doba průzkumu-čas, podrobnosti)</span><span class="sxs-lookup"><span data-stu-id="35e80-124">Command-line parameter names used (i.e. "dataset-name, label-column-name, ml-task, output-path, max-exploration-time, verbosity")</span></span>
- <span data-ttu-id="35e80-125">Adresa MAC s algoritmem hash: kryptograficky (SHA256) anonymní a jedinečné ID pro počítač</span><span class="sxs-lookup"><span data-stu-id="35e80-125">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine</span></span>
- <span data-ttu-id="35e80-126">Časové razítko vyvolání</span><span class="sxs-lookup"><span data-stu-id="35e80-126">Timestamp of an invocation</span></span>
- <span data-ttu-id="35e80-127">Tři oktety: IP adresa (nikoli plná IP adresa) se používá jenom k určení geografického umístění.</span><span class="sxs-lookup"><span data-stu-id="35e80-127">Three octet IP address (not full IP address) used only to determine geographical location</span></span>
- <span data-ttu-id="35e80-128">Název všech argumentů/parametrů použitých.</span><span class="sxs-lookup"><span data-stu-id="35e80-128">Name of all arguments/parameters used.</span></span> <span data-ttu-id="35e80-129">Nejedná se o hodnoty zákazníka, jako jsou například řetězce.</span><span class="sxs-lookup"><span data-stu-id="35e80-129">Not the customer's values, such as strings</span></span>
- <span data-ttu-id="35e80-130">Název souboru datové sady s algoritmem hash</span><span class="sxs-lookup"><span data-stu-id="35e80-130">Hashed dataset filename</span></span>
- <span data-ttu-id="35e80-131">Datová sada – interval velikosti souboru</span><span class="sxs-lookup"><span data-stu-id="35e80-131">Dataset file-size bucket</span></span>
- <span data-ttu-id="35e80-132">Operační systém a verze</span><span class="sxs-lookup"><span data-stu-id="35e80-132">Operating system and version</span></span>
- <span data-ttu-id="35e80-133">Hodnota parametru--Task: Kategorií hodnoty, `regression`jako například, `binary-classification`a`multiclass-classification`</span><span class="sxs-lookup"><span data-stu-id="35e80-133">Value of --task parameter: Categorical values, such as `regression`, `binary-classification`, and `multiclass-classification`</span></span>
- <span data-ttu-id="35e80-134">Verze rozhraní příkazového řádku ML.NET (tj. 0.3.27703.4)</span><span class="sxs-lookup"><span data-stu-id="35e80-134">ML.NET CLI version (i.e. 0.3.27703.4)</span></span>

<span data-ttu-id="35e80-135">Data se na servery Microsoftu odesílají zabezpečeně pomocí technologie [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) , která se drží pod omezeným přístupem, a používají se v rámci přísných bezpečnostních mechanismů pro systémy zabezpečení [Azure Storage](https://azure.microsoft.com/services/storage/) .</span><span class="sxs-lookup"><span data-stu-id="35e80-135">The data is sent securely to Microsoft servers using [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and used under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

### <a name="data-points-not-collected"></a><span data-ttu-id="35e80-136">Datové body nejsou shromažďovány.</span><span class="sxs-lookup"><span data-stu-id="35e80-136">Data points not collected</span></span>
<span data-ttu-id="35e80-137">*Funkce telemetrie* neshromažďuje:</span><span class="sxs-lookup"><span data-stu-id="35e80-137">The telemetry feature *doesn't* collect:</span></span>
- <span data-ttu-id="35e80-138">osobní údaje, jako jsou uživatelská jména</span><span class="sxs-lookup"><span data-stu-id="35e80-138">personal data, such as usernames</span></span>
- <span data-ttu-id="35e80-139">názvy souborů DataSet</span><span class="sxs-lookup"><span data-stu-id="35e80-139">dataset filenames</span></span>
- <span data-ttu-id="35e80-140">data ze souborů datové sady</span><span class="sxs-lookup"><span data-stu-id="35e80-140">data from dataset files</span></span>

<span data-ttu-id="35e80-141">Pokud máte podezření, že telemetrie ML.NET CLI shromažďuje citlivá data, nebo že data jsou nezabezpečená nebo nevhodně zpracovaná, zajistěte si problém v úložišti [ml.NET](https://github.com/dotnet/machinelearning) pro účely šetření.</span><span class="sxs-lookup"><span data-stu-id="35e80-141">If you suspect that the ML.NET CLI telemetry is collecting sensitive data or that the data is being insecurely or inappropriately handled, file an issue in the [ML.NET](https://github.com/dotnet/machinelearning) repository for investigation.</span></span>

## <a name="license"></a><span data-ttu-id="35e80-142">Licence</span><span class="sxs-lookup"><span data-stu-id="35e80-142">License</span></span>

<span data-ttu-id="35e80-143">Distribuce rozhraní ml.NET CLI společnosti Microsoft je licencovaná s [licenčními podmínkami pro software společnosti Microsoft: Knihovna](https://aka.ms/dotnet-core-eula)Microsoft .NET.</span><span class="sxs-lookup"><span data-stu-id="35e80-143">The Microsoft distribution of ML.NET CLI is licensed with the [Microsoft Software License Terms: Microsoft .NET Library](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="35e80-144">Podrobnosti o shromažďování a zpracování dat najdete v části s názvem "data".</span><span class="sxs-lookup"><span data-stu-id="35e80-144">For details on data collection and processing, see the section entitled "Data."</span></span>

## <a name="disclosure"></a><span data-ttu-id="35e80-145">Námitk</span><span class="sxs-lookup"><span data-stu-id="35e80-145">Disclosure</span></span>

<span data-ttu-id="35e80-146">Při prvním spuštění `mlnet auto-train` [příkazu CLI ml.NET](../reference/ml-net-cli-reference.md) , jako je nástroj rozhraní příkazového řádku ml.NET, se zobrazí text s oznámením o odhlášení z telemetrie.</span><span class="sxs-lookup"><span data-stu-id="35e80-146">When you first run a [ML.NET CLI command](../reference/ml-net-cli-reference.md) such as `mlnet auto-train`, the ML.NET CLI tool displays disclosure text that tells you how to opt out of telemetry.</span></span> <span data-ttu-id="35e80-147">Text se může mírně lišit v závislosti na verzi rozhraní příkazového řádku, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="35e80-147">Text may vary slightly depending on the version of the CLI you're running.</span></span>

## <a name="see-also"></a><span data-ttu-id="35e80-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="35e80-148">See also</span></span>
- [<span data-ttu-id="35e80-149">Reference k rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="35e80-149">ML.NET CLI reference</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="35e80-150">Licenční smlouvy pro software společnosti Microsoft: Knihovna Microsoft .NET</span><span class="sxs-lookup"><span data-stu-id="35e80-150">Microsoft Software License Terms: Microsoft .NET Library</span></span>](https://aka.ms/dotnet-core-eula)
- [<span data-ttu-id="35e80-151">Ochrana osobních údajů v Microsoftu</span><span class="sxs-lookup"><span data-stu-id="35e80-151">Privacy at Microsoft</span></span>](https://www.microsoft.com/trustcenter/privacy/)
- [<span data-ttu-id="35e80-152">Prohlášení o zásadách ochrany osobních údajů společnosti Microsoft</span><span class="sxs-lookup"><span data-stu-id="35e80-152">Microsoft Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
