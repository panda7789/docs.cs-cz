---
title: Kolekce telemetrie podle ML.NET CLI
description: Další informace o ML.NET funkce telemetrie cli, které shromažďují informace o využití pro analýzu, která data jsou shromažďována a jak je zakázat. Najděte také odkazy na licenční smlouvu .NET a informace o dodržování nařízení Microsoft GDPR.
ms.topic: conceptual
ms.date: 09/03/2019
ms.custom: mlnet-tooling
ms.openlocfilehash: 99e11acba343cc689c3219ca9316144fc62cd618
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78849741"
---
# <a name="telemetry-collection-by-the-mlnet-cli"></a><span data-ttu-id="b6ff3-104">Kolekce telemetrie podle ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="b6ff3-104">Telemetry collection by the ML.NET CLI</span></span>

<span data-ttu-id="b6ff3-105">Rozhraní [ML.NET CLI](https://aka.ms/mlnet-cli) obsahuje funkci telemetrie, která shromažďuje anonymní data o využití, která jsou agregována pro použití společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b6ff3-105">The [ML.NET CLI](https://aka.ms/mlnet-cli) includes a telemetry feature that collects anonymous usage data that is aggregated for use by Microsoft.</span></span>

## <a name="how-microsoft-uses-the-data"></a><span data-ttu-id="b6ff3-106">Jak společnost Microsoft používá data</span><span class="sxs-lookup"><span data-stu-id="b6ff3-106">How Microsoft uses the data</span></span>

<span data-ttu-id="b6ff3-107">Produktový tým používá ML.NET telemetrická data cli, které pomáhají pochopit, jak zlepšit nástroje.</span><span class="sxs-lookup"><span data-stu-id="b6ff3-107">The product team uses ML.NET CLI telemetry data to help understand how to improve the tools.</span></span> <span data-ttu-id="b6ff3-108">Pokud například zákazníci zřídka používají určitý úkol strojového učení, produktový tým zkoumá proč a pomocí zjištění upřednostňuje vývoj funkcí.</span><span class="sxs-lookup"><span data-stu-id="b6ff3-108">For example, if customers infrequently use a particular machine learning task, the product team investigates why and uses findings to prioritize feature development.</span></span> <span data-ttu-id="b6ff3-109">ML.NET telemetrii CLI také pomáhá s laděním problémů, jako jsou selhání a anomálie kódu.</span><span class="sxs-lookup"><span data-stu-id="b6ff3-109">ML.NET CLI telemetry also helps with debugging of issues such as crashes and code anomalies.</span></span>

<span data-ttu-id="b6ff3-110">I když produktový tým tento přehled oceňuje, víme také, že ne každý chce tato data odeslat.</span><span class="sxs-lookup"><span data-stu-id="b6ff3-110">While the product team appreciates this insight, we also know that not everyone wants to send this data.</span></span> [<span data-ttu-id="b6ff3-111">Zjistěte, jak zakázat telemetrii.</span><span class="sxs-lookup"><span data-stu-id="b6ff3-111">Find out how to disable telemetry.</span></span>](#opt-out-of-data-collection)

## <a name="scope"></a><span data-ttu-id="b6ff3-112">Rozsah</span><span class="sxs-lookup"><span data-stu-id="b6ff3-112">Scope</span></span>

<span data-ttu-id="b6ff3-113">Příkaz `mlnet` spustí ML.NET CLI, ale samotný příkaz neshromažďuje telemetrii.</span><span class="sxs-lookup"><span data-stu-id="b6ff3-113">The `mlnet` command launches the ML.NET CLI, but the command itself doesn't collect telemetry.</span></span>

<span data-ttu-id="b6ff3-114">Telemetrie *není povolena* při `mlnet` spuštění příkazu bez připojeného jiného příkazu.</span><span class="sxs-lookup"><span data-stu-id="b6ff3-114">Telemetry *isn't enabled* when you run the `mlnet` command with no other command attached.</span></span> <span data-ttu-id="b6ff3-115">Například:</span><span class="sxs-lookup"><span data-stu-id="b6ff3-115">For example:</span></span>

- `mlnet`
- `mlnet --help`

<span data-ttu-id="b6ff3-116">Telemetrie *je povolena* při spuštění [příkazu ML.NET CLI](../reference/ml-net-cli-reference.md), například `mlnet auto-train`.</span><span class="sxs-lookup"><span data-stu-id="b6ff3-116">Telemetry *is enabled* when you run an [ML.NET CLI command](../reference/ml-net-cli-reference.md), such as `mlnet auto-train`.</span></span>

## <a name="opt-out-of-data-collection"></a><span data-ttu-id="b6ff3-117">Odhlásit se ze shromažďování údajů</span><span class="sxs-lookup"><span data-stu-id="b6ff3-117">Opt out of data collection</span></span>

<span data-ttu-id="b6ff3-118">Funkce telemetrie ML.NET CLI je ve výchozím nastavení povolena.</span><span class="sxs-lookup"><span data-stu-id="b6ff3-118">The ML.NET CLI telemetry feature is enabled by default.</span></span>

<span data-ttu-id="b6ff3-119">Odhlásit se z funkce telemetrie nastavením proměnné `MLDOTNET_CLI_TELEMETRY_OPTOUT` prostředí na `1` nebo `true`.</span><span class="sxs-lookup"><span data-stu-id="b6ff3-119">Opt out of the telemetry feature by setting the `MLDOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span> <span data-ttu-id="b6ff3-120">Tato proměnná prostředí platí globálně pro nástroj ML.NET CLI.</span><span class="sxs-lookup"><span data-stu-id="b6ff3-120">This environment variable applies globally to the ML.NET CLI tool.</span></span>

## <a name="data-points-collected"></a><span data-ttu-id="b6ff3-121">Shromážděné datové body</span><span class="sxs-lookup"><span data-stu-id="b6ff3-121">Data points collected</span></span>

<span data-ttu-id="b6ff3-122">Tato funkce shromažďuje následující data:</span><span class="sxs-lookup"><span data-stu-id="b6ff3-122">The feature collects the following data:</span></span>

- <span data-ttu-id="b6ff3-123">Jaký příkaz byl vyvolán, například`auto-train`</span><span class="sxs-lookup"><span data-stu-id="b6ff3-123">What command was invoked, such as `auto-train`</span></span>
- <span data-ttu-id="b6ff3-124">Použité názvy parametrů příkazového řádku (to znamená "název datové sady, název sloupce popisku, ml-task, výstupní cesta, max-exploration-time, podrobnost")</span><span class="sxs-lookup"><span data-stu-id="b6ff3-124">Command-line parameter names used (that is, "dataset-name, label-column-name, ml-task, output-path, max-exploration-time, verbosity")</span></span>
- <span data-ttu-id="b6ff3-125">Hashed MAC adresa: kryptograficky (SHA256) anonymní a jedinečné ID pro počítač</span><span class="sxs-lookup"><span data-stu-id="b6ff3-125">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine</span></span>
- <span data-ttu-id="b6ff3-126">Časové razítko vyvolání</span><span class="sxs-lookup"><span data-stu-id="b6ff3-126">Timestamp of an invocation</span></span>
- <span data-ttu-id="b6ff3-127">Tři oktetové IP adresy (ne úplná IP adresa) používané pouze k určení zeměpisné polohy</span><span class="sxs-lookup"><span data-stu-id="b6ff3-127">Three octet IP address (not full IP address) used only to determine geographical location</span></span>
- <span data-ttu-id="b6ff3-128">Název všech použitých argumentů/parametrů.</span><span class="sxs-lookup"><span data-stu-id="b6ff3-128">Name of all arguments/parameters used.</span></span> <span data-ttu-id="b6ff3-129">Nejsou hodnoty zákazníka, například řetězce</span><span class="sxs-lookup"><span data-stu-id="b6ff3-129">Not the customer's values, such as strings</span></span>
- <span data-ttu-id="b6ff3-130">Název souboru hashed dataset</span><span class="sxs-lookup"><span data-stu-id="b6ff3-130">Hashed dataset filename</span></span>
- <span data-ttu-id="b6ff3-131">Kontejner velikosti souboru datové sady</span><span class="sxs-lookup"><span data-stu-id="b6ff3-131">Dataset file-size bucket</span></span>
- <span data-ttu-id="b6ff3-132">Operační systém a verze</span><span class="sxs-lookup"><span data-stu-id="b6ff3-132">Operating system and version</span></span>
- <span data-ttu-id="b6ff3-133">Hodnota parametru --task: Kategorické `regression` `binary-classification`hodnoty, například , a`multiclass-classification`</span><span class="sxs-lookup"><span data-stu-id="b6ff3-133">Value of --task parameter: Categorical values, such as `regression`, `binary-classification`, and `multiclass-classification`</span></span>
- <span data-ttu-id="b6ff3-134">ML.NET verze CLI (tj. 0.3.27703.4)</span><span class="sxs-lookup"><span data-stu-id="b6ff3-134">ML.NET CLI version (that is, 0.3.27703.4)</span></span>

<span data-ttu-id="b6ff3-135">Data se bezpečně odesílají na servery Microsoftu pomocí technologie [Azure Application Insights,](https://azure.microsoft.com/services/application-insights/) která je držena s omezeným přístupem a používá se pod přísnými bezpečnostními kontrolami ze zabezpečených systémů [Azure Storage.](https://azure.microsoft.com/services/storage/)</span><span class="sxs-lookup"><span data-stu-id="b6ff3-135">The data is sent securely to Microsoft servers using [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and used under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

### <a name="data-points-not-collected"></a><span data-ttu-id="b6ff3-136">Neshromažďované datové body</span><span class="sxs-lookup"><span data-stu-id="b6ff3-136">Data points not collected</span></span>

<span data-ttu-id="b6ff3-137">Funkce telemetrie *neshromažďuje:*</span><span class="sxs-lookup"><span data-stu-id="b6ff3-137">The telemetry feature *doesn't* collect:</span></span>

- <span data-ttu-id="b6ff3-138">osobních údajů, jako jsou uživatelská jména</span><span class="sxs-lookup"><span data-stu-id="b6ff3-138">personal data, such as usernames</span></span>
- <span data-ttu-id="b6ff3-139">názvy souborů datové sady</span><span class="sxs-lookup"><span data-stu-id="b6ff3-139">dataset filenames</span></span>
- <span data-ttu-id="b6ff3-140">data ze souborů datové sady</span><span class="sxs-lookup"><span data-stu-id="b6ff3-140">data from dataset files</span></span>

<span data-ttu-id="b6ff3-141">Pokud máte podezření, že telemetrie ML.NET CLI shromažďuje citlivá data nebo že jsou data nebezpečně nebo nevhodně zpracována, zasuzujte problém do [úložiště ML.NET](https://github.com/dotnet/machinelearning) pro šetření.</span><span class="sxs-lookup"><span data-stu-id="b6ff3-141">If you suspect that the ML.NET CLI telemetry is collecting sensitive data or that the data is being insecurely or inappropriately handled, file an issue in the [ML.NET](https://github.com/dotnet/machinelearning) repository for investigation.</span></span>

## <a name="license"></a><span data-ttu-id="b6ff3-142">Licence</span><span class="sxs-lookup"><span data-stu-id="b6ff3-142">License</span></span>

<span data-ttu-id="b6ff3-143">Distribuce ML.NET cli společnosti Microsoft je licencována s [licenčními podmínkami pro software společnosti Microsoft: Microsoft .NET Library](https://aka.ms/dotnet-core-eula).</span><span class="sxs-lookup"><span data-stu-id="b6ff3-143">The Microsoft distribution of ML.NET CLI is licensed with the [Microsoft Software License Terms: Microsoft .NET Library](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="b6ff3-144">Podrobnosti o shromažďování a zpracování údajů naleznete v části s názvem "Data".</span><span class="sxs-lookup"><span data-stu-id="b6ff3-144">For details on data collection and processing, see the section entitled "Data."</span></span>

## <a name="disclosure"></a><span data-ttu-id="b6ff3-145">Zveřejnění</span><span class="sxs-lookup"><span data-stu-id="b6ff3-145">Disclosure</span></span>

<span data-ttu-id="b6ff3-146">Při prvním spuštění [příkazu ML.NET příkazu příkazu příkazu,](../reference/ml-net-cli-reference.md) například `mlnet auto-train`, nástroj ML.NET příkazového příkazu zobrazí zpřístupnění text, který vám řekne, jak se odhlásit z telemetrie.</span><span class="sxs-lookup"><span data-stu-id="b6ff3-146">When you first run a [ML.NET CLI command](../reference/ml-net-cli-reference.md) such as `mlnet auto-train`, the ML.NET CLI tool displays disclosure text that tells you how to opt out of telemetry.</span></span> <span data-ttu-id="b6ff3-147">Text se může mírně lišit v závislosti na verzi spuštěného vodního úpově.</span><span class="sxs-lookup"><span data-stu-id="b6ff3-147">Text may vary slightly depending on the version of the CLI you're running.</span></span>

## <a name="see-also"></a><span data-ttu-id="b6ff3-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="b6ff3-148">See also</span></span>

- [<span data-ttu-id="b6ff3-149">ML.NET odkaz na cli</span><span class="sxs-lookup"><span data-stu-id="b6ff3-149">ML.NET CLI reference</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="b6ff3-150">Licenční podmínky pro software společnosti Microsoft: Knihovna Microsoft .NET</span><span class="sxs-lookup"><span data-stu-id="b6ff3-150">Microsoft Software License Terms: Microsoft .NET Library</span></span>](https://aka.ms/dotnet-core-eula)
- [<span data-ttu-id="b6ff3-151">Ochrana osobních údajů ve společnosti Microsoft</span><span class="sxs-lookup"><span data-stu-id="b6ff3-151">Privacy at Microsoft</span></span>](https://www.microsoft.com/trustcenter/privacy/)
- [<span data-ttu-id="b6ff3-152">Prohlášení společnosti Microsoft o zásadách ochrany osobních údajů</span><span class="sxs-lookup"><span data-stu-id="b6ff3-152">Microsoft Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
