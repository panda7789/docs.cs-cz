---
title: Reference k příkazům rozhraní příkazového řádku ML.NET
description: Přehled, ukázky a Reference k příkazu pro automatický vlak v nástroji CLI ML.NET
ms.date: 12/18/2019
ms.openlocfilehash: 5e59eba91721b26622360818a73adb07a654dc28
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636117"
---
# <a name="the-mlnet-cli-command-reference"></a><span data-ttu-id="b89e5-103">Reference k příkazům rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="b89e5-103">The ML.NET CLI command reference</span></span>

<span data-ttu-id="b89e5-104">Příkaz `auto-train` je hlavním příkazem, který poskytuje nástroj ML.NET CLI.</span><span class="sxs-lookup"><span data-stu-id="b89e5-104">The `auto-train` command is the main command provided by the ML.NET CLI tool.</span></span> <span data-ttu-id="b89e5-105">Tento příkaz umožňuje vygenerovat dobrý model ML.NET s využitím automatizovaného strojového učení (AutoML) a také ukázkový C# kód pro spuštění nebo určení skóre modelu.</span><span class="sxs-lookup"><span data-stu-id="b89e5-105">The command allows you to generate a good quality ML.NET model using automated machine learning (AutoML) as well as the the example C# code to run/score that model.</span></span> <span data-ttu-id="b89e5-106">Kromě toho C# kód pro výuku modelu je vygenerován pro vás, abyste mohli prozkoumat algoritmus a nastavení modelu.</span><span class="sxs-lookup"><span data-stu-id="b89e5-106">In addition, the C# code to train the model is generated for you to research the algorithm and settings of the model.</span></span>

> [!NOTE]
> <span data-ttu-id="b89e5-107">Toto téma odkazuje na ML.NET CLI a ML.NET AutoML, které jsou momentálně ve verzi Preview, a materiál může být změněn.</span><span class="sxs-lookup"><span data-stu-id="b89e5-107">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="overview"></a><span data-ttu-id="b89e5-108">Přehled</span><span class="sxs-lookup"><span data-stu-id="b89e5-108">Overview</span></span>

<span data-ttu-id="b89e5-109">Příklad použití:</span><span class="sxs-lookup"><span data-stu-id="b89e5-109">Example usage:</span></span>

```console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

<span data-ttu-id="b89e5-110">Příkaz `mlnet auto-train` generuje následující prostředky:</span><span class="sxs-lookup"><span data-stu-id="b89e5-110">The `mlnet auto-train` command generates the following assets:</span></span>

- <span data-ttu-id="b89e5-111">Serializovaný model. zip ("nejlepší model") je připravený k použití.</span><span class="sxs-lookup"><span data-stu-id="b89e5-111">A serialized model .zip ("best model") ready to use.</span></span>
- <span data-ttu-id="b89e5-112">C#kód, který se má spustit, nebo vyhodnotit skóre generovaný model.</span><span class="sxs-lookup"><span data-stu-id="b89e5-112">C# code to run/score that generated model.</span></span>
- <span data-ttu-id="b89e5-113">C#kód s školicím kódem, který slouží ke generování tohoto modelu.</span><span class="sxs-lookup"><span data-stu-id="b89e5-113">C# code with the training code used to generate that model.</span></span>

<span data-ttu-id="b89e5-114">První dva prostředky lze použít přímo v aplikacích pro koncové uživatele (ASP.NET Core webové aplikace, služby, aplikace klasické pracovní plochy a další) k tomu, aby předpovědi s modelem.</span><span class="sxs-lookup"><span data-stu-id="b89e5-114">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app and more) to make predictions with the model.</span></span>

<span data-ttu-id="b89e5-115">Třetí Asset a školicí kód vám ukáže, co ML.NET kód rozhraní API používal CLI k výuce vygenerovaného modelu, takže můžete prozkoumat konkrétní algoritmus a nastavení modelu.</span><span class="sxs-lookup"><span data-stu-id="b89e5-115">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate the specific algorithm and settings of the model.</span></span>

## <a name="examples"></a><span data-ttu-id="b89e5-116">Příklady</span><span class="sxs-lookup"><span data-stu-id="b89e5-116">Examples</span></span>

<span data-ttu-id="b89e5-117">Nejjednodušší příkaz CLI pro problém binární klasifikace (AutoML odvodí většinu konfigurace z poskytnutých dat):</span><span class="sxs-lookup"><span data-stu-id="b89e5-117">The simplest CLI command for a binary classification problem (AutoML infers most of the configuration from the provided data):</span></span>

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

<span data-ttu-id="b89e5-118">Další jednoduchý příkaz CLI pro problém regrese:</span><span class="sxs-lookup"><span data-stu-id="b89e5-118">Another simple CLI command for a regression problem:</span></span>

``` console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

