---
title: Reference k příkazům rozhraní příkazového řádku ML.NET
description: Přehled, ukázky a Reference k příkazu pro automatický vlak v nástroji CLI ML.NET
ms.date: 06/03/2020
ms.custom: mlnet-tooling
ms.openlocfilehash: 397f6fda8554024624b3ef630856dc8eca9696b2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594540"
---
# <a name="the-mlnet-cli-command-reference"></a><span data-ttu-id="53b33-103">Reference k příkazům rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="53b33-103">The ML.NET CLI command reference</span></span>

<span data-ttu-id="53b33-104">`classification`Příkazy, `regression` a `recommendation` jsou hlavní příkazy, které poskytuje nástroj ml.NET CLI.</span><span class="sxs-lookup"><span data-stu-id="53b33-104">The `classification`, `regression`, and `recommendation` commands are the main commands provided by the ML.NET CLI tool.</span></span> <span data-ttu-id="53b33-105">Tyto příkazy umožňují generovat kvalitní modely ML.NET pro klasifikace, regrese a modely doporučení pomocí automatizovaného strojového učení (AutoML) a také ukázkového kódu jazyka C# ke spuštění nebo určení skóre modelu.</span><span class="sxs-lookup"><span data-stu-id="53b33-105">These commands allow you to generate good quality ML.NET models for classification, regression, and recommendation models using automated machine learning (AutoML) as well as the example C# code to run/score that model.</span></span> <span data-ttu-id="53b33-106">Kromě toho kód jazyka C# pro výuku modelu je vygenerován pro vás, abyste mohli prozkoumat algoritmus a nastavení modelu.</span><span class="sxs-lookup"><span data-stu-id="53b33-106">In addition, the C# code to train the model is generated for you to research the algorithm and settings of the model.</span></span>

> [!NOTE]
> <span data-ttu-id="53b33-107">Toto téma odkazuje na ML.NET CLI a ML.NET AutoML, které jsou momentálně ve verzi Preview, a materiál může být změněn.</span><span class="sxs-lookup"><span data-stu-id="53b33-107">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="overview"></a><span data-ttu-id="53b33-108">Přehled</span><span class="sxs-lookup"><span data-stu-id="53b33-108">Overview</span></span>

<span data-ttu-id="53b33-109">Příklad použití:</span><span class="sxs-lookup"><span data-stu-id="53b33-109">Example usage:</span></span>

```console
mlnet regression --dataset "cars.csv" --label-col price
```

<span data-ttu-id="53b33-110">`mlnet`Příkazy úkolu ml ( `classification` , a `regression` `recommendation` ) generují následující prostředky:</span><span class="sxs-lookup"><span data-stu-id="53b33-110">The `mlnet` ML task commands (`classification`, `regression`, and `recommendation`) generate the following assets:</span></span>

- <span data-ttu-id="53b33-111">Serializovaný model. zip ("nejlepší model") je připravený k použití.</span><span class="sxs-lookup"><span data-stu-id="53b33-111">A serialized model .zip ("best model") ready to use.</span></span>
- <span data-ttu-id="53b33-112">Kód jazyka C#, který se má spustit, nebo určit skóre vygenerovaného modelu</span><span class="sxs-lookup"><span data-stu-id="53b33-112">C# code to run/score that generated model.</span></span>
- <span data-ttu-id="53b33-113">Kód jazyka C# s školicím kódem, který se používá ke generování tohoto modelu.</span><span class="sxs-lookup"><span data-stu-id="53b33-113">C# code with the training code used to generate that model.</span></span>

<span data-ttu-id="53b33-114">První dva prostředky lze použít přímo v aplikacích pro koncové uživatele (ASP.NET Core webové aplikace, služby, aplikace klasické pracovní plochy a další) k tomu, aby předpovědi s modelem.</span><span class="sxs-lookup"><span data-stu-id="53b33-114">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app and more) to make predictions with the model.</span></span>

<span data-ttu-id="53b33-115">Třetí Asset a školicí kód vám ukáže, co ML.NET kód rozhraní API používal CLI k výuce vygenerovaného modelu, takže můžete prozkoumat konkrétní algoritmus a nastavení modelu.</span><span class="sxs-lookup"><span data-stu-id="53b33-115">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate the specific algorithm and settings of the model.</span></span>

## <a name="examples"></a><span data-ttu-id="53b33-116">Příklady</span><span class="sxs-lookup"><span data-stu-id="53b33-116">Examples</span></span>

