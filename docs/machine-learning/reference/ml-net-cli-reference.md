---
title: Příkaz pro automatické učení v nástroji CLI ML.NET
description: Přehled, ukázky a Reference k příkazu pro automatický vlak v nástroji CLI ML.NET
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: 8363a16ab5e793e715131ac37283106517850439
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929204"
---
# <a name="the-auto-train-command-in-mlnet-cli"></a><span data-ttu-id="21b0a-103">Příkaz Auto-vlak v ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="21b0a-103">The 'auto-train' command in ML.NET CLI</span></span>

> [!NOTE]
> <span data-ttu-id="21b0a-104">Toto téma odkazuje na ML.NET CLI a ML.NET AutoML, které jsou momentálně ve verzi Preview, a materiál může být změněn.</span><span class="sxs-lookup"><span data-stu-id="21b0a-104">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

<span data-ttu-id="21b0a-105">`auto-train` Příkaz je hlavním příkazem, který poskytuje nástroj ml.NET CLI.</span><span class="sxs-lookup"><span data-stu-id="21b0a-105">The `auto-train` command is the main command provided by the ML.NET CLI tool.</span></span> <span data-ttu-id="21b0a-106">Příkaz umožňuje vygenerovat kvalitní model ML.NET (soubor s serializovaným modelem. zip) a ukázkový C# kód pro spuštění nebo určení skóre modelu.</span><span class="sxs-lookup"><span data-stu-id="21b0a-106">The command allows you to generate a good quality ML.NET model (serialized model .zip file) plus the example C# code to run/score that model.</span></span> <span data-ttu-id="21b0a-107">Kromě toho se C# kód pro vytvoření nebo výuku modelu vygeneruje také pro vás, abyste mohli prozkoumat, jaký algoritmus a nastavení používá pro tento vygenerovaný "nejlepší model".</span><span class="sxs-lookup"><span data-stu-id="21b0a-107">In addition, the C# code to create/train that model is also generated for you to research what algorithm and settings it is using for that generated "best model".</span></span>

<span data-ttu-id="21b0a-108">Tyto prostředky můžete vygenerovat z vlastních datových sad, aniž byste je museli kódovat sami, takže také zlepší vaši produktivitu, i když už znáte ML.NET.</span><span class="sxs-lookup"><span data-stu-id="21b0a-108">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="21b0a-109">V současné době jsou úlohy ML podporované rozhraním příkazového řádku ML.NET:</span><span class="sxs-lookup"><span data-stu-id="21b0a-109">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- `binary-classification`
- `multiclass-classification`
- `regression`

- <span data-ttu-id="21b0a-110">Pozdější Další úkoly strojového učení, například</span><span class="sxs-lookup"><span data-stu-id="21b0a-110">Future: Other machine learning tasks, such as</span></span>
  - `recommendation`
  - `anomaly-detection`
  - `clustering`

<span data-ttu-id="21b0a-111">Příklad použití na příkazovém řádku:</span><span class="sxs-lookup"><span data-stu-id="21b0a-111">Example of usage on the command prompt:</span></span>

