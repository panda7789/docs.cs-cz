---
title: odkaz příkazu ML.NET CLI
description: Přehled, ukázky a odkaz na příkaz automatického tácení v nástroji ML.NET CLI.
ms.date: 12/18/2019
ms.custom: mlnet-tooling
ms.openlocfilehash: bb161c596a76134876ee2bf0a6229bc551e0dad2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78848922"
---
# <a name="the-mlnet-cli-command-reference"></a><span data-ttu-id="d204c-103">Odkaz na příkaz ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="d204c-103">The ML.NET CLI command reference</span></span>

<span data-ttu-id="d204c-104">Příkaz `auto-train` je hlavním příkazem poskytovaným nástrojem ML.NET CLI.</span><span class="sxs-lookup"><span data-stu-id="d204c-104">The `auto-train` command is the main command provided by the ML.NET CLI tool.</span></span> <span data-ttu-id="d204c-105">Příkaz umožňuje generovat kvalitní ML.NET modelu pomocí automatizovaného strojového učení (AutoML) a také v příkladu kódu Jazyka C# pro spuštění a skóre tohoto modelu.</span><span class="sxs-lookup"><span data-stu-id="d204c-105">The command allows you to generate a good quality ML.NET model using automated machine learning (AutoML) as well as the example C# code to run/score that model.</span></span> <span data-ttu-id="d204c-106">Kromě toho je generován kód Jazyka C# pro trénování modelu pro výzkum algoritmu a nastavení modelu.</span><span class="sxs-lookup"><span data-stu-id="d204c-106">In addition, the C# code to train the model is generated for you to research the algorithm and settings of the model.</span></span>

> [!NOTE]
> <span data-ttu-id="d204c-107">Toto téma odkazuje na ML.NET cli a ML.NET AutoML, které jsou aktuálně ve verzi Preview, a materiál může být může být možné změnit.</span><span class="sxs-lookup"><span data-stu-id="d204c-107">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="overview"></a><span data-ttu-id="d204c-108">Přehled</span><span class="sxs-lookup"><span data-stu-id="d204c-108">Overview</span></span>

<span data-ttu-id="d204c-109">Příklad použití:</span><span class="sxs-lookup"><span data-stu-id="d204c-109">Example usage:</span></span>

```console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

<span data-ttu-id="d204c-110">Příkaz `mlnet auto-train` generuje následující datové zdroje:</span><span class="sxs-lookup"><span data-stu-id="d204c-110">The `mlnet auto-train` command generates the following assets:</span></span>

- <span data-ttu-id="d204c-111">Serializovaný model .zip ("nejlepší model") připravený k použití.</span><span class="sxs-lookup"><span data-stu-id="d204c-111">A serialized model .zip ("best model") ready to use.</span></span>
- <span data-ttu-id="d204c-112">C# kód ke spuštění/skóre, které vygenerovaly model.</span><span class="sxs-lookup"><span data-stu-id="d204c-112">C# code to run/score that generated model.</span></span>
- <span data-ttu-id="d204c-113">C# kód s trénovací kód slouží ke generování tohoto modelu.</span><span class="sxs-lookup"><span data-stu-id="d204c-113">C# code with the training code used to generate that model.</span></span>

<span data-ttu-id="d204c-114">První dva datové zdroje lze přímo použít ve vašich aplikacích pro koncové uživatele (ASP.NET základní webové aplikace, služby, desktopové aplikace a další) k předpovědi s modelem.</span><span class="sxs-lookup"><span data-stu-id="d204c-114">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app and more) to make predictions with the model.</span></span>

<span data-ttu-id="d204c-115">Třetí prostředek, trénovací kód, ukazuje, jaký ML.NET kód rozhraní API byl použit rozhraní matné rozhraní API k trénování generovaného modelu, takže můžete prozkoumat konkrétní algoritmus a nastavení modelu.</span><span class="sxs-lookup"><span data-stu-id="d204c-115">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate the specific algorithm and settings of the model.</span></span>

## <a name="examples"></a><span data-ttu-id="d204c-116">Příklady</span><span class="sxs-lookup"><span data-stu-id="d204c-116">Examples</span></span>

<span data-ttu-id="d204c-117">Nejjednodušší příkaz CLI pro problém binární klasifikace (AutoML odvodí většinu konfigurace z poskytnutých dat):</span><span class="sxs-lookup"><span data-stu-id="d204c-117">The simplest CLI command for a binary classification problem (AutoML infers most of the configuration from the provided data):</span></span>

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

<span data-ttu-id="d204c-118">Další jednoduchý příkaz CLI pro regresní problém:</span><span class="sxs-lookup"><span data-stu-id="d204c-118">Another simple CLI command for a regression problem:</span></span>

``` console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