<span data-ttu-id="53b33-117">Nejjednodušší příkaz CLI pro problém klasifikace (AutoML odvodí většinu konfigurace z poskytnutých dat):</span><span class="sxs-lookup"><span data-stu-id="53b33-117">The simplest CLI command for a classification problem (AutoML infers most of the configuration from the provided data):</span></span>

```console
mlnet classification --dataset "customer-feedback.tsv" --label-col Sentiment
```

<span data-ttu-id="53b33-118">Další jednoduchý příkaz CLI pro problém regrese:</span><span class="sxs-lookup"><span data-stu-id="53b33-118">Another simple CLI command for a regression problem:</span></span>

``` console
mlnet regression --dataset "cars.csv" --label-col Price
```

<span data-ttu-id="53b33-119">Vytvoření a výuka klasifikačního modelu s datovou sadou vlaků, testovací datovou sadou a dalšími explicitními argumenty přizpůsobení:</span><span class="sxs-lookup"><span data-stu-id="53b33-119">Create and train a classification model with a train dataset, a test dataset, and further customization explicit arguments:</span></span>

```console
mlnet classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-col "InsuranceRisk" --cache on --train-time 600
```

## <a name="command-options"></a><span data-ttu-id="53b33-120">Možnosti příkazu</span><span class="sxs-lookup"><span data-stu-id="53b33-120">Command options</span></span>

<span data-ttu-id="53b33-121">`mlnet`Příkazy úkolu ml ( `classification` , `regression` a `recommendation` ) procházejí několik modelů založených na zadaných možnostech DataSet a ml.NET CLI.</span><span class="sxs-lookup"><span data-stu-id="53b33-121">The `mlnet` ML task commands (`classification`, `regression`, and `recommendation`) train multiple models based on the provided dataset and ML.NET CLI options.</span></span> <span data-ttu-id="53b33-122">Tyto příkazy také vyberou nejlepší model, uloží model jako serializovaný soubor. zip a vygenerují související kód jazyka C# pro bodování a školení.</span><span class="sxs-lookup"><span data-stu-id="53b33-122">These commands also select the best model, save the model as a serialized .zip file, and generate related C# code for scoring and training.</span></span>

### <a name="classification-options"></a><span data-ttu-id="53b33-123">Možnosti klasifikace</span><span class="sxs-lookup"><span data-stu-id="53b33-123">Classification options</span></span>

<span data-ttu-id="53b33-124">Běh `mlnet classification` bude zaškolit klasifikační model.</span><span class="sxs-lookup"><span data-stu-id="53b33-124">Running `mlnet classification` will train a classification model.</span></span> <span data-ttu-id="53b33-125">Tento příkaz vyberte, pokud chcete, aby model ML kategorizoval data do dvou nebo více tříd (např. mínění analýza).</span><span class="sxs-lookup"><span data-stu-id="53b33-125">Choose this command if you want an ML Model to categorize data into 2 or more classes (e.g. sentiment analysis).</span></span>

```console
mlnet classification

--dataset <path> (REQUIRED)

--label-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--ignore-cols <cols>

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

### <a name="regression-options"></a><span data-ttu-id="53b33-126">Možnosti regrese</span><span class="sxs-lookup"><span data-stu-id="53b33-126">Regression options</span></span>

<span data-ttu-id="53b33-127">Běh `mlnet regression` bude mít regresní model.</span><span class="sxs-lookup"><span data-stu-id="53b33-127">Running `mlnet regression` will train a regression model.</span></span> <span data-ttu-id="53b33-128">Tento příkaz vyberte, pokud chcete, aby model ML předpovídat číselnou hodnotu (například předpověď ceny).</span><span class="sxs-lookup"><span data-stu-id="53b33-128">Choose this command if you want an ML Model to predict a numeric value (e.g. price prediction).</span></span>

```console
mlnet classification

--dataset <path> (REQUIRED)

--label-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--ignore-cols <cols>

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

### <a name="recommendation-options"></a><span data-ttu-id="53b33-129">Možnosti doporučení</span><span class="sxs-lookup"><span data-stu-id="53b33-129">Recommendation options</span></span>