```console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

<span data-ttu-id="21b0a-112">`mlnet auto-train` Příkaz vygeneruje následující prostředky:</span><span class="sxs-lookup"><span data-stu-id="21b0a-112">The `mlnet auto-train` command generates the following assets:</span></span>

- <span data-ttu-id="21b0a-113">Serializovaný model. zip ("nejlepší model") je připravený k použití.</span><span class="sxs-lookup"><span data-stu-id="21b0a-113">A serialized model .zip ("best model") ready to use.</span></span>
- <span data-ttu-id="21b0a-114">C#kód pro spuštění nebo určení skóre generovaného modelu (k tomu, aby předpovědi v aplikacích pro koncové uživatele s tímto modelem).</span><span class="sxs-lookup"><span data-stu-id="21b0a-114">C# code to run/score that generated model (To make predictions in your end-user apps with that model).</span></span>
- <span data-ttu-id="21b0a-115">C#kód s školicím kódem, který slouží k vygenerování tohoto modelu (vzdělávací účely).</span><span class="sxs-lookup"><span data-stu-id="21b0a-115">C# code with the training code used to generate that model (Learning purposes).</span></span>

<span data-ttu-id="21b0a-116">První dva prostředky lze použít přímo v aplikacích pro koncové uživatele (ASP.NET Core webové aplikace, služby, aplikace klasické pracovní plochy atd.) k tomu, aby se předpovědi s tímto generovaným modelem ML.</span><span class="sxs-lookup"><span data-stu-id="21b0a-116">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="21b0a-117">Třetí Asset a školicí kód vám ukáže, co ML.NET kód rozhraní API používal CLI k výuce vygenerovaného modelu, takže můžete prozkoumat, jaké konkrétní Trainer/algoritmus a Hyper-Parameters byly vybrány rozhraním příkazového řádku a modulem ML.NET AutoML.</span><span class="sxs-lookup"><span data-stu-id="21b0a-117">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate what specific trainer/algorithm and hyper-parameters were selected by the CLI and the ML.NET AutoML engine.</span></span>

## <a name="the-auto-train-command-uses-the-automl-engine"></a><span data-ttu-id="21b0a-118">Příkaz Auto-vlak používá modul AutoML.</span><span class="sxs-lookup"><span data-stu-id="21b0a-118">The 'auto-train' command uses the AutoML engine</span></span>

<span data-ttu-id="21b0a-119">Rozhraní příkazového řádku používá modul ML.NET AutoML (balíček NuGet) k inteligentnímu vyhledávání nejlepších modelů kvality, jak je znázorněno v následujícím diagramu:</span><span class="sxs-lookup"><span data-stu-id="21b0a-119">The CLI uses the ML.NET AutoML engine (NuGet package) to intelligently search for the best quality models, as shown in the following diagram:</span></span>

<span data-ttu-id="21b0a-120">![Obrázek](./media/ml-net-automl-working-diagram.png "AutoML Engine pracuje v rozhraní příkazového řádku ml.NET")</span><span class="sxs-lookup"><span data-stu-id="21b0a-120">![image](./media/ml-net-automl-working-diagram.png "AutoML engine working inside the ML.NET CLI")</span></span>

<span data-ttu-id="21b0a-121">Při spuštění nástroje ML.NET CLI pomocí příkazu auto-vlak-Command se zobrazí nástroj, který zkouší mnoho iterací s různými algoritmy a kombinacemi konfigurace.</span><span class="sxs-lookup"><span data-stu-id="21b0a-121">When running the ML.NET CLI tool with the \`auto-train- command, you'll see the tool trying many iterations with different algorithms and combinations of configuration.</span></span>

## <a name="reference-for-auto-train-command"></a><span data-ttu-id="21b0a-122">Reference pro příkaz Auto-vlak</span><span class="sxs-lookup"><span data-stu-id="21b0a-122">Reference for 'auto-train' command</span></span>

## <a name="examples"></a><span data-ttu-id="21b0a-123">Příklady</span><span class="sxs-lookup"><span data-stu-id="21b0a-123">Examples</span></span>

<span data-ttu-id="21b0a-124">Nejjednodušší příkaz CLI pro problém binární klasifikace (AutoML bude muset odvodit většinu konfigurace z poskytnutých dat):</span><span class="sxs-lookup"><span data-stu-id="21b0a-124">Simplest CLI command for a binary classification problem (AutoML will need to infer most of the configuration from the provided data):</span></span>

```console
> mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

<span data-ttu-id="21b0a-125">Další jednoduchý příkaz CLI pro problém regrese:</span><span class="sxs-lookup"><span data-stu-id="21b0a-125">Another simple CLI command for a regression problem:</span></span>

``` console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

<span data-ttu-id="21b0a-126">Vytvoření a výuka modelu binární klasifikace s datovou sadou vlaků, testovací datovou sadou a dalšími explicitními argumenty přizpůsobení:</span><span class="sxs-lookup"><span data-stu-id="21b0a-126">Create and train a binary-classification model with a train dataset, a test dataset, and further customization explicit arguments:</span></span>

```console
> mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="name"></a><span data-ttu-id="21b0a-127">Name</span><span class="sxs-lookup"><span data-stu-id="21b0a-127">Name</span></span>

<span data-ttu-id="21b0a-128">`mlnet auto-train`– Vlaky s více modely (n) založené na zadané datové sadě a nakonec vyberou nejlepší model, uloží ho jako serializovaný soubor. zip a vygeneruje související C# kód pro bodování a školení.</span><span class="sxs-lookup"><span data-stu-id="21b0a-128">`mlnet auto-train` - Trains multiple models ('n' iterations) based on the provided dataset and finally selects the best model, saves it as a serialized .zip file plus generates related C# code for scoring and training.</span></span>