<span data-ttu-id="d204c-119">Vytvořte a trénujte model binární klasifikace s datovou sadou vlakových dat, testovací datovou sadou a dalšími explicitními argumenty přizpůsobení:</span><span class="sxs-lookup"><span data-stu-id="d204c-119">Create and train a binary-classification model with a train dataset, a test dataset, and further customization explicit arguments:</span></span>

```console
mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="command-options"></a><span data-ttu-id="d204c-120">Volby příkazů</span><span class="sxs-lookup"><span data-stu-id="d204c-120">Command options</span></span>

<span data-ttu-id="d204c-121">`mlnet auto-train`trénuje více modelů založených na poskytnuté datové sadě a nakonec vybere nejlepší model, uloží jej jako serializovaný soubor ZIP plus generuje související kód C# pro vyhodnocování a trénování.</span><span class="sxs-lookup"><span data-stu-id="d204c-121">`mlnet auto-train` trains multiple models based on the provided dataset and finally selects the best model, saves it as a serialized .zip file plus generates related C# code for scoring and training.</span></span>

```console
mlnet auto-train

--task | --mltask | -T <value>

--dataset | -d <value>

[
 [--validation-dataset | -v <value>]
  --test-dataset | -t <value>
]

--label-column-name | -n <value>
|
--label-column-index | -i <value>

[--ignore-columns | -I <value>]

[--has-header | -h <value>]

[--max-exploration-time | -x <value>]

[--verbosity | -V <value>]

[--cache | -c <value>]

[--name | -N <value>]

[--output-path | -o <value>]

[--help | -h]