<span data-ttu-id="53b33-130">Spuštění `mlnet recommendation` bude mít za to poučení s doporučením modelu.</span><span class="sxs-lookup"><span data-stu-id="53b33-130">Running `mlnet recommendation` will train a recommendation model.</span></span>  <span data-ttu-id="53b33-131">Tento příkaz vyberte, pokud chcete, aby model ML doporučil položky uživatelům na základě hodnocení (např. doporučení produktu).</span><span class="sxs-lookup"><span data-stu-id="53b33-131">Choose this command if you want an ML Model to recommend items to users based on ratings (e.g. product recommendation).</span></span>

```console
mlnet classification

--dataset <path> (REQUIRED)

--item-col <col> (REQUIRED)

--rating-col <col> (REQUIRED)

--user-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

<span data-ttu-id="53b33-132">Neplatné možnosti vstupu způsobí, že nástroj rozhraní příkazového řádku vygeneruje seznam platných vstupů a chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="53b33-132">Invalid input options cause the CLI tool to emit a list of valid inputs and an error message.</span></span>

## <a name="dataset"></a><span data-ttu-id="53b33-133">Datová sada</span><span class="sxs-lookup"><span data-stu-id="53b33-133">Dataset</span></span>

<span data-ttu-id="53b33-134">`--dataset | -d`řetezce</span><span class="sxs-lookup"><span data-stu-id="53b33-134">`--dataset | -d` (string)</span></span>

<span data-ttu-id="53b33-135">Tento argument poskytuje cestu k jedné z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="53b33-135">This argument provides the filepath to either one of the following options:</span></span>

- <span data-ttu-id="53b33-136">Odpověď *: soubor celé datové sady:* Pokud se tato možnost používá a uživatel neposkytuje `--test-dataset` a `--validation-dataset` , pak se k ověřování modelu použije interní ověřování (k skládání atd.) nebo automatizované přístupy k rozdělení dat.</span><span class="sxs-lookup"><span data-stu-id="53b33-136">*A: The whole dataset file:* If using this option and the user is not providing `--test-dataset` and `--validation-dataset`, then cross-validation (k-fold, etc.) or automated data split approaches will be used internally for validating the model.</span></span> <span data-ttu-id="53b33-137">V takovém případě bude muset uživatel pouze zadat FilePath pro datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="53b33-137">In that case, the user will just need to provide the dataset filepath.</span></span>

- <span data-ttu-id="53b33-138">*B: soubor datové sady školení:* Pokud uživatel také poskytuje datové sady pro ověřování modelu (pomocí `--test-dataset` a volitelně `--validation-dataset` ), pak `--dataset` argument znamená, že má mít pouze "školicí datovou sadu".</span><span class="sxs-lookup"><span data-stu-id="53b33-138">*B: The training dataset file:* If the user is also providing datasets for model validation (using `--test-dataset` and optionally `--validation-dataset`), then the `--dataset` argument means to only have the "training dataset".</span></span> <span data-ttu-id="53b33-139">Například při použití přístupu 80%-20% k ověření kvality modelu a získání metrik přesnosti bude mít "školicí datová sada" 80% dat a "testovací sada" bude obsahovat 20% dat.</span><span class="sxs-lookup"><span data-stu-id="53b33-139">For example, when using an 80% - 20% approach to validate the quality of the model and to obtain accuracy metrics, the "training dataset" will have 80% of the data and the "test dataset" would have 20% of the data.</span></span>

## <a name="test-dataset"></a><span data-ttu-id="53b33-140">Testovací datová sada</span><span class="sxs-lookup"><span data-stu-id="53b33-140">Test dataset</span></span>

<span data-ttu-id="53b33-141">`--test-dataset | -t`řetezce</span><span class="sxs-lookup"><span data-stu-id="53b33-141">`--test-dataset | -t` (string)</span></span>

<span data-ttu-id="53b33-142">Cesta k souboru, který odkazuje na soubor sady dat testu, například při použití 80%-20% přístupu při pravidelném ověřování, aby bylo možné získat metriky přesnosti.</span><span class="sxs-lookup"><span data-stu-id="53b33-142">File path pointing to the test dataset file, for example when using an 80% - 20% approach when making regular validations to obtain accuracy metrics.</span></span>

<span data-ttu-id="53b33-143">Pokud používáte `--test-dataset` , `--dataset` je také nutné použít.</span><span class="sxs-lookup"><span data-stu-id="53b33-143">If using `--test-dataset`, then `--dataset` is also required.</span></span>

<span data-ttu-id="53b33-144">`--test-dataset`Argument je nepovinný, pokud se nepoužívá--ověření-DataSet.</span><span class="sxs-lookup"><span data-stu-id="53b33-144">The `--test-dataset` argument is optional unless the --validation-dataset is used.</span></span> <span data-ttu-id="53b33-145">V takovém případě musí uživatel použít tři argumenty.</span><span class="sxs-lookup"><span data-stu-id="53b33-145">In that case, the user must use the three arguments.</span></span>

## <a name="validation-dataset"></a><span data-ttu-id="53b33-146">Ověřovací datová sada</span><span class="sxs-lookup"><span data-stu-id="53b33-146">Validation dataset</span></span>

<span data-ttu-id="53b33-147">`--validation-dataset | -v`řetezce</span><span class="sxs-lookup"><span data-stu-id="53b33-147">`--validation-dataset | -v` (string)</span></span>

<span data-ttu-id="53b33-148">Cesta k souboru, který odkazuje na soubor datové sady ověření.</span><span class="sxs-lookup"><span data-stu-id="53b33-148">File path pointing to the validation dataset file.</span></span> <span data-ttu-id="53b33-149">Datová sada ověření je volitelná, v každém případě.</span><span class="sxs-lookup"><span data-stu-id="53b33-149">The validation dataset is optional, in any case.</span></span>

<span data-ttu-id="53b33-150">Pokud používáte `validation dataset` , musí být toto chování:</span><span class="sxs-lookup"><span data-stu-id="53b33-150">If using a `validation dataset`, the behavior should be:</span></span>

- <span data-ttu-id="53b33-151">`test-dataset`Argumenty a `--dataset` jsou také požadovány.</span><span class="sxs-lookup"><span data-stu-id="53b33-151">The `test-dataset` and `--dataset` arguments are also required.</span></span>

- <span data-ttu-id="53b33-152">`validation-dataset`Datová sada se používá k odhadování chyby předpovědi pro výběr modelu.</span><span class="sxs-lookup"><span data-stu-id="53b33-152">The `validation-dataset` dataset is used to estimate prediction error for model selection.</span></span>

- <span data-ttu-id="53b33-153">`test-dataset`Slouží k vyhodnocení chyby generalizace finálního zvoleného modelu.</span><span class="sxs-lookup"><span data-stu-id="53b33-153">The `test-dataset` is used for assessment of the generalization error of the final chosen model.</span></span> <span data-ttu-id="53b33-154">V ideálním případě by měl být testovací sada uchovávána v "trezoru" a musí být uvedena pouze na konci analýzy dat.</span><span class="sxs-lookup"><span data-stu-id="53b33-154">Ideally, the test set should be kept in a “vault,” and be brought out only at the end of the data analysis.</span></span>

<span data-ttu-id="53b33-155">V podstatě při použití plus a je `validation dataset` `test dataset` fáze ověření rozdělena do dvou částí:</span><span class="sxs-lookup"><span data-stu-id="53b33-155">Basically, when using a `validation dataset` plus the `test dataset`, the validation phase is split into two parts:</span></span>

1. <span data-ttu-id="53b33-156">V první části se jenom podíváte na vaše modely a vyberete nejlepší způsob, jak pomocí ověřovacích dat (= ověřování) vybrat nejvhodnější přístup.</span><span class="sxs-lookup"><span data-stu-id="53b33-156">In the first part, you just look at your models and select the best performing approach using the validation data (=validation)</span></span>
2. <span data-ttu-id="53b33-157">Pak odhadnete přesnost vybraného přístupu (= test).</span><span class="sxs-lookup"><span data-stu-id="53b33-157">Then you estimate the accuracy of the selected approach (=test).</span></span>

<span data-ttu-id="53b33-158">Oddělení dat by proto mohlo být 80/10/10 nebo 75/15/10.</span><span class="sxs-lookup"><span data-stu-id="53b33-158">Hence, the separation of data could be 80/10/10 or 75/15/10.</span></span> <span data-ttu-id="53b33-159">Například:</span><span class="sxs-lookup"><span data-stu-id="53b33-159">For example:</span></span>

- <span data-ttu-id="53b33-160">`training-dataset`soubor by měl mít 75% dat.</span><span class="sxs-lookup"><span data-stu-id="53b33-160">`training-dataset` file should have 75% of the data.</span></span>
- <span data-ttu-id="53b33-161">`validation-dataset`soubor by měl mít 15% dat.</span><span class="sxs-lookup"><span data-stu-id="53b33-161">`validation-dataset` file should have 15% of the data.</span></span>
- <span data-ttu-id="53b33-162">`test-dataset`soubor by měl mít 10% dat.</span><span class="sxs-lookup"><span data-stu-id="53b33-162">`test-dataset` file should have 10% of the data.</span></span>

<span data-ttu-id="53b33-163">V každém případě se tyto procentní podíly určí uživatelem pomocí rozhraní příkazového řádku, který poskytne soubory, které jsou už rozdělené.</span><span class="sxs-lookup"><span data-stu-id="53b33-163">In any case, those percentages will be decided by the user using the CLI who will provide the files already split.</span></span>

## <a name="label-column"></a><span data-ttu-id="53b33-164">Sloupec popisku</span><span class="sxs-lookup"><span data-stu-id="53b33-164">Label column</span></span>

<span data-ttu-id="53b33-165">`--label-col`(int nebo String)</span><span class="sxs-lookup"><span data-stu-id="53b33-165">`--label-col` (int or string)</span></span>

<span data-ttu-id="53b33-166">Pomocí tohoto argumentu je možné zadat konkrétní sloupec cíl/cíl (proměnnou, kterou chcete odhadnout) pomocí názvu sloupce nastaveného v záhlaví datové sady nebo číselného indexu sloupce v souboru datové sady (hodnoty indexu sloupce začínají hodnotou 0).</span><span class="sxs-lookup"><span data-stu-id="53b33-166">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="53b33-167">Tento argument se používá pro problémy *klasifikace* a *regrese* .</span><span class="sxs-lookup"><span data-stu-id="53b33-167">This argument is used for *classification* and *regression* problems.</span></span>

## <a name="item-column"></a><span data-ttu-id="53b33-168">Sloupec položky</span><span class="sxs-lookup"><span data-stu-id="53b33-168">Item column</span></span>

<span data-ttu-id="53b33-169">`--item-col`(int nebo String)</span><span class="sxs-lookup"><span data-stu-id="53b33-169">`--item-col` (int or string)</span></span>

<span data-ttu-id="53b33-170">Sloupec Item (položka) obsahuje seznam položek, které uživatelé budou hodnotit (pro uživatele se doporučuje používat položky).</span><span class="sxs-lookup"><span data-stu-id="53b33-170">The item column has the list of items that users rate (items are recommended to users).</span></span> <span data-ttu-id="53b33-171">Tento sloupec lze zadat pomocí názvu sloupce nastaveného v záhlaví datové sady nebo číselného indexu sloupce v souboru datové sady (hodnoty indexu sloupce začínají hodnotou 0).</span><span class="sxs-lookup"><span data-stu-id="53b33-171">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="53b33-172">Tento argument se používá pouze pro úkol *doporučení* .</span><span class="sxs-lookup"><span data-stu-id="53b33-172">This argument is used only for the *recommendation* task.</span></span>

## <a name="rating-column"></a><span data-ttu-id="53b33-173">Sloupec hodnocení</span><span class="sxs-lookup"><span data-stu-id="53b33-173">Rating column</span></span>

<span data-ttu-id="53b33-174">`--rating-col`(int nebo String)</span><span class="sxs-lookup"><span data-stu-id="53b33-174">`--rating-col` (int or string)</span></span>

<span data-ttu-id="53b33-175">Sloupec hodnocení obsahuje seznam hodnocení, která jsou dána pro položky podle uživatelů.</span><span class="sxs-lookup"><span data-stu-id="53b33-175">The rating column has the list of ratings that are given to items by users.</span></span> <span data-ttu-id="53b33-176">Tento sloupec lze zadat pomocí názvu sloupce nastaveného v záhlaví datové sady nebo číselného indexu sloupce v souboru datové sady (hodnoty indexu sloupce začínají hodnotou 0).</span><span class="sxs-lookup"><span data-stu-id="53b33-176">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="53b33-177">Tento argument se používá pouze pro úkol *doporučení* .</span><span class="sxs-lookup"><span data-stu-id="53b33-177">This argument is used only for the *recommendation* task.</span></span>

## <a name="user-column"></a><span data-ttu-id="53b33-178">Sloupec uživatele</span><span class="sxs-lookup"><span data-stu-id="53b33-178">User column</span></span>

<span data-ttu-id="53b33-179">`--user-col`(int nebo String)</span><span class="sxs-lookup"><span data-stu-id="53b33-179">`--user-col` (int or string)</span></span>

<span data-ttu-id="53b33-180">Sloupec uživatel má seznam uživatelů, kteří přidávají hodnocení položkám.</span><span class="sxs-lookup"><span data-stu-id="53b33-180">The user column has the list of users that give ratings to items.</span></span> <span data-ttu-id="53b33-181">Tento sloupec lze zadat pomocí názvu sloupce nastaveného v záhlaví datové sady nebo číselného indexu sloupce v souboru datové sady (hodnoty indexu sloupce začínají hodnotou 0).</span><span class="sxs-lookup"><span data-stu-id="53b33-181">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="53b33-182">Tento argument se používá pouze pro úkol *doporučení* .</span><span class="sxs-lookup"><span data-stu-id="53b33-182">This argument is used only for the *recommendation* task.</span></span>

## <a name="ignore-columns"></a><span data-ttu-id="53b33-183">Ignorovat sloupce</span><span class="sxs-lookup"><span data-stu-id="53b33-183">Ignore columns</span></span>

<span data-ttu-id="53b33-184">`--ignore-columns`řetezce</span><span class="sxs-lookup"><span data-stu-id="53b33-184">`--ignore-columns` (string)</span></span>

<span data-ttu-id="53b33-185">Pomocí tohoto argumentu můžete ignorovat existující sloupce v souboru DataSet, aby nebyly načteny a použity v školicích procesech.</span><span class="sxs-lookup"><span data-stu-id="53b33-185">With this argument, you can ignore existing columns in the dataset file so they are not loaded and used by the training processes.</span></span>

<span data-ttu-id="53b33-186">Zadejte názvy sloupců, které chcete ignorovat.</span><span class="sxs-lookup"><span data-stu-id="53b33-186">Specify the columns names that you want to ignore.</span></span> <span data-ttu-id="53b33-187">K oddělení více názvů sloupců použijte ', ' (čárka s mezerou) nebo ' ' (mezera).</span><span class="sxs-lookup"><span data-stu-id="53b33-187">Use ', ' (comma with space) or ' ' (space) to separate multiple column names.</span></span> <span data-ttu-id="53b33-188">Můžete použít uvozovky pro názvy sloupců obsahující prázdné znaky (například "přihlášen").</span><span class="sxs-lookup"><span data-stu-id="53b33-188">You can use quotes for column names containing whitespace (e.g. "logged in").</span></span>

<span data-ttu-id="53b33-189">Příklad:</span><span class="sxs-lookup"><span data-stu-id="53b33-189">Example:</span></span>

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a><span data-ttu-id="53b33-190">Má hlavičku</span><span class="sxs-lookup"><span data-stu-id="53b33-190">Has header</span></span>

<span data-ttu-id="53b33-191">`--has-header`logick</span><span class="sxs-lookup"><span data-stu-id="53b33-191">`--has-header` (bool)</span></span>

<span data-ttu-id="53b33-192">Určete, zda mají soubory DataSet řádek záhlaví.</span><span class="sxs-lookup"><span data-stu-id="53b33-192">Specify if the dataset file(s) have a header row.</span></span>
<span data-ttu-id="53b33-193">Možné hodnoty:</span><span class="sxs-lookup"><span data-stu-id="53b33-193">Possible values are:</span></span>

- `true`
- `false`

<span data-ttu-id="53b33-194">Rozhraní příkazového řádku ML.NET se pokusí tuto vlastnost detekovat, pokud tento argument není zadán uživatelem.</span><span class="sxs-lookup"><span data-stu-id="53b33-194">The ML.NET CLI will try to detect this property if this argument is not specified by the user.</span></span>

## <a name="train-time"></a><span data-ttu-id="53b33-195">Doba vlaku</span><span class="sxs-lookup"><span data-stu-id="53b33-195">Train time</span></span>

<span data-ttu-id="53b33-196">`--train-time`řetezce</span><span class="sxs-lookup"><span data-stu-id="53b33-196">`--train-time` (string)</span></span>

<span data-ttu-id="53b33-197">Ve výchozím nastavení je maximální doba průzkumu nebo výuky 30 minut.</span><span class="sxs-lookup"><span data-stu-id="53b33-197">By default, the maximum exploration / train time is 30 minutes.</span></span>

<span data-ttu-id="53b33-198">Tento argument nastaví maximální dobu (v sekundách), po kterou má proces prozkoumat více školitelů a konfigurací.</span><span class="sxs-lookup"><span data-stu-id="53b33-198">This argument sets the maximum time (in seconds) for the process to explore multiple trainers and configurations.</span></span> <span data-ttu-id="53b33-199">Nakonfigurovaný čas může být překročen, pokud je zadaný čas příliš krátký (řekněme 2 sekundy) pro jednu iteraci.</span><span class="sxs-lookup"><span data-stu-id="53b33-199">The configured time may be exceeded if the provided time is too short (say 2 seconds) for a single iteration.</span></span> <span data-ttu-id="53b33-200">V tomto případě je skutečný čas potřebný čas k vytvoření jedné konfigurace modelu v rámci jedné iterace.</span><span class="sxs-lookup"><span data-stu-id="53b33-200">In this case, the actual time is the required time to produce one model configuration in a single iteration.</span></span>

<span data-ttu-id="53b33-201">Čas potřebný pro iterace se může lišit v závislosti na velikosti datové sady.</span><span class="sxs-lookup"><span data-stu-id="53b33-201">The needed time for iterations can vary depending on the size of the dataset.</span></span>

## <a name="cache"></a><span data-ttu-id="53b33-202">Mezipaměť</span><span class="sxs-lookup"><span data-stu-id="53b33-202">Cache</span></span>

<span data-ttu-id="53b33-203">`--cache`řetezce</span><span class="sxs-lookup"><span data-stu-id="53b33-203">`--cache` (string)</span></span>

<span data-ttu-id="53b33-204">Pokud použijete ukládání do mezipaměti, načte se celá datová sada školení v paměti.</span><span class="sxs-lookup"><span data-stu-id="53b33-204">If you use caching, the whole training dataset will be loaded in-memory.</span></span>

<span data-ttu-id="53b33-205">V případě malých a středně velkých datových sad může použití mezipaměti významně zlepšit výkon školení, což znamená, že doba přípravy může být kratší, než když mezipaměť nepoužíváte.</span><span class="sxs-lookup"><span data-stu-id="53b33-205">For small and medium datasets, using cache can drastically improve the training performance, meaning the training time can be shorter than when you don't use cache.</span></span>

<span data-ttu-id="53b33-206">U rozsáhlých datových sad ale načítání všech dat v paměti může negativně ovlivnit vzhledem k tomu, že může dojít k dostatku paměti.</span><span class="sxs-lookup"><span data-stu-id="53b33-206">However, for large datasets, loading all the data in memory can impact negatively since you might get out of memory.</span></span> <span data-ttu-id="53b33-207">Při školení s rozsáhlými soubory DataSet a nepoužíváte-li mezipaměť, bude ML.NET streamovat datové bloky dat z disku, když potřebuje načíst více dat během školení.</span><span class="sxs-lookup"><span data-stu-id="53b33-207">When training with large dataset files and not using cache, ML.NET will be streaming chunks of data from the drive when it needs to load more data while training.</span></span>

<span data-ttu-id="53b33-208">Můžete určit tyto hodnoty:</span><span class="sxs-lookup"><span data-stu-id="53b33-208">You can specify the following values:</span></span>

<span data-ttu-id="53b33-209">`on`: Vynutí, aby se při výuce použila mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="53b33-209">`on`: Forces cache to be used when training.</span></span>
<span data-ttu-id="53b33-210">`off`: Vynutí, aby se mezipaměť nepoužívala při výuce.</span><span class="sxs-lookup"><span data-stu-id="53b33-210">`off`: Forces cache not to be used when training.</span></span>
<span data-ttu-id="53b33-211">`auto`: V závislosti na heuristikách AutoML se mezipaměť použije nebo ne.</span><span class="sxs-lookup"><span data-stu-id="53b33-211">`auto`: Depending on AutoML heuristics, the cache will be used or not.</span></span> <span data-ttu-id="53b33-212">Malé nebo střední datové sady budou obvykle používat mezipaměť a velké datové sady nebudou používat mezipaměť, pokud použijete `auto` volbu.</span><span class="sxs-lookup"><span data-stu-id="53b33-212">Usually, small/medium datasets will use cache and large datasets won't use cache if you use the `auto` choice.</span></span>

<span data-ttu-id="53b33-213">Pokud parametr nezadáte `--cache` , `auto` použije se ve výchozím nastavení konfigurace mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="53b33-213">If you don't specify the `--cache` parameter, then the cache `auto` configuration will be used by default.</span></span>

## <a name="name"></a><span data-ttu-id="53b33-214">Name</span><span class="sxs-lookup"><span data-stu-id="53b33-214">Name</span></span>

<span data-ttu-id="53b33-215">`--name`řetezce</span><span class="sxs-lookup"><span data-stu-id="53b33-215">`--name` (string)</span></span>

<span data-ttu-id="53b33-216">Název vytvořeného výstupního projektu nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="53b33-216">The name for the created output project or solution.</span></span> <span data-ttu-id="53b33-217">Pokud název nezadáte, použije se název `sample-{mltask}` .</span><span class="sxs-lookup"><span data-stu-id="53b33-217">If no name is specified, the name `sample-{mltask}` is used.</span></span>

<span data-ttu-id="53b33-218">Soubor modelu ML.NET (. Soubor ZIP) bude mít stejný název i.</span><span class="sxs-lookup"><span data-stu-id="53b33-218">The ML.NET model file (.ZIP file) will get the same name, as well.</span></span>

## <a name="output-path"></a><span data-ttu-id="53b33-219">Výstupní cesta</span><span class="sxs-lookup"><span data-stu-id="53b33-219">Output path</span></span>

<span data-ttu-id="53b33-220">`--output-path | -o`řetezce</span><span class="sxs-lookup"><span data-stu-id="53b33-220">`--output-path | -o` (string)</span></span>

<span data-ttu-id="53b33-221">Kořenové umístění/složka, do které se umístí vygenerovaný výstup</span><span class="sxs-lookup"><span data-stu-id="53b33-221">Root location/folder to place the generated output.</span></span> <span data-ttu-id="53b33-222">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="53b33-222">The default is the current directory.</span></span>

## <a name="verbosity"></a><span data-ttu-id="53b33-223">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="53b33-223">Verbosity</span></span>

<span data-ttu-id="53b33-224">`--verbosity | -v`řetezce</span><span class="sxs-lookup"><span data-stu-id="53b33-224">`--verbosity | -v` (string)</span></span>

<span data-ttu-id="53b33-225">Nastaví úroveň podrobností standardního výstupu.</span><span class="sxs-lookup"><span data-stu-id="53b33-225">Sets the verbosity level of the standard output.</span></span>

<span data-ttu-id="53b33-226">Povolené hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="53b33-226">Allowed values are:</span></span>

- `q[uiet]`
- <span data-ttu-id="53b33-227">`m[inimal]`(ve výchozím nastavení)</span><span class="sxs-lookup"><span data-stu-id="53b33-227">`m[inimal]`  (by default)</span></span>
- <span data-ttu-id="53b33-228">`diag[nostic]`(úroveň informací o protokolování)</span><span class="sxs-lookup"><span data-stu-id="53b33-228">`diag[nostic]` (logging information level)</span></span>

<span data-ttu-id="53b33-229">Ve výchozím nastavení by měl nástroj rozhraní příkazového řádku při práci zobrazit některé minimální zpětné vazby ( `minimal` ), jako je třeba zmínku o tom, že funguje, a pokud je to možné, kolik času zbývá nebo kolik času bylo dokončeno.</span><span class="sxs-lookup"><span data-stu-id="53b33-229">By default, the CLI tool should show some minimum feedback (`minimal`) when working, such as mentioning that it is working and if possible how much time is left or what % of the time is completed.</span></span>

## <a name="help"></a><span data-ttu-id="53b33-230">Nápověda</span><span class="sxs-lookup"><span data-stu-id="53b33-230">Help</span></span>

`-h |--help`

<span data-ttu-id="53b33-231">Vytiskne nápovědu pro příkaz s popisem pro každý parametr příkazu.</span><span class="sxs-lookup"><span data-stu-id="53b33-231">Prints out help for the command with a description for each command's parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="53b33-232">Viz také</span><span class="sxs-lookup"><span data-stu-id="53b33-232">See also</span></span>

- [<span data-ttu-id="53b33-233">Postup instalace nástroje ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="53b33-233">How to install the ML.NET CLI tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="53b33-234">Přehled rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="53b33-234">Overview of the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="53b33-235">Kurz: analýza mínění pomocí rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="53b33-235">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="53b33-236">Telemetrie v ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="53b33-236">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
