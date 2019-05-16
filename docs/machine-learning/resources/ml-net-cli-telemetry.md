---
title: Shromažďování telemetrie pomocí rozhraní příkazového řádku ML.NET
description: Další informace o rozhraní příkazového řádku ML.NET telemetrické funkce, která shromažďují využití informace pro analýzu, která data se shromažďují a jak ji zakázat. Dozvíte se taky, odkazy na licenční smlouvy .NET a informace o dodržování předpisů Microsoft GDPR.
ms.topic: conceptual
ms.date: 05/05/2019
ms.custom: ''
ms.openlocfilehash: 36f4af48615e2e3247f8e21343d0a00519ba1c0a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645025"
---
# <a name="telemetry-collection-by-the-mlnet-cli"></a><span data-ttu-id="05f9f-104">Shromažďování telemetrie pomocí rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="05f9f-104">Telemetry collection by the ML.NET CLI</span></span>

<span data-ttu-id="05f9f-105">[ML.NET CLI](http://aka.ms/mlnet-cli) obsahuje funkci telemetrická data, která shromažďuje anonymní data o využití, která se zobrazují se pro použití společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="05f9f-105">The [ML.NET CLI](http://aka.ms/mlnet-cli) includes a telemetry feature that collects anonymous usage data that is aggregated for use by Microsoft.</span></span>

## <a name="how-microsoft-uses-the-data"></a><span data-ttu-id="05f9f-106">Jak Microsoft používá data</span><span class="sxs-lookup"><span data-stu-id="05f9f-106">How Microsoft uses the data</span></span>

<span data-ttu-id="05f9f-107">Produktový tým pochopit, jak vylepšit nástroje pomocí rozhraní příkazového řádku ML.NET telemetrická data.</span><span class="sxs-lookup"><span data-stu-id="05f9f-107">The product team uses ML.NET CLI telemetry data to help understand how to improve the tools.</span></span> <span data-ttu-id="05f9f-108">Například pokud zřídka používají zákazníci konkrétní služby machine learning úkolu, produktový tým prověří důvod, proč a zjištění používá k určení priority vývoj funkcí.</span><span class="sxs-lookup"><span data-stu-id="05f9f-108">For example, if customers infrequently use a particular machine learning task, the product team investigates why and uses findings to prioritize feature development.</span></span> <span data-ttu-id="05f9f-109">Rozhraní příkazového řádku ML.NET telemetrie vám také pomůže s laděním problémů, jako je například selhání a kód anomálie.</span><span class="sxs-lookup"><span data-stu-id="05f9f-109">ML.NET CLI telemetry also helps with debugging of issues such as crashes and code anomalies.</span></span> 

<span data-ttu-id="05f9f-110">Zatímco produktový tým oceňuje tyto informace, Víme také, že ne každý chce, aby se tato data Neodesílat.</span><span class="sxs-lookup"><span data-stu-id="05f9f-110">While the product team appreciates this insight, we also know that not everyone wants to send this data.</span></span> [<span data-ttu-id="05f9f-111">Zjistěte, jak zakázat telemetrii.</span><span class="sxs-lookup"><span data-stu-id="05f9f-111">Find out how to disable telemetry.</span></span>](#opt-out-of-data-collection)

## <a name="scope"></a><span data-ttu-id="05f9f-112">Scope</span><span class="sxs-lookup"><span data-stu-id="05f9f-112">Scope</span></span>

<span data-ttu-id="05f9f-113">`mlnet` Spustí příkaz rozhraní příkazového řádku ML.NET, ale samotný příkaz telemetrii neshromažďuje.</span><span class="sxs-lookup"><span data-stu-id="05f9f-113">The `mlnet` command launches the ML.NET CLI, but the command itself doesn't collect telemetry.</span></span>

<span data-ttu-id="05f9f-114">Telemetrie *není povoleno* při spuštění `mlnet` příkaz příkazem žádné další připojené.</span><span class="sxs-lookup"><span data-stu-id="05f9f-114">Telemetry *isn't enabled* when you run the `mlnet` command with no other command attached.</span></span> <span data-ttu-id="05f9f-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="05f9f-115">For example:</span></span>

- `mlnet`
- `mlnet --help`

<span data-ttu-id="05f9f-116">Telemetrie *je povoleno* při spuštění [příkazu rozhraní příkazového řádku ML.NET](../reference/ml-net-cli-reference.md), například `mlnet auto-train`.</span><span class="sxs-lookup"><span data-stu-id="05f9f-116">Telemetry *is enabled* when you run an [ML.NET CLI command](../reference/ml-net-cli-reference.md), such as `mlnet auto-train`.</span></span>

## <a name="opt-out-of-data-collection"></a><span data-ttu-id="05f9f-117">Odhlásit ze shromažďování dat</span><span class="sxs-lookup"><span data-stu-id="05f9f-117">Opt out of data collection</span></span>

<span data-ttu-id="05f9f-118">Ve výchozím nastavení je povolena funkce telemetrie ML.NET rozhraní příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="05f9f-118">The ML.NET CLI telemetry feature is enabled by default.</span></span>

<span data-ttu-id="05f9f-119">Vyjádřit výslovný nesouhlas funkce telemetrie nastavením `DOTNET_CLI_TELEMETRY_OPTOUT` proměnnou prostředí, aby `1` nebo `true`.</span><span class="sxs-lookup"><span data-stu-id="05f9f-119">Opt out of the telemetry feature by setting the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span> <span data-ttu-id="05f9f-120">Tato proměnná prostředí se týká globálně nástroj rozhraní příkazového řádku .NET.</span><span class="sxs-lookup"><span data-stu-id="05f9f-120">This environment variable applies globally to the .NET CLI tool.</span></span>

## <a name="data-points-collected"></a><span data-ttu-id="05f9f-121">Shromážděné datových bodů</span><span class="sxs-lookup"><span data-stu-id="05f9f-121">Data points collected</span></span>

<span data-ttu-id="05f9f-122">Funkci shromažďuje následující data:</span><span class="sxs-lookup"><span data-stu-id="05f9f-122">The feature collects the following data:</span></span>

- <span data-ttu-id="05f9f-123">Byla vyvolána jaké příkazu, jako například `auto-train`</span><span class="sxs-lookup"><span data-stu-id="05f9f-123">What command was invoked, such as `auto-train`</span></span>
- <span data-ttu-id="05f9f-124">Názvy parametrů příkazového řádku používá (to znamená "název datové sady, popisek název sloupce, ml úkolu, výstupní cesta, max běhu zkoumání podrobností")</span><span class="sxs-lookup"><span data-stu-id="05f9f-124">Command-line parameter names used (i.e. "dataset-name, label-column-name, ml-task, output-path, max-exploration-time, verbosity")</span></span>
- <span data-ttu-id="05f9f-125">Hodnoty hash adresy MAC: kryptograficky (SHA256) anonymní a jedinečné ID počítače</span><span class="sxs-lookup"><span data-stu-id="05f9f-125">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine</span></span>
- <span data-ttu-id="05f9f-126">Časové razítko vyvolání</span><span class="sxs-lookup"><span data-stu-id="05f9f-126">Timestamp of an invocation</span></span>
- <span data-ttu-id="05f9f-127">Tři octet IP adresa (IP adresa není úplně) používá jenom k určení zeměpisného umístění</span><span class="sxs-lookup"><span data-stu-id="05f9f-127">Three octet IP address (not full IP address) used only to determine geographical location</span></span>
- <span data-ttu-id="05f9f-128">Název všech argumentů a parametrů použitých.</span><span class="sxs-lookup"><span data-stu-id="05f9f-128">Name of all arguments/parameters used.</span></span> <span data-ttu-id="05f9f-129">Není zákazníka hodnoty, jako jsou třeba řetězce</span><span class="sxs-lookup"><span data-stu-id="05f9f-129">Not the customer's values, such as strings</span></span>
- <span data-ttu-id="05f9f-130">Název souboru hashované datové sady</span><span class="sxs-lookup"><span data-stu-id="05f9f-130">Hashed dataset filename</span></span>
- <span data-ttu-id="05f9f-131">Interval velikosti souboru datové sady</span><span class="sxs-lookup"><span data-stu-id="05f9f-131">Dataset file-size bucket</span></span>
- <span data-ttu-id="05f9f-132">Operační systém a verze</span><span class="sxs-lookup"><span data-stu-id="05f9f-132">Operating system and version</span></span>
- <span data-ttu-id="05f9f-133">Hodnota parametru--úloh: Hodnoty zařazené do kategorií, jako například `regression`, `binary-classification`, a `multiclass-classification`</span><span class="sxs-lookup"><span data-stu-id="05f9f-133">Value of --task parameter: Categorical values, such as `regression`, `binary-classification`, and `multiclass-classification`</span></span>
- <span data-ttu-id="05f9f-134">Verze rozhraní příkazového řádku ML.NET (tj. 0.3.27703.4)</span><span class="sxs-lookup"><span data-stu-id="05f9f-134">ML.NET CLI version (i.e. 0.3.27703.4)</span></span>

<span data-ttu-id="05f9f-135">Data se odesílají bezpečně na servery Microsoftu pomocí [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technologie nachází v části s omezeným přístupem a použít v striktní bezpečnostní opatření ze zabezpečeného [služby Azure Storage](https://azure.microsoft.com/services/storage/) systémy.</span><span class="sxs-lookup"><span data-stu-id="05f9f-135">The data is sent securely to Microsoft servers using [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and used under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

### <a name="data-points-not-collected"></a><span data-ttu-id="05f9f-136">Datové body nejsou shromážděna</span><span class="sxs-lookup"><span data-stu-id="05f9f-136">Data points not collected</span></span>
<span data-ttu-id="05f9f-137">Funkce telemetrie *nebude* shromažďovat:</span><span class="sxs-lookup"><span data-stu-id="05f9f-137">The telemetry feature *doesn't* collect:</span></span>
- <span data-ttu-id="05f9f-138">osobní údaje, jako jsou uživatelská jména</span><span class="sxs-lookup"><span data-stu-id="05f9f-138">personal data, such as usernames</span></span>
- <span data-ttu-id="05f9f-139">názvy souborů datové sady</span><span class="sxs-lookup"><span data-stu-id="05f9f-139">dataset filenames</span></span>
- <span data-ttu-id="05f9f-140">data z datové sady souborů</span><span class="sxs-lookup"><span data-stu-id="05f9f-140">data from dataset files</span></span>

<span data-ttu-id="05f9f-141">Pokud máte podezření, že se citlivá data nebo, který sbírá telemetrie ML.NET rozhraní příkazového řádku dat probíhá nezabezpečeným způsobem nebo neoprávněně zpracována, založte problém v [ML.NET](https://github.com/dotnet/machinelearning) úložiště pro šetření.</span><span class="sxs-lookup"><span data-stu-id="05f9f-141">If you suspect that the ML.NET CLI telemetry is collecting sensitive data or that the data is being insecurely or inappropriately handled, file an issue in the [ML.NET](https://github.com/dotnet/machinelearning) repository for investigation.</span></span>

## <a name="license"></a><span data-ttu-id="05f9f-142">Licence</span><span class="sxs-lookup"><span data-stu-id="05f9f-142">License</span></span>

<span data-ttu-id="05f9f-143">Je distribuce Microsoftu příkazového řádku ML.NET licenci [licenční podmínky pro Software společnosti Microsoft: Knihovna rozhraní Microsoft .NET](https://aka.ms/dotnet-core-eula).</span><span class="sxs-lookup"><span data-stu-id="05f9f-143">The Microsoft distribution of ML.NET CLI is licensed with the [Microsoft Software License Terms: Microsoft .NET Library](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="05f9f-144">Podrobnosti o shromažďování dat a zpracování najdete v části s názvem "Data".</span><span class="sxs-lookup"><span data-stu-id="05f9f-144">For details on data collection and processing, see the section entitled "Data."</span></span>

## <a name="disclosure"></a><span data-ttu-id="05f9f-145">Zpřístupnění</span><span class="sxs-lookup"><span data-stu-id="05f9f-145">Disclosure</span></span>

<span data-ttu-id="05f9f-146">Při prvním spuštění [příkazu rozhraní příkazového řádku ML.NET](../reference/ml-net-cli-reference.md) jako `mlnet auto-train`, nástroje rozhraní příkazového řádku ML.NET zobrazí zpřístupnění text, který vysvětluje, jak vyjádřit výslovný nesouhlas telemetrická data.</span><span class="sxs-lookup"><span data-stu-id="05f9f-146">When you first run a [ML.NET CLI command](../reference/ml-net-cli-reference.md) such as `mlnet auto-train`, the ML.NET CLI tool displays disclosure text that tells you how to opt out of telemetry.</span></span> <span data-ttu-id="05f9f-147">Text může mírně lišit v závislosti na verzi rozhraní příkazového řádku, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="05f9f-147">Text may vary slightly depending on the version of the CLI you're running.</span></span>

## <a name="see-also"></a><span data-ttu-id="05f9f-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05f9f-148">See also</span></span>
- [<span data-ttu-id="05f9f-149">Referenční informace k ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="05f9f-149">ML.NET CLI reference</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="05f9f-150">Licenční podmínky pro Software společnosti Microsoft: Knihovna rozhraní Microsoft .NET</span><span class="sxs-lookup"><span data-stu-id="05f9f-150">Microsoft Software License Terms: Microsoft .NET Library</span></span>](https://aka.ms/dotnet-core-eula)
- [<span data-ttu-id="05f9f-151">Ochrana osobních údajů společnosti Microsoft</span><span class="sxs-lookup"><span data-stu-id="05f9f-151">Privacy at Microsoft</span></span>](https://www.microsoft.com/en-us/trustcenter/privacy/)
- [<span data-ttu-id="05f9f-152">Prohlášení o ochraně osobních údajů společnosti Microsoft</span><span class="sxs-lookup"><span data-stu-id="05f9f-152">Microsoft Privacy Statement</span></span>](https://privacy.microsoft.com/en-us/privacystatement)