## <a name="synopsis"></a><span data-ttu-id="21b0a-129">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="21b0a-129">Synopsis</span></span>

```console
> mlnet auto-train

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

<span data-ttu-id="21b0a-130">Neplatné možnosti vstupu by měly způsobit, že nástroj rozhraní příkazového řádku vygeneruje seznam platných vstupů a chybové zprávy s vysvětlením, který ARG chybí, pokud se jedná o tento případ.</span><span class="sxs-lookup"><span data-stu-id="21b0a-130">Invalid input options should cause the CLI tool to emit a list of valid inputs and an error message explaining which arg is missing, if that is the case.</span></span>

## <a name="options"></a><span data-ttu-id="21b0a-131">Možnosti</span><span class="sxs-lookup"><span data-stu-id="21b0a-131">Options</span></span>

 ----------------------------------------------------------

<span data-ttu-id="21b0a-132">`--task | --mltask | -T`řetezce</span><span class="sxs-lookup"><span data-stu-id="21b0a-132">`--task | --mltask | -T` (string)</span></span>

<span data-ttu-id="21b0a-133">Jeden řetězec, který poskytuje problém k řešení ML.</span><span class="sxs-lookup"><span data-stu-id="21b0a-133">A single string providing the ML problem to solve.</span></span> <span data-ttu-id="21b0a-134">Například kterákoli z následujících úloh (rozhraní příkazového řádku bude nakonec podporovat všechny úlohy podporované v AutoML):</span><span class="sxs-lookup"><span data-stu-id="21b0a-134">For instance, any of the following tasks (The CLI will eventually support all tasks supported in AutoML):</span></span>

- <span data-ttu-id="21b0a-135">`regression`– Vyberte, jestli se má pro předpověď číselné hodnoty použít model ML.</span><span class="sxs-lookup"><span data-stu-id="21b0a-135">`regression` - Choose if the ML Model will be used to predict a numeric value</span></span>
- <span data-ttu-id="21b0a-136">`binary-classification`– Vyberte, jestli má výsledek modelu ML dvě možné kategorií logické hodnoty (0 nebo 1).</span><span class="sxs-lookup"><span data-stu-id="21b0a-136">`binary-classification` - Choose if the ML Model result has two possible categorical boolean values (0 or 1).</span></span>
- <span data-ttu-id="21b0a-137">`multiclass-classification`– Vyberte, jestli má výsledek modelu ML více kategorií možných hodnot.</span><span class="sxs-lookup"><span data-stu-id="21b0a-137">`multiclass-classification` - Choose if the ML Model result has multiple categorical possible values.</span></span>

<span data-ttu-id="21b0a-138">V budoucnu se vydává další úlohy a scénáře v `recommendations`ml `clustering` , `ranking` jako například, a budou podporovány.</span><span class="sxs-lookup"><span data-stu-id="21b0a-138">In future releases additional ML Tasks and scenarios such as `recommendations`, `clustering` and `ranking` will be supported.</span></span>

 <span data-ttu-id="21b0a-139">V tomto argumentu by měla být uvedena pouze jedna úloha ML.</span><span class="sxs-lookup"><span data-stu-id="21b0a-139">Only one ML task should be provided in this argument.</span></span>

 ----------------------------------------------------------

<span data-ttu-id="21b0a-140">`--dataset | -d`řetezce</span><span class="sxs-lookup"><span data-stu-id="21b0a-140">`--dataset | -d` (string)</span></span>

<span data-ttu-id="21b0a-141">Tento argument poskytuje cestu k jedné z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="21b0a-141">This argument provides the filepath to either one of the following options:</span></span>

- <span data-ttu-id="21b0a-142">*URČITÉHO Celý soubor datové sady:* Pokud se tato možnost používá a uživatel neposkytuje `--test-dataset` a `--validation-dataset`, pak se k ověřování modelu použije interní ověřování (k skládání atd.) nebo automatizované přístupy k rozdělení dat.</span><span class="sxs-lookup"><span data-stu-id="21b0a-142">*A: The whole dataset file:* If using this option and the user is not providing `--test-dataset` and `--validation-dataset`, then cross-validation (k-fold, etc.) or automated data split approaches will be used internally for validating the model.</span></span> <span data-ttu-id="21b0a-143">V takovém případě bude muset uživatel pouze zadat FilePath pro datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="21b0a-143">In that case, the user will just need to provide the dataset filepath.</span></span>

- <span data-ttu-id="21b0a-144">*B: Soubor datové sady školení:* Pokud uživatel také poskytuje datové sady pro ověřování modelu (pomocí `--test-dataset` a volitelně `--validation-dataset`), pak `--dataset` argument znamená, že má mít pouze "školicí datovou sadu".</span><span class="sxs-lookup"><span data-stu-id="21b0a-144">*B: The training dataset file:* If the user is also providing datasets for model validation (using `--test-dataset` and optionally `--validation-dataset`), then the `--dataset` argument means to only have the "training dataset".</span></span> <span data-ttu-id="21b0a-145">Například při použití přístupu 80%-20% k ověření kvality modelu a získání metrik přesnosti bude mít "školicí datová sada" 80% dat a "testovací sada" bude obsahovat 20% dat.</span><span class="sxs-lookup"><span data-stu-id="21b0a-145">For example, when using an 80% - 20% approach to validate the quality of the model and to obtain accuracy metrics, the "training dataset" will have 80% of the data and the "test dataset" would have 20% of the data.</span></span>

----------------------------------------------------------

<span data-ttu-id="21b0a-146">`--test-dataset | -t`řetezce</span><span class="sxs-lookup"><span data-stu-id="21b0a-146">`--test-dataset | -t` (string)</span></span>

<span data-ttu-id="21b0a-147">Cesta k souboru, který odkazuje na soubor sady dat testu, například při použití 80%-20% přístupu při pravidelném ověřování, aby bylo možné získat metriky přesnosti.</span><span class="sxs-lookup"><span data-stu-id="21b0a-147">File path pointing to the test dataset file, for example when using an 80% - 20% approach when making regular validations to obtain accuracy metrics.</span></span>

<span data-ttu-id="21b0a-148">Pokud používáte `--test-dataset` `--dataset` , je také nutné použít.</span><span class="sxs-lookup"><span data-stu-id="21b0a-148">If using `--test-dataset`, then `--dataset` is also required.</span></span>

<span data-ttu-id="21b0a-149">`--test-dataset` Argument je nepovinný, pokud se nepoužívá--ověření-DataSet.</span><span class="sxs-lookup"><span data-stu-id="21b0a-149">The `--test-dataset` argument is optional unless the --validation-dataset is used.</span></span> <span data-ttu-id="21b0a-150">V takovém případě musí uživatel použít tři argumenty.</span><span class="sxs-lookup"><span data-stu-id="21b0a-150">In that case, the user must use the three arguments.</span></span>

----------------------------------------------------------

<span data-ttu-id="21b0a-151">`--validation-dataset | -v`řetezce</span><span class="sxs-lookup"><span data-stu-id="21b0a-151">`--validation-dataset | -v` (string)</span></span>

<span data-ttu-id="21b0a-152">Cesta k souboru, který odkazuje na soubor datové sady ověření.</span><span class="sxs-lookup"><span data-stu-id="21b0a-152">File path pointing to the validation dataset file.</span></span> <span data-ttu-id="21b0a-153">Datová sada ověření je volitelná, v každém případě.</span><span class="sxs-lookup"><span data-stu-id="21b0a-153">The validation dataset is optional, in any case.</span></span>

<span data-ttu-id="21b0a-154">Pokud používáte `validation dataset`, musí být toto chování:</span><span class="sxs-lookup"><span data-stu-id="21b0a-154">If using a `validation dataset`, the behavior should be:</span></span>

- <span data-ttu-id="21b0a-155">Argumenty `test-dataset` a`--dataset` jsou také požadovány.</span><span class="sxs-lookup"><span data-stu-id="21b0a-155">The `test-dataset` and `--dataset` arguments are also required.</span></span>

- <span data-ttu-id="21b0a-156">`validation-dataset` Datová sada se používá k odhadování chyby předpovědi pro výběr modelu.</span><span class="sxs-lookup"><span data-stu-id="21b0a-156">The `validation-dataset` dataset is used to estimate prediction error for model selection.</span></span>

- <span data-ttu-id="21b0a-157">`test-dataset` Slouží k vyhodnocení chyby generalizace finálního zvoleného modelu.</span><span class="sxs-lookup"><span data-stu-id="21b0a-157">The `test-dataset` is used for assessment of the generalization error of the final chosen model.</span></span> <span data-ttu-id="21b0a-158">V ideálním případě by měl být testovací sada uchovávána v "trezoru" a musí být uvedena pouze na konci analýzy dat.</span><span class="sxs-lookup"><span data-stu-id="21b0a-158">Ideally, the test set should be kept in a “vault,” and be brought out only at the end of the data analysis.</span></span>

<span data-ttu-id="21b0a-159">V podstatě při použití `validation dataset` `test dataset`plus a je fáze ověření rozdělena do dvou částí:</span><span class="sxs-lookup"><span data-stu-id="21b0a-159">Basically, when using a `validation dataset` plus the `test dataset`, the validation phase is split into two parts:</span></span>

1. <span data-ttu-id="21b0a-160">V první části se jenom podíváte na vaše modely a vyberete nejlepší způsob, jak pomocí ověřovacích dat (= ověřování) vybrat nejvhodnější přístup.</span><span class="sxs-lookup"><span data-stu-id="21b0a-160">In the first part, you just look at your models and select the best performing approach using the validation data (=validation)</span></span>
2. <span data-ttu-id="21b0a-161">Pak odhadnete přesnost vybraného přístupu (= test).</span><span class="sxs-lookup"><span data-stu-id="21b0a-161">Then you estimate the accuracy of the selected approach (=test).</span></span>

<span data-ttu-id="21b0a-162">Oddělení dat by proto mohlo být 80/10/10 nebo 75/15/10.</span><span class="sxs-lookup"><span data-stu-id="21b0a-162">Hence, the separation of data could be 80/10/10 or 75/15/10.</span></span> <span data-ttu-id="21b0a-163">Příklad:</span><span class="sxs-lookup"><span data-stu-id="21b0a-163">For example:</span></span>

- <span data-ttu-id="21b0a-164">`training-dataset`soubor by měl mít 75% dat.</span><span class="sxs-lookup"><span data-stu-id="21b0a-164">`training-dataset` file should have 75% of the data.</span></span>
- <span data-ttu-id="21b0a-165">`validation-dataset`soubor by měl mít 15% dat.</span><span class="sxs-lookup"><span data-stu-id="21b0a-165">`validation-dataset` file should have 15% of the data.</span></span>
- <span data-ttu-id="21b0a-166">`test-dataset`soubor by měl mít 10% dat.</span><span class="sxs-lookup"><span data-stu-id="21b0a-166">`test-dataset` file should have 10% of the data.</span></span>

<span data-ttu-id="21b0a-167">V každém případě se tyto procentní podíly určí uživatelem pomocí rozhraní příkazového řádku, který poskytne soubory, které jsou už rozdělené.</span><span class="sxs-lookup"><span data-stu-id="21b0a-167">In any case, those percentages will be decided by the user using the CLI who will provide the files already split.</span></span>

----------------------------------------------------------

<span data-ttu-id="21b0a-168">`--label-column-name | -n`řetezce</span><span class="sxs-lookup"><span data-stu-id="21b0a-168">`--label-column-name | -n` (string)</span></span>

<span data-ttu-id="21b0a-169">Pomocí tohoto argumentu je možné zadat konkrétní sloupec cíl/cíl (proměnnou, kterou chcete odhadnout) pomocí názvu sloupce nastaveného v záhlaví datové sady.</span><span class="sxs-lookup"><span data-stu-id="21b0a-169">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's name set in the dataset's header.</span></span>

<span data-ttu-id="21b0a-170">Tento argument se používá jenom pro úlohy pod dohledem ML, jako je například *problém s klasifikací*.</span><span class="sxs-lookup"><span data-stu-id="21b0a-170">This argument is used only for supervised ML tasks such as a *classification problem*.</span></span> <span data-ttu-id="21b0a-171">Nedá se použít pro úlohy s nekontrolovanými ML, jako je například *clustering*.</span><span class="sxs-lookup"><span data-stu-id="21b0a-171">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

----------------------------------------------------------

<span data-ttu-id="21b0a-172">`--label-column-index | -i`hmot</span><span class="sxs-lookup"><span data-stu-id="21b0a-172">`--label-column-index | -i` (int)</span></span>

<span data-ttu-id="21b0a-173">Pomocí tohoto argumentu se dá určit konkrétní sloupec cíl/cíl (proměnná, kterou chcete předpovědět), pomocí číselného indexu sloupce v souboru datové sady (hodnoty indexu sloupce začínají na 1).</span><span class="sxs-lookup"><span data-stu-id="21b0a-173">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's numeric index in the dataset's file (The column index values start at 1).</span></span>

<span data-ttu-id="21b0a-174">*Poznámka:* Pokud uživatel také používá `--label-column-name` `--label-column-name` , je ten, který se používá.</span><span class="sxs-lookup"><span data-stu-id="21b0a-174">*Note:* If the user is also using the `--label-column-name`, the `--label-column-name` is the one being used.</span></span>

<span data-ttu-id="21b0a-175">Tento argument se používá jenom pro úlohu pod dohledem ML, jako je například *problém s klasifikací*.</span><span class="sxs-lookup"><span data-stu-id="21b0a-175">This argument is used only for supervised ML task such as a *classification problem*.</span></span> <span data-ttu-id="21b0a-176">Nedá se použít pro úlohy s nekontrolovanými ML, jako je například *clustering*.</span><span class="sxs-lookup"><span data-stu-id="21b0a-176">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

----------------------------------------------------------

<span data-ttu-id="21b0a-177">`--ignore-columns | -I`řetezce</span><span class="sxs-lookup"><span data-stu-id="21b0a-177">`--ignore-columns | -I` (string)</span></span>

<span data-ttu-id="21b0a-178">Pomocí tohoto argumentu můžete ignorovat existující sloupce v souboru DataSet, aby nebyly načteny a použity v školicích procesech.</span><span class="sxs-lookup"><span data-stu-id="21b0a-178">With this argument, you can ignore existing columns in the dataset file so they are not loaded and used by the training processes.</span></span>

<span data-ttu-id="21b0a-179">Zadejte názvy sloupců, které chcete ignorovat.</span><span class="sxs-lookup"><span data-stu-id="21b0a-179">Specify the columns names that you want to ignore.</span></span> <span data-ttu-id="21b0a-180">K oddělení více názvů sloupců použijte ', ' (čárka s mezerou) nebo ' ' (mezera).</span><span class="sxs-lookup"><span data-stu-id="21b0a-180">Use ', ' (comma with space) or ' ' (space) to separate multiple column names.</span></span> <span data-ttu-id="21b0a-181">Můžete použít uvozovky pro názvy sloupců obsahující prázdné znaky (například "přihlášen").</span><span class="sxs-lookup"><span data-stu-id="21b0a-181">You can use quotes for column names containing whitespace (e.g. "logged in").</span></span>

<span data-ttu-id="21b0a-182">Příklad:</span><span class="sxs-lookup"><span data-stu-id="21b0a-182">Example:</span></span>

`--ignore-columns email, address, id, logged_in`

----------------------------------------------------------

<span data-ttu-id="21b0a-183">`--has-header | -h`logick</span><span class="sxs-lookup"><span data-stu-id="21b0a-183">`--has-header | -h` (bool)</span></span>

<span data-ttu-id="21b0a-184">Určete, zda mají soubory DataSet řádek záhlaví.</span><span class="sxs-lookup"><span data-stu-id="21b0a-184">Specify if the dataset file(s) have a header row.</span></span>
<span data-ttu-id="21b0a-185">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="21b0a-185">Possible values are:</span></span>

- `true`
- `false`

<span data-ttu-id="21b0a-186">Výchozí hodnota je `true` , pokud uživatel nezadá tento argument.</span><span class="sxs-lookup"><span data-stu-id="21b0a-186">The by default value is `true` if this argument is not specified by the user.</span></span>

<span data-ttu-id="21b0a-187">Aby bylo možné použít `--label-column-name` argument, je nutné mít v souboru DataSet hlavičku a `--has-header` nastavit na `true` (což je ve výchozím nastavení výchozí).</span><span class="sxs-lookup"><span data-stu-id="21b0a-187">In order to use the `--label-column-name` argument, you need to have a header in the dataset file and `--has-header` set to `true` (which is by default).</span></span>

----------------------------------------------------------

<span data-ttu-id="21b0a-188">`--max-exploration-time | -x`řetezce</span><span class="sxs-lookup"><span data-stu-id="21b0a-188">`--max-exploration-time | -x` (string)</span></span>

<span data-ttu-id="21b0a-189">Ve výchozím nastavení je maximální doba průzkumu 30 minut.</span><span class="sxs-lookup"><span data-stu-id="21b0a-189">By default, the maximum exploration time is 30 minutes.</span></span>

<span data-ttu-id="21b0a-190">Tento argument nastaví maximální dobu (v sekundách), po kterou má proces prozkoumat více školitelů a konfigurací.</span><span class="sxs-lookup"><span data-stu-id="21b0a-190">This argument sets the maximum time (in seconds) for the process to explore multiple trainers and configurations.</span></span> <span data-ttu-id="21b0a-191">Nakonfigurovaný čas může být překročen, pokud je zadaný čas příliš krátký (řekněme 2 sekundy) pro jednu iteraci.</span><span class="sxs-lookup"><span data-stu-id="21b0a-191">The configured time may be exceeded if the provided time is too short (say 2 seconds) for a single iteration.</span></span> <span data-ttu-id="21b0a-192">V tomto případě je skutečný čas potřebný čas k vytvoření jedné konfigurace modelu v rámci jedné iterace.</span><span class="sxs-lookup"><span data-stu-id="21b0a-192">In this case, the actual time is the required time to produce one model configuration in a single iteration.</span></span>

<span data-ttu-id="21b0a-193">Čas potřebný pro iterace se může lišit v závislosti na velikosti datové sady.</span><span class="sxs-lookup"><span data-stu-id="21b0a-193">The needed time for iterations can vary depending on the size of the dataset.</span></span>

----------------------------------------------------------

<span data-ttu-id="21b0a-194">`--cache | -c`řetezce</span><span class="sxs-lookup"><span data-stu-id="21b0a-194">`--cache | -c` (string)</span></span>

<span data-ttu-id="21b0a-195">Pokud použijete ukládání do mezipaměti, načte se celá datová sada školení v paměti.</span><span class="sxs-lookup"><span data-stu-id="21b0a-195">If you use caching, the whole training dataset will be loaded in-memory.</span></span>

<span data-ttu-id="21b0a-196">V případě malých a středně velkých datových sad může použití mezipaměti významně zlepšit výkon školení, což znamená, že doba přípravy může být kratší, než když mezipaměť nepoužíváte.</span><span class="sxs-lookup"><span data-stu-id="21b0a-196">For small and medium datasets, using cache can drastically improve the training performance, meaning the training time can be shorter than when you don't use cache.</span></span>

<span data-ttu-id="21b0a-197">U rozsáhlých datových sad ale načítání všech dat v paměti může negativně ovlivnit vzhledem k tomu, že může dojít k dostatku paměti.</span><span class="sxs-lookup"><span data-stu-id="21b0a-197">However, for large datasets, loading all the data in memory can impact negatively since you might get out of memory.</span></span> <span data-ttu-id="21b0a-198">Při školení s rozsáhlými soubory DataSet a nepoužíváte-li mezipaměť, bude ML.NET streamovat datové bloky dat z disku, když potřebuje načíst více dat během školení.</span><span class="sxs-lookup"><span data-stu-id="21b0a-198">When training with large dataset files and not using cache, ML.NET will be streaming chunks of data from the drive when it needs to load more data while training.</span></span>

<span data-ttu-id="21b0a-199">Můžete zadat následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="21b0a-199">You can specify the following values:</span></span>

<span data-ttu-id="21b0a-200">`on`: Vynutí použití mezipaměti při školení.</span><span class="sxs-lookup"><span data-stu-id="21b0a-200">`on`: Forces cache to be used when training.</span></span>
<span data-ttu-id="21b0a-201">`off`: Vynutí, aby se mezipaměť nepoužívala při výuce.</span><span class="sxs-lookup"><span data-stu-id="21b0a-201">`off`: Forces cache not to be used when training.</span></span>
<span data-ttu-id="21b0a-202">`auto`: V závislosti na heuristikách AutoML se mezipaměť použije nebo ne.</span><span class="sxs-lookup"><span data-stu-id="21b0a-202">`auto`: Depending on AutoML heuristics, the cache will be used or not.</span></span> <span data-ttu-id="21b0a-203">Malé nebo střední datové sady budou obvykle používat mezipaměť a velké datové sady nebudou používat mezipaměť, pokud použijete `auto` volbu.</span><span class="sxs-lookup"><span data-stu-id="21b0a-203">Usually, small/medium datasets will use cache and large datasets won't use cache if you use the `auto` choice.</span></span>

<span data-ttu-id="21b0a-204">Pokud `--cache` parametr nezadáte, použije se ve výchozím nastavení `auto` konfigurace mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="21b0a-204">If you don't specify the `--cache` parameter, then the cache `auto` configuration will be used by default.</span></span>

----------------------------------------------------------

<span data-ttu-id="21b0a-205">`--name | -N`řetezce</span><span class="sxs-lookup"><span data-stu-id="21b0a-205">`--name | -N` (string)</span></span>

<span data-ttu-id="21b0a-206">Název vytvořeného výstupního projektu nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="21b0a-206">The name for the created output project or solution.</span></span> <span data-ttu-id="21b0a-207">Pokud název nezadáte, použije se název `sample-{mltask}` .</span><span class="sxs-lookup"><span data-stu-id="21b0a-207">If no name is specified, the name `sample-{mltask}` is used.</span></span>

<span data-ttu-id="21b0a-208">Soubor modelu ML.NET (. Soubor ZIP) bude mít stejný název i.</span><span class="sxs-lookup"><span data-stu-id="21b0a-208">The ML.NET model file (.ZIP file) will get the same name, as well.</span></span>

----------------------------------------------------------

<span data-ttu-id="21b0a-209">`--output-path | -o`řetezce</span><span class="sxs-lookup"><span data-stu-id="21b0a-209">`--output-path | -o` (string)</span></span>

<span data-ttu-id="21b0a-210">Kořenové umístění/složka, do které se umístí vygenerovaný výstup</span><span class="sxs-lookup"><span data-stu-id="21b0a-210">Root location/folder to place the generated output.</span></span> <span data-ttu-id="21b0a-211">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="21b0a-211">The default is the current directory.</span></span>

----------------------------------------------------------

<span data-ttu-id="21b0a-212">`--verbosity | -V`řetezce</span><span class="sxs-lookup"><span data-stu-id="21b0a-212">`--verbosity | -V` (string)</span></span>

<span data-ttu-id="21b0a-213">Nastaví úroveň podrobností standardního výstupu.</span><span class="sxs-lookup"><span data-stu-id="21b0a-213">Sets the verbosity level of the standard output.</span></span>

<span data-ttu-id="21b0a-214">Povolené hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="21b0a-214">Allowed values are:</span></span>

- `q[uiet]`
- <span data-ttu-id="21b0a-215">`m[inimal]`(ve výchozím nastavení)</span><span class="sxs-lookup"><span data-stu-id="21b0a-215">`m[inimal]`  (by default)</span></span>
- <span data-ttu-id="21b0a-216">`diag[nostic]`(úroveň informací o protokolování)</span><span class="sxs-lookup"><span data-stu-id="21b0a-216">`diag[nostic]` (logging information level)</span></span>

<span data-ttu-id="21b0a-217">Ve výchozím nastavení by měl nástroj rozhraní příkazového řádku při práci zobrazit určitou minimální odezvu (minimální), jako je třeba zmínku o tom, že funguje, a pokud je to možné, kolik času zbývá nebo kolik času bylo dokončeno.</span><span class="sxs-lookup"><span data-stu-id="21b0a-217">By default, the CLI tool should show some minimum feedback (minimal) when working, such as mentioning that it is working and if possible how much time is left or what % of the time is completed.</span></span>

----------------------------------------------------------

`-h|--help`

<span data-ttu-id="21b0a-218">Vytiskne nápovědu pro příkaz s popisem pro každý parametr příkazu.</span><span class="sxs-lookup"><span data-stu-id="21b0a-218">Prints out help for the command with a description for each command's parameter.</span></span>

----------------------------------------------------------

## <a name="see-also"></a><span data-ttu-id="21b0a-219">Viz také:</span><span class="sxs-lookup"><span data-stu-id="21b0a-219">See also</span></span>

- [<span data-ttu-id="21b0a-220">Postup instalace nástroje ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="21b0a-220">How to install the ML.NET CLI tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="21b0a-221">Automatizace školení modelů pomocí rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="21b0a-221">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="21b0a-222">Kurz: Automatické generování binárního klasifikátoru pomocí rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="21b0a-222">Tutorial: Auto generate a binary classifier using the ML.NET CLI</span></span>](../tutorials/mlnet-cli.md)
- [<span data-ttu-id="21b0a-223">Telemetrie v ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="21b0a-223">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