```

<span data-ttu-id="d204c-122">Neplatné možnosti zadávání způsobí, že nástroj rozhraní se konstatování rozhraní A CLI vyzařuje seznam platných vstupů a chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="d204c-122">Invalid input options cause the CLI tool to emit a list of valid inputs and an error message.</span></span>

## <a name="task"></a><span data-ttu-id="d204c-123">Úkol</span><span class="sxs-lookup"><span data-stu-id="d204c-123">Task</span></span>

<span data-ttu-id="d204c-124">`--task | --mltask | -T`(řetězec)</span><span class="sxs-lookup"><span data-stu-id="d204c-124">`--task | --mltask | -T` (string)</span></span>

<span data-ttu-id="d204c-125">Jeden řetězec poskytující problém ML k vyřešení.</span><span class="sxs-lookup"><span data-stu-id="d204c-125">A single string providing the ML problem to solve.</span></span> <span data-ttu-id="d204c-126">Například některý z následujících úkolů (příkaz příkazpříkaz příkazového konto nakonec bude podporovat všechny úkoly podporované v automatické ml):</span><span class="sxs-lookup"><span data-stu-id="d204c-126">For instance, any of the following tasks (The CLI will eventually support all tasks supported in AutoML):</span></span>

- <span data-ttu-id="d204c-127">`regression`- Zvolte, zda bude model ML použit k předvídání číselné hodnoty</span><span class="sxs-lookup"><span data-stu-id="d204c-127">`regression` - Choose if the ML Model will be used to predict a numeric value</span></span>
- <span data-ttu-id="d204c-128">`binary-classification`- Zvolte, zda má výsledek modelu ML dvě možné kategorie logických hodnot (0 nebo 1).</span><span class="sxs-lookup"><span data-stu-id="d204c-128">`binary-classification` - Choose if the ML Model result has two possible categorical boolean values (0 or 1).</span></span>
- <span data-ttu-id="d204c-129">`multiclass-classification`- Zvolte, zda má výsledek modelu ML více kategorických možných hodnot.</span><span class="sxs-lookup"><span data-stu-id="d204c-129">`multiclass-classification` - Choose if the ML Model result has multiple categorical possible values.</span></span>

<span data-ttu-id="d204c-130">V tomto argumentu by měl být poskytnut pouze jeden úkol ML.</span><span class="sxs-lookup"><span data-stu-id="d204c-130">Only one ML task should be provided in this argument.</span></span>

## <a name="dataset"></a><span data-ttu-id="d204c-131">Datová sada</span><span class="sxs-lookup"><span data-stu-id="d204c-131">Dataset</span></span>

<span data-ttu-id="d204c-132">`--dataset | -d`(řetězec)</span><span class="sxs-lookup"><span data-stu-id="d204c-132">`--dataset | -d` (string)</span></span>

<span data-ttu-id="d204c-133">Tento argument poskytuje cestu k souboru jedné z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="d204c-133">This argument provides the filepath to either one of the following options:</span></span>

- <span data-ttu-id="d204c-134">*A: Celý soubor datové sady:* Pokud používáte tuto možnost a `--test-dataset` `--validation-dataset`uživatel neposkytuje a , pak křížové ověření (k-fold, atd.) nebo automatizované přístupy rozdělení dat budou použity interně pro ověření modelu.</span><span class="sxs-lookup"><span data-stu-id="d204c-134">*A: The whole dataset file:* If using this option and the user is not providing `--test-dataset` and `--validation-dataset`, then cross-validation (k-fold, etc.) or automated data split approaches will be used internally for validating the model.</span></span> <span data-ttu-id="d204c-135">V takovém případě bude uživatel potřebovat pouze poskytnout cestu souboru datové sady.</span><span class="sxs-lookup"><span data-stu-id="d204c-135">In that case, the user will just need to provide the dataset filepath.</span></span>

- <span data-ttu-id="d204c-136">*B: Soubor trénovací datové sady:* Pokud uživatel také poskytuje datové sady pro `--test-dataset` ověření `--validation-dataset`modelu (pomocí a volitelně ), pak `--dataset` argument znamená mít pouze "trénovací datové sady".</span><span class="sxs-lookup"><span data-stu-id="d204c-136">*B: The training dataset file:* If the user is also providing datasets for model validation (using `--test-dataset` and optionally `--validation-dataset`), then the `--dataset` argument means to only have the "training dataset".</span></span> <span data-ttu-id="d204c-137">Například při použití 80 % - 20% přístup k ověření kvality modelu a získat metriky přesnosti, "trénovací datové sady" bude mít 80 % dat a "testovací datové sady" bude mít 20 % dat.</span><span class="sxs-lookup"><span data-stu-id="d204c-137">For example, when using an 80% - 20% approach to validate the quality of the model and to obtain accuracy metrics, the "training dataset" will have 80% of the data and the "test dataset" would have 20% of the data.</span></span>

## <a name="test-dataset"></a><span data-ttu-id="d204c-138">Testovací datová sada</span><span class="sxs-lookup"><span data-stu-id="d204c-138">Test dataset</span></span>

<span data-ttu-id="d204c-139">`--test-dataset | -t`(řetězec)</span><span class="sxs-lookup"><span data-stu-id="d204c-139">`--test-dataset | -t` (string)</span></span>

<span data-ttu-id="d204c-140">Cesta k souboru směřující k souboru testovací datové sady, například při použití přístupu 80 % až 20 % při provádění pravidelných ověření za účelem získání metrik přesnosti.</span><span class="sxs-lookup"><span data-stu-id="d204c-140">File path pointing to the test dataset file, for example when using an 80% - 20% approach when making regular validations to obtain accuracy metrics.</span></span>

<span data-ttu-id="d204c-141">Pokud `--test-dataset`používáte `--dataset` , pak je také nutné.</span><span class="sxs-lookup"><span data-stu-id="d204c-141">If using `--test-dataset`, then `--dataset` is also required.</span></span>

<span data-ttu-id="d204c-142">Argument `--test-dataset` je volitelný, pokud --validation-dataset se používá.</span><span class="sxs-lookup"><span data-stu-id="d204c-142">The `--test-dataset` argument is optional unless the --validation-dataset is used.</span></span> <span data-ttu-id="d204c-143">V takovém případě musí uživatel použít tři argumenty.</span><span class="sxs-lookup"><span data-stu-id="d204c-143">In that case, the user must use the three arguments.</span></span>

## <a name="validation-dataset"></a><span data-ttu-id="d204c-144">Ověřovací datová sada</span><span class="sxs-lookup"><span data-stu-id="d204c-144">Validation dataset</span></span>

<span data-ttu-id="d204c-145">`--validation-dataset | -v`(řetězec)</span><span class="sxs-lookup"><span data-stu-id="d204c-145">`--validation-dataset | -v` (string)</span></span>

<span data-ttu-id="d204c-146">Cesta k souboru směřující k ověřovacímu souboru datové sady.</span><span class="sxs-lookup"><span data-stu-id="d204c-146">File path pointing to the validation dataset file.</span></span> <span data-ttu-id="d204c-147">Ověřovací datová sada je v každém případě volitelná.</span><span class="sxs-lookup"><span data-stu-id="d204c-147">The validation dataset is optional, in any case.</span></span>

<span data-ttu-id="d204c-148">Pokud používáte `validation dataset`, chování by mělo být:</span><span class="sxs-lookup"><span data-stu-id="d204c-148">If using a `validation dataset`, the behavior should be:</span></span>

- <span data-ttu-id="d204c-149">A `test-dataset` `--dataset` argumenty jsou také požadovány.</span><span class="sxs-lookup"><span data-stu-id="d204c-149">The `test-dataset` and `--dataset` arguments are also required.</span></span>

- <span data-ttu-id="d204c-150">Datová `validation-dataset` sada se používá k odhadu chyby předpovědi pro výběr modelu.</span><span class="sxs-lookup"><span data-stu-id="d204c-150">The `validation-dataset` dataset is used to estimate prediction error for model selection.</span></span>

- <span data-ttu-id="d204c-151">Slouží `test-dataset` k posouzení chyby generalizace konečného zvoleného modelu.</span><span class="sxs-lookup"><span data-stu-id="d204c-151">The `test-dataset` is used for assessment of the generalization error of the final chosen model.</span></span> <span data-ttu-id="d204c-152">V ideálním případě by testovací sada měla být uložena v "trezoru" a měla by být vyvedena pouze na konci analýzy dat.</span><span class="sxs-lookup"><span data-stu-id="d204c-152">Ideally, the test set should be kept in a “vault,” and be brought out only at the end of the data analysis.</span></span>

<span data-ttu-id="d204c-153">V podstatě, `validation dataset` při `test dataset`použití plus , fáze validace je rozdělena do dvou částí:</span><span class="sxs-lookup"><span data-stu-id="d204c-153">Basically, when using a `validation dataset` plus the `test dataset`, the validation phase is split into two parts:</span></span>

1. <span data-ttu-id="d204c-154">V první části se stačí podívat na své modely a vybrat nejvýkonnější přístup pomocí ověřovacích dat (=ověření)</span><span class="sxs-lookup"><span data-stu-id="d204c-154">In the first part, you just look at your models and select the best performing approach using the validation data (=validation)</span></span>
2. <span data-ttu-id="d204c-155">Poté odhadnete přesnost zvoleného přístupu (=test).</span><span class="sxs-lookup"><span data-stu-id="d204c-155">Then you estimate the accuracy of the selected approach (=test).</span></span>

<span data-ttu-id="d204c-156">Oddělení údajů by proto mohlo být 80/10/10 nebo 75/15/10.</span><span class="sxs-lookup"><span data-stu-id="d204c-156">Hence, the separation of data could be 80/10/10 or 75/15/10.</span></span> <span data-ttu-id="d204c-157">Například:</span><span class="sxs-lookup"><span data-stu-id="d204c-157">For example:</span></span>

- <span data-ttu-id="d204c-158">`training-dataset`soubor by měl mít 75% dat.</span><span class="sxs-lookup"><span data-stu-id="d204c-158">`training-dataset` file should have 75% of the data.</span></span>
- <span data-ttu-id="d204c-159">`validation-dataset`soubor by měl mít 15% dat.</span><span class="sxs-lookup"><span data-stu-id="d204c-159">`validation-dataset` file should have 15% of the data.</span></span>
- <span data-ttu-id="d204c-160">`test-dataset`soubor by měl mít 10% dat.</span><span class="sxs-lookup"><span data-stu-id="d204c-160">`test-dataset` file should have 10% of the data.</span></span>

<span data-ttu-id="d204c-161">V každém případě budou tyto procenta rozhodovat uživatel pomocí rozhraní se kli, který poskytne soubory, které jsou již rozděleny.</span><span class="sxs-lookup"><span data-stu-id="d204c-161">In any case, those percentages will be decided by the user using the CLI who will provide the files already split.</span></span>

## <a name="label-column-name"></a><span data-ttu-id="d204c-162">Název sloupce popisku</span><span class="sxs-lookup"><span data-stu-id="d204c-162">Label column name</span></span>

<span data-ttu-id="d204c-163">`--label-column-name | -n`(řetězec)</span><span class="sxs-lookup"><span data-stu-id="d204c-163">`--label-column-name | -n` (string)</span></span>

<span data-ttu-id="d204c-164">Pomocí tohoto argumentu lze zadat konkrétní sloupec cíle/cíle (proměnnou, kterou chcete předpovědět) pomocí názvu sloupce nastaveného v záhlaví datové sady.</span><span class="sxs-lookup"><span data-stu-id="d204c-164">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's name set in the dataset's header.</span></span>

<span data-ttu-id="d204c-165">Tento argument se používá pouze pro úkoly ML pod dohledem, jako je *například problém klasifikace*.</span><span class="sxs-lookup"><span data-stu-id="d204c-165">This argument is used only for supervised ML tasks such as a *classification problem*.</span></span> <span data-ttu-id="d204c-166">Nelze jej použít pro úlohy ML bez dohledu, jako je *clustering*.</span><span class="sxs-lookup"><span data-stu-id="d204c-166">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

## <a name="label-column-index"></a><span data-ttu-id="d204c-167">Index sloupce popisku</span><span class="sxs-lookup"><span data-stu-id="d204c-167">Label column index</span></span>

<span data-ttu-id="d204c-168">`--label-column-index | -i`(int)</span><span class="sxs-lookup"><span data-stu-id="d204c-168">`--label-column-index | -i` (int)</span></span>

<span data-ttu-id="d204c-169">Pomocí tohoto argumentu lze zadat konkrétní sloupec cíle/cíle (proměnnou, kterou chcete předpovědět) pomocí číselného indexu sloupce v souboru datové sady (Hodnoty indexu sloupce začínají na 1).</span><span class="sxs-lookup"><span data-stu-id="d204c-169">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's numeric index in the dataset's file (The column index values start at 1).</span></span>

<span data-ttu-id="d204c-170">*Poznámka:* Pokud uživatel také používá `--label-column-name`, `--label-column-name` je ten, který se používá.</span><span class="sxs-lookup"><span data-stu-id="d204c-170">*Note:* If the user is also using the `--label-column-name`, the `--label-column-name` is the one being used.</span></span>

<span data-ttu-id="d204c-171">Tento argument se používá pouze pro úkol ml pod dohledem, jako je *například problém klasifikace*.</span><span class="sxs-lookup"><span data-stu-id="d204c-171">This argument is used only for supervised ML task such as a *classification problem*.</span></span> <span data-ttu-id="d204c-172">Nelze jej použít pro úlohy ML bez dohledu, jako je *clustering*.</span><span class="sxs-lookup"><span data-stu-id="d204c-172">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

## <a name="ignore-columns"></a><span data-ttu-id="d204c-173">Ignorovat sloupce</span><span class="sxs-lookup"><span data-stu-id="d204c-173">Ignore columns</span></span>

<span data-ttu-id="d204c-174">`--ignore-columns | -I`(řetězec)</span><span class="sxs-lookup"><span data-stu-id="d204c-174">`--ignore-columns | -I` (string)</span></span>

<span data-ttu-id="d204c-175">Pomocí tohoto argumentu můžete ignorovat existující sloupce v souboru datové sady, aby nebyly načteny a používány trénovacími procesy.</span><span class="sxs-lookup"><span data-stu-id="d204c-175">With this argument, you can ignore existing columns in the dataset file so they are not loaded and used by the training processes.</span></span>

<span data-ttu-id="d204c-176">Zadejte názvy sloupců, které chcete ignorovat.</span><span class="sxs-lookup"><span data-stu-id="d204c-176">Specify the columns names that you want to ignore.</span></span> <span data-ttu-id="d204c-177">K oddělení více názvů sloupců použijte ', ' (čárka s mezerou) nebo '' (mezera).</span><span class="sxs-lookup"><span data-stu-id="d204c-177">Use ', ' (comma with space) or ' ' (space) to separate multiple column names.</span></span> <span data-ttu-id="d204c-178">U názvů sloupců obsahujících mezery (např.</span><span class="sxs-lookup"><span data-stu-id="d204c-178">You can use quotes for column names containing whitespace (e.g. "logged in").</span></span>

<span data-ttu-id="d204c-179">Příklad:</span><span class="sxs-lookup"><span data-stu-id="d204c-179">Example:</span></span>

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a><span data-ttu-id="d204c-180">Má záhlaví</span><span class="sxs-lookup"><span data-stu-id="d204c-180">Has header</span></span>

<span data-ttu-id="d204c-181">`--has-header | -h`(bool)</span><span class="sxs-lookup"><span data-stu-id="d204c-181">`--has-header | -h` (bool)</span></span>

<span data-ttu-id="d204c-182">Určete, zda mají soubory datové sady řádek záhlaví.</span><span class="sxs-lookup"><span data-stu-id="d204c-182">Specify if the dataset file(s) have a header row.</span></span>
<span data-ttu-id="d204c-183">Možné hodnoty:</span><span class="sxs-lookup"><span data-stu-id="d204c-183">Possible values are:</span></span>

- `true`
- `false`

<span data-ttu-id="d204c-184">Výchozí hodnota je, `true` pokud tento argument není určen uživatelem.</span><span class="sxs-lookup"><span data-stu-id="d204c-184">The by default value is `true` if this argument is not specified by the user.</span></span>

<span data-ttu-id="d204c-185">Chcete-li použít `--label-column-name` argument, musíte mít záhlaví v souboru `--has-header` datové `true` sady a nastavit na (což je ve výchozím nastavení).</span><span class="sxs-lookup"><span data-stu-id="d204c-185">In order to use the `--label-column-name` argument, you need to have a header in the dataset file and `--has-header` set to `true` (which is by default).</span></span>

## <a name="max-exploration-time"></a><span data-ttu-id="d204c-186">Maximální doba průzkumu</span><span class="sxs-lookup"><span data-stu-id="d204c-186">Max exploration time</span></span>

<span data-ttu-id="d204c-187">`--max-exploration-time | -x`(řetězec)</span><span class="sxs-lookup"><span data-stu-id="d204c-187">`--max-exploration-time | -x` (string)</span></span>

<span data-ttu-id="d204c-188">Ve výchozím nastavení je maximální doba průzkumu 30 minut.</span><span class="sxs-lookup"><span data-stu-id="d204c-188">By default, the maximum exploration time is 30 minutes.</span></span>

<span data-ttu-id="d204c-189">Tento argument nastaví maximální čas (v sekundách) pro proces prozkoumat více školitelů a konfigurace.</span><span class="sxs-lookup"><span data-stu-id="d204c-189">This argument sets the maximum time (in seconds) for the process to explore multiple trainers and configurations.</span></span> <span data-ttu-id="d204c-190">Nakonfigurovaný čas může být překročen, pokud je zadaný čas příliš krátký (řekněme 2 sekundy) pro jednu iteraci.</span><span class="sxs-lookup"><span data-stu-id="d204c-190">The configured time may be exceeded if the provided time is too short (say 2 seconds) for a single iteration.</span></span> <span data-ttu-id="d204c-191">V tomto případě skutečný čas je požadovaný čas k vytvoření jedné konfigurace modelu v jedné iteraci.</span><span class="sxs-lookup"><span data-stu-id="d204c-191">In this case, the actual time is the required time to produce one model configuration in a single iteration.</span></span>

<span data-ttu-id="d204c-192">Potřebný čas pro iterací se může lišit v závislosti na velikosti datové sady.</span><span class="sxs-lookup"><span data-stu-id="d204c-192">The needed time for iterations can vary depending on the size of the dataset.</span></span>

## <a name="cache"></a><span data-ttu-id="d204c-193">Mezipaměť</span><span class="sxs-lookup"><span data-stu-id="d204c-193">Cache</span></span>

<span data-ttu-id="d204c-194">`--cache | -c`(řetězec)</span><span class="sxs-lookup"><span data-stu-id="d204c-194">`--cache | -c` (string)</span></span>

<span data-ttu-id="d204c-195">Pokud používáte ukládání do mezipaměti, bude celá trénovací datová sada načtena do paměti.</span><span class="sxs-lookup"><span data-stu-id="d204c-195">If you use caching, the whole training dataset will be loaded in-memory.</span></span>

<span data-ttu-id="d204c-196">U malých a středních datových sad může použití mezipaměti výrazně zlepšit výkon školení, což znamená, že doba školení může být kratší než při nepoužívání mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="d204c-196">For small and medium datasets, using cache can drastically improve the training performance, meaning the training time can be shorter than when you don't use cache.</span></span>

<span data-ttu-id="d204c-197">U velkých datových sad však načítání všech dat v paměti může mít negativní dopad, protože může dojít k nedostatku paměti.</span><span class="sxs-lookup"><span data-stu-id="d204c-197">However, for large datasets, loading all the data in memory can impact negatively since you might get out of memory.</span></span> <span data-ttu-id="d204c-198">Při trénování s velkými soubory datových sad a nepoužíváte mezipaměť, ML.NET bude streamování bloků dat z jednotky, když potřebuje načíst více dat při trénování.</span><span class="sxs-lookup"><span data-stu-id="d204c-198">When training with large dataset files and not using cache, ML.NET will be streaming chunks of data from the drive when it needs to load more data while training.</span></span>

<span data-ttu-id="d204c-199">Můžete určit tyto hodnoty:</span><span class="sxs-lookup"><span data-stu-id="d204c-199">You can specify the following values:</span></span>

<span data-ttu-id="d204c-200">`on`: Vynutí použití mezipaměti při trénování.</span><span class="sxs-lookup"><span data-stu-id="d204c-200">`on`: Forces cache to be used when training.</span></span>
<span data-ttu-id="d204c-201">`off`: Vynutí, aby se mezipaměť při trénování nepoužívala.</span><span class="sxs-lookup"><span data-stu-id="d204c-201">`off`: Forces cache not to be used when training.</span></span>
<span data-ttu-id="d204c-202">`auto`: V závislosti na heuristici automatické homl bude mezipaměť použita či nikoli.</span><span class="sxs-lookup"><span data-stu-id="d204c-202">`auto`: Depending on AutoML heuristics, the cache will be used or not.</span></span> <span data-ttu-id="d204c-203">Malé a střední datové sady obvykle používají mezipaměť a velké datové `auto` sady nebudou používat mezipaměť, pokud použijete volbu.</span><span class="sxs-lookup"><span data-stu-id="d204c-203">Usually, small/medium datasets will use cache and large datasets won't use cache if you use the `auto` choice.</span></span>

<span data-ttu-id="d204c-204">Pokud `--cache` parametr nezadáte, bude konfigurace `auto` mezipaměti použita ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="d204c-204">If you don't specify the `--cache` parameter, then the cache `auto` configuration will be used by default.</span></span>

## <a name="name"></a><span data-ttu-id="d204c-205">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="d204c-205">Name</span></span>

<span data-ttu-id="d204c-206">`--name | -N`(řetězec)</span><span class="sxs-lookup"><span data-stu-id="d204c-206">`--name | -N` (string)</span></span>

<span data-ttu-id="d204c-207">Název vytvořeného výstupního projektu nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="d204c-207">The name for the created output project or solution.</span></span> <span data-ttu-id="d204c-208">Pokud není zadán žádný `sample-{mltask}` název, bude použit název.</span><span class="sxs-lookup"><span data-stu-id="d204c-208">If no name is specified, the name `sample-{mltask}` is used.</span></span>

<span data-ttu-id="d204c-209">Soubor modelu ML.NET (. ZIP) dostane stejný název, stejně.</span><span class="sxs-lookup"><span data-stu-id="d204c-209">The ML.NET model file (.ZIP file) will get the same name, as well.</span></span>

## <a name="output-path"></a><span data-ttu-id="d204c-210">Výstupní cesta</span><span class="sxs-lookup"><span data-stu-id="d204c-210">Output path</span></span>

<span data-ttu-id="d204c-211">`--output-path | -o`(řetězec)</span><span class="sxs-lookup"><span data-stu-id="d204c-211">`--output-path | -o` (string)</span></span>

<span data-ttu-id="d204c-212">Kořenové umístění/složka pro umístění generovaného výstupu.</span><span class="sxs-lookup"><span data-stu-id="d204c-212">Root location/folder to place the generated output.</span></span> <span data-ttu-id="d204c-213">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="d204c-213">The default is the current directory.</span></span>

## <a name="verbosity"></a><span data-ttu-id="d204c-214">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="d204c-214">Verbosity</span></span>

<span data-ttu-id="d204c-215">`--verbosity | -V`(řetězec)</span><span class="sxs-lookup"><span data-stu-id="d204c-215">`--verbosity | -V` (string)</span></span>

<span data-ttu-id="d204c-216">Nastaví úroveň podrobností standardního výstupu.</span><span class="sxs-lookup"><span data-stu-id="d204c-216">Sets the verbosity level of the standard output.</span></span>

<span data-ttu-id="d204c-217">Povolené hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="d204c-217">Allowed values are:</span></span>

- `q[uiet]`
- <span data-ttu-id="d204c-218">`m[inimal]`(ve výchozím nastavení)</span><span class="sxs-lookup"><span data-stu-id="d204c-218">`m[inimal]`  (by default)</span></span>
- <span data-ttu-id="d204c-219">`diag[nostic]`(úroveň informací o protokolování)</span><span class="sxs-lookup"><span data-stu-id="d204c-219">`diag[nostic]` (logging information level)</span></span>

<span data-ttu-id="d204c-220">Ve výchozím nastavení by měl nástroj zaokreslování vykazovat minimální zpětnou vazbu (minimální) při práci, například zmínku, že funguje a pokud je to možné, kolik času zbývá nebo kolik % času je dokončeno.</span><span class="sxs-lookup"><span data-stu-id="d204c-220">By default, the CLI tool should show some minimum feedback (minimal) when working, such as mentioning that it is working and if possible how much time is left or what % of the time is completed.</span></span>

## <a name="help"></a><span data-ttu-id="d204c-221">Nápověda</span><span class="sxs-lookup"><span data-stu-id="d204c-221">Help</span></span>

`-h|--help`

<span data-ttu-id="d204c-222">Vytiskne nápovědu pro příkaz s popisem pro parametr každého příkazu.</span><span class="sxs-lookup"><span data-stu-id="d204c-222">Prints out help for the command with a description for each command's parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="d204c-223">Viz také</span><span class="sxs-lookup"><span data-stu-id="d204c-223">See also</span></span>

- [<span data-ttu-id="d204c-224">Jak nainstalovat nástroj ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="d204c-224">How to install the ML.NET CLI tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="d204c-225">Přehled ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="d204c-225">Overview of the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="d204c-226">Kurz: Analýza mínění pomocí ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="d204c-226">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="d204c-227">Telemetrie v ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="d204c-227">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
