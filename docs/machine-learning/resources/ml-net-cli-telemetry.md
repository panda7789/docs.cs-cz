---
title: Shromažďování telemetrie pomocí rozhraní příkazového řádku ML.NET
description: Další informace o rozhraní příkazového řádku ML.NET telemetrické funkce, která shromažďují využití informace pro analýzu, která data se shromažďují a jak ji zakázat. Dozvíte se taky, odkazy na licenční smlouvy .NET a informace o dodržování předpisů Microsoft GDPR.
ms.topic: conceptual
ms.date: 05/05/2019
ms.custom: ''
ms.openlocfilehash: 49ebd6c9e1b77c85d891b8c9fb8cbd5c66b478a9
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65066157"
---
# <a name="telemetry-collection-by-the-mlnet-cli"></a><span data-ttu-id="e04fb-104">Shromažďování telemetrie pomocí rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="e04fb-104">Telemetry collection by the ML.NET CLI</span></span>

<span data-ttu-id="e04fb-105">[ML.NET CLI](http://aka.ms/mlnet-cli) obsahuje funkci telemetrická data, která shromažďuje anonymní data o využití, která se zobrazují se pro použití společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e04fb-105">The [ML.NET CLI](http://aka.ms/mlnet-cli) includes a telemetry feature that collects anonymous usage data that is aggregated for use by Microsoft.</span></span>

## <a name="how-microsoft-uses-the-data"></a><span data-ttu-id="e04fb-106">Jak Microsoft používá data</span><span class="sxs-lookup"><span data-stu-id="e04fb-106">How Microsoft uses the data</span></span>

<span data-ttu-id="e04fb-107">Produktový tým pochopit, jak vylepšit nástroje pomocí rozhraní příkazového řádku ML.NET telemetrická data.</span><span class="sxs-lookup"><span data-stu-id="e04fb-107">The product team uses ML.NET CLI telemetry data to help understand how to improve the tools.</span></span> <span data-ttu-id="e04fb-108">Například pokud zřídka používají zákazníci konkrétní služby machine learning úkolu, produktový tým prověří důvod, proč a zjištění používá k určení priority vývoj funkcí.</span><span class="sxs-lookup"><span data-stu-id="e04fb-108">For example, if customers infrequently use a particular machine learning task, the product team investigates why and uses findings to prioritize feature development.</span></span> <span data-ttu-id="e04fb-109">Rozhraní příkazového řádku ML.NET telemetrie vám také pomůže s laděním problémů, jako je například selhání a kód anomálie.</span><span class="sxs-lookup"><span data-stu-id="e04fb-109">ML.NET CLI telemetry also helps with debugging of issues such as crashes and code anomalies.</span></span> 

<span data-ttu-id="e04fb-110">Zatímco produktový tým oceňuje tyto informace, Víme také, že ne každý chce, aby se tato data Neodesílat.</span><span class="sxs-lookup"><span data-stu-id="e04fb-110">While the product team appreciates this insight, we also know that not everyone wants to send this data.</span></span> [<span data-ttu-id="e04fb-111">Zjistěte, jak zakázat telemetrii.</span><span class="sxs-lookup"><span data-stu-id="e04fb-111">Find out how to disable telemetry.</span></span>](#opt-out-of-data-collection)

## <a name="scope"></a><span data-ttu-id="e04fb-112">Scope</span><span class="sxs-lookup"><span data-stu-id="e04fb-112">Scope</span></span>

<span data-ttu-id="e04fb-113">`mlnet` Spustí příkaz rozhraní příkazového řádku ML.NET, ale samotný příkaz telemetrii neshromažďuje.</span><span class="sxs-lookup"><span data-stu-id="e04fb-113">The `mlnet` command launches the ML.NET CLI, but the command itself doesn't collect telemetry.</span></span>

<span data-ttu-id="e04fb-114">Telemetrie *není povoleno* při spuštění `mlnet` příkaz příkazem žádné další připojené.</span><span class="sxs-lookup"><span data-stu-id="e04fb-114">Telemetry *isn't enabled* when you run the `mlnet` command with no other command attached.</span></span> <span data-ttu-id="e04fb-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e04fb-115">For example:</span></span>

- `mlnet`
- `mlnet --help`

<span data-ttu-id="e04fb-116">Telemetrie *je povoleno* při spuštění [příkazu rozhraní příkazového řádku ML.NET](../reference/ml-net-cli-reference.md), například `mlnet auto-train`.</span><span class="sxs-lookup"><span data-stu-id="e04fb-116">Telemetry *is enabled* when you run an [ML.NET CLI command](../reference/ml-net-cli-reference.md), such as `mlnet auto-train`.</span></span>

## <a name="opt-out-of-data-collection"></a><span data-ttu-id="e04fb-117">Odhlásit ze shromažďování dat</span><span class="sxs-lookup"><span data-stu-id="e04fb-117">Opt out of data collection</span></span>

<span data-ttu-id="e04fb-118">Ve výchozím nastavení je povolena funkce telemetrie ML.NET rozhraní příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="e04fb-118">The ML.NET CLI telemetry feature is enabled by default.</span></span>

<span data-ttu-id="e04fb-119">Vyjádřit výslovný nesouhlas funkce telemetrie nastavením `DOTNET_CLI_TELEMETRY_OPTOUT` proměnnou prostředí, aby `1` nebo `true`.</span><span class="sxs-lookup"><span data-stu-id="e04fb-119">Opt out of the telemetry feature by setting the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span> <span data-ttu-id="e04fb-120">Tato proměnná prostředí se týká globálně nástroj rozhraní příkazového řádku .NET.</span><span class="sxs-lookup"><span data-stu-id="e04fb-120">This environment variable applies globally to the .NET CLI tool.</span></span>

## <a name="data-points-collected"></a><span data-ttu-id="e04fb-121">Shromážděné datových bodů</span><span class="sxs-lookup"><span data-stu-id="e04fb-121">Data points collected</span></span>

<span data-ttu-id="e04fb-122">Funkci shromažďuje následující data:</span><span class="sxs-lookup"><span data-stu-id="e04fb-122">The feature collects the following data:</span></span>

- <span data-ttu-id="e04fb-123">Jsou vyvolány které příkazy, jako například `auto-train`</span><span class="sxs-lookup"><span data-stu-id="e04fb-123">Which commands are invoked, such as `auto-train`</span></span>
- <span data-ttu-id="e04fb-124">Hodnoty hash adresy MAC: kryptograficky (SHA256) anonymní a jedinečné ID počítače</span><span class="sxs-lookup"><span data-stu-id="e04fb-124">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine</span></span>
- <span data-ttu-id="e04fb-125">Časové razítko vyvolání</span><span class="sxs-lookup"><span data-stu-id="e04fb-125">Timestamp of an invocation</span></span>
- <span data-ttu-id="e04fb-126">Tři octet IP adresu použít pouze k určení zeměpisného umístění</span><span class="sxs-lookup"><span data-stu-id="e04fb-126">Three octet IP address used only to determine geographical location</span></span>
- <span data-ttu-id="e04fb-127">Název všech argumentů a parametrů použitých.</span><span class="sxs-lookup"><span data-stu-id="e04fb-127">Name of all arguments/parameters used.</span></span> <span data-ttu-id="e04fb-128">Není zákazníka hodnoty, jako jsou třeba řetězce</span><span class="sxs-lookup"><span data-stu-id="e04fb-128">Not the customer's values, such as strings</span></span>
- <span data-ttu-id="e04fb-129">Operační systém a verze</span><span class="sxs-lookup"><span data-stu-id="e04fb-129">Operating system and version</span></span>
- <span data-ttu-id="e04fb-130">Hodnota parametru--ml úloh: Hodnoty zařazené do kategorií, jako například `regression`, `binary-classification`, a `multiclass-classification`</span><span class="sxs-lookup"><span data-stu-id="e04fb-130">Value of --ml-task parameter: Categorical values, such as `regression`, `binary-classification`, and `multiclass-classification`</span></span>
- <span data-ttu-id="e04fb-131">[Logaritmické zaokrouhlí](https://en.wikipedia.org/wiki/Rounding#Rounding_to_a_specified_power) velikost souboru datové sady (nejbližší Mocnina 2)</span><span class="sxs-lookup"><span data-stu-id="e04fb-131">[Logarithmic rounded](https://en.wikipedia.org/wiki/Rounding#Rounding_to_a_specified_power) dataset file size (nearest power of 2)</span></span>
- <span data-ttu-id="e04fb-132">`ExitCode` příkaz</span><span class="sxs-lookup"><span data-stu-id="e04fb-132">`ExitCode` of the command</span></span>

<span data-ttu-id="e04fb-133">Data se odesílají bezpečně na servery Microsoftu pomocí [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technologie nachází v části s omezeným přístupem a použít v striktní bezpečnostní opatření ze zabezpečeného [služby Azure Storage](https://azure.microsoft.com/services/storage/) systémy.</span><span class="sxs-lookup"><span data-stu-id="e04fb-133">The data is sent securely to Microsoft servers using [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and used under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

### <a name="data-points-not-collected"></a><span data-ttu-id="e04fb-134">Datové body nejsou shromážděna</span><span class="sxs-lookup"><span data-stu-id="e04fb-134">Data points not collected</span></span>
<span data-ttu-id="e04fb-135">Funkce telemetrie *nebude* shromažďovat:</span><span class="sxs-lookup"><span data-stu-id="e04fb-135">The telemetry feature *doesn't* collect:</span></span>
- <span data-ttu-id="e04fb-136">osobní údaje, jako jsou uživatelská jména</span><span class="sxs-lookup"><span data-stu-id="e04fb-136">personal data, such as usernames</span></span>
- <span data-ttu-id="e04fb-137">názvy souborů datové sady</span><span class="sxs-lookup"><span data-stu-id="e04fb-137">dataset filenames</span></span>
- <span data-ttu-id="e04fb-138">data z datové sady souborů</span><span class="sxs-lookup"><span data-stu-id="e04fb-138">data from dataset files</span></span>

<span data-ttu-id="e04fb-139">Pokud máte podezření, že se citlivá data nebo, který sbírá telemetrie ML.NET rozhraní příkazového řádku dat probíhá nezabezpečeným způsobem nebo neoprávněně zpracována, založte problém v [ML.NET](https://github.com/dotnet/machinelearning) úložiště pro šetření.</span><span class="sxs-lookup"><span data-stu-id="e04fb-139">If you suspect that the ML.NET CLI telemetry is collecting sensitive data or that the data is being insecurely or inappropriately handled, file an issue in the [ML.NET](https://github.com/dotnet/machinelearning) repository for investigation.</span></span>

## <a name="license"></a><span data-ttu-id="e04fb-140">Licence</span><span class="sxs-lookup"><span data-stu-id="e04fb-140">License</span></span>

<span data-ttu-id="e04fb-141">Je distribuce Microsoftu příkazového řádku ML.NET licenci [licenční podmínky pro Software společnosti Microsoft: Knihovna rozhraní Microsoft .NET](https://aka.ms/dotnet-core-eula).</span><span class="sxs-lookup"><span data-stu-id="e04fb-141">The Microsoft distribution of ML.NET CLI is licensed with the [Microsoft Software License Terms: Microsoft .NET Library](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="e04fb-142">Podrobnosti o shromažďování dat a zpracování najdete v části s názvem "Data".</span><span class="sxs-lookup"><span data-stu-id="e04fb-142">For details on data collection and processing, see the section entitled "Data."</span></span>

## <a name="disclosure"></a><span data-ttu-id="e04fb-143">Zpřístupnění</span><span class="sxs-lookup"><span data-stu-id="e04fb-143">Disclosure</span></span>

<span data-ttu-id="e04fb-144">Při prvním spuštění [příkazu rozhraní příkazového řádku ML.NET](../reference/ml-net-cli-reference.md) jako `mlnet auto-train`, nástroje rozhraní příkazového řádku ML.NET zobrazí zpřístupnění text, který vysvětluje, jak vyjádřit výslovný nesouhlas telemetrická data.</span><span class="sxs-lookup"><span data-stu-id="e04fb-144">When you first run a [ML.NET CLI command](../reference/ml-net-cli-reference.md) such as `mlnet auto-train`, the ML.NET CLI tool displays disclosure text that tells you how to opt out of telemetry.</span></span> <span data-ttu-id="e04fb-145">Text může mírně lišit v závislosti na verzi rozhraní příkazového řádku, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="e04fb-145">Text may vary slightly depending on the version of the CLI you're running.</span></span>

## <a name="see-also"></a><span data-ttu-id="e04fb-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e04fb-146">See also</span></span>
- [<span data-ttu-id="e04fb-147">Referenční informace k ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="e04fb-147">ML.NET CLI reference</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="e04fb-148">Licenční podmínky pro Software společnosti Microsoft: Knihovna rozhraní Microsoft .NET</span><span class="sxs-lookup"><span data-stu-id="e04fb-148">Microsoft Software License Terms: Microsoft .NET Library</span></span>](https://aka.ms/dotnet-core-eula)
- [<span data-ttu-id="e04fb-149">Ochrana osobních údajů společnosti Microsoft</span><span class="sxs-lookup"><span data-stu-id="e04fb-149">Privacy at Microsoft</span></span>](https://www.microsoft.com/en-us/trustcenter/privacy/)
- [<span data-ttu-id="e04fb-150">Prohlášení o ochraně osobních údajů společnosti Microsoft</span><span class="sxs-lookup"><span data-stu-id="e04fb-150">Microsoft Privacy Statement</span></span>](https://privacy.microsoft.com/en-us/privacystatement)