<span data-ttu-id="b89e5-119">Vytvoření a výuka modelu binární klasifikace s datovou sadou vlaků, testovací datovou sadou a dalšími explicitními argumenty přizpůsobení:</span><span class="sxs-lookup"><span data-stu-id="b89e5-119">Create and train a binary-classification model with a train dataset, a test dataset, and further customization explicit arguments:</span></span>

```console
mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="command-options"></a><span data-ttu-id="b89e5-120">Možnosti příkazu</span><span class="sxs-lookup"><span data-stu-id="b89e5-120">Command options</span></span>

<span data-ttu-id="b89e5-121">`mlnet auto-train` vlacích v závislosti na zadané datové sadě a nakonec vybírá nejlepší model, uloží ho jako serializovaný soubor. zip a vygeneruje související C# kód pro bodování a školení.</span><span class="sxs-lookup"><span data-stu-id="b89e5-121">`mlnet auto-train` trains multiple models based on the provided dataset and finally selects the best model, saves it as a serialized .zip file plus generates related C# code for scoring and training.</span></span>

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

<span data-ttu-id="b89e5-122">Neplatné možnosti vstupu způsobí, že nástroj rozhraní příkazového řádku vygeneruje seznam platných vstupů a chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="b89e5-122">Invalid input options cause the CLI tool to emit a list of valid inputs and an error message.</span></span>

## <a name="task"></a><span data-ttu-id="b89e5-123">Úloha</span><span class="sxs-lookup"><span data-stu-id="b89e5-123">Task</span></span>

<span data-ttu-id="b89e5-124">`--task | --mltask | -T` (String)</span><span class="sxs-lookup"><span data-stu-id="b89e5-124">`--task | --mltask | -T` (string)</span></span>

<span data-ttu-id="b89e5-125">Jeden řetězec, který poskytuje problém k řešení ML.</span><span class="sxs-lookup"><span data-stu-id="b89e5-125">A single string providing the ML problem to solve.</span></span> <span data-ttu-id="b89e5-126">Například kterákoli z následujících úloh (rozhraní příkazového řádku bude nakonec podporovat všechny úlohy podporované v AutoML):</span><span class="sxs-lookup"><span data-stu-id="b89e5-126">For instance, any of the following tasks (The CLI will eventually support all tasks supported in AutoML):</span></span>

- <span data-ttu-id="b89e5-127">`regression` – vyberte, jestli se má pro předpověď číselné hodnoty použít model ML.</span><span class="sxs-lookup"><span data-stu-id="b89e5-127">`regression` - Choose if the ML Model will be used to predict a numeric value</span></span>
- <span data-ttu-id="b89e5-128">`binary-classification` – vyberte, jestli má výsledek modelu ML dvě možné kategorií logické hodnoty (0 nebo 1).</span><span class="sxs-lookup"><span data-stu-id="b89e5-128">`binary-classification` - Choose if the ML Model result has two possible categorical boolean values (0 or 1).</span></span>
- <span data-ttu-id="b89e5-129">`multiclass-classification` – vyberte, jestli má výsledek modelu ML více kategorií možných hodnot.</span><span class="sxs-lookup"><span data-stu-id="b89e5-129">`multiclass-classification` - Choose if the ML Model result has multiple categorical possible values.</span></span>

<span data-ttu-id="b89e5-130">V tomto argumentu by měla být uvedena pouze jedna úloha ML.</span><span class="sxs-lookup"><span data-stu-id="b89e5-130">Only one ML task should be provided in this argument.</span></span>

## <a name="dataset"></a><span data-ttu-id="b89e5-131">Datová sada</span><span class="sxs-lookup"><span data-stu-id="b89e5-131">Dataset</span></span>

<span data-ttu-id="b89e5-132">`--dataset | -d` (String)</span><span class="sxs-lookup"><span data-stu-id="b89e5-132">`--dataset | -d` (string)</span></span>

<span data-ttu-id="b89e5-133">Tento argument poskytuje cestu k jedné z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="b89e5-133">This argument provides the filepath to either one of the following options:</span></span>

- <span data-ttu-id="b89e5-134">Odpověď *: soubor celé datové sady:* Pokud tato možnost používá a uživatel neposkytuje `--test-dataset` a `--validation-dataset`, pak se k ověřování modelu použije interní ověřování (k přeložení atd.) nebo automatizované přístupy k rozdělení dat.</span><span class="sxs-lookup"><span data-stu-id="b89e5-134">*A: The whole dataset file:* If using this option and the user is not providing `--test-dataset` and `--validation-dataset`, then cross-validation (k-fold, etc.) or automated data split approaches will be used internally for validating the model.</span></span> <span data-ttu-id="b89e5-135">V takovém případě bude muset uživatel pouze zadat FilePath pro datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="b89e5-135">In that case, the user will just need to provide the dataset filepath.</span></span>

- <span data-ttu-id="b89e5-136">*B: soubor datové sady školení:* Pokud uživatel také poskytuje datové sady pro ověřování modelu (pomocí `--test-dataset` a volitelně `--validation-dataset`), pak argument `--dataset` znamená, že má pouze "školicí sadu".</span><span class="sxs-lookup"><span data-stu-id="b89e5-136">*B: The training dataset file:* If the user is also providing datasets for model validation (using `--test-dataset` and optionally `--validation-dataset`), then the `--dataset` argument means to only have the "training dataset".</span></span> <span data-ttu-id="b89e5-137">Například při použití přístupu 80%-20% k ověření kvality modelu a získání metrik přesnosti bude mít "školicí datová sada" 80% dat a "testovací sada" bude obsahovat 20% dat.</span><span class="sxs-lookup"><span data-stu-id="b89e5-137">For example, when using an 80% - 20% approach to validate the quality of the model and to obtain accuracy metrics, the "training dataset" will have 80% of the data and the "test dataset" would have 20% of the data.</span></span>

## <a name="test-dataset"></a><span data-ttu-id="b89e5-138">Testovací datová sada</span><span class="sxs-lookup"><span data-stu-id="b89e5-138">Test dataset</span></span>

<span data-ttu-id="b89e5-139">`--test-dataset | -t` (String)</span><span class="sxs-lookup"><span data-stu-id="b89e5-139">`--test-dataset | -t` (string)</span></span>

<span data-ttu-id="b89e5-140">Cesta k souboru, který odkazuje na soubor sady dat testu, například při použití 80%-20% přístupu při pravidelném ověřování, aby bylo možné získat metriky přesnosti.</span><span class="sxs-lookup"><span data-stu-id="b89e5-140">File path pointing to the test dataset file, for example when using an 80% - 20% approach when making regular validations to obtain accuracy metrics.</span></span>

<span data-ttu-id="b89e5-141">Pokud používáte `--test-dataset`, vyžaduje se také `--dataset`.</span><span class="sxs-lookup"><span data-stu-id="b89e5-141">If using `--test-dataset`, then `--dataset` is also required.</span></span>

<span data-ttu-id="b89e5-142">Argument `--test-dataset` je nepovinný, pokud se nepoužívá--ověření-DataSet.</span><span class="sxs-lookup"><span data-stu-id="b89e5-142">The `--test-dataset` argument is optional unless the --validation-dataset is used.</span></span> <span data-ttu-id="b89e5-143">V takovém případě musí uživatel použít tři argumenty.</span><span class="sxs-lookup"><span data-stu-id="b89e5-143">In that case, the user must use the three arguments.</span></span>

## <a name="validation-dataset"></a><span data-ttu-id="b89e5-144">Ověření datové sady</span><span class="sxs-lookup"><span data-stu-id="b89e5-144">Validation dataset</span></span>

<span data-ttu-id="b89e5-145">`--validation-dataset | -v` (String)</span><span class="sxs-lookup"><span data-stu-id="b89e5-145">`--validation-dataset | -v` (string)</span></span>

<span data-ttu-id="b89e5-146">Cesta k souboru, který odkazuje na soubor datové sady ověření.</span><span class="sxs-lookup"><span data-stu-id="b89e5-146">File path pointing to the validation dataset file.</span></span> <span data-ttu-id="b89e5-147">Datová sada ověření je volitelná, v každém případě.</span><span class="sxs-lookup"><span data-stu-id="b89e5-147">The validation dataset is optional, in any case.</span></span>

<span data-ttu-id="b89e5-148">Pokud používáte `validation dataset`, mělo by se jednat o toto chování:</span><span class="sxs-lookup"><span data-stu-id="b89e5-148">If using a `validation dataset`, the behavior should be:</span></span>

- <span data-ttu-id="b89e5-149">Jsou také požadovány argumenty `test-dataset` a `--dataset`.</span><span class="sxs-lookup"><span data-stu-id="b89e5-149">The `test-dataset` and `--dataset` arguments are also required.</span></span>

- <span data-ttu-id="b89e5-150">Datová sada `validation-dataset` slouží k odhadu chyby předpovědi pro výběr modelu.</span><span class="sxs-lookup"><span data-stu-id="b89e5-150">The `validation-dataset` dataset is used to estimate prediction error for model selection.</span></span>

- <span data-ttu-id="b89e5-151">`test-dataset` se používá pro vyhodnocení chyby generalizace finálního zvoleného modelu.</span><span class="sxs-lookup"><span data-stu-id="b89e5-151">The `test-dataset` is used for assessment of the generalization error of the final chosen model.</span></span> <span data-ttu-id="b89e5-152">V ideálním případě by měl být testovací sada uchovávána v "trezoru" a musí být uvedena pouze na konci analýzy dat.</span><span class="sxs-lookup"><span data-stu-id="b89e5-152">Ideally, the test set should be kept in a “vault,” and be brought out only at the end of the data analysis.</span></span>

<span data-ttu-id="b89e5-153">V podstatě při použití `validation dataset` a `test dataset`je fáze ověření rozdělená na dvě části:</span><span class="sxs-lookup"><span data-stu-id="b89e5-153">Basically, when using a `validation dataset` plus the `test dataset`, the validation phase is split into two parts:</span></span>

1. <span data-ttu-id="b89e5-154">V první části se jenom podíváte na vaše modely a vyberete nejlepší způsob, jak pomocí ověřovacích dat (= ověřování) vybrat nejvhodnější přístup.</span><span class="sxs-lookup"><span data-stu-id="b89e5-154">In the first part, you just look at your models and select the best performing approach using the validation data (=validation)</span></span>
2. <span data-ttu-id="b89e5-155">Pak odhadnete přesnost vybraného přístupu (= test).</span><span class="sxs-lookup"><span data-stu-id="b89e5-155">Then you estimate the accuracy of the selected approach (=test).</span></span>

<span data-ttu-id="b89e5-156">Oddělení dat by proto mohlo být 80/10/10 nebo 75/15/10.</span><span class="sxs-lookup"><span data-stu-id="b89e5-156">Hence, the separation of data could be 80/10/10 or 75/15/10.</span></span> <span data-ttu-id="b89e5-157">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b89e5-157">For example:</span></span>

- <span data-ttu-id="b89e5-158">soubor `training-dataset` by měl mít 75% dat.</span><span class="sxs-lookup"><span data-stu-id="b89e5-158">`training-dataset` file should have 75% of the data.</span></span>
- <span data-ttu-id="b89e5-159">soubor `validation-dataset` by měl mít 15% dat.</span><span class="sxs-lookup"><span data-stu-id="b89e5-159">`validation-dataset` file should have 15% of the data.</span></span>
- <span data-ttu-id="b89e5-160">soubor `test-dataset` by měl mít 10% dat.</span><span class="sxs-lookup"><span data-stu-id="b89e5-160">`test-dataset` file should have 10% of the data.</span></span>

<span data-ttu-id="b89e5-161">V každém případě se tyto procentní podíly určí uživatelem pomocí rozhraní příkazového řádku, který poskytne soubory, které jsou už rozdělené.</span><span class="sxs-lookup"><span data-stu-id="b89e5-161">In any case, those percentages will be decided by the user using the CLI who will provide the files already split.</span></span>

## <a name="label-column-name"></a><span data-ttu-id="b89e5-162">Název sloupce popisku</span><span class="sxs-lookup"><span data-stu-id="b89e5-162">Label column name</span></span>

<span data-ttu-id="b89e5-163">`--label-column-name | -n` (String)</span><span class="sxs-lookup"><span data-stu-id="b89e5-163">`--label-column-name | -n` (string)</span></span>

<span data-ttu-id="b89e5-164">Pomocí tohoto argumentu je možné zadat konkrétní sloupec cíl/cíl (proměnnou, kterou chcete odhadnout) pomocí názvu sloupce nastaveného v záhlaví datové sady.</span><span class="sxs-lookup"><span data-stu-id="b89e5-164">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's name set in the dataset's header.</span></span>

<span data-ttu-id="b89e5-165">Tento argument se používá jenom pro úlohy pod dohledem ML, jako je například *problém s klasifikací*.</span><span class="sxs-lookup"><span data-stu-id="b89e5-165">This argument is used only for supervised ML tasks such as a *classification problem*.</span></span> <span data-ttu-id="b89e5-166">Nedá se použít pro úlohy s nekontrolovanými ML, jako je například *clustering*.</span><span class="sxs-lookup"><span data-stu-id="b89e5-166">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

## <a name="label-column-index"></a><span data-ttu-id="b89e5-167">Index sloupce popisku</span><span class="sxs-lookup"><span data-stu-id="b89e5-167">Label column index</span></span>

<span data-ttu-id="b89e5-168">`--label-column-index | -i` (int)</span><span class="sxs-lookup"><span data-stu-id="b89e5-168">`--label-column-index | -i` (int)</span></span>

<span data-ttu-id="b89e5-169">Pomocí tohoto argumentu se dá určit konkrétní sloupec cíl/cíl (proměnná, kterou chcete předpovědět), pomocí číselného indexu sloupce v souboru datové sady (hodnoty indexu sloupce začínají na 1).</span><span class="sxs-lookup"><span data-stu-id="b89e5-169">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's numeric index in the dataset's file (The column index values start at 1).</span></span>

<span data-ttu-id="b89e5-170">*Poznámka:* Pokud uživatel používá taky `--label-column-name`, `--label-column-name` je ten, který se používá.</span><span class="sxs-lookup"><span data-stu-id="b89e5-170">*Note:* If the user is also using the `--label-column-name`, the `--label-column-name` is the one being used.</span></span>

<span data-ttu-id="b89e5-171">Tento argument se používá jenom pro úlohu pod dohledem ML, jako je například *problém s klasifikací*.</span><span class="sxs-lookup"><span data-stu-id="b89e5-171">This argument is used only for supervised ML task such as a *classification problem*.</span></span> <span data-ttu-id="b89e5-172">Nedá se použít pro úlohy s nekontrolovanými ML, jako je například *clustering*.</span><span class="sxs-lookup"><span data-stu-id="b89e5-172">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

## <a name="ignore-columns"></a><span data-ttu-id="b89e5-173">Ignorovat sloupce</span><span class="sxs-lookup"><span data-stu-id="b89e5-173">Ignore columns</span></span>

<span data-ttu-id="b89e5-174">`--ignore-columns | -I` (String)</span><span class="sxs-lookup"><span data-stu-id="b89e5-174">`--ignore-columns | -I` (string)</span></span>

<span data-ttu-id="b89e5-175">Pomocí tohoto argumentu můžete ignorovat existující sloupce v souboru DataSet, aby nebyly načteny a použity v školicích procesech.</span><span class="sxs-lookup"><span data-stu-id="b89e5-175">With this argument, you can ignore existing columns in the dataset file so they are not loaded and used by the training processes.</span></span>

<span data-ttu-id="b89e5-176">Zadejte názvy sloupců, které chcete ignorovat.</span><span class="sxs-lookup"><span data-stu-id="b89e5-176">Specify the columns names that you want to ignore.</span></span> <span data-ttu-id="b89e5-177">K oddělení více názvů sloupců použijte ', ' (čárka s mezerou) nebo ' ' (mezera).</span><span class="sxs-lookup"><span data-stu-id="b89e5-177">Use ', ' (comma with space) or ' ' (space) to separate multiple column names.</span></span> <span data-ttu-id="b89e5-178">Můžete použít uvozovky pro názvy sloupců obsahující prázdné znaky (například "přihlášen").</span><span class="sxs-lookup"><span data-stu-id="b89e5-178">You can use quotes for column names containing whitespace (e.g. "logged in").</span></span>

<span data-ttu-id="b89e5-179">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b89e5-179">Example:</span></span>

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a><span data-ttu-id="b89e5-180">Má hlavičku</span><span class="sxs-lookup"><span data-stu-id="b89e5-180">Has header</span></span>

<span data-ttu-id="b89e5-181">`--has-header | -h` (bool)</span><span class="sxs-lookup"><span data-stu-id="b89e5-181">`--has-header | -h` (bool)</span></span>

<span data-ttu-id="b89e5-182">Určete, zda mají soubory DataSet řádek záhlaví.</span><span class="sxs-lookup"><span data-stu-id="b89e5-182">Specify if the dataset file(s) have a header row.</span></span>
<span data-ttu-id="b89e5-183">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="b89e5-183">Possible values are:</span></span>

- `true`
- `false`

<span data-ttu-id="b89e5-184">Výchozí hodnota je `true`, pokud tento argument není zadán uživatelem.</span><span class="sxs-lookup"><span data-stu-id="b89e5-184">The by default value is `true` if this argument is not specified by the user.</span></span>

<span data-ttu-id="b89e5-185">Aby bylo možné použít argument `--label-column-name`, musíte mít v souboru DataSet hlavičku a `--has-header` nastavit na `true` (což je ve výchozím nastavení).</span><span class="sxs-lookup"><span data-stu-id="b89e5-185">In order to use the `--label-column-name` argument, you need to have a header in the dataset file and `--has-header` set to `true` (which is by default).</span></span>

## <a name="max-exploration-time"></a><span data-ttu-id="b89e5-186">Maximální doba průzkumu</span><span class="sxs-lookup"><span data-stu-id="b89e5-186">Max exploration time</span></span>

<span data-ttu-id="b89e5-187">`--max-exploration-time | -x` (String)</span><span class="sxs-lookup"><span data-stu-id="b89e5-187">`--max-exploration-time | -x` (string)</span></span>

<span data-ttu-id="b89e5-188">Ve výchozím nastavení je maximální doba průzkumu 30 minut.</span><span class="sxs-lookup"><span data-stu-id="b89e5-188">By default, the maximum exploration time is 30 minutes.</span></span>

<span data-ttu-id="b89e5-189">Tento argument nastaví maximální dobu (v sekundách), po kterou má proces prozkoumat více školitelů a konfigurací.</span><span class="sxs-lookup"><span data-stu-id="b89e5-189">This argument sets the maximum time (in seconds) for the process to explore multiple trainers and configurations.</span></span> <span data-ttu-id="b89e5-190">Nakonfigurovaný čas může být překročen, pokud je zadaný čas příliš krátký (řekněme 2 sekundy) pro jednu iteraci.</span><span class="sxs-lookup"><span data-stu-id="b89e5-190">The configured time may be exceeded if the provided time is too short (say 2 seconds) for a single iteration.</span></span> <span data-ttu-id="b89e5-191">V tomto případě je skutečný čas potřebný čas k vytvoření jedné konfigurace modelu v rámci jedné iterace.</span><span class="sxs-lookup"><span data-stu-id="b89e5-191">In this case, the actual time is the required time to produce one model configuration in a single iteration.</span></span>

<span data-ttu-id="b89e5-192">Čas potřebný pro iterace se může lišit v závislosti na velikosti datové sady.</span><span class="sxs-lookup"><span data-stu-id="b89e5-192">The needed time for iterations can vary depending on the size of the dataset.</span></span>

## <a name="cache"></a><span data-ttu-id="b89e5-193">Mezipaměť</span><span class="sxs-lookup"><span data-stu-id="b89e5-193">Cache</span></span>

<span data-ttu-id="b89e5-194">`--cache | -c` (String)</span><span class="sxs-lookup"><span data-stu-id="b89e5-194">`--cache | -c` (string)</span></span>

<span data-ttu-id="b89e5-195">Pokud použijete ukládání do mezipaměti, načte se celá datová sada školení v paměti.</span><span class="sxs-lookup"><span data-stu-id="b89e5-195">If you use caching, the whole training dataset will be loaded in-memory.</span></span>

<span data-ttu-id="b89e5-196">V případě malých a středně velkých datových sad může použití mezipaměti významně zlepšit výkon školení, což znamená, že doba přípravy může být kratší, než když mezipaměť nepoužíváte.</span><span class="sxs-lookup"><span data-stu-id="b89e5-196">For small and medium datasets, using cache can drastically improve the training performance, meaning the training time can be shorter than when you don't use cache.</span></span>

<span data-ttu-id="b89e5-197">U rozsáhlých datových sad ale načítání všech dat v paměti může negativně ovlivnit vzhledem k tomu, že může dojít k dostatku paměti.</span><span class="sxs-lookup"><span data-stu-id="b89e5-197">However, for large datasets, loading all the data in memory can impact negatively since you might get out of memory.</span></span> <span data-ttu-id="b89e5-198">Při školení s rozsáhlými soubory DataSet a nepoužíváte-li mezipaměť, bude ML.NET streamovat datové bloky dat z disku, když potřebuje načíst více dat během školení.</span><span class="sxs-lookup"><span data-stu-id="b89e5-198">When training with large dataset files and not using cache, ML.NET will be streaming chunks of data from the drive when it needs to load more data while training.</span></span>

<span data-ttu-id="b89e5-199">Můžete určit tyto hodnoty:</span><span class="sxs-lookup"><span data-stu-id="b89e5-199">You can specify the following values:</span></span>

<span data-ttu-id="b89e5-200">`on`: Vynutí použití mezipaměti při školení.</span><span class="sxs-lookup"><span data-stu-id="b89e5-200">`on`: Forces cache to be used when training.</span></span>
<span data-ttu-id="b89e5-201">`off`: vynutí, aby se mezipaměť nepoužívala při výuce.</span><span class="sxs-lookup"><span data-stu-id="b89e5-201">`off`: Forces cache not to be used when training.</span></span>
<span data-ttu-id="b89e5-202">`auto`: v závislosti na heuristikách AutoML se mezipaměť použije nebo ne.</span><span class="sxs-lookup"><span data-stu-id="b89e5-202">`auto`: Depending on AutoML heuristics, the cache will be used or not.</span></span> <span data-ttu-id="b89e5-203">Malé nebo střední datové sady budou obvykle používat mezipaměť a velké datové sady nebudou používat mezipaměť, pokud použijete možnost `auto`.</span><span class="sxs-lookup"><span data-stu-id="b89e5-203">Usually, small/medium datasets will use cache and large datasets won't use cache if you use the `auto` choice.</span></span>

<span data-ttu-id="b89e5-204">Pokud parametr `--cache` nezadáte, použije se ve výchozím nastavení mezipaměť `auto` konfigurace.</span><span class="sxs-lookup"><span data-stu-id="b89e5-204">If you don't specify the `--cache` parameter, then the cache `auto` configuration will be used by default.</span></span>

## <a name="name"></a><span data-ttu-id="b89e5-205">Name</span><span class="sxs-lookup"><span data-stu-id="b89e5-205">Name</span></span>

<span data-ttu-id="b89e5-206">`--name | -N` (String)</span><span class="sxs-lookup"><span data-stu-id="b89e5-206">`--name | -N` (string)</span></span>

<span data-ttu-id="b89e5-207">Název vytvořeného výstupního projektu nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="b89e5-207">The name for the created output project or solution.</span></span> <span data-ttu-id="b89e5-208">Pokud název nezadáte, použije se název `sample-{mltask}`.</span><span class="sxs-lookup"><span data-stu-id="b89e5-208">If no name is specified, the name `sample-{mltask}` is used.</span></span>

<span data-ttu-id="b89e5-209">Soubor modelu ML.NET (. Soubor ZIP) bude mít stejný název i.</span><span class="sxs-lookup"><span data-stu-id="b89e5-209">The ML.NET model file (.ZIP file) will get the same name, as well.</span></span>

## <a name="output-path"></a><span data-ttu-id="b89e5-210">Výstupní cesta</span><span class="sxs-lookup"><span data-stu-id="b89e5-210">Output path</span></span>

<span data-ttu-id="b89e5-211">`--output-path | -o` (String)</span><span class="sxs-lookup"><span data-stu-id="b89e5-211">`--output-path | -o` (string)</span></span>

<span data-ttu-id="b89e5-212">Kořenové umístění/složka, do které se umístí vygenerovaný výstup</span><span class="sxs-lookup"><span data-stu-id="b89e5-212">Root location/folder to place the generated output.</span></span> <span data-ttu-id="b89e5-213">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="b89e5-213">The default is the current directory.</span></span>

## <a name="verbosity"></a><span data-ttu-id="b89e5-214">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b89e5-214">Verbosity</span></span>

<span data-ttu-id="b89e5-215">`--verbosity | -V` (String)</span><span class="sxs-lookup"><span data-stu-id="b89e5-215">`--verbosity | -V` (string)</span></span>

<span data-ttu-id="b89e5-216">Nastaví úroveň podrobností standardního výstupu.</span><span class="sxs-lookup"><span data-stu-id="b89e5-216">Sets the verbosity level of the standard output.</span></span>

<span data-ttu-id="b89e5-217">Povolené hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="b89e5-217">Allowed values are:</span></span>

- `q[uiet]`
- <span data-ttu-id="b89e5-218">`m[inimal]` (ve výchozím nastavení)</span><span class="sxs-lookup"><span data-stu-id="b89e5-218">`m[inimal]`  (by default)</span></span>
- <span data-ttu-id="b89e5-219">`diag[nostic]` (úroveň informací o protokolování)</span><span class="sxs-lookup"><span data-stu-id="b89e5-219">`diag[nostic]` (logging information level)</span></span>

<span data-ttu-id="b89e5-220">Ve výchozím nastavení by měl nástroj rozhraní příkazového řádku při práci zobrazit určitou minimální odezvu (minimální), jako je třeba zmínku o tom, že funguje, a pokud je to možné, kolik času zbývá nebo kolik času bylo dokončeno.</span><span class="sxs-lookup"><span data-stu-id="b89e5-220">By default, the CLI tool should show some minimum feedback (minimal) when working, such as mentioning that it is working and if possible how much time is left or what % of the time is completed.</span></span>

## <a name="help"></a><span data-ttu-id="b89e5-221">Nápověda</span><span class="sxs-lookup"><span data-stu-id="b89e5-221">Help</span></span>

`-h|--help`

<span data-ttu-id="b89e5-222">Vytiskne nápovědu pro příkaz s popisem pro každý parametr příkazu.</span><span class="sxs-lookup"><span data-stu-id="b89e5-222">Prints out help for the command with a description for each command's parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="b89e5-223">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b89e5-223">See also</span></span>

- [<span data-ttu-id="b89e5-224">Postup instalace nástroje ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="b89e5-224">How to install the ML.NET CLI tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="b89e5-225">Přehled rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="b89e5-225">Overview of the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="b89e5-226">Kurz: analýza mínění pomocí rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="b89e5-226">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="b89e5-227">Telemetrie v ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="b89e5-227">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
